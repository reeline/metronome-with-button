/*
Metronome sketch
The servo motor arm will swing back and forth with a tick sound coming
from a piezo buzzer.
31 August 2013
by Don Wilcher
доработан Чернышовым Андреем 16 июля 2015 года
добавлена функция кнопки для изменения частоты метронома по сигналу
*/
#include <Servo.h>
Servo myservo; // create servo object to control a servo
// a maximum of eight servo objects can be created
int switchPin = 10; // Для удобства задаем имя «switchPin» для 10 вывода
int pos = 0; // variable to store the servo position
int PBuzzer = 7; // piezo buzzer pin number
void setup()
{
pinMode(switchPin, INPUT); // Конфигурируем 10 вывод Arduino на вход. Т.к. мы будем считывать состояние кнопки.
myservo.attach(9); // attaches the servo on pin 9 to the servo object
pinMode(PBuzzer, OUTPUT);
}
void loop()
{
if (digitalRead(switchPin) == HIGH) // Если кнопка нажата, наша переменная switchPin будет иметь значение HIGH (логическую 1) и выполниться код на след. строке
{for(pos = 0; pos <=45; pos += 1) // goes from 0 degrees to 45 degrees
{ // in steps of 1 degree
if(pos==45){
digitalWrite(PBuzzer, LOW);
delay(15);
digitalWrite(PBuzzer, HIGH);
delay(15);
digitalWrite(PBuzzer, LOW);
delay(15);
}
myservo.write(pos); // go to position in variable 'pos'
delay(15); // waits 15ms to reach the position
}
for(pos = 45; pos>=1; pos-=1) // goes from 45 degrees to 0 degrees
{
if (pos==1){
digitalWrite(PBuzzer, LOW);
delay(15);
digitalWrite(PBuzzer, HIGH);
delay(15);
digitalWrite(PBuzzer, LOW);
delay(15);
}
myservo.write(pos); // go to position in variable 'pos'
delay(15); // waits 15ms to reach the position
}}
else // Если кнопка не нажата выполниться код идущий ниже.
{for(pos = 0; pos <=90; pos += 1) // goes from 0 degrees to 90 degrees
{ // in steps of 1 degree
if(pos==90){
digitalWrite(PBuzzer, LOW);
delay(30);
digitalWrite(PBuzzer, HIGH);
delay(30);
digitalWrite(PBuzzer, LOW);
delay(30);
}
myservo.write(pos); // go to position in variable 'pos'
delay(30); // waits 15ms to reach the position
}
for(pos = 90; pos>=1; pos-=1) // goes from 90 degrees to 0 degrees
{
if (pos==1){
digitalWrite(PBuzzer, LOW);
delay(30);
digitalWrite(PBuzzer, HIGH);
delay(30);
digitalWrite(PBuzzer, LOW);
delay(30);
}
myservo.write(pos); // go to position in variable 'pos'
delay(30); // waits 15ms to reach the position
}}
}
