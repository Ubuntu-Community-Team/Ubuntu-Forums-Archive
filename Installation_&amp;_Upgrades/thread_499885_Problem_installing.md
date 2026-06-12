---
title: "Problem installing"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by aco on 2007-07-13
Hi i need help

Untill now i had Xp and ubuntu on a single hard drive, i inserted new hard drive and wanted to place xp on one and ubuntu on other drive.
I installed Xp on one and it works but when i installed ubuntu on second, when i try to boot my pc speaker goes nutz and there is only black screen, what is wrong 

My hardware
2 hard drives seagate 320GB
Asus p5wd2
p4 650 3,4ghz

---

### Post by aco on 2007-07-13
I've tried to install it again with the same result, if i boot from Xp hard drive xp works perfectly, and if i try to boot from Ubuntu hard drive only black screen and pc speaker is going crazy, what is going on please anyone

---

### Post by pxwpxw on 2007-07-13
Are you changing the bios boot drive selection to boot ubuntu/xp?

---

### Post by aco on 2007-07-13
yes, because it doesent install any grub loader

---

### Post by pxwpxw on 2007-07-13
Do you mean that you are just not seeing a grub boot menu , or that nothing at all happens when you try to boot from the ubuntu drive? 

It probably means your grub first stage has got onto the ubuntu disk but the configuration is wrong for dual boot,  you may need to get a "super grub" cd to sort out the problem and get the grub loader and menu reinstalled. Normally grub loader would overwrite the xp MBR, unless you want to avoid that.

Edit 

Need to install ubuntu and grub while the 2 drives are set up as you intend them to operate, and install grub to the startup drive MBR.
This can probably be done by reinstalling grub, but requires using ubuntu live cd, or supergrub to rerun grub install. (if you cant boot the hard disk ubuntu /)

---

### Post by aco on 2007-07-13
after bios post about memory etc.... i get black screen and pc speaker is beeping rapidly thats all

---

### Post by pxwpxw on 2007-07-13
If you could recall where ubuntu installed grub it would help. If you changed the drive boot order after installing, that is always a problem.
But I don't have a PC running  here now, so I don't think I can help much more, maybe some one else will carry on.

---

### Post by aco on 2007-07-13
i sure hope it will because i have no idea how to fix this issue

---

### Post by Pumalite on 2007-07-13
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by aco on 2007-07-13
Link for super grub download is broken and there is no other place to download from and for the second solution it doesent work i already tried that, is there any other place where i can download supergrub

---

### Post by merlinus on 2007-07-13
[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

This page loaded very quickly for me.

-merlin

---

### Post by aco on 2007-07-13
Ok so i downloaded it, but it does exactly the same thing as running grub from console in live cd, in other words it doesent function

---

### Post by Pumalite on 2007-07-13
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by aco on 2007-07-13
This link is broken

---

### Post by merlinus on 2007-07-13
> **aco said:**
> Ok so i downloaded it, but it does exactly the same thing as running grub from console in live cd, in other words it doesent function

I assume that you downloaded the .iso file, burned it to a cd as a disk image, and then booted from the cd?

-merlin

---

### Post by aco on 2007-07-13
yes i did, and than booted from it, started automatic procedure he said that everything completed sucsesfully but when i reset only windows are booting directly without grub menu, and if i change in bios boot directly from ubuntu hard drive only black screen with fast beeps from pc speaker

---

### Post by merlinus on 2007-07-13
Did you look at these suggestions?

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Super_Grub_Disk_Quick_Help](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Super_Grub_Disk_Quick_Help)

-merlin

---

### Post by aco on 2007-07-14
I did it, i switched sata ports on motherboard so that now windows disk iz sata1 and linux sata2 and everything functions by itself, what a weird problem this was, thanks for help merlin

---

