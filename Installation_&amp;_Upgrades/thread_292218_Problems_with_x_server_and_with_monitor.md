---
title: "Problems with x server and with monitor"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by rionoco on 2006-11-03
hi, i try everything i can.
i can not install Ubuntu because of my monitor i think.
First i get this message:


[B]Failed to start the X server (your graphical interface).
It is likely that it is not set up correctly.

X Windows system version 7.0.0
Release Date 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0

Build Operating System: Linux ubuntu 2.6.15-23-386 #1 PREEMPT Tue
May 23 13:49:40 UTC 2006 i686

Fatal server error:
no screen found
XIO: fatal I0 error 104 (connection reset by peer) on X server ":0.0"
after 0 request (0 known processed with 0 events remaining)[/B]



Then..i have tryed the following:
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install xserver

and the response was the following:


[B]Reading package list...Done
Building dependency tree...Done
E: Couldn´t find package x
[/B]


Then i try to configure with:
sudo dpkg-reconfigure xserver-xorg

but i could get anywhere...appear the message at the end:


[B]Fatal server error:
no screen found
XIO: fatal I0 error 104 (connection reset by peer) on X server ":0.0"
after 0 request (0 known processed with 0 events remaining)[/B]


The system can´t find my screen: ViewSonic VA521

Plz help me out on this, i´m getting crazy!!

Thnx.

---

### Post by wpshooter on 2006-11-03
I don't think this has anything to do with your monitor.  It is a video card problem.

Have you tried installing from the **ALTERNATE** CD version of Ubuntu ?

---

### Post by rionoco on 2006-11-03
Thnx for responding.

I don´t have the alternative cd....i only have the Ubuntu version 6.06 LTS.

---

### Post by wpshooter on 2006-11-03
You can download it from the Ubuntu site.

In any case, you should be using the 6.06.1 version.

Good luck.

---

### Post by JayTheHun on 2006-11-04
years ago, with RH linux, there was an X tool to probe your devices.  I haven't found it in Edgy.

---

