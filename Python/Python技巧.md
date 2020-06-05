# 一般
## 显示Python版本
```Python
import sys
print sys.version
```
## 检查默认编码
```Python
import sys 
sys.getfilesystemencoding() 
```
## 执行操作系统命令
Linux 上执行命令date。 
```Python
import os 
os.system('date') 
```
## 启动Photoshop
```Python
import os 
os.system('"C:\\Program Files\\Adobe\\Adobe Photoshop CC 2015\\Photoshop.exe"')
```
## 获取环境变量的值
```Python
import os 
os.environ.get('MAYA_APP_DIR')
```
## 查找当前目录
```Python
import os 
os.getcwd() 
```
## 更改当前目录
```Python
import os 
os.chdir('/home/someone/')
```
## 使用路径名
```Python
import os 
path = '/aaa/bbb/ccc.ddd' 
```
- 提取扩展名 
    ```Python
    os.path.splitext(path) 
    ```
- 提取文件名 
    ```Python
    os.path.basename(path) 
    ```
- 提取目录名称 
    ```Python
    os.path.dirname(path) 
    ```
- 目录和文件名分开 
    ```Python
    os.path.split(path) 
    ```


## 文件操作
- 复制文件
文件将文件tmp1 复制到tmp2。 
    ```Python
    import shutil 
    shutil.copyfile('tmp1', 'tmp2')
    ```
- 移动文件
如果tmp2是目录，请将tmp1移至tmp2。 
    ```Python
    import shutil 
    shutil.move('tmp1', 'tmp2')
    ```
- 重命名文件
将文件tmp1 名字改成tmp2。 
    ```Python
    import os 
    os.rename('tmp1', 'tmp2')
    ```
- 读取文件
    1. 逐行读取。
    ```Python
    f = open('test.txt', 'r')
    for line in f:
        print line
    f.close()
    ```
    2. 逐行读取。
    ```Python
    with open('test.txt', 'r') as f:
        for line in f:
            print line
    ```
    3. 直接读取
    ```Python
    with open(path,'r') as f:
        data =  f.read()
    ```
    4. 
    ```Python
    def data_read(filepath):
        fp = open(filepath, "r")
        datas = []#存储处理后的数据
        lines = fp.readlines()#读取整个文件数据
        for line in lines: 
            datas.append(line)
        fp.close()    
        return datas
    ```
## 写入文件
- tr中包含的字符串写入文件test1.txt。
    1. 
    ```Python
    str = 'test'
    f = open('test1.txt', 'w')
    f.write(str)
    f.close()
    ```
    2. 
    ```Python
    str = 'test'
    with open('test1.txt', 'w') as f:
        f.write(str)
    ```
- 将str2中包含的字符串添加到文件test1.txt中并将其写入。
    1. 
    ```Python
    str2 = 'test2'
    f = open('test1.txt', 'a')
    f.write(str2)
    f.close()
    ```
    2. 
    ```Python
    str2 = 'test2'
    with open('test1.txt', 'a') as f:
        f.write(str2)
    ```
- 将列表strs中的字符串写入文件test2.txt。
    1. 
    ```Python
    strs = ['test1\n', 'test2\n']
    f = open('test2.txt', 'w')
    f.writelines(''.join(strs))
    f.close()
    ```
    2. 
    ```Python
    strs = ['test1\n', 'test2\n']
    with open('test2.txt', 'w') as f:
        f.writelines(''.join(strs))
    ```

## 获取目录的文件名
获取目录中文件名的列表。 
```Python
import glob 
glob.glob('tmp*') 
```
```Python
import os 
os.listdir('E:/aaa/aaa') 
```

## 获取命令行参数
```Python
import sys 
sys.argv 
```
## 检查对象是否为字符串
字符串的字符串可以是Unicode，因此isinstance（）函数将检查基字符串。 
```Python
s1 = 'test' 
s2 = u'unicode' 
isinstance(s1, basestring) 
isinstance(s2, basestring) 
isinstance(s2, str) 
```
>True 
>True 
>False
## 从列表中随机选择
```Python
import random 
random.sample(range(10), 5) 
```
>[2、4、6、3、8] 
```Python
list1 = ['aaa', 'bbb', 'ccc', 5, 10, 20] 
random.sample(list1, 3)
``` 
>['aaa'，5，20]
## 执行时间测量
```Python
import timeit 
timeit.Timer('range(10)').timeit() 
``` 
## 查找对象的类型
```Python
n = 3 
type(n) 
``` 

## 在不使用if语句的情况下截断除范围外的其他内容
```Python
x = max(x, 0) 
x = min(x, 3)
```
## 从列表中删除相同的元素
```Python
list1 = [1, 2, 3, 4, 5, 3, 2] 
list2 = list(set(list1)) 
```
## 带循环计数器的过程清单
```Python
list1=['a', 'b', 'c']
for i, s in enumerate(list1):
   print i,s
```
>0 a
>1 b
>2 c
## 通过合并两个列表进行处理
```Python
list1=[1, 2, 3]
list2=['a', 'b', 'c']
for n, s in zip(list1, list2):
    print n,s
```
>1 a
>2 b
>3 c
## 连接嵌套列表
```Python
m = [[1, 2, 3], [4, 5, 6], [7, 8, 9]] 
sum(m, []) 
```
>[1、2、3、4、5、6、7、8、9] 
```Python
reduce(lambda x, y: x + y, m, []) 
```
>[1、2、3、4、5、6、7、8、9] 

对于任何列表
```Python
def flatten(l):
    if isinstance(l, list):
        return reduce(lambda x, y: x + flatten(y), l, [])
    else:
        return [l]
flatten([[1, 2], [3, [4, 5]], [6, [[7, 8], 9]]]) 
```
>[1, 2, 3, 4, 5, 6, 7, 8, 9]

## 轮数
```Python
round(1.5) 
round(0.3)
``` 
## 求平均值
```Python
a = [1, 2, 3, 4, 5] 
sum(a) 
sum(a)/len(a) 
```
## 捕获shell命令输出
```Python
import commands 
commands.getoutput('date') 
```
windows
```Python
import os 
os.system('date') 
```
## 加载并执行python脚本
```Python
execfile("./test.py")
```
## 在python脚本中执行MEL命令
```Python
import maya.mel as mel
maya.mel.eval("ls")
```
## 在MEL脚本中执行python命令
```Mel
python("maya.cmds.sphere()")
```
## 删除空白行
```Python
import re
import sys
list = []
for line in sys.stdin:
    list.append(line)
pat = re.compile("^$")
for n in list:
    if pat.match(n):
        list.remove(n)
print "".join(list)
```

```Python
import sys
import re
re.sub(r"\n+", "\n", sys.stdin.read())
```
## 空的可索引集合和副本
```Python
data = [1, 2, 3] 
empty = data[:0] 
print empty 
```
>[] 
```Python
data = (1, 2, 3) 
empty = data[:0] 
print empty 
```
>() 
```Python
data = 'abcde' 
empty = data[:0] 
print empty 
```
## 检查字符串是否仅是数字
```Python
str1 = '123' 
str1.isdigit() 
```
>True 
```Python
str2 = '-123' 
str2.isdigit() 
```
>False

## 将字符串分成两个字符
`str = 'abcdefgh'`拆卸为`['ab', 'cd', 'ef', 'gh']`
- 迭代器
    ```Python
    import operator 
    iter = iter(str) 
    map(operator.add, iter, iter)
    ```
- map
    ```Python
    import operator 
    map(operator.add, str[::2], str[1::2])
    ```
- 正则
    ```Python
    import re 
    re.findall('..', str)
    ```
- other1
    ```Python
    [str[n:n+2] for n in xrange(0, len(str), 2)]
    ```
- other2
    ```Python
    [t + u for t, u in zip(str[::2], str[1::2])]
    ```

## 字符串长度
```Python
data='asdfasef'
print len(data)
```
## 启动HTTP服务器
```Python
import SimpleHTTPServer 
SimpleHTTPServer.test()
```
## HTTP服务器启动（使用CGI）
```Python
import CGIHTTPServer 
CGIHTTPServer.test()
```
## 使用itertools的二维循环
```Python
import itertools 
for i,j in itertools.product(range(3), range(2)): 
    print i,j 
```
>...
0 0 
0 1 
1 0 
1 1 
2 0 
2 1
```Python
import itertools 
for i,j in itertools.product(range(3), repeat=2): 
    print i,j 
```
>...
0 0 
0 1 
0 2 
1 0 
1 1 
1 2 
2 0 
2 1 
2 2
## 使用IterTools进行3D循环
```Python
import itertools 
for i,j,k in itertools.product(range(4), range(3), range(2)): 
    print i,j,k 
```
>...
0 0 0 
0 0 1 
0 1 0 
0 1 1 
0 2 0 
...
```Python
for i,j,k in itertools.product(range(3), repeat=3): 
    print i,j,k 
```
>...
0 0 0 
0 0 1 
0 0 2 
0 1 0 
...
## 异常
```Python
try:
    test
except NameError:
    print 'not exist'
```
## globals()使用方法
```py
if 'test' in globals():
    print 'exist'
```
## 装饰器，用于计算功能已执行的次数
```py
def count(func):
    def infunc(*args, **kwargs):
        ret = func(*args, **kwargs)
        infunc.n += 1
        print func.__name__, infunc.n
        return ret
    infunc.n = 0
    return infunc

@count
def test1():
    pass

@count
def test2(n):
    return 2 * n
```
## 如何用字典替换if语句
有以下代码，则可以用字典替换if语句。
```py
if x == 'aaa':
    test1()
elif x == 'bbb':
    test2()
elif x == 'ccc':
    test3()
```
将该函数赋予字典的值，如下所示。
```py
d = {'aaa':test1, 'bbb':test2, 'ccc':test3}
x = 'aaa'
d[x]()
```
d [x]被test1代替，并执行test1（）。 
但是，如果字典关键字中不存在x的值，则会发生错误，在这种情况下，请使用不执行以下操作的函数do_nothing（）并使用get（）方法。　
```py
def do_nothing(*arg):
    pass

x = 'ddd'
d.get(x, do_nothing)()
```
由于d ['ddd']不存在，因此将执行do_nothing（）。
## 项目相关
- 找出当前活动项目的名称
    ```py
    maya.cmds.workspace(q=True,active=True)
    ```
- 找出当前活动项目的路径
    ```py
    maya.cmds.workspace(q=True,directory=True)
    ```
- 获取项目名称列表
    ```py
    maya.cmds.workspace(listWorkspaces=True) 
    ```
- 同时获取项目名称的目录路径时的命令 
    ```py
    maya.cmds.workspace(listFullWorkspaces=True) 
    ```
- 更改项目
    ```py
    maya.cmds.workspace('test',openWorkspace=True)
    ```
## 启动Maya后立即创建对象（Python）

>库/文档/maya/2018/scripts/userSetup.py
## 如何执行独立脚本
首先，在独立脚本的开头编写以下命令。 以下命令描述了普通的Python脚本。 编写脚本后，将通过命令执行独立脚本。
`test.py`
```py
import maya.standalone
maya.standalone.initialize( name='python' )
```
>mayapy.exe test.py

## 将mayaBinary转换为mayaAscii
test.mb（mayaBinary）转换为test.ma（mayaAscii）
mbtoma.py
```py
import maya.standalone
maya.standalone.initialize( name='python' )
import maya
maya.cmds.file('test.mb',o=True)
maya.cmds.file(rename='test.ma')
maya.cmds.file(save=True, type='mayaAscii')
```
>mayapy.exe mbtoma.py
## 执行批处理渲染的独立脚本（mayaSoftware）
```py
import maya.standalone
maya.standalone.initialize( name='python' )
import maya
maya.cmds.file('test.mb',open=True)
maya.cmds.render(batch=True)
```
## 使用mentalray批量渲染
```py
maya.cmds.Mayatomr(render=True)
```
## 检查渲染器的类型
由currentRenderer属性defaultRenderGlobals节点可以确定渲染器组在渲染设置的类型。
```py
renderer = maya.cmds.getAttr("defaultRenderGlobals.currentRenderer")
if renderer == "mentalRay":
    maya.cmds.Mayatomr(render=True)
elif renderer == "mayaSoftware":
    maya.cmds.render(b=True)
elif renderer == "mayaHardware":
    maya.cmds.hwRender()
elif renderer == "mayaVector":
    maya.cmds.vectorize()
```
## 更改图像格式并执行批量渲染
```py
maya.cmds.setAttr("defaultRenderGlobals.imageFormat",19) 
```
## 更改为动画设置并执行批渲染
以文件名格式名称。####。ext渲染1至60帧的命令如下。
```py
maya.cmds.setAttr("defaultRenderGlobals.animation",1)
maya.cmds.setAttr("defaultRenderGlobals.putFrameBeforeExt",1)
maya.cmds.setAttr("defaultRenderGlobals.periodInExt",1)
val = maya.cmds.getAttr("defaultRenderGlobals.outFormatControl")
if val is 1:
    maya.cmds.setAttr("defaultRenderGlobals.outFormatControl",0)
maya.cmds.setAttr("defaultRenderGlobals.extensionPadding",4)
maya.cmds.setAttr("defaultRenderGlobals.startFrame",1)
maya.cmds.setAttr("defaultRenderGlobals.endFrame",60)
```
## 加载插件
```py
try:
	maya.cmds.pluginInfo('myPlugin', q=True, n=True)
except:
	maya.cmds.loadPlugin('c:/home/abe/python/Plugin.py')
```
## 外部MEL命令执行
1. 使用名称rmc.py创建以下Python脚本
    ```py
    import socket
    import sys

    sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    sock.connect(('localhost', 8888)) 

    com = sys.stdin.read()
    com = com.replace('\n', '')
    sock.send(com)
    ```
2. 在Maya中运行以下MEL命令 
    ```mel
    commandPort -n ":8888";
    ```
3. 从命令行运行以下命令 
    >echo sphere | python rmc.py 

    如果未安装Python，请mayapy运行。
4. 在Maya场景中创建的NURBS球体
5. 执行MEL脚本 
    - Linux Shell时
        >cat test.mel | python rmc.py 
    - 对于Windows命令提示符
        >type test.mel | python rmc.py 

    python如果命令不存在 mayapy，请使用命令等。

localhost您也可以将 rmc.py中的地址更改为另一台计算机的地址。