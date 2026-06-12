---
title: "Nvidia install on ubuntu"
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by dragonspitfire0 on 2007-09-23
this might of been mentions many time .. but i been to many sites for 4 days now and none have help , so this is only place left .

I have installed the latest ubuntu and im trying to install my Nvidia GeForce 6500 correctly.
I tryed installing from the Nvidia website and looked at many examples but notthing helps .. some how i always get stuck somewhere along the process .

i only been working with linux for 5 days now .. and i'm really interested in linux and so far this is the only thing slowing me down .. i will be very very happy if i can get this done.

if u need any further information .. plz let me know ..

---

### Post by jrib on 2007-09-23
The best and easiest way to install the nvidia drivers is to use the Restricted Drivers Manager.  You can find it in your menu:  System -> Administration -> Restricted Drivers Manager.  See [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) for more info.

---

### Post by Pumalite on 2007-09-23
There are many ways of doing it.
1.-At the terminal: sudo apt-get install nvidia-glx (or glx-new)
2.-Ctrl+alt+F1, login with your username, your password, then sudo /etc/init.d/gdm stop, then: sudo sh /path/to/driver/NVIDIA-Linux-x86 blah, blah, blah, then: sudo /etc/init.d/gdm start
3.-ENVY

---

### Post by dragonspitfire0 on 2007-09-23
Wow .. i feel so Stupid that it was that simple to install ... well it seems to be working correctly im able to use Desktop Effects before i couldnt .. but how do i change settings now .. and THANK U SO MUCH :):KS:lolflag:

---

### Post by Pumalite on 2007-09-23
Glad you got it working!

---

