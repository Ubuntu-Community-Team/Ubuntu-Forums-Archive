---
title: "I am in serious trouble"
date: 2010-03-13
forum: Installation &amp; Upgrades
---

### Post by borneseller on 2010-03-13
I've run out of space on my laptop. Thus I thought I would try to uninstall ubuntu to open up room for XP. I deleted the Linux partitions through Window Disk Management but I don't have a windows CD to boot from and now I am unable to boot into Windows. 

This is very serious for me - - I own my own business and alll of my information is on that laptop.

Please help!

---

### Post by StephenOK on 2010-03-13
> **borneseller said:**
> I've run out of space on my laptop. Thus I thought I would try to uninstall ubuntu to open up room for XP. I deleted the Linux partitions through Window Disk Management but I don't have a windows CD to boot from and now I am unable to boot into Windows. 

This is very serious for me - - I own my own business and alll of my information is on that laptop.

Please help!

You probably should have used gparted to resize the partitions, but that's a should have could have answer, which is useless in this case.

The following tutorial will be helpful, but you'll have to borrow a cd from someone:

[http://www.askvg.com/how-to-remove-linux-boot-loader-from-startup-after-deleting-linux-partition-on-a-dual-boot-system/](http://www.askvg.com/how-to-remove-linux-boot-loader-from-startup-after-deleting-linux-partition-on-a-dual-boot-system/)

Good Luck

---

### Post by mah817 on 2010-03-13
You can download a boot disk here I'm told that will work: [http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm)

---

### Post by Sef on 2010-03-13
>  This is very serious for me - - I own my own business and alll of my  information is on that laptop.

Before doing anything else, **back up** your **data**.   If you have the Ubuntu Live CD, use that to get your data off of your laptop.   If that does not work, then use [Knoppix]("http://knoppix.com").  If you have no way to burn a cd, then order one from either [Linuxcd]("http://linuxcd.org") or [OSDisc]("http://osdisc.com").

---

### Post by efflandt on 2010-03-13
If your computer did not come with software disks, the very **first** thing you should have done was burned the disks from the utility that likely came on the computer, along with any utility or rescue, or OS backup disks.  You may be able to order them from the manufacturer, if not too old.

I also do not need to tell you that it is foolish to start tampering with your drive without backing up any essential data (which you could have done to CD or DVD if no external drive)

If you have any sort of USB drive, you should be able to boot an Ubuntu install CD into live mode and be able to copy files to USB flash or hard drive.  I have done that for laptops with failing drives (or one case when WinXP was hopelessly infected and would not let the user do anything, not even boot to safe mode).

It might be as simple as putting a Windows mbr on the hard drive.  But for some reason when I removed Ubuntu from a Win7 drive (even though I did not touch the mbr and specifically put grub on a partition marked as boot partition), then switched the boot partition back to Win7, it would not boot (could not find bootmgr).  So I had to boot the Win7 (CD or DVD?) a couple of times before it totally fixed that.

For my work laptop, I run Ubuntu from a USB hard drive, and made absolutely certain that I put grub on the mbr of the USB drive (not default to internal drive).  That also worked for that Win7 laptop after I fixed its internal drive to boot itself.

---

### Post by ljrmorgan on 2010-03-16
You could well be fine. What may have happened is you installed the GRUB bootloader on your MBR, which would let you boot linux and windows, and then deleted the file that GRUB looks at when you wiped your linux partitions. GRUB will still be installed, but it wont know what to do to boot windows. You can manually enter the command in GRUB (not sure off hand how), and get into windows that way. Then, the first thing you should do is download a utility for restoring the windows bootloader - that will replace GRUB and you'll be fine.

Apologies if I have misunderstood your problem - if this doesn't work perhaps you could post any messages you get when you turn on your laptop.

For future reference, the best idea is to boot into windows, restore the windows bootloader to the MBR and *then* delete linux (if you're sure that's what you really want to do!)

---

### Post by dE_logics on 2010-03-16
Well... you can buy a windows disk as usual and ask for techenical support from MS. That's the best stuff they do -- wiping anything non MS.

---

### Post by ljrmorgan on 2010-03-16
I think EasyBCD ([http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)) is the tool I used to restore my Windows bootloader when I had to.

---

