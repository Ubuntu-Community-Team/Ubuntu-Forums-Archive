---
title: "Karmic: Hard Disk acting odd."
date: 2009-09-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hellsgator on 2009-09-18
Is this normal? Am I going crazy or am I just missing 10GB somehow? :confused:

Palimpsest output:

160 GB Hard Disk
ATA WDC WD1600BEVT-22ZCT0
MBR Partition Table

/dev/sda: 160GB, 149GiB, 160,041,885,696 bytes

/dev/sda1 154GB Filesytem Linux Ext4 (version 1.0): 154GB, 143GiB, 153.500.143.104 bytes Partition 1 (Linux(0x83))

/dev/sda2 Extented logical partition: 6.5GB, 6.1GiB, 6.539.097.600 bytes Unrecognized Partition 2 (Extended(0x05))

/dev/sda5 Unrecognized (Unknown or Unused): 6.5GB, 6.1GiB, 6.539.065.344 bytes Unrecognized Partition 5 (Linux (Linux(0x83))

/dev/mapper/cryptswap Swap Space:  6.5GB, 6.1GiB, 6.539.065.344 bytes Cleartext Luks device

GParted ouput:

/dev/sda 149.05GiB

/dev/sda1 ext 4 142.96 GiB
/dev/sda2 extended 6.09 GiB
/dev/sda5 unknown 6.09 GiB (Unable to detect file system. Possible reasons are...)

fdisk -l output:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c1293

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   83  Linux

Any tips or info explaining this? Completely confused for the last 48 hours.

---

### Post by bruno9779 on 2009-09-18
I really do not see where the problem is.

10 GB missing? are you sure you are not confusing Gigabytes with Gibibytes?

GB is not the same as GiB

[http://en.wikipedia.org/wiki/Gibibyte](http://en.wikipedia.org/wiki/Gibibyte)

---

### Post by hellsgator on 2009-09-18
Well, let me tell you why....

When I install Ubuntu it shows this size of my Hard Disk:

143 GB /dev/sda1
6.1 GB /dev/sda5 

Making it a Hard Disk of 149.1 GB. I have a 160GB Hard Disk. So, what happened with the 10.9 GB? I did install with using all of the Hard Disk. :confused:

Could be a tiny mistake in the install program. Showing it in GiB instead of GB. I don't know this for sure. So that's why I am slightly puzzled about it.

---

### Post by hellsgator on 2009-09-18
this is after a clean install:

160 GB HD
 |
 |
 |__154 GB Filesytem sda1
 |
 |__6.5 GB Extended sda2
     |
     |__ 6.5 GB Unrecognized Linux Swap sda5
          |
          |__ 6.5 GB Swap space /dev/mapper/cryptswap1

this is a normal setup? just to be sure of myself? :confused:

---

### Post by oldfred on 2009-09-18
Seems to be the same as my Jaunty: (only sdb my 160GB drive shown)
fred@ubuntuDuo:~$ sudo sfdisk -luM
Disk /dev/sdb: 19457 cylinders, 255 heads, 63 sectors/track
Units = mebibytes of 1048576 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start   End    MiB    #blocks   Id  System
/dev/sdb1   *     0+ 146687- 146688- 150207718+  83  Linux
/dev/sdb2     146687+ 152625-  5939-   6080602+   5  Extended
/dev/sdb3         0      -      0          0    0  Empty
/dev/sdb4         0      -      0          0    0  Empty
/dev/sdb5     146687+ 152625-  5939-   6080571   82  Linux swap / Solaris

---

