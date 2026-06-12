---
title: "Live USB &quot;Boot Error&quot;"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by banzoo on 2008-11-14
I am trying to install the ubuntu from a Live usb, but when try to boot on that usb key, I get "Boot Error" messages from my thinkpad T500. I've tested the live usb on a Dell Laptop and it works. Does anyone knows how to fix this? any hints?
Would it be some retarded Bios problem? (Although the current version of the bios dates back in sept08 )

---

### Post by cariboo on 2008-11-14
Is **Boot Error** all you get, or is there more to the message? Does Grub start up? More information please.

Jim

---

### Post by banzoo on 2008-11-14
> **cariboo907 said:**
> Is **Boot Error** all you get, or is there more to the message? Does Grub start up? More information please.

Jim

I get only "Boot Error" as soon as I choose to boot on the USB, nothing more!

I'm suspecting Bios, but is there a way to boot a USB drive using the windows "boot.ini" in case the problem is a lame Bios?

---

### Post by banzoo on 2008-11-15
Is there anyway to boot from a usb key avoiding the Bios? (using grub or windows boot.ini for instance?)

---

### Post by caljohnsmith on 2008-11-15
Banzoo, how about opening a terminal (Applications > Accessories > Terminal) and please post the output of the following command while your USB drive is connected:
```
sudo fdisk -lu
```
Does that command show any of the partition(s) on your USB drive marked as bootable (with the asterisk *)? If not, that could be your issue. If that is the case, I can help you set one of the partitions as bootable, and probably your BIOS will boot it fine after that.

---

### Post by banzoo on 2008-11-15
> **caljohnsmith said:**
> Banzoo, how about opening a terminal (Applications > Accessories > Terminal) and please post the output of the following command while your USB drive is connected:
```
sudo fdisk -lu
```
Does that command show any of the partition(s) on your USB drive marked as bootable (with the asterisk *)? If not, that could be your issue. If that is the case, I can help you set one of the partitions as bootable, and probably your BIOS will boot it fine after that.

This is the output part of the usb (I can see that it's not that clean!), I made the live usb using UNetbootin, and other methods too. I should note again that it worked on other laptops.

```


Disk /dev/sdb: 1027 MB, 1027604480 bytes
32 heads, 62 sectors/track, 1011 cylinders, total 2007040 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb0bcd68e

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?  3223366781  3470046704   123339962   78  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(518, 102, 15) logical=(1624680, 26, 50)
Partition 1 has different physical/logical endings:
     phys=(743, 0, 62) logical=(1749015, 15, 15)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?   432871117  1208554935   387841909+  10  OPUS
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(205, 7, 0) logical=(218181, 0, 14)
Partition 2 has different physical/logical endings:
     phys=(920, 235, 50) logical=(609150, 21, 34)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?  1869562563  3788792630   959615034   8b  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(260, 125, 54) logical=(942319, 26, 56)
Partition 3 has different physical/logical endings:
     phys=(893, 46, 60) logical=(1909673, 22, 35)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?   912785408   921108501     4161547    a  OS/2 Boot Manager
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(269, 111, 50) logical=(460073, 9, 19)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(464268, 12, 46)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order


```

---

### Post by caljohnsmith on 2008-11-15
Wow, I've never seen fdisk complain so much about the partition table for just one drive. :? All the block numbers are wrong as far as partition sizes. Do you really have four partitions on that little 1 GB USB drive? What did you use to partition it? 

For one thing, it doesn't look like any of your partitions are marked bootable, but in fact fdisk just reports a question mark. I suppose you could go ahead and try marking one partition bootable and see if it works. Personally though, I would reformat the drive and start over because of the crazy head/cylinder geometry on that drive; the geometry doesn't even seem to be consistent between partitions. How about trying:
```
sudo fdisk /dev/sdb
```
Press "a", "1" for the partition, "w" to write the change, and "q" to quit. Then see if you can boot the USB drive. Let me know how it goes.

---

### Post by banzoo on 2008-11-15
> **caljohnsmith said:**
> [...]
How about trying:
```
sudo fdisk /dev/sdb
```
Press "a", "1" for the partition, "w" to write the change, and "q" to quit. Then see if you can boot the USB drive. Let me know how it goes.

I didn't partition it manually, but apparently the tool I used to create the liveusb have made all that dirty job!
and wow, fdisk wasn't happy, I got the following:
```
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 2: No such file or directory.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.

```

But nothing changed after trying it with this.

---

### Post by caljohnsmith on 2008-11-15
I'm really surprised that USB stick works in another computer. Are you sure your computer supports booting a USB drive? Which program/tool did you use to create the Live USB? If I were you, I would wipe it clean and start over (make sure to delete the partition table entirely). Have you tried using UNetBootin? Or Intrepid comes with its own USB installer under System > Admin > Create a USB Startup Disk, which you could try.

---

### Post by banzoo on 2008-11-15
It's UNetBootin what I was using! And did that several times, so I think it might be some feature missing with Laptop Bios (or most probably a bug). Maybe I should wait an update, and meanwhile, install Ubunutu the old way (with a real CD).

---

### Post by cariboo on 2008-11-15
If you've got Intrepid running, you can use the builtin usb boot device creation tool. Go to System-->Administration-->Create a USB Startup DIsk

Jim

---

### Post by C.S.Cameron on 2008-11-15
It looks like you need to format your flash drive.
I have found that trying to format one with multiple partitions in Windows can brick it.
Suggest you reformat your flash drive using the partition editor on the Live CD, (gparted).
Format in FAT 32 and try Unetbootin again, or the tool on the 8.10 CD.
If you use Unetbootin select Diskimage and not Distribution or Custom.

---

### Post by banzoo on 2008-11-15
I got the usb key formatted using gparted, and then using create USB startup disk. fdisk -lu shows only one partition with an asterisk under Boot. But ironically, when trying to boot under the usb key, I got no more "Boot Error" message, in fact I get no messages at all, only a blank screen! (But I still can ctrl+alt+del).
Tough, the live usb works normally on a Dell Laptop.

---

### Post by linko47 on 2008-12-20
I think it has something to do with the BIOS.  I have an X61 with the exact same problem.  It has nothing to do with your partitioning.  When you were using unetbootin, it didn't write partitions to your disk, it was writing raw data.  Fdisk doesn't apply in those situations since there are no partitions.  My flash drive looked exactly the same after putting a Slackware boot image on a flash drive.  It would boot fine on other laptops, but not this thinkpad.  Something is wrong...  Please post if you have any ideas.

---

### Post by meierfra. on 2008-12-20
My thinkpad SL500  also refuses to boot from my external USB hard drive. But I have two different work arounds

1)   I boot to the grub menu on the internal drive. Press "ctr-alt-del" to reboot, press "F12"  and then I can choose to boot from the USB drive.


2)  I added the boot manager [Plop]("http://www.plo/en/bootmanager.html") to my grub menu. After choosing "Plop" at the grub menu, I get a boot menu where I can choose to boot from  the "USB" drive.
You can also install Plop to the MBR if you don't want to go through two boot menus.

Warning: When Plop is installed to the MBR, it has some powerful features. For example it  lets you change the partition table. When I first installed Plop, I  played around with it, to see what it can do ( after only having glanced over the instruction). Well, I succeed to completely mess up my partition table, even the hard disk geometry had changed.
Luckily I was able to restore the partition table with testdisk.

---

### Post by tubaman on 2010-04-21
Ubuntu 9.10(karmic) USB drives created with unetbootin and usb-creator-gtk all failed to boot with "Boot Error" on multiple machines.  I ended up running the [universal USB installer]("http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/") under Windows and that booted with no issues.

[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/]("http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/")

---

### Post by x13es on 2011-05-04
I have fixed this "boot error" issue by formatting my usb to fat32 and using unetbootin to create a bootable usb.

---

