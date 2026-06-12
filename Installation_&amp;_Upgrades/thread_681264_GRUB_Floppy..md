---
title: "GRUB Floppy."
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by wolterh on 2008-01-28
Hi. I'm currently on my livecd session right now...

I need to make a GRUB boot floppy, its already formatted and all.

I just need to know how to get grub's files (stage1, stage2, menu.lst) of the latest version and put them in my floppy. I hope the menu.lst files contains a menu for ubuntu.

I don't want to install anything on the hard drive. Is that possible?

---

### Post by 5starog on 2008-01-28
take a look here [http://ubuntuforums.org/showthread.p...ng+windows+mbr](http://ubuntuforums.org/showthread.p...ng+windows+mbr)

---

### Post by logos34 on 2008-01-28
I believe this is what you're looking for:
[https://help.ubuntu.com/community/GrubHowto/BootFloppy](https://help.ubuntu.com/community/GrubHowto/BootFloppy)

---

### Post by wolterh on 2008-01-29
That guide is infering that I have the grub installed on my machine, and I don't. I'm just running from the live CD, and I have no /boot/grub dir under my root.

What I need is to install the grub ONLY on the floppy. If that isn't possible, I'll have to wait for the IT guy to come tomorrow and install me the Ubuntu.

I tried to do it with my LiveCD but there is an error with a file at 52%. That's why I haven't installed it, but the IT guy has an original Ubuntu CD, so he is coming tomorrow to install it. Can't wait lol.

Anyway, I'm going to give a shot to burning a non-RW DVD I have, to see what happens.

---

### Post by confused57 on 2008-01-29
> **woli said:**
> That guide is infering that I have the grub installed on my machine, and I don't. I'm just running from the live CD, and I have no /boot/grub dir under my root.

What I need is to install the grub ONLY on the floppy. If that isn't possible, I'll have to wait for the IT guy to come tomorrow and install me the Ubuntu.

I tried to do it with my LiveCD but there is an error with a file at 52%. That's why I haven't installed it, but the IT guy has an original Ubuntu CD, so he is coming tomorrow to install it. Can't wait lol.

Anyway, I'm going to give a shot to burning a non-RW DVD I have, to see what happens.
You might be able to boot Ubuntu with Super Grub Disk, using the option to direct kernel boot:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Select_the_appropriate_Super_Grub_Menu](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Select_the_appropriate_Super_Grub_Menu)

Here's the homepage for downloading, burning, & using SGD:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by wolterh on 2008-01-31
Thanks. Problem solved.

---

