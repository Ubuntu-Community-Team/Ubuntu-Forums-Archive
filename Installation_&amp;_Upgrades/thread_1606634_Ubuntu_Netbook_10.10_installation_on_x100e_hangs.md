---
title: "Ubuntu Netbook 10.10 installation on x100e hangs"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by dimavin on 2010-10-26
Hi,
I am installing Ubuntu Netbook Edition 10.10 from USB drive on Thinkpad x100e. The installation hangs while displaying message "Retrieving file 1 of 18".
Installation from the same USB drive finishes successfully on a different PC.

I have the same problem on this x100e when installing UNE 10.04. Installation hangs earlier while showing "Copying files..." 
The same problem happened when the installation was burned on a CD and I tried to install it from an external CD drive.

x100e BIOS has been upgraded to latest version 1.28.
The laptop is fully functional under Windows 7, its original OS.

I will appreciate any hints or directions on how to solve this problem.
Thanks,
Dmitriy

---

### Post by stu19uk on 2010-10-26
Hi
I have the dual core X100e and just installed 10.10 netbook version on it tonight from an external CD and it went through the full install OK.
Everything worked until I chose a post install option to upgrade the ATI graphics and then the screen has gone all funny and is not usable. Note that the ATI issue is being tracked in a different post already.
I just downloaded the iso image from Ubuntu and used Nero to create a DVD, then rebooted using the DVD.

---

### Post by dimavin on 2010-10-26
Hi [stu19uk]("http://ubuntuforums.org/member.php?u=1175796"),
I know from thinkpad forums, e.g. [http://forum.thinkpads.com/viewtopic.php?f=59&t=88534](http://forum.thinkpads.com/viewtopic.php?f=59&t=88534)
that people successfully use ubuntu on x100e.
It looks like it is specific to my machine, so I am looking for some advice on how to debug the situation, for some istaller's logs to look at etc. Lenovo support is no help as this is not their pre-installed software problem.
Thanks

---

### Post by stu19uk on 2010-10-27
[SIZE=3]Looks like its all down to the ATI driver we need for our 'enhanced graphics' card. My son has installed 10.10 on his Dell netbook, and it all works perfectly.
I un-installed that graphics driver option that came up when I first installed it all and now the screen is OK, but I'm back to a rather slow lethargic OS.:(

It seems member 'juliobahar' seems to have done it on this thread;

[http://ubuntuforums.org/showthread.php?t=1525267&highlight=x100e](http://ubuntuforums.org/showthread.php?t=1525267&highlight=x100e)

Lets ask him![/SIZE]

---

### Post by stu19uk on 2010-10-29
[SIZE="3"]Just to let you know that i installed the 64  bit Desktop version on my X100e and it works fully. I was then able to install the ATI driver OK. If you are not too bothered with 64bit then i would probably go for the 32bit as you are more likely to get other drivers for it. For instance i wanted to install a printer driver from Lexmark website but they only had a 32bit version for Linux. [/SIZE]

---

### Post by Ibidem on 2010-12-05
Same issue trying to install Kubuntu Desktop 10.04.1.  I think the install may not work if the network isn't set up first.

---

