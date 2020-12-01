# Einen Engel fliegen lassen
## ~avatar avatar @unplugged
![FlatterEngel](https://github.com/r00b1nh00d/engelchenflieg/blob/master/FlaterEngel%20(1).gif?raw=true) <br>
Du brauchst dringend noch ein Geschenk für deine Eltern oder Größeltern? <br>
Über eine selbstgebastelte Weihnachtsdeko freuen sie sich bestimm.<br>
Eine ganz besondere Bastelei wäre so ein flatternder Engel.


## ~ @unplugged
Zum ausschneiden des Engels habe ich dir hier eine Vorlage hochgeladen. <br>
![Engel](https://github.com/r00b1nh00d/engelchenflieg/blob/master/EngelSkizze.jpg?raw=true) <br>

Für die Flügel findest du hier ebenfalls eine Vorlage. <br>
![Fluegel](https://github.com/r00b1nh00d/engelchenflieg/blob/master/FluegelSkizze.jpg?raw=true) <br>

## ~ @unplugged
Vermutlich ist dies dein erstes Projekt mit einem Servo Motor. <br>
Ein Servo Motor ist eine spezielle Art von Elektromotor, in ihm ist noch etwas Elektronik verbaut, welche die die genaue Position misst. Die meisten dieser Motoren im RC bzw. Bastelbereich lassen sich in einem Winkel von 0° bis 180° drehen und werden meistens mit ca. 4,5V bis 5V Spannung betrieben. Der Calliope läuft mit einer Spannung von 3.3V d.h. du benötigst hier unter Umstämdem die zusätzlichen Batterien für den Servo Motor. Die Skizze zeigt dir wie du den Servo Motor mit dem Calliope verbinden kannst. <br>  
![ServoAnschluss](https://github.com/r00b1nh00d/engelchenflieg/blob/master/ServoAnschluss.jpg?raw=true)

## Schritt 1
Zur Prorammierung eines Servo Motors gibt es im Breich ``||pins:Pins||`` Einen Block ``||pins: setze Winkel von Servo auf||``. Schiebe diesen am besten erstmal in die Blöcke ``||input:wenn Knopf A gedrückt||``, ``||input:wenn Knopf B gedrückt||`` und ``||input:wenn Knopf A+B gedrückt||`` Stelle nun die Winkel 0°, 90° und 180° ein und schau wie sich der Servomotor dreht wenn du die jeweiligen Tasten drückst. 

```blocks 
input.onButtonPressed(Button.A, function () {
    pins.servoWritePin(AnalogPin.P1, 0)
})
input.onButtonPressed(Button.B, function () {
    pins.servoWritePin(AnalogPin.P1, 90)
})

``` 


## Schritt 2
Um den Engel später automatisch zum flattern zu bringen kannst du eine Schleife nutzen um den Servo langsam nach und nach gewisse Winkel anfahren zu lassen oder eben einfach Abwechselnd die winkel 0° bzw. 90° anfahren lassen.


## ~ unplugged 

basic.forever(function () {
    for (let Index = 0; Index <= 90; Index++) {
        pins.servoWritePin(AnalogPin.P1, Index)
        basic.pause(10)
    }
    for (let Index = 0; Index <= 90; Index++) {
        pins.servoWritePin(AnalogPin.P1, 90 - Index)
        basic.pause(10)
    }
})
