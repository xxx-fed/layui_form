#表单 - 页面元素


----------

参考

[http://www.layui.com/doc/element/form.html](http://www.layui.com/doc/element/form.html)


##小睹为快

![](http://img.hb.aicdn.com/f03e77934038f074bc558c2a71ec86af3207ff26606e-uPIPRF_fw658)

###html结构

	<form class="layui-form" action="">
	  <div class="layui-form-item">
	    <label class="layui-form-label">输入框</label>
	    <div class="layui-input-block">
	      <input type="text" name="title" required  lay-verify="required" placeholder="请输入标题" autocomplete="off" class="layui-input">
	    </div>
	  </div>
	  <div class="layui-form-item">
	    <label class="layui-form-label">密码框</label>
	    <div class="layui-input-inline">
	      <input type="password" name="password" required lay-verify="required" placeholder="请输入密码" autocomplete="off" class="layui-input">
	    </div>
	    <div class="layui-form-mid layui-word-aux">辅助文字</div>
	  </div>
	  <div class="layui-form-item">
	    <label class="layui-form-label">选择框</label>
	    <div class="layui-input-block">
	      <select name="city" lay-verify="required">
	        <option value=""></option>
	        <option value="0">北京</option>
	        <option value="1">上海</option>
	        <option value="2">广州</option>
	        <option value="3">深圳</option>
	        <option value="4">杭州</option>
	      </select>
	    </div>
	  </div>
	  <div class="layui-form-item">
	    <label class="layui-form-label">复选框</label>
	    <div class="layui-input-block">
	      <input type="checkbox" name="like[write]" title="写作">
	      <input type="checkbox" name="like[read]" title="阅读" checked>
	      <input type="checkbox" name="like[dai]" title="发呆">
	    </div>
	  </div>
	  <div class="layui-form-item">
	    <label class="layui-form-label">开关</label>
	    <div class="layui-input-block">
	      <input type="checkbox" name="switch" lay-skin="switch">
	    </div>
	  </div>
	  <div class="layui-form-item">
	    <label class="layui-form-label">单选框</label>
	    <div class="layui-input-block">
	      <input type="radio" name="sex" value="男" title="男">
	      <input type="radio" name="sex" value="女" title="女" checked>
	    </div>
	  </div>
	  <div class="layui-form-item layui-form-text">
	    <label class="layui-form-label">文本域</label>
	    <div class="layui-input-block">
	      <textarea name="desc" placeholder="请输入内容" class="layui-textarea"></textarea>
	    </div>
	  </div>
	  <div class="layui-form-item">
	    <div class="layui-input-block">
	      <button class="layui-btn" lay-submit lay-filter="formDemo">立即提交</button>
	      <button type="reset" class="layui-btn layui-btn-primary">重置</button>
	    </div>
	  </div>
	</form>
	 
	<script>
		//Demo
		var layui_form=require('layui_form');

	  	//监听提交
	  	layui_form.on('submit(formDemo)', function(data){
	    	layer.msg(JSON.stringify(data.field));
	    	return false;
	  	});
	</script>

UI的最终呈现得益于Form组件的全自动渲染，她将原本普通的诸如select、checkbox、radio等元素重置为你所看到的模样。

##输入框

	<input type="text" name="title" required lay-verify="required" placeholder="请输入标题" autocomplete="off" class="layui-input">   

	required：注册浏览器所规定的必填字段 
	lay-verify：注册form组件需要验证的类型 
	class="layui-input"：layui.css提供的通用CSS类 

##下拉选择框

	<select name="city" lay-verify="">
	  <option value="">请选择一个城市</option>
	  <option value="010">北京</option>
	  <option value="021">上海</option>
	  <option value="0571">杭州</option>
	</select>  

上述option的第一项主要是占个坑，让form组件预留“请选择”的提示空间，否则将会把第一项（存在value值）作为默认选中项。你可以在option的空值项中自定义文本，form组件的“请选择”将会替换成它，但请注意：不能设置value值，其它的选项value是可以随便定义的。

通过设定 selected 来设定默认选中项：

	<select name="city" lay-verify="">
	  <option value="010">北京</option>
	  <option value="021" disabled>上海（禁用效果）</option>
	  <option value="0571" selected>杭州</option>
	</select>   

你还可以通过optgroup标签给select分组：

	<select name="quiz">
	  <optgroup label="城市记忆">
	    <option value="你工作的第一个城市">你工作的第一个城市？</option>
	  </optgroup>
	  <optgroup label="学生时代">
	    <option value="你的工号">你的工号？</option>
	    <option value="你最喜欢的老师">你最喜欢的老师？</option>
	  </optgroup>
	</select>

属性selected可设定默认项 

属性disabled开启禁用，select和option标签都支持

##复选框

	<input type="checkbox" name="" title="写作" checked>
	<input type="checkbox" name="" title="发呆"> 
	<input type="checkbox" name="" title="禁用" disabled> 

	属性title可自定义文本 
	属性checked可设定默认选中

##开关

其实就是checkbox复选框的“变种”，通过设定 lay-skin="switch" 形成了开关风格

	<input type="checkbox" name="open" lay-skin="switch" checked>
	<input type="checkbox" name="close" lay-skin="switch">
	<input type="checkbox" name="close" lay-skin="switch" disabled>

	属性checked可设定默认开 
	属性disabled开启禁用

##单选框

	<input type="radio" name="sex" title="男">
	<input type="radio" name="sex" title="女" checked>
	<input type="radio" name="sex" title="中性" disabled>

	属性title可自定义文本 
	属性disabled开启禁用



##文本域

	<textarea name="" required lay-verify="required" placeholder="请输入" class="layui-textarea"></textarea>

##组装行内表单

	<div class="layui-form-item">
	 
	  <div class="layui-inline">
	    <label class="layui-form-label">范围</label>
	    <div class="layui-input-inline" style="width: 100px;">
	      <input type="text" name="price_min" placeholder="￥" autocomplete="off" class="layui-input">
	    </div>
	    <div class="layui-form-mid">-</div>
	    <div class="layui-input-inline" style="width: 100px;">
	      <input type="text" name="price_max" placeholder="￥" autocomplete="off" class="layui-input">
	    </div>
	  </div>
	  
	  <div class="layui-inline">
	    <label class="layui-form-label">密码</label>
	    <div class="layui-input-inline" style="width: 100px;">
	      <input type="password" name="" autocomplete="off" class="layui-input">
	    </div>
	  </div>
	  
	</div>

class="layui-inline"：定义外层行内 

class="layui-input-inline"：定义内层行内


##预设元素属性

事实上在使用表单时，你的一半精力可能会在元素本身上。所以我们把一些基础属性的配置恰恰安放在了标签本身上。如：

	<input type="text" lay-verify="email">
	<input type="checkbox" checked lay-skin="switch" lay-filter="encrypt" title="是否加密">
	<button lay-submit>提交</button>

上述的lay-verify、lay-skin、lay-filter、lay-submit神马的都是我们所说的预设的元素属性，他们可以使得一些交互操作交由Form模块内部、或者你来借助form提供的JS接口精确控制。目前我们可支持的属性如下表所示：

<table class="site-table">
        <thead>
          <tr>
            <th style="width: 80px;">属性名</th>
            <th style="width: 150px;">属性值</th>
            <th>用途</th>
          </tr> 
        </thead>
        <tbody>
          <tr>
            <td>title</td>
            <td>任意字符</td>
            <td>设定元素名称，一般用于checkbox、radio框</td>
          </tr>
          <tr>
            <td>lay-skin</td>
            <td>switch</td>
            <td>定义元素的风格，目前只对checkbox元素有效，可将其转变为开关样式</td>
          </tr>
          <tr>
            <td>lay-filter</td>
            <td>任意字符</td>
            <td>事件过滤器，主要用于事件的精确匹配，跟选择器是比较类似的。其实它并不私属于Form模块，它在Layui的很多基于事件的接口中都会应用到。</td>
          </tr>
          <tr>
            <td>lay-verify</td>
            <td>required（必填项）<br>phone（手机号）<br>email（邮箱）<br>url（网址）<br>number（数字）<br>date（日期）<br>identity（身份证）<br>自定义值</td>
            <td>除了我们内置的校验规则，你还可以给他设定任意的值，比如lay-verify="pass"，那么你就需要借助form.verify()方法对pass进行一个校验规则的定义</td>
          </tr>
          <tr>
            <td>lay-submit</td>
            <td>无需填写值</td>
            <td>绑定触发提交的元素，如button</td>
          </tr>
        </tbody>
      </table>

##事件监听

语法：layui_form.on('event(过滤器值)', callback);

Form模块在Layui事件机制中注册了form模块事件，所以当你使用layui.onevent()自定义模块事件时，请勿占用form名。form支持的事件如下：

<table class="site-table">
        <thead>
          <tr>
            <th>event</th>
            <th>描述</th>
          </tr> 
        </thead>
        <tbody>
          <tr>
            <td>select</td>
            <td>监听select下拉选择事件</td>
          </tr>
          <tr>
            <td>checkbox</td>
            <td>监听checkbox复选框勾选事件</td>
          </tr>
          <tr>
            <td>switch</td>
            <td>监听checkbox复选框开关事件</td>
          </tr>
          <tr>
            <td>radio</td>
            <td>监听radio单选框事件</td>
          </tr>
          <tr>
            <td>submit</td>
            <td>监听表单提交事件</td>
          </tr>
        </tbody>
      </table>

默认情况下，事件所监听的是全部的元素，但如果你只想监听某一个元素，使用事件过滤器即可。
如：<select lay-filter="test"></select>


	layui_form.on('select(test)', function(data){
	  console.log(data);
	});
      

##监听select选择

下拉选择框被选中时触发，回调函数返回一个object参数，携带两个成员：

	layui_form.on('select(filter)', function(data){
	  console.log(data.elem); //得到select原始DOM对象
	  console.log(data.value); //得到被选中的值
	});  

请注意：如果你想监听所有的select，去掉过滤器(filter)即可。下面将不再对此进行备注。

##监听checkbox复选
复选框点击勾选时触发，回调函数返回一个object参数，携带两个成员：

	layui_form.on('checkbox(filter)', function(data){
	  console.log(data.elem); //得到checkbox原始DOM对象
	  console.log(data.elem.checked); //是否被选中，true或者false
	  console.log(data.value); //复选框value值，也可以通过data.elem.value得到
	});  

##监听switch开关
开关被点击时触发，回调函数返回一个object参数，携带两个成员： 

	layui_form.on('switch(filter)', function(data){
	  console.log(data.elem); //得到checkbox原始DOM对象
	  console.log(data.elem.checked); //开关是否开启，true或者false
	  console.log(data.value); //开关value值，也可以通过data.elem.value得到
	}); 

##监听radio单选
radio单选框被点击时触发，回调函数返回一个object参数，携带两个成员：  

	layui_form.on('radio(filter)', function(data){
	  console.log(data.elem); //得到radio原始DOM对象
	  console.log(data.value); //被点击的radio的value值
	});    

##监听submit提交
按钮点击或者表单被执行提交时触发，其中回调函数只有在验证全部通过后才会进入，回调返回三个成员：

	layui_form.on('submit(*)', function(data){
	  console.log(data.elem) //被执行事件的元素DOM对象，一般为button对象
	  console.log(data.form) //被执行提交的form对象，一般在存在form标签时才会返回
	  console.log(data.field) //当前容器的全部表单字段，名值对形式：{name: value}
	  return false; //阻止表单跳转。如果需要表单跳转，去掉这段即可。
	});
      
再次温馨提示：上述的submit(*)中的 * 号为事件过滤器的值，是在你绑定执行提交的元素时设定的，如：

	<button lay-submit lay-filter="*">提交</button>     

你可以把*号换成任意的值，如：lay-filter="go"，但监听事件时也要改成 form.on('submit(go)', callback);

##表单验证
我们对表单的验证进行了非常巧妙的支持，大多数时候你只需要在表单元素上加上lay-verify="value"即可。如：

	<input type="text" lay-verify="email"> 

上述对输入框定义了一个邮箱规则的校验，它会在Form内部完成。目前我们内置的校验支持见上文的：预设元素属性

除了内置的校验规则外，你还可以自定义验证规则，通常对于比较复杂的校验，这是非常有必要的。

	layui_form.verify({
	  username: function(value){
	    if(!new RegExp("^[a-zA-Z0-9_\u4e00-\u9fa5\\s·]+$").test(value)){
	      return '用户名不能有特殊字符';
	    }
	    if(/(^\_)|(\__)|(\_+$)/.test(value)){
	      return '用户名首尾不能出现下划线\'_\'';
	    }
	    if(/^\d+\d+\d$/.test(value)){
	      return '用户名不能全为数字';
	    }
	  }
	  
	  //我们既支持上述函数式的方式，也支持下述数组的形式
	  //数组的两个值分别代表：[正则匹配、匹配不符时的提示文字]
	  ,pass: [
	    /^[\S]{6,12}$/
	    ,'密码必须6到12位，且不能出现空格'
	  ] 
	});      

当你自定义了类似上面的验证规则后，你只需要把key赋值给输入框的 lay-verify 属性即可：

	<input type="text" lay-verify="username" placeholder="请输入用户名">
	<input type="password" lay-verify="pass" placeholder="请输入密码">


##更新渲染
有些时候，你的有些表单元素可能是动态插入的。这时Form模块的自动化渲染是会对其失效的。虽然我们没有双向绑定机制（因为我们叫经典模块化框架，咩哈哈哈哈。。。），但没事，你只需要执行 form.render(type); 方法即可。 
其中的type即表单的type类型，可选。默认对全部类型的表单进行一次更新。可局部刷新的type如下表：

<table class="site-table">
        <thead>
          <tr>
            <th>参数（type）值</th>
            <th>描述</th>
          </tr> 
        </thead>
        <tbody>
          <tr>
            <td>select</td>
            <td>刷新select选择框渲染</td>
          </tr>
          <tr>
            <td>checkbox</td>
            <td>刷新checkbox复选框（含开关）渲染</td>
          </tr>
          <tr>
            <td>radio</td>
            <td>刷新radio单选框框渲染</td>
          </tr>
        </tbody>
      </table>

	form.render(); //更新全部
	form.render('select'); //刷新select选择框渲染
	//……
      