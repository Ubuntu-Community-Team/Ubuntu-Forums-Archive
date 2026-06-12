---
title: "No Ubuntu Bootloader"
date: 2014-12-01
forum: Installation &amp; Upgrades
---

### Post by yann9 on 2014-12-01
Hi, brand new here and with ubuntu/linux stuff.  I want to try it...  Already installed ubuntu 14.1 in partition "d:" and partition "c:" contain windows xp.  When installed ubuntu I choosed "act4" or "ext4" as system file, if my memory is still good.

I searched the web and found stuff about easybdc (not working with xp) and other stuff.

My problem : can't find a way to load/start ubuntu...  always starting windows.  I tryed modding the boot.ini with no luck.

There is my boot ini if needed : 

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professionnel" /noexecute=optin /fastdetect

Thanks to all for your time.

P.S. I hope I don'tstart a tread already started.  Sorry in advance if this is the case.

Yann

---

### Post by Bashing-om on 2014-12-01
yann9; Hi ! Welcome to the f0rum .

Boot loader problem, OK; Consider this as the solution:
Ubuntu has GRUB ( Grand Unified Bootloader ) to control the boot process And as well GRUB will recognize Windows and chain load it onto it's boot menu.

So let us see what we are working with to advise you further.
Boot up the liveDVD in " try ubuntu " mode to terminal ( at desk top key combo ctl+alt+t ) and post back the outputs - Between Code Tags -  of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
which shows the partitioning of the hard disk(s) and we get an indication of what it will take to install the boot loader ( GRUB ).

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Elfy on 2014-12-01
To make it easier for people to help you - or even know they might - use thread titles that actually mean something pertinent to the issue at hand please ;)

> Where is it? doesn't fit the bill really ;)

---

### Post by yann9 on 2014-12-01
@bashing-om : thanks will do soon as I get home.

@ elfy : thanks you changed it.  You are right!  Sorry.

Thanks

---

### Post by Elfy on 2014-12-01
A thing occurs to me.

You say 

> Already installed ubuntu 14.1 in partition "d:"

Did you install Ubuntu while still in Windows using the wubi installer? 

If you did that then I would stop and start again doing a real install ;)

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by yann9 on 2014-12-01
@elfy : I installed it with the cd prompt at startup in dos.

Yann

---

### Post by Bashing-om on 2014-12-01
yann9; Hey;

We will see what is, and what we are working with from my requested outputs.
IF this is in fact a WUBI install, that installation is no longer supported. As Elfy advises in that event, a proper installation of ubuntu as a true dual boot in is order.

[INDENT][INDENT]a tale in the telling
[/INDENT][/INDENT]

---

### Post by yann9 on 2014-12-01
I did the install exactly like the post say.

This one (elfy recommandation)  : 
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Yann

---

### Post by Bashing-om on 2014-12-01
@yann9;
K, Then we looking to (RE-)install GRUB, awaiting requested outputs, so we know what is what and where -> so we know the how.

all in the process

---

### Post by yann9 on 2014-12-02
Finaly did it, but screenshot it with cellphone.  OS is running slow on CD...  wasent able to open firefox.

There are the results for sudo fdisk -lu and sudo parted -l : 

[[IMG]http://img4.hostingpics.net/pics/93340920141201232907Large.jpg[/IMG]]("http://www.hostingpics.net/viewer.php?id=93340920141201232907Large.jpg")

[[IMG]http://img4.hostingpics.net/pics/27526520141201234626Large.jpg[/IMG]]("http://www.hostingpics.net/viewer.php?id=27526520141201234626Large.jpg")

The problem might be up there \\:D/ in the last lines...

Thanks for your time.

Yann

---

### Post by oldfred on 2014-12-02
The error is that sr0 is read only. But sr0 is your CD/DVD and it is of course read only, so not a real error.

Since you did install to drive sdb, did you install grub2's boot loader to sdb or somewhere else. 
It should be installed to sdb, not to a partition. And best not to install to sda, unless you have a system that only boots from sda (some older ones).

If you installed grub2 boot loader to sdb, then in BIOS choose to boot from sdb. Or you may have a one time boot key like f10 or f12(varies by vendor and may be anything if available).

---

### Post by yann9 on 2014-12-02
I think i installed everything at the same place...  should i reinstall ubuntu on the same partition with windows?  Easyer?????

---

### Post by oldfred on 2014-12-02
You cannot install Ubuntu in Windows except with wubi which is now not supported.
You have to have Linux formatted partitions like ext4 not Windows formats like NTFS.

If not sure where things are at, install this into your live installer and post link to summary report.
DO NOT run the auto fix. It will install grub to both drives, and you want to keep the Windows boot loader in sda. You can use advanced mode and choose the Ubuntu install and the drive that is sdb to reinstall grub just to sdb.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Current version ppa now available.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by yann9 on 2014-12-02
@ oldfred : how do I do that, I can only boot ubuntu in "try mode" from the cd and the PC is VERY slow in this mode.

Yann

---

### Post by oldfred on 2014-12-02
Boot the live installer in the try mode and install Boot-Repair. 
Post link to summary report.
See post #13

---

### Post by yann9 on 2014-12-03
Problem fixed!!!

From windows, I formated the ubuntu partition.  Then I did a new ubuntu install with taking care of installing the loader on the first HD instead of the second one with linux...  

Thanks all!

Yann

---

### Post by Elfy on 2014-12-03
Nice one - always good when you get a fix :)

You can mark this solved in thread tools at the top.

---

