---
title: "Installation failed and partitions disappeared"
date: 2010-09-11
forum: Installation &amp; Upgrades
---

### Post by Snitz on 2010-09-11
Hello,

I've decided to give ubuntu another test drive now that I got a bigger and better desktop. I downloaded the latest version of ubuntu, loaded it into my usb stick and booted from it. I then clicked on the install icon on the desktop to star the installation. 

Everything was going ok, until I came to the partitioning part.
I had already (on windows 7) created a separate partition for ubuntu which is 56GB. so I chose "manual partitioning" and selected the ubuntu partition as /home and began the installation.

Everything seemed to have went well, the window suddenly closed and then nothing happened. I waited for 15mins and still nothing happened. I decided to restart and see what happened, but I discovered that I couldn't boot into windows anymore. It said something about intel boot manager cannot find filesystem.

So I decided to boot back from the usb and see if I can reinstall ubuntu, I came to the partitioning part and all the drives were gone, I couldn't see anything, it was blank.

I don't know what to do, I'm really stuck here. Any advise please?

---

### Post by srs5694 on 2010-09-11
Boot the Ubuntu disc into its live CD mode, open a terminal (a command prompt shell), and type "sudo fdisk -lu". Post the results here, preferably preceded by [noparse]```
[/noparse] and followed by [noparse]
```[/noparse] for legibility. This will show us the nitty-gritty on your partition table. My suspicion is that something like [this](http://www.rodsbooks.com/missing-parts/index.html) is happening, but I can't be positive of that.

---

### Post by Snitz on 2010-09-12
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x36ec9971

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848  1024002047   511897600    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3      1024002048  1830641663   403319808    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4      1830643710  1953521663    61438977    f  W95 Ext'd (LBA)
Partition 4 does not end on cylinder boundary.
/dev/sda5      1830643712  1953521663    61438976   83  Linux

Disk /dev/sdb: 2054 MB, 2054426624 bytes
64 heads, 62 sectors/track, 1011 cylinders, total 4012552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb0bcd68e

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?  3223366781  3470046704   123339962   78  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(518, 102, 15) logical=(812340, 26, 50)
Partition 1 has different physical/logical endings:
     phys=(743, 0, 62) logical=(874507, 47, 15)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?   432871117  1208554935   387841909+  10  OPUS
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(205, 7, 0) logical=(109090, 32, 14)
Partition 2 has different physical/logical endings:
     phys=(920, 235, 50) logical=(304575, 21, 34)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?  1869562563  3788792630   959615034   8b  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(260, 125, 54) logical=(471159, 58, 56)
Partition 3 has different physical/logical endings:
     phys=(893, 46, 60) logical=(954836, 54, 35)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?  2119696384  2128019511     4161564    a  OS/2 Boot Manager
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(269, 111, 50) logical=(534197, 43, 23)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(536295, 15, 22)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```

This is what you've asked.

PS: I can see windows partitions now from ubuntu, and I can open them too.

EDIT: I have attached a screenshot of "GParted" to show you my drives. Note that I attempted to install ubuntu on /sd4/ and if I go there I can find the ubuntu files but I'm not sure if it installed correctly as I can still see the install button on the desktop.

---

### Post by Snitz on 2010-09-12
Ok, I gave up on the quest to install ubuntu on sda5 and simply selected it to install next to windows (default option) and it worked. Ubuntu is now installed though but on booting, windows 7 does not show up. I need to be able to boot into windows as well. Only ubuntu shows.

How can I fix this?

---

### Post by srs5694 on 2010-09-12
Try downloading and running the [Boot Info Script,](http://sourceforge.net/projects/bootinfoscript/) then post the results here.

---

