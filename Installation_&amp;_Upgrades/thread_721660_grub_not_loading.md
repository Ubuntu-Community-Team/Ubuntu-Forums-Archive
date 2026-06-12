---
title: "grub not loading"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by @tticus on 2008-03-11
Hey,

 It seems that I've got some serious problem. I have a Win Xp and an Ubuntu on separate partitions. I could load them without any problems. I have accidentally deleted some java source files from my hard (simple java files ) and I've downloaded two data recovery programs and started them with wine but couldn't recover them, so I decided to try to run them under windows and I restarted my laptop.....but the grub loader was not loading....it says" GRUB..." and does not see any OS on my laptop. 
This is all the info I know. Do you have any suggestion ?

Should I download a mini-linux distro or reinstall ubuntu ? ( I did an ubuntu reinstall a couple of weeks ago but I've lost all my files, I don't want that again ). 

Do you have any idea what to do ?

Thanks,
   @tticus

---

### Post by Pumalite on 2008-03-11
Boot your Ubuntu Live CD and post:
sudo fdisk -lu
(to see first how your drive/partitions look)

---

### Post by @tticus on 2008-03-11
I finally found my ubuntu disk and started the live cd

```
sudo fdsik -lu
```
gives the following output

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   195371567    97685783+  ee  EFI GPT

what should I do next ?

---

### Post by Pumalite on 2008-03-11
Looks like your partitions are toast. Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Post a screenshot.

---

### Post by @tticus on 2008-03-11
I couldn't make a screenshot but the list looks like this

It has a couple of GParted -LiveCD 0.3.14 lines then:

Boot MBR on first hard drive
Boot partition #1 on first hard drive
Boot partition #2 on first hard drive
Boot partition #3 on first hard drive
Boot partition #4 on first hard drive
Boot MBR on second hard drive
Boot partition #1 on second hard drive

I couldn't load MBR on the first cuz it gives the same problem as I mentioned in the first post.

Thanks for helping me out !

---

### Post by Pumalite on 2008-03-11
What second hard drive?. Your sudo fdisk shows only one.
BTW, in Gparted Live CD, at the bottom you have a camera icon to take screenshots.

---

