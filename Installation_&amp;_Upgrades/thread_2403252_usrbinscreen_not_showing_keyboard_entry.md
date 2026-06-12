---
title: "usr/bin/screen not showing keyboard entry"
date: 2018-10-09
forum: Installation &amp; Upgrades
---

### Post by stepheny on 2018-10-09
I have succesfully paired and connected an Arduino to my Ubuntu 18.04 laptop via an HC05 bluetooth module. I can send data to the Arduino using the terminal opened with ```
sudo screen /dev/rfcomm0 9600
``` I know the Arduino is receiving the data because I have programmed a LED to switch on and of when a '1' or a '0' is received.

The problem I have is that I cannot see the input in the terminal opened with sudo screen /dev/rfcomm0 9600. The commands reach the Arduino but the terminal remains black with a blinking underscore character in the top left position. The blinking underscore character remains in the top left posion no matter what I input. 

I have tried /usr/bin/screen with 18.04 under both Wayland and X. And tried it with other serial ports, for instance. ```
sudo /usr/bin/screen /dev/ttyS0
``` The result is always a black screen that passes on data but doesn't show what it is sending. How can I get to see the input in this screen?

---

### Post by stepheny on 2018-10-09
I have found a part-solution that satisfies my requirements. Instead of screen I use minicom. At first minicom has exactly the same problem but you can switch local echo on with Control-A then E after which you can see what data you are sending.

According to the man page you should be able to turn screen local echo on with  > sudo /usr/bin/screen /dev/rfcomm0 echo but I haven't been able to get that to work. I will now stick with the minicom solution.

---

