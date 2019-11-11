# 前端开发标准规范
>
> ### 一、规范目的
> ### 二、基本规则
> ### 三、前端开发基本规范
> ### 四、Vue框架使用规范
> ### 五、Git版本管理使用规范



为提高团队协作效率，便于后台人员添加功能及前端后期优化维护，输出高质量的文档。



## 1.规范目的 ##

Web前端作为开发团队中不可或缺的一部分，需要按照相关规定进行合理编写（一部分不良习惯可能给自己和他人造成不必要的麻烦）。为提高团队协作效率，便于后台人员添加功能及前端后期优化维护，输出高质量的文档。为此根据公司前端团队的要求进行全面详细的整理。




## 2.基本规则 ##

* 符合web标准（UTF-8，HTML5），语义化html（HTML5新增要求，减少div和span等无特定语义的标签使用），结构表现行为分离（HTML、CSS、JS代码分离，不同行为代码高内聚低耦合），兼容性优良（早期IE浏览器兼容，移动端和PC端设备兼容）。

* 页面性能方面（减少请求次数，例如使用精灵图和sass语法），代码要求简洁明了有序，尽可能的减小服务器负载，保证最快的解析速度（减小repaint和reflow）。

  

## 3.前端开发基本规范 ##
### 3.1 文件命名规范 ###
* html，css，js，images，lib文件均存放至项目的目录中。如果使用相关前端框架，根据框架的文件、格式进行合理布局。

* 所有文件夹及文件使用英文命名（避免使用中文路径）。

* html文件：入口文件使用index.html。如果有对应的设计组设计原稿，需要将对应的设计稿和html文件命名一致并合理存放。

* css文件命名：后缀.css。通用common.css，初始化base.css，首页index.css，其他页面按照对应的html命名。

* Js文件命名：英文命名，后缀.js。通用common.js，初始化base.js。 其他页面按照对应的html命名。

  


### 3.2 HTML规范 ###
* 文档类型声明及编码统一为html5声明类型`<!DOCTYPE html>`(这里可以有html4的声明类型)；编码统一为`<meta charset="UTF-8">` ，书写时利用IDE实现层次分明的缩进（默认缩进4空格）。

* 非特殊情况下CSS文件放在body部分`<meta>`标签后。非特殊情况下大部分JS文件放在`<body>`标签尾部（如果需要界面未加载前执行的代码可以放在head标签后）避免行内 JS 和 CSS代码。

* 所有编码遵循xhtml标准，标签 & 属性 & 属性命名必须由小写字母及下划线数字组成。且所有标签必须闭合，包括`br(<br/>), hr(<hr />)`等，属性值必须用双引号包括。

* 引入JS库文件，文件名须包含库名称及版本号及是否为压缩版，比如：jquery-1.4.1.min.js。引入插件，文件名格式为库名称 + 插件名称，比如：jQuery.bootstrap.js。

* 充分利用无兼容性的html自身标签（比如：span、em、strong,、label等等）需要为html元素添加自定义属性的时候，首先要考虑下有没有默认的自己的合适标签去设置，如果没有，可以使用以`data-`为前缀来添加自定义属性，避免使用`data:`等其它命名方式。

* 语义化html，比如标签根据重要性用h*(同一页面只能有一个h1)，段落标记用p，列表用ul，内联元素中不可嵌套块级元素。

* 尽可能减少div嵌套

  正例：

  ```html
    <div class=”box”>
    	<p>欢迎访问xxx，您的用户名是<span>用户名</span></p>
    </div>
  ```

  反例：

  ```  html
    <div class="box">
    		<div class="welcome">
          欢迎访问xxx您的用户名是
    			<div class="name">用户名</div>
    		</div>
    <div>
  ```

* 在页面中尽量避免使用行内样式（style属性），即`style="…"`。

* 必须为含有描述性表单元素`（input，textarea）`添加`label`，

  正例：

  ```html 
  <p><label for="name">姓名：</label><input type="text" id="name" /></p>
  ```

  反例：

  ```html
  <p>姓名：<input type="text" id="name" name="name" /></p>
  ```

* 能以背景形式呈现的图片，尽量写入css样式中。

* 重要图片必须加alt属性，给重要的元素和截断的元素加上title。

* 给区块代码及重要功能，比如 `循环` 加上注释，方便后台添加功能。

* 书写页面过程中，请考虑向后扩展性，比如 `class&id `。

* 书写链接地址时，必须避免重定向，比如 `href="http://myUrl.com/"` 即须在URL地址后面加上 `"/"`

* 特殊符号使用时尽可能使用代码替代，比如 `<(<)&>(>)&空格()&»(»)）` 等等



### 3.3 CSS规范

* 编码统一为`utf-8`

* 协作开发及分工：指定前端开发人员会根据各个模块，同时根据页面相似程序，事先写好大体框架文件，再分配给其他前端人员实现内部结构、表现、行为；共用css文件由指定人员统一书写，协作开发过程中，每个页面请务必都要引入，此文件包含reset及头部样式，此文件不可随意修改。

* class与id的使用：id是唯一的并是父级的，class是可以重复的并是子级的，所以id仅使用在大的模块上，class可用在重复使用率高及子级中。id原则上都是由指定人员分发框架文件时命名的，为JS预留钩子的除外。注意：同一个ID名，在页面中只能出现一次 。

* 为JS预留钩子的命名，请以js_起始，比如 `js_hide，js_show`。

* 书写代码前，提高样式重复使用率。

* Class与id命名：大的框架命名，比如 `header/footer/wrapper/left/right` 之类的在项目中由指定人员统一命名，其它样式名称由小写英文、数字、-来组合命名，比如 `***-comment，fontred, width200` ，避免使用中文拼音，尽量使用简易的单词组合；总之，命名要语文化，简明化。

* 充分利用html自身属性及样式继承原理减少代码量 
   正例：
   
   ```html
   <ul class="list">
     <li>这儿是标题列表<span>2013-10-16</span></li>
   </ul>
   ```
   定义：
   ```css
   Ul.list li { positon:relative } 
   ul.list li span{ position:absolute; right:0 }
   ```
即可实现日期居右显示
   
* 样式表中中文字体名，请务必转码成 `unicode码`，以避免编码错误时乱码。

* 背景图片请尽可能使用精灵图技术，减小http请求，考虑到多人协作开发，精灵图按模块制作。

* 避免兼容性属性的使用，比如 `text-shadow || css3` 的部分属性

* 规避class与id命名

  * a. 通过从属写法规避

  * b. 取父级元素id/class命名部分命名

  * c. 重复使用率高的命名，请以模块代号加下划线起始，比如 `***-clear `

  * a,b两条，适用于在项目中已建好框架的页面，如要在项目中已建好框架的页面代码
  ```html
    <div id="mainnav"></div>
  ```
   按a命名法则：

  ```html
    <div id="mainnav">
      <div class="firstnav">…</div>
    </div>
  ```

  样式写法：

  ```html
    #mainnav .firstnav{…}
  ```

  按b命名法则 ：

  ```html
    <div id="mainnav">
        <div class="main-firstnav">…</div>
    </div>
  ```

  样式写法：
      ```css
   .main-firstnav{…}
      ```

* css属性写法顺序，建议遵循：a. 布局定位属性  b. 自身属性 c. 文本属性 d. 其他属性此条可根据自身习惯书写，但尽量保证同类属性写在一起，比如：

  * 布局定位属性主要包括：`display & list-style & position (相应的top, right, bottom, left) & float & clear & visibility & overflow`
  * 自身属性主要包括： `width & height & margin & padding & border & background `
  * 文本属性主要包括： `color & font & text-decoration & text-align & vertical-align & white-space & content`

* 使用png图片做图片时，要求图片格式为png-24格式，若png-24实在影响图片质量或其中半透明效果，再单独定义背景。

* 代码缩进与格式：建议单行书写，可根据自身习惯做相应优化。

* 使用table标签时（尽量避免使用table标签），请不要用 `width/height/cellspacing/cellpadding` 等table属性直接定义表现，应尽可能的利用table自身私有属性分离结构与表现，比如：`Caption、thread、tr、td、tbody、tfoot；(cellspacing 及 cellpadding的css控制方法：table{border:0; margin:0; border-collapse:collapse;} table th, table td{padding:0}， 一般情况下base.css文件中会初始化表格样式)`。

* 减少使用影响性能的属性，比如 `position:absolute || float`。

* 必须为大区块样式添加注释，小区块矢量注释。

* common.css 公共默认定义、系统结构样式、常用的间距及浮动；layout.css 表单样式、按钮、下拉框、复选框、搜索框、单选、列表； main.css  插件样式、其它页面的样式 



### 3.4 javascript书写规范 

* 文件编码统一为utf-8， 书写过程中，每行代码结束必须有分号；原则上所有功能根据xxx项目需求原生开发，以避免网上down下来的代码造成代码污染（冗余代码 || 与现有代码冲突||…） 。

* 变量命名：驼峰式命名，原生javascript变量要求是纯英文字母，首字母须小写如：iMyVue；
  jQuery变量要求首字符为"_"，其他与原生javascript规则相同，比如：_iMyVue；另外，要求变量集中声明，避免全局变量。

* 常量以及全局变量全部使用大写字母，单词之间用下划线分隔： 
  
    ```javascript
    var LIMIT_TIME, ALERT_MESSAGE;
    ```
* 方法内部变量使用多个单词组成复合词，camel命名法：
    
    ```javascript
    var arrNumList, objSubmitButton; 
    ```
* 对于代表DOM变量名，尽量使用elm、obj或elem、obj开头命名： 
    
    ```javascript
    var objSumbmitButton = document.getElementById(“btn_submit”); 
    ```
* 对于代表字符串对象的变量名，尽量使用str或str开头命名： 
    
    ```javascript
    var strmaxsizeLimit = "已超过最大限制";
    ```
* 对于代表数字的变更名，尽量使用num或num开头命名： 
    
    ```javascript
    var numMsxCount = 300; 
    ```
* 布尔值的变更名前加 is ，同理还可以为 has或can和should：
  
    ```javascript
    var isChecked, hasValue;
    ```
* 循环变量使用 i、j、k(依次类推)等名称的变量：

  ```javascript
  for (var i = 0; i< 10; i ++) {… }
  ```

* 用于返回结果变量使用ret变量：
  
      ```javascript
       function getNameStr() { 
          var ret = "alex"; 
          return ret;  
       } 
      ```
  
* 临时的使用temp或以temp开头的命名，横向、纵向坐标用x、y；捕获错误的变更用e 。
  
* 表示数组的变量在单词前加arr进行修饰：
  
      ```javascript
      var arrCity = ["北京","天津"];
      ```
  
* 避免使用否定方式的命名方式。
  
       ```javascript
      var isNotError, isNotFind;  //为非法的命名方式。
      ```
  
* 类命名：首字母大写，驼峰式命名， 如` IMyVue`。
  
* 函数命名：首字母小驼峰式命名， 如 `iMyVue()` 。
  
* 命名语义化，尽可能利用英文单词或其缩写。
  
* 尽量避免使用存在兼容性及消耗资源的方法或属性，比如 `eval() & innerText`。
  
* 后期优化中，javascript非注释类中文字符须转换成unicode编码使用，以避免编码错误时乱码显示。
  
* 代码结构明确，加注释，提高函数重用率。
  
* 注重与html分离，减小reflow， 注重性能。
  
* 所有页面引用jquery.框架和公共的文件common.js。
  
* 所有模块逻辑代码开发：
  
      形式一： 
  
      ```javascript
      var 功能名称 = function(){}
      ```
  
      形式二：
  
      ```javascript
        function 模块名称(){ 
          /*属性的定义*/ 
          url:“http://www.baidu.com”;  
        } 
        模块名称.prototype = { 
          /*方法的定义*/
          init:function(){  } 
        } 
        var obj模块名称 = new 模块名称();
        obj模块名称.init();
      ```
  
* 插件开发 ：
  
      采用闭包的形式：
  
      ```javascript
        function 插件名称(){
          /*属性的定义*/ 
          url:"http://www.baidu.com”;
        }
        插件名称.prototype = {   
          /*方法的定义*/ 
          init: function(){  }
        }
        var obj插件名称 = new 插件名称();
        obj插件名称.init(); 
      ```



### 3.4 图片规范

* 所有页面元素类图片均放入`/images`文件夹。
* 图片格式仅限于 `gif || png || jpg`。
* 命名全部用小写英文字母 || 数字 || _ 的组合，其中不得包含汉字 || 空格 || 特殊字符；尽量用易懂的词汇，便于团队其他成员理解；另，命名分头尾两部分，用下划线隔开，比如 `ad_left01.gif || btn_submit.gif`。
* 在保证视觉效果的情况下选择最小的图片格式与图片质量，以减少加载时间。
* 尽量避免使用半透明的png图片。
* 运用css sprite技术集中小的背景图或图标，减小页面 http请求，请务必在对应的sprite psd 源图中划参考线，并保存至images目录下。



### 3.5 注释规范

* Html注释 ：注释格式`<!-- 这儿是注释 -->`，只能在注释 的始末位置，不可置入注释文字区域。
* Css注释：注释格式`/*这儿是注释*/`。
* Javascript注释：单行注释使用`//这儿是单行注释`，多行注释`/*这儿是多行注释*/ `。



### 3.6 开发及测试工具约定

*  代码中利用`console`调试时，应避免使用浏览器的`console`（造成代码上线后可能造成调试输出或调试工具函数不存在而报错）。

* 代码中禁用`alert`输出打印信息。

* 页面兼容测试：IE8及以上、Firefox、Safari、Opera、Chrome、360、搜狗、QQ、UC、百度、遨游 。

  

# 4.Vue框架使用规范 #

### 4.1 强制

#### 4.1.1 组件名为多个单词

> 组件名应该始终是多个单词的，根组件 App 除外。

正例：

```javascript
export default {
  name: 'TodoItem',
  // ...
}
```

反例：

```javascript
export default {
  name: 'Todo',
  // ...
}
```

#### 4.1.2 组件数据

> 组件的 data 必须是一个函数。
> 当在组件中使用 data 属性的时候 (除了 new Vue 外的任何地方)，它的值必须是返回一个对象的函数。

正例：

```javascript
// In a .vue file
export default {
  data () {
    return {
      foo: 'bar'
    }
  }
}
// 在一个 Vue 的根实例上直接使用对象是可以的，
// 因为只存在一个这样的实例。
new Vue({
  data: {
    foo: 'bar'
  }
})
```

反例：

```javascript
export default {
  data: {
    foo: 'bar'
  }
}
```

#### 4.1.3 Prop定义

>Prop 定义应该尽量详细。
>在你提交的代码中，prop 的定义应该尽量详细，至少需要指定其类型。

正例：

```javascript
props: {
  status: String
}
// 更好的做法！
props: {
  status: {
    type: String,
    required: true,
    validator: function (value) {
      return [
        'syncing',
        'synced',
        'version-conflict',
        'error'
      ].indexOf(value) !== -1
    }
  }
}
```

反例：

```javascript
// 这样做只有开发原型系统时可以接受
props: ['status']
```

#### 4.1.4 为 v-for 设置键值

> 总是用 key 配合 v-for。
> 在组件上_总是_必须用 key 配合 v-for，以便维护内部组件及其子树的状态。甚至在元素上维护可预测的行为，比如动画中的对象固化 (object constancy)，也是一种好的做法。

正例：

```html
<ul>
  <li
    v-for="todo in todos"
    :key="todo.id"
  >
    {{ todo.text }}
  </li>
</ul>
```

反例：

```html
<ul>
  <li v-for="todo in todos">
    {{ todo.text }}
  </li>
</ul>
```

#### 4.1.5 避免 v-if 和 v-for 用在一起

> 永远不要把 v-if 和 v-for 同时用在同一个元素上。
>  一般我们在两种常见的情况下会倾向于这样做：
>
> * 为了过滤一个列表中的项目 (比如 v-for="user in users" v-if="user.isActive")。在这种情形下，请将 users 替换为一个计算属性 (比如 activeUsers)，让其返回过滤后的列表。
>
> * 为了避免渲染本应该被隐藏的列表 (比如 v-for="user in users" v-if="shouldShowUsers")。这种情形下，请将 v-if 移动至容器元素上 (比如 ul, ol)。

正例：

```html
<ul v-if="shouldShowUsers">
  <li
    v-for="user in users"
    :key="user.id"
  >
    {{ user.name }}
  </li>
</ul>
```

反例：

```html
<ul>
  <li
    v-for="user in users"
    v-if="shouldShowUsers"
    :key="user.id"
  >
    {{ user.name }}
  </li>
</ul>
```

#### 4.1.6 为组件样式设置作用域

> 对于应用来说，顶级 App 组件和布局组件中的样式可以是全局的，但是其它所有组件都应该是有作用域的。这条规则只和单文件组件有关。你不一定要使用 scoped 特性。设置作用域也可以通过 CSS Modules，那是一个基于 class 的类似 BEM 的策略，当然你也可以使用其它的库或约定。
>
> ###### 不管怎样，对于组件库，我们应该更倾向于选用基于 class 的策略而不是 scoped 特性。
>
> 这让覆写内部样式更容易：使用了常人可理解的 class 名称且没有太高的选择器优先级，而且不太会导致冲突。

正例：

```html
<template>
  <button class="c-Button c-Button--close">X</button>
</template>

<!-- 使用 BEM 约定 -->
<style>
.c-Button {
  border: none;
  border-radius: 2px;
}

.c-Button--close {
  background-color: red;
}
</style>
```

反例：

```html
<template>
  <button class="btn btn-close">X</button>
</template>

<style>
.btn-close {
  background-color: red;
}
</style>

<template>
  <button class="button button-close">X</button>
</template>

<!-- 使用 `scoped` 特性 -->
<style scoped>
.button {
  border: none;
  border-radius: 2px;
}

.button-close {
  background-color: red;
}
</style>
```



### 4.2 强烈推荐（增强可读性）

#### 4.2.1 组件文件

> 只要有能够拼接文件的构建系统，就把每个组件单独分成文件。
> 当你需要编辑一个组件或查阅一个组件的用法时，可以更快速的找到它。

正例：

```javascript
components/
|- TodoList.vue
|- TodoItem.vue
```

反例：

```javascript
Vue.component('TodoList', {
  // ...
})

Vue.component('TodoItem', {
  // ...
})
```

#### 4.2.2 单文件组件文件的大小写

> 单文件组件的文件名应该要么始终是单词大写开头

正例：

```javascript
components/
|- MyComponent.vue
```

反例：

```javascript
components/
|- myComponent.vue
|- mycomponent.vue
```

#### 4.2.3 基础组件名

> 应用特定样式和约定的基础组件 (也就是展示类的、无逻辑的或无状态的组件) 应该全部以一个特定的前缀开头，比如 Base、App 或 V。

正例：

```javascript
components/
|- BaseButton.vue
|- BaseTable.vue
|- BaseIcon.vue
```

反例：

```javascript
components/
|- MyButton.vue
|- VueTable.vue
|- Icon.vue
```

#### 4.2.4 单例组件名

> 只应该拥有单个活跃实例的组件应该以 The 前缀命名，以示其唯一性。
>  这不意味着组件只可用于一个单页面，而是每个页面只使用一次。这些组件永远不接受任何 prop，因为它们是为你的应用定制的，而不是它们在你的应用中的上下文。如果你发现有必要添加 prop，那就表明这实际上是一个可复用的组件，只是目前在每个页面里只使用一次。

正例：

```javascript
components/
|- TheHeading.vue
|- TheSidebar.vue
```

反例：

```javascript
components/
|- Heading.vue
|- MySidebar.vue
```

####4.2.5 紧密耦合的组件名

> 和父组件紧密耦合的子组件应该以父组件名作为前缀命名。
> 如果一个组件只在某个父组件的场景下有意义，这层关系应该体现在其名字上。因为编辑器通常会按字母顺序组织文件，所以这样做可以把相关联的文件排在一起。

正例：

```javascript
components/
|- TodoList.vue
|- TodoListItem.vue
|- TodoListItemButton.vue
components/
|- SearchSidebar.vue
|- SearchSidebarNavigation.vue
```

反例：

```javascript
components/
|- SearchSidebar.vue
|- NavigationForSearchSidebar.vue
```

#### 4.2.6 组件名中的单词顺序

> 组件名应该以高级别的 (通常是一般化描述的) 单词开头，以描述性的修饰词结尾。

正例：

```javascript
components/
|- SearchButtonClear.vue
|- SearchButtonRun.vue
|- SearchInputQuery.vue
|- SearchInputExcludeGlob.vue
|- SettingsCheckboxTerms.vue
|- SettingsCheckboxLaunchOnStartup.vue
```

反例：

```javascript
components/
|- ClearSearchButton.vue
|- ExcludeFromSearchInput.vue
|- LaunchOnStartupCheckbox.vue
|- RunSearchButton.vue
|- SearchInput.vue
|- TermsCheckbox.vue
```

#### 4.2.7 模板中的组件名大小写

> 总是 PascalCase 的，也就是当变量名和函式名称是由二个或二个以上单字连结在一起，而构成的唯一识别字时，用以增加变量和函式的可读性。

正例：

```javascript
<!-- 在单文件组件和字符串模板中 -->
<MyComponent/>
```

反例：

```javascript
<!-- 在单文件组件和字符串模板中 -->
<mycomponent/>
<!-- 在单文件组件和字符串模板中 -->
<myComponent/>
```

#### 4.2.8 完整单词的组件名

> 组件名应该倾向于完整单词而不是缩写。

正例：

```javascript
components/
|- StudentDashboardSettings.vue
|- UserProfileOptions.vue
```

反例:

```javascript
components/
|- SdSettings.vue
|- UProfOpts.vue
```

#### 4.2.9 多个特性的元素

> 多个特性的元素应该分多行撰写，每个特性一行。

正例：

```html
<img
  src="https://vuejs.org/images/logo.png"
  alt="Vue Logo"
>
<MyComponent
  foo="a"
  bar="b"
  baz="c"
/>
```

反例：

```html
<img src="https://vuejs.org/images/logo.png" alt="Vue Logo">
<MyComponent foo="a" bar="b" baz="c"/>
```

#### 4.2.10 模板中简单的表达式

> 组件模板应该只包含简单的表达式，复杂的表达式则应该重构为计算属性或方法。
> 复杂表达式会让你的模板变得不那么声明式。我们应该尽量描述应该出现的是什么，而非如何计算那个值。而且计算属性和方法使得代码可以重用。

正例：

```javascript
<!-- 在模板中 -->
{{ normalizedFullName }}
// 复杂表达式已经移入一个计算属性
computed: {
  normalizedFullName: function () {
    return this.fullName.split(' ').map(function (word) {
      return word[0].toUpperCase() + word.slice(1)
    }).join(' ')
  }
}
```

反例：

```javascript
{{
  fullName.split(' ').map(function (word) {
    return word[0].toUpperCase() + word.slice(1)
  }).join(' ')
}}
```

#### 4.2.11 简单的计算属性

正例：

```javascript
computed: {
  basePrice: function () {
    return this.manufactureCost / (1 - this.profitMargin)
  },
  discount: function () {
    return this.basePrice * (this.discountPercent || 0)
  },
  finalPrice: function () {
    return this.basePrice - this.discount
  }
}
```

反例：

```javascript
computed: {
  price: function () {
    var basePrice = this.manufactureCost / (1 - this.profitMargin)
    return (
      basePrice -
      basePrice * (this.discountPercent || 0)
    )
  }
}
```

#### 4.2.12 带引号的特性值

> 非空 HTML 特性值应该始终带引号 (单引号或双引号，选你 JS 里不用的那个)。
> 在 HTML 中不带空格的特性值是可以没有引号的，但这样做常常导致带空格的特征值被回避，导致其可读性变差。

正例：

```html
<AppSidebar :style="{ width: sidebarWidth + 'px' }">
```

反例：

```html
<AppSidebar :style={width:sidebarWidth+'px'}>
```

#### 4.2.13 缩写指令

> 都用指令缩写 (用 : 表示 v-bind: 和用 @ 表示 v-on:)

正例：

```html
<input
  @input="onInput"
  @focus="onFocus"
>
```

反例：

```html
<input
  v-bind:value="newTodoText"
  :placeholder="newTodoInstructions"
>
```

### 4.3 推荐

#### 4.3.1 单文件组件的顶级元素的顺序

> 单文件组件应该总是让<script>、<template> 和 <style> 标签的顺序保持一致。且 <style> 要放在最后，因为另外两个标签至少要有一个。

```html
<!-- ComponentA.vue -->
<template>...</template>
<script>/* ... */</script>
<style>/* ... */</style>
```

### 4.4 谨慎使用（有潜在危险的模式）

#### 4.4.1 没有在 v-if/v-if-else/v-else 中使用 key

> 如果一组 v-if + v-else 的元素类型相同，最好使用 key (比如两个 <div> 元素)。

正例：

```html
<div
  v-if="error"
  key="search-status"
>
  错误：{{ error }}
</div>
<div
  v-else
  key="search-results"
>
  {{ results }}
</div>
```

反例：

```html
<div v-if="error">
  错误：{{ error }}
</div>
<div v-else>
  {{ results }}
</div>
```

#### 4.4.2 scoped 中的元素选择器

> 元素选择器应该避免在 scoped 中出现。
> 在 scoped 样式中，类选择器比元素选择器更好，因为大量使用元素选择器是很慢的。

正例：

```html
<template>
  <button class="btn btn-close">X</button>
</template>

<style scoped>
.btn-close {
  background-color: red;
}
</style>
```

反例：

```html
<template>
  <button>X</button>
</template>

<style scoped>
button {
  background-color: red;
}
</style>
```

#### 4.4.3 隐性的父子组件通信

> 应该优先通过 prop 和事件进行父子组件之间的通信，而不是 this.$parent 或改变 prop。

正例：

```javascript
Vue.component('TodoItem', {
  props: {
    todo: {
      type: Object,
      required: true
    }
  },
  template: `
    <input
      :value="todo.text"
      @input="$emit('input', $event.target.value)"
    >
  `
})
```

反例：

```javascript
Vue.component('TodoItem', {
  props: {
    todo: {
      type: Object,
      required: true
    }
  },
  methods: {
    removeTodo () {
      var vm = this
      vm.$parent.todos = vm.$parent.todos.filter(function (todo) {
        return todo.id !== vm.todo.id
      })
    }
  },
  template: `
    <span>
      {{ todo.text }}
      <button @click="removeTodo">
        X
      </button>
    </span>
  `
})
```

#### 4.4.4 非 Flux 的全局状态管理

> 应该优先通过 Vuex 管理全局状态，而不是通过 this.$root 或一个全局事件总线。

正例：

```javascript
// store/modules/todos.js
export default {
  state: {
    list: []
  },
  mutations: {
    REMOVE_TODO (state, todoId) {
      state.list = state.list.filter(todo => todo.id !== todoId)
    }
  },
  actions: {
    removeTodo ({ commit, state }, todo) {
      commit('REMOVE_TODO', todo.id)
    }
  }
}
<!-- TodoItem.vue -->
<template>
  <span>
    {{ todo.text }}
    <button @click="removeTodo(todo)">
      X
    </button>
  </span>
</template>

<script>
import { mapActions } from 'vuex'

export default {
  props: {
    todo: {
      type: Object,
      required: true
    }
  },
  methods: mapActions(['removeTodo'])
}
</script>
```

反例：

```javascript
// main.js
new Vue({
  data: {
    todos: []
  },
  created: function () {
    this.$on('remove-todo', this.removeTodo)
  },
  methods: {
    removeTodo: function (todo) {
      var todoIdToRemove = todo.id
      this.todos = this.todos.filter(function (todo) {
        return todo.id !== todoIdToRemove
      })
    }
  }
})
```


## 5.Git版本管理使用规范 ##

#### 更新代码后提交：

> * 每日上班第一件事，更新版本库。确保提交代码之前，工作目录是最新版本的代码，如果pull之后，代码有更新，一定要重新测试之后再提交。不允许提交冲突代码。

####提交代码必须达到上线标准：

> * 提交的代码必须能够达到上限标准，不允许提交测试代码，未通过测试的代码，错误代码。控制提交频率，一个完整功能模块一次提交，每次提交的时间尽可能短，减少提交冲突出现的可能性。一次提交只解决一个问题，不能一次性提交过个功能模块的更新。

####提交时必须写明文字注释：

> * 每次提交时，需要清晰的写清本次版本代码所做的修改，要求项目组其他成员不需要详细查看代码就能够知道本次代码更新的内容。比如文案：
> * 修复bug：fix：bug描述；
> * 新增功能：add：新功能描述；
> * 功能下线：del：下线功能描述，下线原因；
> *  更能更新：update：功能描述。

#### 上线：

> 提交后的代码，需要检查是否有遗漏的文件或者代码片段未提交。
> 提交的代码，需要立即安排上线，所有上线代码必须走版本库，不允许ftp上线代码。

#### 权限：

> 未经授权，不允许私自修改他人负责项目模块的业务代码，尤其是配置文件等重要文件。
> 每次git操作，要使用自己的账户和密码，不允许窃用他人权限。

#### 分支管理：

> 主干分支只能用来发布代码使用，必须保证主干分支每个版本的代码都是可以达到上线标准的干净的代码，不许在主干分支上做开发、测试。
> 测试分支代码的主要功能是整个项目组共用功能测试以及紧急bug修复测试使用，不可长期作为开发使用，代码测试通过后，方可合并到主干分支。
> 每个项目组成员需要有自己的开发分支，用于日常开发，达到测试标准后需要合并到测试分支进行测试。
