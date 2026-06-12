---
title: "After Installing ubuntu"
date: 2007-08-05
forum: Installation &amp; Upgrades
---

### Post by iAndrew on 2007-08-05
Hi, I just installed Ubuntu 7.04.

I'm having a problem, it boots correctly, but before login screen I get this error message.

Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

YES                          NO

---

### Post by bulldog on 2007-08-05
What kind of graphics do you use?
In most cases you need to install some kind of driver for your graphics.

---

### Post by Pumalite on 2007-08-05
You have to configue your xserver. Try: sudo dpkg-reconfigure xserver-xorg
Answer yes to most defaults, choose 'vesa' as your driver. At the end: startx

---

### Post by iAndrew on 2007-08-05
Thanks for the quick replies. I'll try it out

---

### Post by iAndrew on 2007-08-05
Okay. I tried that.

I get:

Fatal server error:
no screens found
XIO: fatal io error 104 (Connection reset by peer) on X server ":0.0"
after 0 requests (0 known processed) with 0 events remaining.
root@ubuntu:~#

---

### Post by Pumalite on 2007-08-05
Better re-install with the Alternate CD and avoid the graphical interface problem altogether. (text mode). It also solves other unknown hardware problems. [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Check the box below the green sign that says: 'Start Download'

---

### Post by iAndrew on 2007-08-05
I'm using Ubuntu Alternative i386 CD.

---

### Post by Pumalite on 2007-08-05
Post your specs.

---

### Post by iAndrew on 2007-08-05
I'll try my best:

Intel Celeron @ 2.60 Ghz
Level 2 Cache: 128kb
System memory: 512 mb

Video Controller: Intel 852GM/GME/GMV
Panel Type: 14" XGA
Audio Controller: Sigmatel 9750
Modem Controller: Conexant D480 MDC
Primary HDD: 30 GB
Modular Bay: CD-RW/DVD Combo

---

### Post by Pumalite on 2007-08-05
If you have integrated graphics, you should go with Xubuntu Alternate CD: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

### Post by iAndrew on 2007-08-05
um, is there a way I can upgrade to this? Because, I don't want to go find each ubuntu studio app, and redownload and install them.

---

### Post by Pumalite on 2007-08-05
Look into Xubuntu and you will find out is an entirely different animal.

---

