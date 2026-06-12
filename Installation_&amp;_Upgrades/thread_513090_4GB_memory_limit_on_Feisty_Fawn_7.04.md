---
title: "4GB memory limit on Feisty Fawn 7.04"
date: 2007-07-30
forum: Installation &amp; Upgrades
---

### Post by burnsje on 2007-07-30
I've been running ubuntu desktop since May-07 with 2GB memory, system working fine then.
When I add 2GB for total of 4GB memory the system hangs and will not start.
I edited my /boot/grub/menu.lst and removed "quiet splash" during startup. 
When I boot now, system gets hung with this message;
[67.645112] <0>Kernal panic - not syncing: Attempted to kill the idel task!
[67.645116] _

Anyone have any idea what this means?
Thanks for you help!

---

### Post by frodon on 2007-07-30
Which kernel are you using ?

I beleive the i386 kernel can't handle more than 4Gb of ram memory (including swap).

---

### Post by burnsje on 2007-07-30
Yes, I'm booting  i386 kernel.
I was told at Ubuntu Live that 4GB was not a problem.

---

### Post by frodon on 2007-07-30
Maybe you should try to fill a bug report, this is where you are more likely to get accurate informations :
[https://launchpad.net/ubuntu/+filebug](https://launchpad.net/ubuntu/+filebug)

Don't forget to give the full error message you get and the maximum details.

EDIT: this thread will surely interest you : [http://ubuntuforums.org/showthread.php?t=510561](http://ubuntuforums.org/showthread.php?t=510561)

---

