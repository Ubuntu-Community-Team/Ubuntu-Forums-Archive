---
title: "[SOLVED] Need Help Please"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by Arkas on 2008-02-20
First may I explain what i have done.

I installed Ubuntu server thinking it was what i  needed, after realising with some help, I actually needed Ubuntu desktop.

So now when i install Ubuntu desktop it goes fine right up untill it say remove cd disk, then boots and goes blank.( i do get the Ubuntu logo screen )

I have tried to start in Safe mode and when it boots up I only see the desktop but its frozen.

So then i hit ESC before it loads and put in the command ( dpkg-reconfigure -phigh xserver-xorg ).
It tells me i dont have xserver -xorg.

I dont know how to  re install.

I seem to think it may be the video card ( old PCI card) drivers or in conflick with Ubuntu server.
How do I get rid of Ubuntu server?

Please help

---

### Post by Partyboi2 on 2008-02-20
when you are installing and get to the partitioning part choose to manually partition and make sure there is a tick in the box to format the /root partition.
did you check the [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") for the desktop version?

---

### Post by Arkas on 2008-02-20
I put the disc in and it ask whether to install or to start , so I press enter and the Ubuntu logo screen comes and want to run, how do i check the partitioning now or uninstall Ubuntu desktop  to start again?

I

sorry i am very new to Linux!


Thanks again for you help

---

### Post by Partyboi2 on 2008-02-21
Are you dual booting with windows or are you using the whole hard drive for ubuntu?
when you are at the main menu instead of choosing to install select the option to check disk for defects.

---

### Post by Arkas on 2008-02-21
Yes the machine is completley for Linux OS, 

I will try that now also i have run the check for the disc and that 100%



Thanks again ( crosses fingers)

---

### Post by Partyboi2 on 2008-02-21
try using something like [dban]("http://sourceforge.net/projects/dban/") to wipe the drive then reinstall ubuntu

---

### Post by Arkas on 2008-02-21
Thanks, I will, and once again it was 100%.

---

