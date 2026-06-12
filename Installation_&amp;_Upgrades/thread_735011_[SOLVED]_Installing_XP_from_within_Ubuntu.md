---
title: "[SOLVED] Installing XP from within Ubuntu?"
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by kevin8o8 on 2008-03-25
Howdy,

I have an IBM thinkpad T30 with a broken CD-rom. Ubuntu occupied the entire hard disk. Now I want to install Windows XP (because I have to do something using XP). Are there any ways to install Win XP from Ubuntu? It doesn't matter if I have to erase any data in the hard disk but the big problem is that I have a broken CD-rom, which doesn't allow me to install using the CD.

I know my question sounds stupid but I really hope someone can provide a helping hand.

---

### Post by housam on 2008-03-25
I think it is better to fix your CD ROM. I don't know if using an external HDD with preinstalled xp can be done or not.

---

### Post by firmit on 2008-03-25
A google search answers your question. 

[https://help.ubuntu.com/community/VirtualBox]("https://help.ubuntu.com/community/VirtualBox")

If I understand you correctly, you did not leave a free partition for installing xp. You could create a new partition with available space for dual boot, but I suggest you try a virtual machine.

VirtualBox or VMWare Player (or server) does the trick. It allows you to install XP "inside" the created virtual machine, running it in a window inside ubuntu.

Of course - you need available disc space to do any of this...
added: run in terminal
```
df -h
```
If you don't plan to run a whole bunch of appz in your vm, a couple (~4?) of gb's for winxp should be enough.

---

### Post by kevin8o8 on 2008-03-26
Thanks for all your replies.

Life would have been much easier if I have a working CD-rom. 

I knew about VirtualBox or VMware long time ago but it's tough for my thinkpad to run two operating systems simultaneously (high cpu usage and high temperature). If possible, I can erase the entire hard disk and reinstall xp.

One thing I want to ask: Does XP installation require some free space to copy the installation files?

---

### Post by ZALMAN on 2008-03-26
Yes, XP does require space to copy files prior to installation. One thing you might consider rather than replacing you're cdrom (which in laptops can cost a lot (every thing is more expensive)) is getting an external usb cd/dvd rom, it would make life a lot easier.

---

### Post by kevin8o8 on 2008-03-26
Thanks for your information.

After replacing another XP installation CD, I was able to go straight through xp installation. (That's not the cd-rom problem, but the broken CD.)

Thread closed.

---

