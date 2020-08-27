Below are the add-ons that are used:

1. MATLAB Support Package for Arduino Hardware
2. Simulink Support Package for Arduino Hardware
3. Arduino_Engineering_Kit_Hardware_Support
4. Simulink library for Arduino Liquid Crystal Display

Below data indicates the number of digital pin of the Arduino board and to which part of the circuit it is beign connected to (for ex: D1 indicates digital port 1 of
the arduino borad):

D0 is not used
D1 is not used
D2 is connected to the 7th pin of LCD display (DB7)
D3 is connected to the 6th pin of LCD display (DB6)
D4 is connected to the 5th pin of LCD display (DB5)
D5 is connected to the 4th pin of LCD display (DB4)
D6 is connected to the 3rd port of L293D DC motor driver
D7 is connected to the 6th port of L293D DC motor driver
D8 is connected to the trig port of Ultrasoninc sensor
D9 is connected to the echo port of Ultrasonic sensor
D10 is connected to the servo motor
D11 is connected to E of the LCD display
D12 is connected to RS of the LCD display
D13 is connected to the red LED

This particular simulink file has two function blocks namely obstacle detection function (od) and LCD display fucntion (lcd_fn) which ensures the functionality
of the obstacle avoiding robot.

1.od:

The input description is as follows:
•flag_in: It reads the value from the ‘flag’ data store read block.
•rand_in: It reads the value from the ‘random’ data store write read block and has a random value between -1 to 1.
•usonic: It gets value from the Arduino ultrasonic sensor and the value is in accordance with the distance between sensor and the obstacle.
•rand: It gets input from the uniform random number block with a sample time of 0.3 seconds.

The output description is as follows:
•flag_out: writes to the ‘flag’ data store write block
•rand_out: writes to the ‘random’ data store write block.
•dist: Shows distance between obstacle and the ultrasonic sensor inside simulink's display block 
•dc_motor_1: output to arduino pin 6 and acts as link to turn on or off the motor.
•dc_motor_2: output to arduino pin 6 and acts as link to turn on or off the motor.
•led_on: it is connected to arduino pin 13 and turns on when obstacle is detected.
•lcd_alert: This acts as an input to led_fn and when turned on, ALERT message gets displayed over LCD.
•servo_on: Used to turn the servo motor either to left or right depending upon the random number generated that gets generated.
•turn: It is used to display either the string ‘TURNING RIGHT’ or ‘TURNING LEFT’ or the rpm value(300) on the LCD.
•lcd_rpm: Displays the string ‘RPM’ in the LCD display.

2. lcd_fn
 
It controls the messages that gets displaced on the LCD. There are two lines and charecters are configured in such a way that it gives "od" function to control 
according to the situation, i.e, whether obstacle is detected or not.
•lcd_alert: Displays the string ‘ALERT’ when it is enabled
•lcd_rpm: Enables the string ‘RPM’ on LCD display when its value is 1.
•turn: It is used to display either the string ‘TURNING RIGHT’ (when turn=1) or ‘TURNING LEFT’(when turn=0) or the rpm value(300)(when turn=2) on the LCD.
The value of it is decided by "od" function.




