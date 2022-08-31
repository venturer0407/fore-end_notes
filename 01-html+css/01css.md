# css盒子模型
## 优先级
## 权值叠加
## 谷歌排错
1. 哪里出错点哪里，右键检查
2. css上一行出错，下一行会受影响
3. 检查过程中，黄色感叹号表示语法错误
4. 谁没生效就是谁语法错误，都没生效就是大括号外面的有错
## Pxcook(像素大厨)
测量尺寸使用的
1. png、jpg文件用设计进行测量
2. psd文件开发模式进行测量
3. 尺子量尺寸
4. 吸管用来吸取颜色
5. 抓手用来拖动图片
## 盒子模型(做布局)
### 介绍
1. 盒子模型就是一个标签，每个标签都是一个盒子
2. 盒子构成：内容区域content、内边距区域padding、边框区域border、外边距区域margin
### 内容的宽度和高度
用来设置盒子内容区域的大小  
属性width height  
常见取值：数字+px
### border 连写形式
#### border基本属性
单个取值的连写，取值之间用空格隔开  
如：border:10px solid red;  
border:像素值 样式(点线，直线，加粗...) 颜色
快捷键：bd+tab  
样式：dashed 虚线 dotted点线  solid实线
#### border单方向设置
只给盒子的某个方向设置边框
border-方位名词
属性值：连写的取值
border-top、bottom、left、right(上、下、左、右)
单个属性：border-width、style、color(粗细、样式、颜色)
**了解即可，基本甚少用，连写可以满足**
### 盒子实际大小初级计算公式
盒子实际大小=内容大小(width/height)+border大小
**border会撑大尺寸**
### 盒子模型-新浪导航
从外到内进行书写:
1. 先宽高背景色
2. 再放内容
3. 调节内容位置
4. 调节内容细节
### 内边距padding  
padding:50px;
四个方向的内边距
padding:20px 10px 10px 0px
padding:上 右 下 左(四值)
padding:20px 10px 10px 
padding:上 左右 下(三值)
padding:20px 10px 
padding:上下 左右(两值) 
*顺时针转一圈，没有的看对面*
### 盒子实际大小终极计算公式
####  手动内减
手动计算，操作麻烦
####  自动内减
属性：box-sizing: border-box;
###  外边距margin
####  淘宝代码
*{}清楚默认样式
```html
*{
    margin:0;
    padding:0;
}
```
####  京东代码
集合形式，清楚外边距默认样式
```html
h1,body,button,dt{
    margin:0;
    padding:0;
}
```
#### 版心居中
```html
margin:0 auto;
```
#### 外边距的折叠现象
#####  合并现象
垂直布局的块级元素，上下的margin会合并**最终两者的距离为Margin的最大值**
#####  塌陷现象（外边距，**坑爹行为**）
互相嵌套的块级元素，子元素的margin-top会作用在父元素上，导致父元素下移
1. 给父元素设置border-top**不完美，本没有要求让加，多了边框**或者padding-top（分隔父子元素＋margin-top**完美解决**）
2. 给父元素设置overflow:hidden**完美解决**
3. 转换成行内块元素(子元素设置成display:inline-block)
4. 设置浮动
####  行内元素垂直内外边距
内边距padding，外边距margin的上下边距均有影响
可以用line-height来作用改变上下边距
  
#  css浮动
##  结构伪类
###  基本用法
根据元素在html中的结构关系查找元素
1. 父元素中第一个子元素**E:first-child{}**
2. 父元素中最后一个子元素**E:last-child{}**
3. 父元素中第n个子元素 **E:nth-child（n）{}**
4. 父元素中倒数第n个子元素  E:nth-last-child（n）{}
n可以是公式：2n、even偶数；2n+1、2n-1、odd奇数；-n+5找到前5个；n+5找到从第5个往后
###  伪元素
利用css创建标签，装饰性的不重要的小图
1. ::before在父元素最前加一个伪元素
2. ::after在父元素内容的最后加一个伪元素
**必须有content属性才能生效，否则伪类元素不生效**
```html
.father::before {
            content: '老鼠';
        }
        <!-- 文字必须加引号，单双均可，且必须是英文符号 -->
.father::after {
            content: '大米';
        }
```
**默认为行内元素，调整宽高不生效**
###  标准流
默认的样式规格，标准流与浮动定位配合使用才可设计成网页
## 浮动
1. 早期作用：图文环绕  
2. 现代作用：网页布局   
   
用display更改默认样式，中间出现空隙，但是用float:left;属性更改则没有空隙
###  浮动的特点
1. 浮动标签会脱离标准流，不占用标签位置（在空中漂浮）
2. 浮动元素比标准流元素高半个级别，可以覆盖标准流中的元素
3. 浮动后的元素具备行内块的特点，一行可以显示多个，可以设置宽高
4. 下一个浮动元素会再上一个后面显示，左右浮动，**浮动找浮动**
   有浮动之后，盒子无法设置居中,无法使用margin：0 auto；来作用

## css书写顺序
1. 浮动/display
2. 盒子模型 margin、border、padding、宽高背景颜色
3. 文字样式
  
##  清除浮动
清除浮动带来的影响,*父子级标签，子级标签浮动，父级没有高度，后面的标准流盒子会受影响*
**解决方案**
1. 父级标签加高度
2. 额外标签法 父元素的最后加一个块级元素，给添加的块级元素设置clear:both;**在页面中添加额外标签，使html变得复杂**
```html
  .clearfix {
            clear: both;
        }

        <div class="father">
        <div class="left"></div>
        <div class="right"></div>
        <div class="clearfix"></div>
    </div>
    <div class="son"></div>
 ```
3. 单伪元素清除法
**第一种：基本写法**
```html
.clearfix::after{
    content:'';
    display:block;
    clear:both;
}
```
**第二种：补充写法**
```html
.clearfix::after{
    content:'';
    display:block;
    clear:both;
    height:0;
    visibility:hidden;
}
```
4. 双伪元素清除法
```html
 .clearfix::before,
        .clearfix::after {
            content: '';
            display: table;
        }

        .clearfix::after {
            clear: both
        }
```
**外边距塌陷：父子标签，都是块级，子集加margin会影响父级的位置**
5. 给父元素设置overflow：hidden，**外边距塌陷和清除浮动影响均可以使用**


## 定位
### 常见使用方式
使用定位的步骤
1. **设置定位方式**
属性名：position
常见属性值:
1. 相对定位 relative:相对于之前的位置进行改变，占有原来的位置，不改变显示模式特点，**没有脱标**
2. 绝对定位 absolute：**脱标，不占位置，改变标签显示模式特点，具备了行内块特点；*子绝父相***
3. 固定定位 fixed:固定定位，**脱标，不占位置；位置改变参考浏览器窗口；具备行内块特点**
2. **设置偏移值**
水平&垂直
left、right
top、bottom
**left right都有以left为准，top bottom都有以bottom为准**
### 元素的层级关系
标准流<浮动<定位
定位先后顺序：后来者居上
z-index: ;取值越大，显示越靠上，默认值是0，**有定位z-index才能生效**
## css定位装饰
### 垂直对其方式
居中vertical-align: ;middle、top、baseline、bottom
**浏览器把行内和行内块都当作文字来处理，有基线存在，所以无法完全对齐**
#### vertical-align可以的问题
1. 文本框和表单按钮无法对齐问题
2. input和img无法对齐问题
3. div中的文本框，文本框无法贴顶问题
4. div不设高度由img标签撑开，此时img标签下面会存在额外间隙问题
5. 使用line-height让img标签垂直居中问题
### 光标类型
设置鼠标显示的样式，属性名cursor
1. default：默认值，箭头 
2. pointer：小手特效，提示用户可以点击
3. text：工字形，提示用户可以选择文字
4. move：十字光标，提示用户可以移动
### 边框圆角
border-radios：数字+px/百分比；
#### 四种类型
border-radios：10px；四个角一致
border-radios：10px 20px 40px 80px；左上，右上，右下，左下
border-radios：10px 20px；有就设置，没有跟对角线保持一致

#### 常见应用
正圆 
1. 盒子尺寸的一半
2. 取百分比50%

### 溢出部分显示模式
overflow
1. visible:默认值，部分溢出可见
2. hidden：溢出部分隐藏
3. scroll：无论是否溢出，都显示滚动条
4. auto：根据是否溢出，自动显示或隐藏滚动条
### 元素本身隐藏
#### 常见属性
1. visibility：hidden
2. display：none
**区别**
1. visibility：hidden 隐藏元素本身，并且在网页中 **占位置**
2. display：none 隐藏元素本身，并且在网页中 **不占位置**
### 透明度
属性名：opacity，**整个标签全部透明**
属性值：数字0-1
### 精灵图
小图合成大图，大图称为精灵图
小图->大图，减少服务器发送次数，加快加载速度
#### 使用步骤
1. 创建一个盒子，盒子的尺寸和小图相同
2. 通过PxCook量取小图片大小，将小图片的宽高设置给盒子
3. 将精灵图设置为盒子的背景图片 
4. 通过PxCook测量小图片左上角坐标，分别取负值设置给盒子的background-position：x y
**精灵图标签基本都用行内标签,设置背景图位置的时候用负值**
### 背景图片大小
background-size：宽度 高度；
取值：
1. 数字+px
2. 百分比：相当于当前盒子的宽高百分比
3. contain：包含，将背景图片等比例缩放，直到不会超出盒子的最大
4. cover：覆盖，将背景图片等比例缩放，直到刚好填满整个盒子没有空白
#### backgroud连写拓展
background:color image repeat position/size
background-size和background连写同时设置时，需要**注意覆盖问题** 
**解决：** 
1. 要么单独的样式写连写的下面 
2. 要么单独的样式写在连写的里面
### 文字阴影
### 盒子阴影
属性名：box-shadow
h-shadow:必须，水平偏移量，允许负值
v-shadow:必须，垂直偏移量，允许负值
blur:可选，模糊度
spread:可选，阴影扩大
color:可选，阴影颜色
inset:可选，将阴影改为内部阴影
**不是inset会报错，outset不用写**
### 过渡
属性名：transition
all:所有属性 width：只变更宽度
**过渡属性给需要过渡的元素-本身加**
## 项目前置认知
### 网页骨架
<!DOCTYPE html>
### SEO三大标签
搜索引擎优化：搜索时排名靠前
*常见方法：*
1. 竞价排名
2. 将网页制作成html后缀
3. 标签语义化，在合适的位置用合适的标签
#### 标签语义化
1. title网页标题标签
2. description：网页描述标签
3. keywords：网页关键词标签
## 项目结构搭建







   
