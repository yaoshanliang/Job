##WEB前端工程师笔试题

姓名:姚善良&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&nbsp;       学校:苏州大学&emsp;&emsp;&emsp;&emsp;&nbsp;        专业:软件工程 &emsp;&emsp;&emsp;&emsp;&emsp;日期:2015年4月10日

手机:18896581232&emsp;&emsp;&emsp; 邮箱:i@iat.net.cn&emsp;&emsp;&emsp; 主页:[http://iat.net.cn](http://iat.net.cn)

1、请写出10种以上标准HTML（不包含HTML5）文档中的标签，并且注明其语义。
<table width = "80%">
<tr>
<th>标签</th>
<th>语义</th>
</tr>

<tr>
<td>&lt;a&gt;&lt;/a&gt;</td>
<td>超链接</td>
</tr>

<tr>
<td>&lt;h1&gt;&lt;/h1&gt;~&lt;h6&gt;&lt;/h6&gt;</td>
<td>标题，由大到小</td>
</tr>

<tr>
<td>&lt;blockquote&gt;&lt;/blockquote&gt;</td>
<td>引用段落</td>
</tr>

<tr>
<td>&lt;address&gt;&lt;/address&gt;</td>
<td>定义地址</td>
</tr>

<tr>
<td>&lt;b&gt;&lt;/b&gt;</td>
<td>粗体</td>
</tr>

<tr>
<td>&lt;br /&gt;</td>
<td>换行</td>
</tr>

<tr>
<td>&lt;meta&gt;</td>
<td>源信息标签</td>
</tr>

<tr>
<td>&lt;center&gt;&lt;/center&gt;</td>
<td>居中</td>
</tr>

<tr>
<td>&lt;pre&gt;&lt;/pre&gt;</td>
<td>预格式文本</td>
</tr>

<tr>
<td>&lt;font&gt;</td>
<td>设置字体</td>
</tr>


<tr>
<td>&lt;img&gt;</td>
<td>插入图片</td>
</tr>


</table>
2、请尽可能实现以下效果。要求的HTML结构为`<div id=”box”></div>`。（宽度、高度、倾斜角度自定，背景颜色为#6f9518，整个图形定位于屏幕的正中央。）

![](http://i.imgur.com/v37Lk3o.png)

	<!DOCTYPE HTML>
	<html>
		<head></head>
		<body>
			<style type="text/css">
				body
				{ 
					text-align:center
				} 
				#box
				{
					margin: 0 auto;	
					width: 100px;
					height: 60px;
					background: #6f9518;
					display:inline-block;
					-webkit-transform:skew(-30deg);
				}
			</style>
			<div id="box">
			</div>
		</body>
	</html>


3、请尽可能实现以下样式及功能的表单，表单提交的方法为post，并且验证Email跟password是否为空。
（要求：表单整体宽度为500px，内边距为10px，输入框未选中时边框颜色为#ccc，被选中时边框为#28a0d8且# 41bfe5阴影。）
![](http://i.imgur.com/1WgWU8y.png)

* 法一：引用jQuery

		<!DOCTYPE HTML>
		<html>
			<head>
				<link rel="stylesheet" href="//netdna.bootstrapcdn.com/bootstrap/3.0.3/css/bootstrap.min.css">
			</head>
			<body>
				<style type="text/css">
					#form
					{
						width:500px;
						padding:10px;
						border:1px solid #ccc;
					}
				</style>
	
				<div id="form">
					<form role="form">
						<div class="form-group">
							<label for="exampleInputEmail1">Email address</label>
							<input type="email" class="form-control" id="exampleInputEmail1" placeholder="Enter email" required>
						</div>
						<div class="form-group">
							<label for="exampleInputPassword1">Password</label>
							<input type="password" class="form-control" id="exampleInputPassword1" placeholder="Password" required>
						</div>
						<div class="form-group">
							<label for="exampleInputFile">File input</label>
							<input type="file" id="exampleInputFile">
							<p class="help-block">Example block-level help text here.</p>
						</div>
						<div class="checkbox">
							<label><input type="checkbox"> Check me out</label>
						</div>
						<button type="submit" class="btn btn-default">Submit</button>
					</form>
				</div>
			</body>
		</html>	

* 法二：自定义CSS

		<!DOCTYPE HTML>
		<html>
			<head></head>
			<body>
				<style type="text/css">
					.container
					{
						width:500px;
						padding:10px;
						border:1px solid #ccc;
						
					}
					.input-text
					{
						width: 100%;
						height: 20px;
						border-radius:3px;
					}
					.normal
					{
						
					}
					.focus
					{
						border:1px solid #28a0d8;
						box-shadow: 1px 1px 1px #41bfe5;
					}
				</style>
				<div class="container">
					<form name="form" method="post">
						<p>
							<label><b>Email address</b></label><br />
							<input type="email" name="email" class="input-text normal" placeholder="Enter email" required></p>
						<p>
							<label><b>Password</b></label><br />
							<input type="password" name="password" class="input-text normal" placeholder="Password" required></p>
						<p>
							<label><b>File input</b></label><br />
							<input type="file"></p>
						<p>
							<input type="checkbox"> Check me out
						</p>
						<input type="submit" value="Submit">
					</form>
				</div>
				<script type="text/javascript"> 
					function focusInput(focusClass, normalClass) 
					{
						var elements = document.getElementsByTagName("input");
						for (var i = 0; i < elements.length; i++) 
						{
							if (elements[i].type == "email" || elements[i].type == "password") 
							{
		
								elements[i].onfocus = function() { this.className = focusClass; };
								elements[i].onblur = function() { this.className = normalClass||''; };
							}
						}
					}
				</script>
				<script type="text/javascript">
					window.onload = function () 
					{
						focusInput('input-text focus', 'input-text normal');
					}
				</script>
			</body>
		</html>

4、简述Jquery中的$.ajax()方法并写出AJAX返回的数据格式有哪些？

* $.ajax()为jQuery中的ajax技术，主要包括请求的地址、请求的方法、请求的参数、获取请求返回结果等过程。如下以一个ajax验证用户名的例子，讲解$.ajax方法。

		<input id = "name" type = "text" name = "name" value = "">
		<div id = "checkname"></div>

		//调用jQuery中的blur()方法，监测name的合法性
		$("#name").blur(function() {
			$.ajax({
				url : "checkname.php",//请求地址
				type : "POST",//请求方法
				data : {name : $("#name").val()},//post文本框中的值
				datatype : "text",//返回类型
				beforeSend : function() {
					//设置发送请求时触发的函数
					console.log("beforeSend");//控制台里查看请求过程
				},
				success : function(data) {
					//设置请求成功时触发的函数
					$("#checkname").html(data);
					console.log("success");
				},
				error : function() {
					//设置请求失败时触发的函数
					$("#checkname").html("异步请求失败");
					console.log("error");
				},
				complete : function() {
					//设置请求完成时触发的函数
					console.log("complete");
				},
			});
		});
		
		//异步请求的页面checkname.php中只做了一个简单的验证，判断文本框中时候包含中文：
		if (isset($_POST['name']) && $_POST['name'] != '') {
			echo preg_match("/[\x{4e00}-\x{9fa5}]+/u",$_POST['name']) ? '用户名不能包含中文' : '';
		}

* 返回的数据格式：xml、html、text、json、jsonp、script

5、请用JSON的语法介绍下自己。

	var myself = 
		{
			"names" : 
			[
				["english_name" : "iat"], 
				["chinese_name" : "姚善良"]
			],
			"school" : 
			[
				["english_name" : "Schoow University"],
				["chinese_name" : "苏州大学"]
			],
			"age" : 22,
			"telephone" : "18896581232",
			"email" : "i@iat.net.cn",
			"homepage" : "http://iat.net.cn"
		};


6、请分别写出attachEvent与addEventListener的用法，二者有何区别？

* attachEvent：
	
	attachEvent共有2个参数：element.attachEvent(type,listener);
	<table width = "80%">
		<tr><th>参数</th><th>说明</th></tr>
		<tr><td>type</td><td>事件名称</td></tr>
		<tr><td>listener</td><td>绑定的事件监听函数</td></tr>
	</table>

* addEventListener：

	addEventListener共有3个参数：element.addEventListener(type,listener,useCapture);
	<table width = "80%">
		<tr><th>参数</th><th>说明</th></tr>
		<tr><td>type</td><td>事件名称</td></tr>
		<tr><td>listener</td><td>绑定的事件监听函数</td></tr>
		<tr><td>userCapture</td><td>事件监听方式</td></tr>
	</table>
* 区别：
 * 1、 attachEvent是IE私有的，不符合W3C规范，而且在IE下，只能使用它来绑定事件，addEventListener是无效的。addEventListener是符合W3C规范的事件绑定方法，FireFox、Chrome、Safari都是用它来绑定事件。
 * 事件名称，attachEvent需要加上事件前边的"on"，比如"onclick"和"onmouseover",addEventListener不需要。

7、请为Array增加一个原型方法：该方法的功能是删除数组中的某一项n。

	Array.prototype.del = function(n) {
		if (n < 0 || n >= this.length) {
 			return ;
		}
		for (var i = n; i < this.length; i++) {
			this[i] = this[i + 1];
		}
		this.length -= 1;
	}

8、请写出至少五种移动端H5前端性能优化方法。

* 减少HTTP请求，通过合并js、CSS等方法，减少请求，提高性能。
* 预加载，对用户行为分析，可以在当前页加载下一页资源，提升速度。
* 压缩图片，对于较大的图片进行技术处理，减少大小，提高加载速度。
* 缓存，将部分可缓存的资源（如图片）缓存在本地，下次载入时直接在本地读取，减少请求网页造成的等待
* 异步加载，对于一些外部文件或者资源比较大的文件，采用异步加载的方式，加载中的时候给出动画，完全加载好再显示出来，而不是一直处于等待的状态，这样用户体验也相对较好。
