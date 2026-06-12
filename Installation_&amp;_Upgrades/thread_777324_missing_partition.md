---
title: "missing partition"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by SikEnCide on 2008-05-01
I used Wubi to install Ubuntu 8.04 beta. By far the easiest Ubuntu install I have ever done. Runs great. I recently did the upgrade to the full release, the only problem is now it does not see my Vista partition. Before i upgraded it would show up on the desktop as "media" or something like that. After the upgrade it is no longer there. I go into Computer and all i see is "file system"

I would like it to see the other partition again.

---

### Post by Sef on 2008-05-01
Let's check the partitions:

Applications > Accessories > Terminal

then type this code:

```
sudo fdisk -l
``` Small L

Paste the information in a new post here.

---

### Post by brigux on 2008-05-01
Check your /etc/fstab
I noticed that 8.04 may change the drive type.
look for your partition in the list and make sure the device is appropriate: sda and not hda for instance.

---

### Post by SikEnCide on 2008-05-01
ok did
```
sudo fdisk -l
```
and got the following.

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69f807c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         243     1951866   1b  Hidden W95 FAT32
/dev/sda2   *         244       14593   115266375    7  HPFS/NTFS

```

dump of the fstab.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by SikEnCide on 2008-05-02
I found it its located at 

file:///media/widnows part

which is what i named it.... for some reason it just shows up as a folder instead of a disk like it did in the beta.

---

### Post by djchandler on 2008-05-02
> **SikEnCide said:**
> I found it its located at 

file:///media/widnows part

which is what i named it.... for some reason it just shows up as a folder instead of a disk like it did in the beta.

Please post hardware specs, i.e., motherboard chipset, make and model of hard disk.  I'm having a similar problem. See other thread in this forum "8.04 Doesn't detect drives..."

Two of us are having problems getting Western Digital hard disks recognized at all by the installer. The alternate install CD routine keeps asking for a driver on a floppy.

---

### Post by SikEnCide on 2008-05-02
> **djchandler said:**
> Please post hardware specs, i.e., motherboard chipset, make and model of hard disk.  I'm having a similar problem. See other thread in this forum "8.04 Doesn't detect drives..."

Two of us are having problems getting Western Digital hard disks recognized at all by the installer. The alternate install CD routine keeps asking for a driver on a floppy.

I am running on an Asus F3Jc Laptop.
```

    * Processor: Intel Core Duo T2350 - 1.8GHz (x2), 533MHz FSB, 2MB L2 Cache
    * RAM: 2GB DDR2-667MHz
    * Hard Drive: 120 GB SATA 5400RPM
    * Screen: 15.4" Widescreen TFT (1280x800)
    * Optical Drive: DVD±RW Super Multi
    * Wireless LAN: 802.11a/b/g
    * Bluetooth: Bluetooth Enabled
    * Built-In 1.3 MegaPixel Camera
    * Card Reader (MMC, MS, MS-pro, SD) 

```

Everything works fine. even the function keys.  only problem i had was the little quirk with the partition. i made a luncher on the desktop so that problem is solved.. im dual booting with vista business with all the current updates.

---

### Post by djchandler on 2008-05-02
Thanks for the info. Glad you solved your problem. I still have mine though. It must be the hard drive. I'm installing Debian Etch 64-bit right now, no problems so far.

I hope you enjoy your Ubuntu experience. It looks as though the Ubuntu hardware parade has passed my computer by, 64-bit capable or not.

---

### Post by SikEnCide on 2008-05-02
glad i could help some

---

