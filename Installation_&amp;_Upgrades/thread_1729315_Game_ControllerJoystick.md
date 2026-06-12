---
title: "Game Controller/Joystick"
date: 2011-04-14
forum: Installation &amp; Upgrades
---

### Post by dailyfare on 2011-04-14
I'm new to xubuntu and im having an issue installing logitech gamepad f310. I've used wine to install the software that came with the controller, to no avail...no usb controller detected. I've opened a terminal and used "sudo apt-get install jscalibrator" as i've seen in various forums and here's what happens : Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package jscalibrator

so yeah i have no idea how to proceed....i checked the software centre for xubuntu and installed joystick a set of calibration tools for joysticks and still no dice.

any suggestions?

ps. sorry if this already solved!!:D

---

### Post by alexisj on 2011-05-26
How do you solved that?

I have bought also a F310 logitech gamepad thaht doesnt work with ubuntu 11.04

(french thread: [http://forum.ubuntu-fr.org/viewtopic.php?id=507431](http://forum.ubuntu-fr.org/viewtopic.php?id=507431))

---

### Post by 0AintLifeGrand0 on 2011-08-07
I had the same problem.

This is what I did to get it working in 11.04.
- install joystick :
```
sudo apt-get install joystick
```
- Place the mode button on the bottom side of the controller in 'x' mode (so not  'd'  mode like other,older forums say)

- check if it is recognised with e.g.:
```
dmesg
```
it shoud show something like this: ```
 4-1: new full speed USB device using uhci_hcd and address 3
[ 2291.569228] Registered led device: xpad1
[ 2291.569320] input: Generic X-Box pad as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input14 
``` 

that did it for me, I can use it perfectly in zsnes now.

Hope that helps, regards

---

