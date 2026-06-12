---
title: "[SOLVED] Invalid or missing boot.ini after installing Gutsy!"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by deathspal on 2007-10-23
Just finished installing Gutsy and after the reboot I got an error that was something to the effect of invalid or missing boot.ini. The machine then booted into windows fine, but sure enough the boot.ini is missing from the root of c: in windows. I resized the second drive in my system (freeded up 80gb) for Ubuntu and the install seemed to go fine. but now I have not boot.ini and no joy to get to my ubuntu install...   :(

---

### Post by deathspal on 2007-10-24
Bump

---

### Post by deathspal on 2007-10-25
Bump day 3

---

### Post by Steve1961 on 2007-10-25
To rebuild your boot.ini boot the pc from the windows disk (i'm assuming it's xp), enter the recovery console and type:

bootcfg /rebuild

To get into Ubuntu it sound like you need to reinstall grub.  To do this boot from the live cd and follow the instructions in this thread:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by deathspal on 2007-10-25
k thanks will give it a try...

---

### Post by deathspal on 2007-10-25
Thanks the recovery consol worked like a charm on my boot INI problem.

And I found the real problem with grub. My bios thought one drive was the boot drive and grub thought the other drive was the boot drive. I swaped them in the bios and was instantly transported to the utiopa of Ubuntu...  ;)

---

### Post by Steve1961 on 2007-10-25
Glad you got it sorted out :)

---

