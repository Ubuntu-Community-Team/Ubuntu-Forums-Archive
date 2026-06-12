---
title: "Kernel Update"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by Mortos on 2010-07-12
Hi, guys !

I have the following problem... I'm running on Ubuntu 7,04 and I've tried to update my kernel(which currently is 2.6.20) to the newest available version which is 2.6.34 and i followed the instructions from this site [http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html](http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html) but when I've tried to compile the kernel i get this [IMG]http://img5.imageshack.us/img5/5433/screenshotcw.png[/IMG]. Any idea what to do ?

---

### Post by dino99 on 2010-07-12
you can choose a kernel from this url (ready to install)

how to install:

you need gdebi installed (into synaptic)
then install in that order: 
- header-all
- header
- image

choose them either 32 or 64 bits (less problem with 32, ie i386)

---

### Post by Mortos on 2010-07-12
well thx for the advice but I'm newbie to Linux and I don't know anything about it so could you write me exactly what to do in the terminal. 10q

---

### Post by kansasnoob on 2010-07-12
> I'm running on Ubuntu 7,04

Are you aware that 7.04 reached end-of-life in October 2008?

That's a very long time without security updates and such. Even package management gets very shaky after a release reaches EOL.

---

### Post by Mortos on 2010-07-12
I'm with this version because my RAM is 256DDR MB, and the next versions of ubuntu require at least 512 RAM. If you have idea what to do I'll be thankful ;)

---

### Post by Blümchen Blau on 2010-07-12
> **Mortos said:**
> well thx for the advice but I'm newbie to Linux and I don't know anything about it so could you write me exactly what to do in the terminal. 10q

If you're a newbie - don't even think of compiling a "very new kernel-version" for a system that is outdated by 18 month.

What is the reason for not simply downloading Lucid Lynx and doing a nice, fresh install? And then - if you don't like the 2.6.32-Kernel you can get a 2.6.34-Kernel for Lucid from [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://[URL=%22http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/%22") and install as dino99 described it.

BB

---

### Post by Blümchen Blau on 2010-07-12
> **Mortos said:**
> I'm with this version because my RAM is 256DDR MB, and the next versions of ubuntu require at least 512 RAM. If you have idea what to do I'll be thankful ;)

Take a look at Lubuntu. It is very light-weight with LXDE-Desktop. And as far as I remember OK for running with that low RAM.

BB

EDIT: Lubuntu boots flawlessly in my Virtualbox-Installation with 256 MB RAM (Just set it down to - no difference in speed to be recognised.)

---

### Post by Mortos on 2010-07-12
10x for the help, the whole story was that I have a wifi adapter TPLINK WN721N and I want to install drivers with the following guide [http://leonardom.wordpress.com/2010/05/24/install-wireless-usb-adapter-tl-wn721n-driver-on-ubuntu-10-4/](http://leonardom.wordpress.com/2010/05/24/install-wireless-usb-adapter-tl-wn721n-driver-on-ubuntu-10-4/) 
This guide doesn't work on XUbuntu so I installed this old version of Ubuntu, and I'm wondering will this guide works on Lubuntu?

---

### Post by Blümchen Blau on 2010-07-12
I guess your problem wasn't connected with Xubuntu. Is it possible, that your troubles were with executing the make-commands?
If so, did you have installed the "build-essentials" (a package in the repositories):?:

Because without the necessary tools you will fail to install from a source on any installation.

BB

Or in terminal:```
sudo apt-get install build-essential
```

---

### Post by Mortos on 2010-07-12
oK So I'll install the Lubuntu and then I'll write here if I have problems with the adapter ;) 10q a lot for the help !

---

### Post by mörgæs on 2010-07-12
I would go for a minimal install of Ubuntu 10.04: 

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

