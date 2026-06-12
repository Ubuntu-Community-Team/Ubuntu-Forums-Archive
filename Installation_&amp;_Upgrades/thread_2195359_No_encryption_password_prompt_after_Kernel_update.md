---
title: "No encryption password prompt after Kernel update"
date: 2013-12-23
forum: Installation &amp; Upgrades
---

### Post by nicolasdiogo on 2013-12-23
hello


i have installed my system with full-disk encryption.

normally i find that i have to provide my password for the disk during boot.

this has worked fine for many years when i have used various version of Ubuntu/LinuxMint

i have now updated my kernel and i find that my system drops into a prompt that states:

```

cryptsetup: evms_activate is not available

```

since there is no longer a prompt for decrypting my disk, i figure that something went wrong while updating the Kernel.

so the question is:

**how can i fix this problem?**

as this disk is enrypted there is no way that i can access my data inside this partition.

**YES** the system is fully back-up! i have burned myself in the past (and learnt)

so could i please ask some instructions for Dummies 

It seems that a few other people are also suffering this problem:
[bug 1003309]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1003309")

please let me know if further info is required,


with regards,

Nicolas

---

### Post by nicolasdiogo on 2013-12-23
to be clearer

i have tried to open this partition with:
```

cryptsetup luksOpen /dev/sda5 rescueRoot

```

but it returns:

```

Device /dev/sda5 is not a valid LUKS device.

```


so i am not using the correct approach to read this partition? or is there something that i have missed - as i was trying to follow the steps described on the bug report.

thanks,

---

### Post by nicolasdiogo on 2013-12-27
really finding difficult to savage this installation.

my disk has the following partitions - using LinuxMint Live from a USB:

```

# fdisk -l

Disk /dev/sda: 180.0 GB, 180045766656 bytes
255 heads, 63 sectors/track, 21889 cylinders, total 351651888 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ee10b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   351649791   175574017    5  Extended
/dev/sda5          501760   351649791   175574016    7  HPFS/NTFS/exFAT

```

the strangest thing for me is the sda5 - that should be the encrypted partition - is identified as a NTFS partition.

any suggestion on how i can read this partition?

thanks,

---

### Post by nicolasdiogo on 2014-07-13
just given up ..

---

