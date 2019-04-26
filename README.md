## 效果 && demo介绍

------

### 效果图：

![tool-editor](http://index.jsx6.com/image/three_periodictable.gif)

### 说明：

> * 利用 three.js 元素周期表
> * 自动旋转
> * 自动切换模式
> * 签到&&投票卡片动画


**模拟签到&&投票**
```
    // 模拟推送数据
    var s = setInterval(function () {
        // get animate
        var rand_in = parseInt(Math.random() * _in.length, 10);
        var rand_out = parseInt(Math.random() * _out.length, 10);

        $('.show_info').show();
        $('.show_info').addClass(_in[rand_in]);

        if (CurPersonNum >= table.length) {
            CurPersonNum = 0;
        }
        setTimeout(function () {

            $('.show_info').removeClass(_in[rand_in]);

            // 更改展示的图片
            var img = document.getElementsByClassName('element')[CurPersonNum].getElementsByTagName('img')[0];
            img.setAttribute('src', 'touxiang.jpg');
            document.getElementsByClassName('element')[CurPersonNum].getElementsByClassName('details')[0].innerHTML = CurPersonNum;
            ++CurPersonNum;

            //卡片关闭效果
            setTimeout(function () {
                $('.show_info').addClass(_out[rand_out]);
                setTimeout(function () {
                    $('.show_info').removeClass(_out[rand_out]);
                    $('.show_info').hide();
                }, 1000);
            }, 1500);

        }, 1000);
    }, 4500);
```

**卡片总数初始化**
```
    for (var i = 0; i < 120; i++) {
            table.push({
                'name': i,
                'p_x': i % 15 + 1,
                'p_y': parseInt(i / 15) + 1,
                'image': ''
            })
        }
```


**欲知更多，请看源码🔍**
