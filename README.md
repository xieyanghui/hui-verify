#hui-verify
jquery验证插件

依赖jquery

可input单独验证 也可form验证 可扩展

支持AMD CMD加载

使用方法

单独input验证

    verify.verifyInput('one',{
        check:['noNull','noSpechars'],//验证列表
        name:'用户名',//输出默认消息时的名称
        method:'input propertychange blur',//触发方法 默认是blur
        megs:{noNull:'重要的东西不能为空',noSpechars:'只能用E文'},
        location:'err'          //要显示元素的ID/或选择器
    //            location:function(){      //相对元素的位置
    //                return $(this).nextAll('div');
    //            }
    });



form集中验证


    verify.verifyForm('testForm',{
            //验证列表
            one: {
                check: ['noSpechars'],//验证列表
                name: '1'//输出默认消息时的名称
            },
            two: {
                check: ['null', {'length':[3,5]}],//验证列表
                name: '2',//输出默认消息时的名称
                location:""  //覆盖全局的位置
            },
            three: {
                check: ['noNull', 'phone'],//验证列表
                name: '3',//输出默认消息时的名称
                method:'blur'//覆盖全局事件
            }
        }, {
            //异步提交
            'success':function(){
                console.log('提交后回调函数');
            },
            'before':function(){
                console.log('提交前执行');
            }
        },
        'err',//全局location输出
        'input'//全局事件
        );

内置check

phone `电话号码验证`

noSczw `特殊字符除去中文验证`

money   `货币验证`

email  `邮件验证`

regExp(re,megs) `正则验证`

    re 正则表达式 ，megs 没通过的错误信息

contrast(input) `对比同form下德其他`

    input 同form下其他的input name

ajax(url)  `Ajax 验证 发送{formID.inputName} 给服务端验证 返回 json数据，name名字 ，isNull是否存在`

    url 服务端URL

length(min,max) `字符长度验证`

    min 最短长度  max最长长度可选

null `空验证 只要有验证就会验证noNull 有些的可以为空需要手动调用`

noNull `不为空验证  只有没有 null 就会自动调用`












