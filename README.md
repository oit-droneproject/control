# DJITelloPy
OITドローンプロジェクトのサイトです．
DJITelloPyのライブリーを使用してTelloを操作しましょう．
## pipでインストール
以下のコマンドでDJITelloPyをインストールすることができます．

DJItelloPyのページ
[DJItelloPy](https://github.com/damiafuentes/DJITelloPy)
```bash
pip install djitellopy
```
## 離陸と着陸
### tello_sample01.py
以下のコードは，Telloドローンを接続し，離陸させ，着陸させ，最後に通信を終了する基本的な流れを示します．

それぞれのメソッドを使ってTelloの動きを確認しましょう．
```python
from djitellopy import Tello

tello = Tello()
tello.connect() #Telloに通信を開始
tello.takeoff() #離陸
tello.land()    #着率
tello.end()     #通信終了
```


## Getter
### tello_sample02.py
このコードは，Telloの状態を知ることができるコードです．
バッテリーの残量を知ることができるメソッドもあります．
状態を知ることができる代表的なメソッドだけを記載します．
Telloの状態を確認しましょう．

```python
from djitellopy import Tello
import time

tello = Tello()

tello.connect()
print(f"Battery: {tello.get_battery()}%")
tello.takeoff()

print(f"flight_time:{tello.get_flight_time()}s")
print(f"Tof:{tello.get_distance_tof()}cm")
print(f"current_state:{tello.get_current_state()}")

tello.land()
tello.end()
```

## 上昇と下降
### tello_sample03.py
以下のコードはTelloを上昇と下降させるためのコードです．それぞれメソッドの引数はセンチメートルです．
#### move_up(self, x),move_down(self, x)
$20 \leq  x \leq 500$
```python
from djitellopy import Tello

tello = Tello()

tello.connect()
print(f"Battery: {tello.get_battery()}%")
tello.takeoff()

tello.move_up(50)        #50cm上昇
tello.move_down(50)      #50cm下降

tello.land()
tello.end()
```


##  前進，後進，左右移動
### tello_sample04.py
次のコードは，Telloを前進，後進，左，右に移動させるためのコードです．それぞれのメソッドの引数はセンチメートルです．
それぞれのメソッドを使ってTelloの動きを確認しましょう．
#### move_forward(self, x),move_back(self, x),move_left(self, x),move_right(self, x)
$20 \leq  x \leq 500$
```python
from djitellopy import Tello

tello = Tello()

tello.connect()
print(f"Battery: {tello.get_battery()}%")
tello.takeoff()

tello.move_left(50)    #50cm 左に並行移動
tello.move_right(50)   #50cm 右に並行移動
tello.move_forward(50) #50cm 前進
tello.move_back(50)    #50cm 後進

tello.land()
tello.end()
```


## 旋回
### tello_sample05.py
次のコードはTelloを旋回させるためのコードである．rotate_clockwiseは時計回りにTelloを旋回させるメソッドです．
メソッドの引数は角度を示す．
それぞれのメソッドを使ってTelloの動きを確認しましょう．
#### rotate_clockwise(self, x)
 $1 \leq  x \leq 360$
```python
from djitellopy import Tello
import time

tello = Tello()

tello.connect()
print(f"Battery: {tello.get_battery()}%")
tello.takeoff()


tello.rotate_clockwise(90)          #時計回りに90度
tello.rotate_counter_clockwise(90)  #反時計回りに90度

tello.land()
tello.end()
```


## ラジオコントロール
### tello_sample06.py
次のコードはTelloを上下左右旋回させるためのコードである．それぞれの引数はスピードを表す。
それぞれのメソッドを使ってTelloの動きを確認しましょう．
#### send_rc_control(left_right_velocity, forward_backward_velocity, up_down_velocity, yaw_velocity)
 $-100 \leq  left_right_velocity \leq 100$
 $-100 \leq  forward_backward_velocity \leq 100$
 $-100 \leq  up_down_velocity \leq 100$
 $-100 \leq  yaw_velocity \leq 100$
```python
from djitellopy import Tello
import time

tello = Tello()

tello.connect()
print(f"Battery: {tello.get_battery()}%")
tello.takeoff()


tello.send_rc_control(20,20,20,20)
tello.send_rc_control(-20,-20,-20,-20)

tello.land()
tello.end()
```


## 課題
1. 水平方向に１辺の長さが50cmの正方形をTelloで描きましょう！
2. 垂直方向に1辺の長さが50cmの正方形をTelloで描きましょう！
