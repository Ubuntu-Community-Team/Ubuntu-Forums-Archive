---
title: "ubuntu 10.10 fails to start GUI after patch install"
date: 2011-07-24
forum: Installation &amp; Upgrades
---

### Post by wwcorigan on 2011-07-24
After backing out a patch that was not needed Ubuntu 10.10 can't startx after reboot. It appears the video driver has reverted to some linux/ubuntu default that can't drive the graphics card or display.

The /var/log/Xorg.0.log says: *(typed, can't paste in text mode on another ubuntu system)
From the log:
Cannot get EDID infromation from CRT1  #(note CRT1 -> Hanng HG281D)
...
(The fglrx(0) reject all display modes, for one reason or another
the first failure notice is:)
DCI initialization failed
...
kernel module fglrx.be may be missing or incompatible.

So what's up with this? 
The display driver is an on-board ATI radeon HD4250

It seems that some linux parch/kernel upgrades, in general, won't use existing display drivers and have to be manually re-installed. What is up with this logic???

Where can I get an ATI radeon HD4250 ubuntu driver that will support 1920x1080 resolution the HD4250 is capable. The monitor is, above, is 28" lcd.

What are the command line commands to install the HD4250 driver?

---

### Post by stanbx on 2012-07-24
I am having this exact problem...

Please help!

---

### Post by wildmanne39 on 2012-07-24
Hi, this is an old thread so it has been closed please start a new thread of your own with a descriptive title. 
Thanks

---

