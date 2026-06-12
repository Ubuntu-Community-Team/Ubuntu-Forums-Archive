---
title: "grub wont overwrite windows boot loader"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by legit on 2008-05-15
I've just installed ubuntu 8.04 by overwriting my windows drive.  So I no longer have windows at all.

The only problem is Grub somehow didn't overwrite the windows boot loader, when I turn on my computer I get the windows boot loader and immediately following that I get a message saying that Windows is corrupt and it couldn't boot.

The only way I can get into the ubuntu thats installed on the drive is by booting into the liveCD and telling it to boot from the first hard disk.  In this case I get Grub and can boot successfully into ubuntu.

I've tried redoing the Grub install with grub-install and setup(from within grub's interface) and both failed.

Any suggestions?

thanks,
- legit

---

### Post by Rallg on 2008-05-15
How many partitions does your disk have? My computer started out with 3 partitions: A small FAT16 partition with special manufactuer's stuff, a Windows Recovery partition, then Windows (Vista). Drive (hd0,0) was the first of these. It was not visible from within Windows, meaning that if you didn't use a Linux partitioner such as GParted, you wouldn't know it was there.

Possibly your problem is that the master boot record (MBR) is not on the partition that the Ubuntu installler selected. An unchanged MBR would point to to location of the (former) Windows boot software, rather than to Grub.

Ty this: Use the live CD, and launch GParted from the desktop menu. Look at the hard drive partitions. Is there a partition that you did not expect to see? If it is a manufacturer's partition at the start of the hard drive, I would not delete it (who knows what it contains?). Look for the "boot" flag, which will be shown for exectly one of the partitions. Is is where you expect it to be? If not, GParted can change the boot flag.

Changing the boot flag may or may not help. If it does not help, then you may have to re-install Grub without accepting the default location on your drive. Since you have deleted Windows and have only Ubuntu, try this: From Gparted, determine which partition has the Ubuntu root system. Remember that the first partition (which may or may not be Ubuntu) is (hd0,0), followed by (hd0,1), (hd0,2), and so forth. Re-install Ubuntu (you have no files to lose at this point, yes?). When you get to the screen that gives you a summary of selected actions before final install, look for the "Advanced" button. Change the Grub installation location to (hd0,n) where n is appropriate for you.

Then attempt to boot to the re-installed Ubuntu. It should work. If the computer says that there is "no operating system" or other dire message, it probably means that the boot flag is in the wrong place; if so, use GParted from the live CD to fix the flag.

---

### Post by meierfra. on 2008-05-15
> when I turn on my computer I get the windows boot loader and immediately following that I get a message saying that Windows is corrupt and it couldn't boot.

 This sound like you did not overwrite Windows. Boot from the Ubuntu Live CD, open a terminal (Applications->Accessories->Terminal) and post the output of

```
sudo fdisk -l
```
(l is a lower case L)

---

### Post by psusi on 2008-05-15
Do you have more than one physical disk drive?  Or maybe a USB disk plugged in when you installed?  It sounds like grub got installed to a disk other than the one the computer boots from.

---

### Post by tim_hunsicker on 2008-07-02
I have this same problem.  

I did the sudo fdisk -l command and got the following.

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3492    28049458+  83  Linux
/dev/sda2            3493        3648     1253070    5  Extended
/dev/sda5            3493        3648     1253038+  82  Linux swap / Solaris

Disk /dev/sdb: 2399.9 GB, 2399932514304 bytes
255 heads, 63 sectors/track, 291775 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000b94d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24426   196199008   83  Linux

I don't see the "hidden" partition and don't know how or where on the Live CD to get the GParted app.

Any advice?

---

### Post by SkonesMickLoud on 2008-07-03
> **tim_hunsicker said:**
> 
I don't see the "hidden" partition and don't know how or where on the Live CD to get the GParted app.

Any advice?

GParted in the LiveCD is under System >> Administration >> GParted.

Also, when you installed Ubuntu, did you format the drive first, or did you simply let the installer do it?

Typically when doing such an extreme change in operating systems, it is wise to physically run GParted once, and possibly twice, to ensure a thorough cleaning of the parts of the disk you wish to format.  Be careful to only format partitions you can afford to lose.  And as Rallg said, you should keep the manufacturer partition unless you are absolutely sure of what you're doing, and even then, it probably doesn't hurt to keep it.

---

