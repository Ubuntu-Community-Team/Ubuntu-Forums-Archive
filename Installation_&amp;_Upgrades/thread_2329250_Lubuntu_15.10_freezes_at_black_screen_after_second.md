---
title: "Lubuntu 15.10 freezes at black screen after second rebootnig"
date: 2016-06-29
forum: Installation &amp; Upgrades
---

### Post by Justarandomnicknam on 2016-06-29
I have a problem like this one: [http://ubuntuforums.org/showthread.php?t=2322111](http://ubuntuforums.org/showthread.php?t=2322111) but any solution isn't work for me.

I have Dell Inspiron Mini 1012 netbook.
First of all, I installed **lubuntu-15.10-desktop-i386.iso **and just after installing *first* reboot works well. Knowing issue witch Broadcome drivers, I change Additional Driver in Settings like this (not my screenshot but anyway):
[CENTER][IMG]http://i.imgur.com/QDRbYWp.png[/IMG][/CENTER]

And like in Thread mentioned above, I check ***xserver-xorg-video-intel*** packet in Synaptic but everything was already installed.
WiFi now working well.

After that I rebooted system *second* time - just black screen -> rebooting manualy with power button -> Grub menu apears -> after pressing *e *and inputing *nomodese* - another freeze:
[CENTER][IMG]http://i.imgur.com/RsBY77C.jpg[/IMG][/CENTER]

without *nomodeset *(simple reboot):[CENTER][IMG]http://i.imgur.com/CXHi4FG.jpg[/IMG]
[/CENTER]


Same problem with **Xubuntu 15.10**. 
**Lubuntu 16.04 **in LiveCD mode just doesn't want to launch.

Anyone know how to fix this cr@p?

---

### Post by mörgæs on 2016-07-01
Hi, welcome to the fora.

Let's see the hardware details. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

