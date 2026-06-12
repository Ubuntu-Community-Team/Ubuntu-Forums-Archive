---
title: "lm-sensors"
date: 2008-02-14
forum: Installation &amp; Upgrades
---

### Post by kaiwan on 2008-02-14
Hi! 
I want to install lm-sensors. But this error message I get:

------
The following NEW packages will be installed:
  lm-sensors
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/509kB of archives.
After unpacking 1556kB of additional disk space will be used.
Selecting previously deselected package lm-sensors.
(Reading database ... 185344 files and directories currently installed.)
Unpacking lm-sensors (from .../lm-sensors_1%3---a2.10.4-1ubuntu1_i386.deb) ...
Setting up lm-sensors (1:2.10.4-1ubuntu1) ...
Can't call method "description" on an undefined value at /usr/share/perl5/Debconf/Question.pm line 93, <GEN0> line 1.
dpkg: error processing lm-sensors (--configure):
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
 lm-sensors
E: Sub-process /usr/bin/dpkg returned an error code (1)
---

Now this shows every time I install something.

I tried autoremove and it removes the package and than I have no error, but I would like to have lm-sensors. 
Tried with purge and autoclean...didnt help

thanks

---

### Post by Pumalite on 2008-02-14
What kernel are you running and what are your specs?

---

### Post by kaiwan on 2008-02-14
Well I run Ubuntu Gutsy, have all updates ....
So I have the kernel you get after updating ubuntu gutsy...I think it is 2.6.22-14...

I have Core 2 Duo, ABIT motherboard, dual boot with XP

---

### Post by Pumalite on 2008-02-14
lm-sensors is in Synaptic. I just installed it with your same kernel without difficulties. You must have dependencies that will not be met with your method. Try Synaptic.

---

### Post by kaiwan on 2008-02-15
tried synaptic and apt-get ... still the same error....

---

