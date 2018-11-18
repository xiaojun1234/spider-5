# spider-5
# pyquery也是一个css选择器，id是#  ，class是.
## 初始化
### 字符初始化
<pre>
html = '''
<div>
    <ul>
    <li class="item-0">first item</li>
    <li class="item-1"><a href="link2.html">second item</a></li>
    <li class="item-0 active"><a href="link3.html"><span class="bold">third item</span></a></li>
    <li class="item-1 active"><a href="link4.html">fourth item</a></li>
    <li class="item-0"><a href="link4.html">fifth item</a></li>
    </ul>
</div>
'''
from pyquery import PyQuery as pq
doc = pq(html)
print(doc('li'))
</pre>
### URL初始化
<pre>
from pyquery import PyQuery as pq
doc = pq(url='http://www.baidu.com')
print(doc('head'))
</pre>
### 文件初始化
<pre>
from pyquery import PyQuery as pq
doc = pq(filename='demo.html')
print(doc('li'))
</pre>
### 基本css选择器
<pre>
from pyquery import PyQuery as pq
doc = pq(html)
print(doc('#container .list li'))      /*先查id为container的，再查里边class为list的，再查list里边的li*/
</pre>
## 查找元素
### 子元素
<pre>
from pyquery import PyQuery as pq
doc = pq(html)
items = doc('.list')
print(items)
lis = items.find('li')
print(lis)
</pre>
### items.children()是直接子元素

### 父元素,一定只有一个
<pre>
from pyquery import PyQuery as pq
doc = pq(html)
items = doc('.list')
container = items.parent()
print(container)
</pre>
### 祖先元素items.parents()
<pre>
from pyquery import PyQuery as pq
doc = pq(html)
items = doc('.list')
container = items.parents()
print(container)
</pre>
### 兄弟元素
<pre>
from pyquery import PyQuery as pq
doc = pq(html)
li = doc('.list .item-0.active')
print(li.siblings('.active'))
</pre>
## 遍历
<pre>
from pyquery import PyQuery as pq
doc = pq(html)
list = doc('li').items()
for li in lis:
    print(li)
</pre>
### 获得信息
<pre>
from pyquery import PyQuery as pq
doc = pq(html)
a = doc('.list.active a')
print(a)
print(a.attr('href'))
print(a.attr.href)
</pre>
### 获取文本
<pre>
from pyquery import PyQuery  as pq
doc = pq(html)
a = doc('.list.active a')
print(a.text())
</pre>
### 获取HTML
<pre>
from pyquery import PyQuery as pq
doc = pq(html)
li = doc('.list.active')
print(li)
print(li.html())
</pre>
## dom操作
### addClass、removeClass
<pre>
from pyquery import PyQuery as pq
doc = pq(html)
li = doc('.list.active')
print(li)
li.removeClass('active')
print(li)
li.addClass('active')
print(li)
</pre>
### attr、css
<pre>
from pyquery import PyQuery as pq
doc = pq(html)
li = doc('.list.active')
print(li)
li.attr('name','link')              /*加了个name属性*/
print(li)
li.css('font-size','14px')       /*style属性*/
print(li)
</pre>
### remove
<pre>
html = '''
<div class="wrap">
    hello,world
    <p>sjdfjkhsadkfhdjkf</p>
</div>
'''
from pyquery import PyQuery as pq
doc = pq(html)
li = doc('.wrap')
print(li.text())
li.find('p').remove()
print(li.text())
</pre>
## 伪类选择器
<pre>
from puquery import PyQuery as pq
doc = pq(html)
li = doc('li:first-child')    /*选择第一个li*/
print(li)
li = doc('li:last-child')     /*选择最后一个li*/
print(li)
li = doc('li:nth-child(2)')    /*选择第二个li*/
print(li)
li = doc('li:gt(2)')           /*选择第二个后面的li*/
print(li)
li = doc('li:nth-child(2n)')      /*选择为偶数的li*/
print(li)
li = doc('li:contains(second)')      /*选择内容为‘second’的li*/
print(li)
</pre>
