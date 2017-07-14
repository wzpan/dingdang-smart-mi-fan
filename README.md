# dingdang-smart-mi-fan

[叮当机器人](http://github.com/wzpan/dingdang-robot) 的智米电风扇插件，可以使用叮当机器人声控智米电风扇。功能包括：

* 电源开关
* 风量调节
* 预约关机
* 自然风开关
* 摇头开关

## 依赖

* python2-miio

## 安装

先安装 python2-miio ：

``` sh
pip install python2-miio
```

之后，克隆本项目到任意目录：

``` sh
git clone https://github.com/wzpan/dingdang-smart-mi-fan.git
```

再将里头的 SmartMiFan.py 拷贝至 /home/pi/.dingdang/custom 目录。

``` sh
cp dingdang-smart-mi-fan/SmartMiFan.py /home/pi/.dingdang/custom/
```

如果没有 custom 目录，就先创建它然后再执行上面的拷贝命令：

``` sh
mkdir /home/pi/.dingdang/custom
```

> custom 目录和 contrib 目录的区别在于 custom 用于存放用户的个人的插件，而 contrib 用于存放共享插件。将这两类插件分开存放，有利于保证 contrib 可以顺利更新而不会影响 custom 里存放的用户自定义插件。

然后，确保你的智米电风扇已开机并和叮当所在的机器处于同一个局域网下。然后执行以下命令获取风扇的 `host` 和  `token`:

``` sh
miio2 discover
```

最后在 /home/pi/.dingdang/profile.yml 中添加如下配置：

``` yml
# 智米风扇
smart_mi_fan:
    host: "192.168.1.106"
    token: "32e9af2050bc9d6f599c061733effee0"
    angle: 60  # 摇头的角度范围。可选值为 30/60/90/120
```

完成后重启叮当即可使用本插件。

## 指令列表

| 指令 | 相同指令  |  用途 |
| ---- | -------- | ----- |
| 打开风扇 | 启动风扇 | 打开风扇 |
| 关闭风扇 | - | 关闭风扇 |
| 开启自然风 | 启动自然风    | 切换到自然风模式 |
| 关闭自然风 | 关闭自然风    | 切换到普通模式 |
| 开始摇头 | 开启摇头    | 开始摇头 |
| 停止摇头 | 结束摇头，关闭摇头    | 结束摇头 |
| 加大风速 | 加快风速，加大风量，加大风力    | 加大风扇转速 |
| 减少风速 | 减慢风速，减少风量，减小风力    | 降低风扇转速 |
| $num $unit 后关闭风扇 | $num 是数字，$unit 可以是秒/分钟/小时  | 预约关机 |



