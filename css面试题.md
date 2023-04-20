## 上中下左中右自适应布局

**方案1：** flex布局

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
         *{
            margin: 0;
            padding: 0;
        }
        body{
            display: flex;
            flex-direction: column;
            height: 100vh; /*这一行很关键*/
        }
        .top{
            background-color: antiquewhite;
            height: 100px;
        }
        .main{
            flex: 1 1 auto;
            background-color: violet;
            display: flex;
        }
        .left{
            background-color: aqua;
            width: 100px;
        }
        .middle{
            background-color: aquamarine;
            flex: 1;
        }
        .right{
            background-color: azure;
            width: 100px;
        }
        .bottom{
            background-color: yellow;
            height: 50px;
        }

    </style>
</head>
<body>
    <div class="top"></div>
    <div class="main">
        <div class="left"></div>
        <div class="middle"></div>
        <div class="right"></div>
    </div>
    <div class="bottom"></div>
</body>
</html>
```

**方案二**： 浮动+vh

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
         *{
            margin: 0;
            padding: 0;
        }
        .top{
            background-color: antiquewhite;
            height: 100px;
        }
        .main{
            background-color: violet;
            height: calc(100vh - 150px);
        }
        .left{
            background-color: aqua;
            float: left;
            height: 100%;
            width: 100px;
        }
        .middle{
            background-color: aquamarine;
            height: 100%;
            padding: 0 100px;
        }
        .right{
            background-color: red;
            width: 100px;
            height: 100%;
            float: right;
        }
        .bottom{
            background-color: yellow;
            height: 50px;
        }

    </style>
</head>
<body>
    <div class="top"></div>
    <div class="main">
        <div class="left"></div>
        <div class="right"></div> <!--注意右盒子的顺序-->
        <div class="middle"></div>

    </div>
    <div class="bottom"></div>
</body>
</html>
```

**方案三**： grid布局

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
         *{
            margin: 0;
            padding: 0;
        }
        body{
            height: 100vh; /*这一行是必须的*/
            display: grid;
            grid-template-rows: 100px auto 50px;
            grid-template-columns: 100px auto 100px;
            grid-template-areas: 'top top top'
                                  'left middle right'
                                  'bottom bottom bottom';
        }
        .top{
            background-color: antiquewhite;
            grid-area: top;
        }
        .left{
            background-color: aqua;
            grid-area: left;
        }
        .middle{
            background-color: aquamarine;
            grid-area: middle;
        }
        .right{
            background-color: red;
            grid-area: right;
        }
        .bottom{
            background-color: yellow;
            grid-area: bottom;
        }

    </style>
</head>
<body>
    <div class="top"></div>
    <div class="left"></div>
    <div class="right"></div>
    <div class="middle"></div>
    <div class="bottom"></div>
</body>
</html>
```





## 实现一个宽度自适应，高度为宽度的一半的矩形

方案一：使用css新特性

```css
.box{
    width: 100%;
    aspect-ratio: 2/1; /*固定宽高比*/
}

```

方案二： 利用padding、margin使用百分比单位时，是相对于上层元素的宽度的特性

```css
.box{
    width:  100%;
    height: 0; /*高度由padding撑开，所以这里需要设置为0*/
    padding-top: 50%;
}
```
