---
title: "Ubuntu doesn't see any drives"
date: 2015-03-11
forum: Installation &amp; Upgrades
---

### Post by ben_c3 on 2015-03-11
I recently got a new SSD and am trying to install Ubuntu on it. The problem is that it won't recognize any other drive except for the USB that I am booting from. I have no what to do. Running ````
sudo fdisk -l
``` yields 
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/loop0: 1 GiB, 1115594752 bytes, 2178896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 14.9 GiB, 16008609792 bytes, 31266816 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x002fbf82

Device     Boot Start      End  Sectors  Size Id Type
/dev/sda1  *     2048 31266815 31264768 14.9G  c W95 FAT32 (LBA)
```

I also have installed Windows on the drive and it recognizes the drives fine, and in my bios I can see them as well. Between 3 harddrives, Ubuntu won't see any of them. Does anyone have an suggestions?

---

### Post by DarkSapphire on 2015-03-18
What version of Ubuntu are you installing?  A more recent version will give you better hardware detection, especially for a new SSD.

---

### Post by fantab on 2015-03-19
Post the output of the following from Live Ubuntu:
```
sudo parted -l
```

Is your Windows hibernating? If Windows 8 then have you disabled [FastStartup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html")?

---

### Post by Vladlenin5000 on 2015-03-19
No, hibernation has nothing to do with it and one or more drives being SSDs neither.
The disks aren't being recognized in Ubuntu -and- we already know they're fine: Recognized in BIOS, Windows is installed and also recognizes the drives so... The problem is between _Ubuntu and the SATA controller_ where the drives are connected.
Is it by any chance an external (add-on) controller board? If so please post details.
If their connected directly to the motherboard, hence using the onboard controller (or more than one), please post at least the brand/model.

We'll get to the bottom of this, eventually...

---

