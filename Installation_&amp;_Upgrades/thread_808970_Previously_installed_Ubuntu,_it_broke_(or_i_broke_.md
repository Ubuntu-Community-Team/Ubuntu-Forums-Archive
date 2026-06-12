---
title: "Previously installed Ubuntu, it broke (or i broke it), want to try again"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by healthpellets on 2008-05-27
I previously had installed 6.06.1 on a dual boot with XP.  I didn't have any problems until one day it wouldn't boot (kernal error).  I didn't have time to play around w/it anymore, so I've been using XP ever since.  I'm tired of messing with XP, and want to get back to Ubuntu.  

I've burned the 8.04 live CD, but cannot get it to boot.  I've checked the BIOS and it's set to boot off the CD before the HDD.  But before anything happens GRUB pops up and i'm forced to choose between an Ubuntu install that doesn't work or XP.  

So any thoughts regarding how to proceed with both getting booted off the new Live CD and general thoughts on how to proceed re: new install of Ubuntu after my first failed install would be appreciated.

Thanks.

---

### Post by pytheas22 on 2008-05-27
First, you could try popping in some other bootable disk (e.g. an older Ubuntu live CD, XP install CD) and see if it boots.  If it works with a different disk, you could try burning the Hardy CD again; if not, you'll have to figure out why you can't boot to CD.

You could also try installing Ubuntu from within Windows by using [wubi]("http://wubi-installer.org/").  It's better to do a real install if you can, but wubi is almost as good if you don't have time to troubleshoot the CD boot problem.  wubi is also nice because it allows you to easily uninstall Ubuntu if you run into trouble using the XP add/remove programs utility.

As for doing the new install, you can just put it on top of the old Ubuntu install, as long as there's not anything on it that you wanted to keep.  If you describe the specific problems you had with the first install attempt, maybe we can make suggestions on how to avoid them this time.

---

### Post by healthpellets on 2008-05-27
is there a way to prevent GRUB from operating so that the CD drive will be read?  i assume what's happening is that GRUB kicks in before the drive is read.

thanks

---

### Post by housam on 2008-05-27
> **healthpellets said:**
> is there a way to prevent GRUB from operating so that the CD drive will be read?  i assume what's happening is that GRUB kicks in before the drive is read.

thanks

As long as you set the bios to make the cdrom is the first boot option there is no deal with grub. it is either the cd itself ( not burned as required )or something else in the bios.

---

