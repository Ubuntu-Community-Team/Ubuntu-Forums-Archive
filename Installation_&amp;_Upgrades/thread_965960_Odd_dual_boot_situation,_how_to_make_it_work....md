---
title: "Odd dual boot situation, how to make it work...?"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by ModemMisuser on 2008-10-31
Ok, I've got an odd dual boot situation I'm trying to get working.

I have an ASUS P5E Mobo, which has Intel ICH9R "fake" RAID onboard.  I've got 3 disks total, 2 of them are setup as a stripe, and the other is a non-raid disk.   

Vista Ultimate is installed on the stripe and has been working fine for ages.

I've installed Intrepid on the NON RAID disk.

I need to swap between the two and since the "fake" raid is a problem, I'm wanting to use Vista's boot manager to handle it.

When setup with the commonly found "use dd to grab the linux bootsector, then point Vista's loader to it" method... when I choose the Linux boot choice, GRUB just displays "GRUB" and halts.  

If I go into the BIOS and change the boot order so that the non-raid disk is the primary drive, Linux will boot fine, no problem.   But of course... no Vista.

The question is, why is GRUB halting on me, when I have the disks setup the way they need to be (with the stripe primary)?

I've got to find a way to get this thing working.

device.map:

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

(/dev/sdc is where Linux is... sda and b are the drives that are part of the stripe)

menu.lst:

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		142112cc-39b8-40ff-a88e-285bf24ce2ef
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=142112cc-39b8-40ff-a88e-285bf24ce2ef ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		142112cc-39b8-40ff-a88e-285bf24ce2ef
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=142112cc-39b8-40ff-a88e-285bf24ce2ef ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		142112cc-39b8-40ff-a88e-285bf24ce2ef
kernel		/boot/memtest86+.bin
quiet

---

### Post by caljohnsmith on 2008-11-01
> **ModemMisuser said:**
> 
When setup with the commonly found "use dd to grab the linux bootsector, then point Vista's loader to it" method... when I choose the Linux boot choice, GRUB just displays "GRUB" and halts.  

Unfortunately, since you have Ubuntu on a different drive than Vista, doing the classic "dd copy boot sector and install in Windows" will not work unless you install Grub to the boot sector in a special way; it is necessary to do it in a special way so that Grub will point to the correct drive when you move the boot sector over to the Windows drive.
> **ModemMisuser said:**
> 
If I go into the BIOS and change the boot order so that the non-raid disk is the primary drive, Linux will boot fine, no problem.   But of course... no Vista.
If you add an entry for Vista into your Grub's menu.lst, most likely you can get that to work despite your RAID setup. how about first posting:
```
sudo fdisk -lu
```
And also, go ahead and boot your Ubuntu drive, and when you get the Grub menu, press "c" to get the Grub command line. Then type:
```
grub> geometry (hd
```
Press TAB for tab-completion, and it should show a list of your drives. Next, for each drive do:
```
grub> geometry (hd0)
```
And also use (hd1), (hd2), etc if you have those drives listed too. Based on the output it gives you (partitions and drive size), let me know which (hdX) drive has Vista on it. We can work from there if you want. :)

---

### Post by ModemMisuser on 2008-11-01
Oddly enough, I did get it working... I just added an entry for Vista into menu.lst ... and GRUB chainloads Vista just fine.  

So I'll just leave the non-raid disk primary and go on.  

Odd. :D

---

