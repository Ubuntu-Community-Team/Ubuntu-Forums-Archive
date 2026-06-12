---
title: "&quot;Can't access tty&quot; problem on a Sony Vaio"
date: 2006-11-22
forum: Installation &amp; Upgrades
---

### Post by Metalhacker on 2006-11-22
Hello,

I successfully installed Ubuntu 6.10 and Kubuntu 6.10 on 4 different machines here at home. I had some problems, but always solved 'em somehow.

Now, I was trying to install Ubuntu (also tried Kubuntu) on a Sony Vaio PCG-SR11k.

Here are the computer's specs :

Pentium III processor 600mhz
256 Mb RAM
Intel 440ZX Chipset
S3 Savage IX 8mb SGRAM
10gb HDD
Yamaha YMF754B-R Sound.
PCGA-CD51/A Cd-Rom Drive

At the moment, i've got a Win 2k installation, but I'm happy to wipe it out and put Ubuntu on it...tho here's what the problem is :

I insert the Ubuntu 6.10 Live CD (that worked on ALL other computers), I boot from CD and, as usual, I get to the spash screen where I get to choose how to boot and/or what do to, I choose to boot/install Ubuntu, he loads some stuff, and after that, I get :

/bin/sh: can't access tty; job control turned off

What can I do?
I can't even live boot it, or check for errors or anything, i keep getting this error :|

I know this is usually related to the fact that if u swith HDD from one IDE channel, to another, Ubuntu won't recognize it and won't boot... but this error comes up before installing :(

I've looked up a lot of forums, and could only find problems related to post-installation errors, not PRE-installation :/

Would really appreciate any help you can give, hope to hear from u soon :)

---

### Post by Metalhacker on 2006-11-23
bump

I tried installing the alternate CD, but not only it's amazingly slow, but after a few boots (after installation) i get a nice black screen.

:/

---

### Post by drtvasudevan on 2006-11-24
live cd- all varities-official ones- ubuntu kubuntu 64 bit versions- same problem with a desktop here.
no solution that i could find on net.

the alternate cd ended up with a problem not detecting the cdrom

---

### Post by dentonlt on 2007-03-17
If you're using an VAIO with an external CD drive on PCMCIA interface, you'll need to add the boot option

ide1=0x180,0x386

Using a Sony Z505SX, my live CD (Dapper Drake) is unusually whiney.   I tried MANY boot option combos, and finally got it to boot using:

acpi=off pci=off ide1=0x180,0x386

Clearly, no pci leaves things in shambles ... but this is better than no boot.  The screen settings still aren't right, either - even the 'safe graphics mode' boot doesn't help.  I just get a solid blue screen.  I'll noodle with it until it works out.

Hope this helps, despite.

---

