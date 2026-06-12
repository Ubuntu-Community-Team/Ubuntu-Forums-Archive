---
title: "Wiping a hard drive"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by Bcrowes11 on 2011-04-07
Would wiping the drive completely of everything on here (***dows) get rid of the bios therefore making it possible to boot ubuntu? If so, how would I do that?

---

### Post by srs5694 on 2011-04-07
The BIOS is stored on the computer's motherboard, so nothing you do to the hard disk will affect the BIOS. (Well, unless you write a program to the hard disk that flashes a new BIOS image and then run that program.)

The presumption in your question that the BIOS is preventing Linux from booting is incorrect. On most PCs, the BIOS is *required* to boot *any* OS, including Linux.

I recommend you post back with details about the nature of your problem, since it's unclear just what sort of problem you've encountered.

---

### Post by jcolyn on 2011-04-07
> **Bcrowes11 said:**
> Would wiping the drive completely of everything on here (***dows) get rid of the bios therefore making it possible to boot ubuntu? If so, how would I do that?

The bios is a ROM chip on the motherboard. Wiping the drive has nothing to do with the bios..

If you are having problems with bootup of Ubuntu check the motherboards maker for any bios upgrade for that particular model board..

---

### Post by jcolyn on 2011-04-07
If you are referring to the Inspiron 1545 in your sig the current bios version is A14. If yours is an earlier version go to the Dell site to download the current version..

I suspect your problem though is files in hidden Dell partitions that are designed to protect your installation. If this is the case a complete wipe of the hard drive should take care of that problem. I would however recommend you build a set of recovery DVD's from the recovery partition before wiping the drive.

You can download the free version of Killdisk from here [http://www.killdisk.com/downloadfree.htm](http://www.killdisk.com/downloadfree.htm)

You need to get the bootable CD version called [Download Bootable ISO Image of Active@ KillDisk                                  to burn CD]("http://software.lsoft.net/boot-cd-iso.zip") click this link for instant download.. Unzip and burn an iso.

The free version allows for a single pass wipe but you can run it however many times you like..

---

