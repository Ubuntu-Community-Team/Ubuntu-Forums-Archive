---
title: "Finally ditched Wubi"
date: 2010-12-15
forum: Installation &amp; Upgrades
---

### Post by Kramer2010 on 2010-12-15
Well I finally did it, ditched wubi and installed ubuntu properly?  Everything seems ok so far, but... This is what I did

1) In windows I shrank my windows partition (eek)
2) My new partition E is approx 130gig (have 150gig for win 7 in C/)
3) At installation I chose "install alongside window"
4) I dragged slider to left to get max storage and continued install.

After install Ubuntu disk usage analyzer shows 2.9GB of 119.9GB used.

However in windows 7 Drive E is shown as having a total of 3GB... did I screw up?

here's my sudo fdisk-1

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x43764375

Device Boot Start End Blocks Id System
/dev/sda1 1 1658 13312000 27 Unknown
/dev/sda2 * 1658 1671 102400 7 HPFS/NTFS
/dev/sda3 1671 21939 162808152 7 HPFS/NTFS
/dev/sda4 21940 38914 136345601 f W95 Ext'd (LBA)
/dev/sda5 21940 22331 3145988 7 HPFS/NTFS
/dev/sda6 22331 38235 127746048 83 Linux
/dev/sda7 38235 38914 5451776 82 Linux swap / Solaris

Also... windows 7 disk management

[http://farm6.static.flickr.com/5202/...9cc32856_b.jpg](http://farm6.static.flickr.com/5202/...9cc32856_b.jpg)

---

### Post by kansasnoob on 2010-12-15
What version of Ubuntu did you install?

Also please post the output of:

```
sudo parted /dev/sda print
```

Please "wrap" the terminal output in "code" tags by clicking on the # at the top of this reply box, then pasting between the code tags. It makes it much easier to read :D

---

### Post by Kramer2010 on 2010-12-15
Ubuntu 10.10


Model: ATA WDC WD3200BEVT-2 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  13.6GB  13.6GB  primary   ntfs            diag
 2      13.6GB  13.7GB  105MB   primary   ntfs            boot
 3      13.7GB  180GB   167GB   primary   ntfs
 4      180GB   320GB   140GB   extended                  lba
 5      180GB   184GB   3221MB  logical   ntfs
 6      184GB   314GB   131GB   logical   ext4
 7      314GB   320GB   5583MB  logical   linux-swap(v1)
```

```

---

### Post by kansasnoob on 2010-12-15
Maverick got a new Live Installer:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

Regardless that looks pretty darn good.

You have three actual Windows primary partitions:

/dev/sda1 13.6GB Windows diagnostic
/dev/sda2 105MB  Windows boot files
/dev/sda3 167GB  Windows main partition

Then an extended partition:

/dev/sda4 140GB extended lba

And the extended contains three logical partitions:

/dev/sda5 3221MB logical ntfs
/dev/sda6 131GB  logical ext4 (your Ubuntu)
/dev/sda7 5583MB logical Ubuntu SWAP

It might be interesting to use Nautilus to snoop and see what, if anything, is in sda5, but otherwise you have a 167GB Windows and a 131GB Ubuntu.

---

### Post by Kramer2010 on 2010-12-15
Thanks for that.  What I dont understand is the extended partition:/dev/sda4 140GB extended lba?  All the other partitions make sense, but ```

```140GB + 167GB (windows) + 131 GB (ubuntu) = 438GB!!...

```

```Also the Ubuntu partitions, 2 make sense, but what is the /dev/sda5 3221MB logical ntfs?

```

```Apologies for gross stupidity in  advance..

---

### Post by Kramer2010 on 2010-12-15
Just looked at that 3.2 gig partition using disk utility.  It says its unmounted.

---

### Post by kansasnoob on 2010-12-15
> **Kramer2010 said:**
> Just looked at that 3.2 gig partition using disk utility.  It says its unmounted.

Arrgh, never use the Ubuntu disk utility (aka: palimpsest). That was pushed by Gnome (and developed by Red Hat):

> palimpsest (from the gnome-disk-utility project) is a tool to manage disk
drives and media:

 * Format and partition drives.
 * Mount and unmount partitions.
 * Query S.M.A.R.T. attributes.

It utilizes udisks.

IMHO it's garbage!

---

### Post by kansasnoob on 2010-12-15
> **Kramer2010 said:**
> Thanks for that.  What I dont understand is the extended partition:/dev/sda4 140GB extended lba?  All the other partitions make sense, but ```

```140GB + 167GB (windows) + 131 GB (ubuntu) = 438GB!!...

```

```Also the Ubuntu partitions, 2 make sense, but what is the /dev/sda5 3221MB logical ntfs?

```

```Apologies for gross stupidity in  advance..

When you look at the total of all Windows partitions it's closer to 181GB for Windows, and if you include everything within the extended partition Ubuntu is using 140GB so the total is 321GB.

Hey these calculations are better than they used to be :D

I rained on the "fix device measurements" parade when I filed this bug:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/538165](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/538165)

It's still happening, just much more slowly :D

---

### Post by kansasnoob on 2010-12-15
Regarding "/dev/sda5 **3221MB** logical ntfs" boot into Ubuntu and navigate to Places > Computer.

There you should see devices/partitions listed by either device name/label or by size.

Browse, just don't be stupid and delete or change anything!

My guess is that the 3221MB contains nothing, but what's 3221MB worth on a 320GB drive?

If everything is working leave well enough alone!

---

### Post by Kramer2010 on 2010-12-16
Just booted into widows 7 and had a look in the 3GB partition.  There is one file called bootsqm.dat and its 4KB.

---

