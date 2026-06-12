---
title: "Getting G-Tech Pro RR to communicate with PASS software on Maverick"
date: 2011-06-24
forum: Installation &amp; Upgrades
---

### Post by orlandocarguy on 2011-06-24
Hello all,

I have a G-Tech Pro RR (the accelerometer device that you attach to a car's windshield to get performance figures like 0-60 times) that I wanted to make work on Ubuntu 10.10. The  software installed just fine, and it runs just fine through Wine. But I  had to buy a USB-to-serial adapter for it when I got it (even for  Windows), as the G-Tech only has a serial port on the back. From what I  can tell, I've downloaded the right driver for the adapter, as it comes  up in the list of connected devices when I enter lsusb into the  terminal, and I've connected to it through cu.

This is all per the following Google results: [here]("http://forums.reprap.org/read.php?12,4546") and [here]("http://ubuntuforums.org/showthread.php?t=1598647")

But I cannot get the  G-Tech device to communicate with the G-Tech software. You have to have  the right serial port settings in the software ( COM1 through COM8 ) and  I've tried them all with no luck. 

In Windows, I would just go into the Control Panel, in the list of devices, and it would show me the device with the proper COM designation in its name.

I'm still fooling around with minicom,  but I haven't learned how to use that yet.

Anyone else have any idea? This is actually the only thing holding me up from making the complete switchover to Ubuntu.

---

### Post by orlandocarguy on 2011-06-26
Anyone have any ideas?

---

### Post by orlandocarguy on 2011-06-28
I think I'm one step closer to getting this to work, but I still can't.

Some more research led me to this LaunchPad question ([link](https://answers.launchpad.net/ubuntu/+source/util-linux/+question/143750)) which is essentially the same question I'm asking. The answer at the bottom by Eliah Kagan sent me over to WineHQ ([link](http://www.winehq.org/docs/wineusr-guide/misc-things-to-configure)) which gave me the following command to rename a port as a COM port.

The link gives this command:
ln -s /dev/ttyS0 com1

[FONT=Verdana]but since the port I want to rename is /dev/ttyUSB0, I entered the command as

[/FONT]ln -s /dev/ttyUSB0 com1

[FONT=Verdana]which makes sense to me at least.

However, the only output I get is this:

[/FONT][FONT=Verdana]
[/FONT]ln -s /dev/ttyUSB0 com1
ln: creating symbolic link `com1': File exists

[FONT=Verdana]Again, I'm somewhat of an Ubuntu n00b... does that mean the port is already renamed COM1?

If so, why am I still unable to get the software to communicate with the G-Tech even when it's set to read COM1?
[/FONT][FONT=Verdana]
[/FONT]

---

### Post by orlandocarguy on 2011-06-30
Still no ideas?

---

### Post by orlandocarguy on 2011-07-16
Still could use some help here... anyone?

---

### Post by orlandocarguy on 2011-10-04
Thanks to some help from a friend and a more thorough search of the forum, I finally got the answer to my question:

[http://ubuntuforums.org/showthread.php?t=1335098](http://ubuntuforums.org/showthread.php?t=1335098)

G-Tech is communicating properly and downloading data finally!

---

