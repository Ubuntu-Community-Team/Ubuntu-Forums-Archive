---
title: "Installation problems"
date: 2007-08-04
forum: Installation &amp; Upgrades
---

### Post by bayhawk on 2007-08-04
I am trying to install ubuntu on my dell 5150 laptop and the installation is freezing just after i select the initial "Start or install Ubuntu" screen.  It reads the loads the kernel and reads the cd for 2 minutes but will stop when the bar is 3/4 complete.  I have tried to redownload the ISO and reburn the cd to no avail.  When the bar freezes, the fan on the computer shuts down and the cd drive will not eject the cd.  Nothing responds when it gets to 3/4 of the bar.  Same spot every time.  I tried to install 7.04 and 6.10 with the same results.

---

### Post by Pumalite on 2007-08-04
You probably need the Alternate CD. I could be more precise if you post your specs.

---

### Post by bayhawk on 2007-08-04
Pentium 4 - 1.5ghz
512 Ram
40 gig HD

---

### Post by Deco_21 on 2007-08-04
Try using the "Safe graphic mode Install", it should work , just make right that your graphic card works in ubuntu. 

Could you tell me what kind is ?

---

### Post by bayhawk on 2007-08-04
I also formatted my hard with Kill Disk ([http://www.killdisk.com](http://www.killdisk.com)) before i attempted the install.  I do not want a dual boot.  Ubuntu only.

---

### Post by Pumalite on 2007-08-04
According to memory you can go with Ubuntu Alternate. Mark the box below the green sign that says: Start Download:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by bayhawk on 2007-08-04
Ill give it a try and let you know...thanks for the help.

---

### Post by bayhawk on 2007-08-04
Here is what happened.  The installation completely finished successfully with the alternate download, but during the 1st boot from the harddrive, the screen froze at the exact same spot, 3/4 way through the bar.

---

### Post by Pumalite on 2007-08-04
[https://help.ubuntu.com/community/Installation#head-194b248381c71c37f7b187c6b814bbe7e31d91d6](https://help.ubuntu.com/community/Installation#head-194b248381c71c37f7b187c6b814bbe7e31d91d6)

---

### Post by bayhawk on 2007-08-04
I read through this link and did have followed that procedure for the installation.  Any other ideas?

---

### Post by Pumalite on 2007-08-04
Try: Ctrl+Alt+F1. If you get command line: sudo dpkg-reconfigure xserver-xorg. Answer yes to most defaults. Choose 'vesa' as driver; then startx.

---

