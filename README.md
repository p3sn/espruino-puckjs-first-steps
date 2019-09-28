# espruino-puckjs-first-steps
my first steps with puckjs

When you received your fresh bought Puck, follow the Getting Started Guide at:
https://www.espruino.com/Quick+Start+BLE#puckjs

If you connected the Puck with web-bluetooth at https://www.espruino.com/ide/, we can enter our first piece of code. 

## Hello Blink
```
var  on = false;
setInterval(function() {
  on = !on;
  LED1.write(on);
}, 500);
```
Use the code above and press the button 'send to Espruino'. The button is in the center of your screen. You will see your Puck blinking RED. 

## Led colours
Clear all code and enter:
```
/// LED COLOURS: RED, GREEN, BLUE
var rgb = '100';
digitalWrite([LED1,LED2,LED3], parseInt(rgb).toString(10));
```
In the example 100 means: red on, green and blue off.
You can change rgb to 111 to turn red, green and blue altogether on. 
This binary number needs to be changed to decima. That's the part with parseInt and toString. 10 = decimal.

## Button and LED
If you use the button example code on https://www.espruino.com/Puck.js and combine it with LED, you can create a code example like this. On every button press, the led will change color. In the console log you will see how it works. 
```
var on = false;
var counter = 0;
setWatch(function() {
  console.log("Pressed");
  on = !on;
  console.log("On = " + on);
  var color = 0;
  if(!on) {
    console.log("Turn off LED");
  } else {
    if(counter == 7) counter = 0;
    counter++;
    color = counter;
    console.log("Binary color: " + color);
  }  
  digitalWrite([LED1,LED2,LED3], color);
}, BTN, {edge:"rising", debounce:50, repeat:true});
```

