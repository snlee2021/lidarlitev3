# lidarlitev3

Lidar-Lite
- DAR-Lite는 드론, 로봇 또는 무인 차량용 소형 고성능 광학 원거리 측정 센서.I2C 또는 PWM에 연결
*2016 이전은 pwm 연결하고 이후는 I2C 연결


실제로는 아래와 같이 결선
* 1번이 캐패시터(680MF)라는 것 주의 


1: 680uF 2. GND 3. SDA 4. SCL 5. +5V
​- Pixhawk를 올린 F450 Frame 에 장착


​- Pixhawk 설정

​
RNGFND_TYPE = 15 “LidarLiteV3-I2c”
RNGFND_MAX= 4000 
RNGFND_MIN_CM= 5 
실제 SETTING..

RNGFND_ADDR,0

RNGFND_FUNCTION,0

RNGFND_GAIN,0.2

RNGFND_GNDCLEAR,5

RNGFND_MAX_CM,4000

RNGFND_MIN_CM,5

RNGFND_OFFSET,0

RNGFND_ORIENT,25

RNGFND_PIN,-1

RNGFND_POS_X,0

RNGFND_POS_Y,0

RNGFND_POS_Z,0

RNGFND_PWRRNG,0

RNGFND_RMETRIC,1

RNGFND_SCALING,1

RNGFND_SETTLE,0

RNGFND_STOP_PIN,-1

RNGFND_TYPE,21

F450 frame의 정 중간(CG)에 설치가 안되어 있으면

RNGFND_POS_X와 RNGFND_POS_Y를 넣어준다.


https://blog.naver.com/jinydoggebi/221784261968

EKF2 Estimation System
(라이다로 고도값 사용하기)

1. To use it in the control loops, set AHRS_EKF_TYPE = 2

2. Enable the new EKF by setting EK2_ENABLE = 1. EKF2 will now be running in parallel and logging, etc but it will not be used by the control loops.

3. EK2_ALT_SOURCE which sensor to use as the primary altitude source

가) 0 : use barometer (default)
나) 1 : use range finder. Do not use this option unless the vehicle is being flown indoors where the ground is flat. For terrain following please see copter and plane specific terrain following instructions which do not require changing this parameter.
다) 2 : use GPS. Useful when GPS quality is very good and barometer drift could be a problem. For example if the vehicle will perform long distance missions with altitude changes of >100m.

4. EK2_RNG_USE_HGT = 70
