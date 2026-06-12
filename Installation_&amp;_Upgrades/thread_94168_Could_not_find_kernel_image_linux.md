---
title: "Could not find kernel image: linux"
date: 2005-11-23
forum: Installation &amp; Upgrades
---

### Post by delbene on 2005-11-23
Hi guys, I would like to try Ubuntu, but when I try to boot from the install cd I get this error: 

```
Boot CD-ROM Type: Non Emulation Booting 

ISOLINUX 2.04 2003-04-16 Copyright (C) 1994-2003 H. Peter Anvin 
Could not find kernel image: linux 
boot:

```


The checksum of the iso is ok, the burning is correct (I tried with two different software, nero and clonedvd), and finally my laptop (Acer TravelMate 291LMi) can boot other linux live-cd (like LNX-BBC). 

Btw, this is a problem Ubuntu share with Debian, Knoppix and Auditor (all based on Debian): their iso give me exactly the same error. 

Any help?

---

### Post by yesplease on 2005-11-23
It is possible to install linux on that laptop. What you can do is look how others did it on [http://www.linux-on-laptops.com/acer.html](http://www.linux-on-laptops.com/acer.html) and [http://tuxmobil.org/acer.html](http://tuxmobil.org/acer.html) . They often give pointers for installation if it is out of the ordinary. Ofcourse you can also search here. 

Not the answer that solves your problems immediately, but it may be a good start.

Edit: What I mean is in this way you may find clues, for instance some people benifit from special boot options. I hope someone else can provide better help.

---

### Post by delbene on 2005-11-24
Yes, I know it can be installed! I installed Red Hat and Mandrake in the past on this same laptop without problems.
 
My problem is just with Ubuntu and other Debian derived distros...

---

### Post by delbene on 2005-11-24
I tried on an ASUS laptop too, redownloading the iso with it, burning again and what I get is: 
 
ASUS laptop: 
```
 
 
ISOLINUX 3.08 2005-05-19 Copyright (C) 1994-2005 H. Peter Anvin 
isolinux: Disk error 20, AX = 4210, drive EF 
Boot failed: press a key to retry... 

```

ACER laptop: 
```
 
Boot CD-ROM Type: Non Emulation Booting 
ISOLINUX 3.08 2005-05-19 Copyright (C) 1994-2005 H. Peter Anvin 
Could not find kernel image: linux 
boot: 

```

I'm using CD-RWs (various), could be this the problem?

---

### Post by yesplease on 2005-11-24
This howto describes howto make a bootdiskette, it is applicable when you have aCDrom player but cant boot from it  [http://wiki.ubuntuusers.de/Bootdiskette](http://wiki.ubuntuusers.de/Bootdiskette)

The author advises to use [http://uranus.it.swin.edu.au/~jn/linux/rawwritewin-0.7.zip](http://uranus.it.swin.edu.au/~jn/linux/rawwritewin-0.7.zip) in windows to write a bootdiskimage [http://slackware.at/data/slackware-current/rootdisks/sbootmgr.dsk](http://slackware.at/data/slackware-current/rootdisks/sbootmgr.dsk) to a diskette.

Put diskette and CDrom in the computer and restart.

(In linux you can make the diskette by writing 
dd if=./sbootmgr.dsk of=/dev/fd0
in a console (terminal)

I am curious if this works.

Keyes also found a floppy boot: [http://www.ubuntuforums.org/showthread.php?t=94633](http://www.ubuntuforums.org/showthread.php?t=94633)

---

### Post by delbene on 2005-11-25
Unfortunatly I don't have a floppy reader on my laptop.
 
Anyway, I found that the problem is ISOLINUX. I cannot boot any cd using it, while I'm able to boot correctly those with SYSLINUX. Do you know why?
 
So, now the question is: how can I start the ubuntu installer if I boot from another distro like LNX-BBC? I have already the partition set and formatted on my hd...

---

### Post by yesplease on 2005-11-25
Starting in version 1.65, ISOLINUX supports booting disk images of other operating systems. However, this feature depends on BIOS functionality which is apparently broken in a very large number of BIOSes. Therefore, this may not work on any particular system. 

This is from [http://syslinux.zytor.com/iso.php](http://syslinux.zytor.com/iso.php)

I have seen this before, but thought this was a very old problem, and I dont know if it applies here.

---

### Post by delbene on 2005-11-27
Thank you for the help, I managed to install Ubuntu following the "The CD approach" part of this guide:
 
[https://wiki.ubuntu.com/Installation/FromWindows]("https://wiki.ubuntu.com/Installation/FromWindows")
 
and the installation was without any big problems (I only had to manually mount the cdrom).
 
An idea for the future could be to create an image of Ubuntu booting with SYSLINUX...

---

### Post by yesplease on 2005-11-27
Excellent! This method does not seem very hard, were the instructions complete?

---

### Post by delbene on 2005-11-28
Pretty complete. I found also these that can be useful:
 
[http://marc.herbert.free.fr/linux/win2linstall.html]("http://marc.herbert.free.fr/linux/win2linstall.html")
 
[http://ubuntuforums.org/showthread.php?t=28948&highlight=booting+iso+hd]("http://ubuntuforums.org/showthread.php?t=28948&highlight=booting+iso+hd")
 
As said the only problem was that the installer was not able to mount automatically the cdrom, So I had to open the shell and digit two times (dunno why but the first time doesn't work):
 
```
 
mount /dev/cdroms/cdrom0 /cdrom

```
 
and then going back to the installation, it completed succesfully.

---

### Post by delbene on 2005-11-30
[quote=delbene]I'm using CD-RWs (various), could be this the problem?[/quote]

Quoting myself, yes, that was the problem, as I suspected.
For some reason ISOLINUX + CD-RW don't get along very well. Use a standard CD-R and all will be fine...

---

