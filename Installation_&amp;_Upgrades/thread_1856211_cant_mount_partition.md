---
title: "cant mount partition"
date: 2011-10-07
forum: Installation &amp; Upgrades
---

### Post by Karottenbaum on 2011-10-07
Im not able to mount sda3.
just so you know, i installed xubunto and this long i know linux....

i created all three partitions as primary, when it came to sda3 (supposed to be for movies and music) i didnt know what mountpoint to select (dont know anything about mountpoints)..
but i choosed opt/ as mountpoint, bcause i didnt know what to do... as far as i remember i formated it as FA32 (i know not good)

i found a file named opt/ which has the size of ma partition but i cant write on it,

something else: is it a bad idea to create all three partitions as primary?

how can i make xubuntu make use of the SWAP?
[B]

sudo fdisk -l[/B]

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb8f0ffa4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14647296   83  Linux
/dev/sda2            1824        2189     2929664   82  Linux swap / Solaris
/dev/sda3            2189        9730    60572672   83  Linux


```

---

### Post by Toz on 2011-10-07
> **Karottenbaum said:**
> Im not able to mount sda3.
just so you know, i installed xubunto and this long i know linux....

i created all three partitions as primary, when it came to sda3 (supposed to be for movies and music) i didnt know what mountpoint to select (dont know anything about mountpoints)..
but i choosed opt/ as mountpoint, bcause i didnt know what to do...
Then the /opt directory is probably mounted on that drive. Post back the results of:
```
mount
```...to verify.

> as far as i remember i formated it as FA32 (i know not good)
FAT32 is an okay choice if the plan is to share the partition with a windows install. If you don't have a windows install on that computer, then yes, there are better options.

> i found a file named opt/ which has the size of ma partition but i cant write on it,
By default, /opt is root-writeable only.

> something else: is it a bad idea to create all three partitions as primary?
Not necessarily.

> how can i make xubuntu make use of the SWAP?
Maybe it is already in use. Post back the results of:
```
cat /proc/swaps
```
...and the contents of **/etc/fstab**

> sudo fdisk -l[/B]
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb8f0ffa4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14647296   83  Linux
/dev/sda2            1824        2189     2929664   82  Linux swap / Solaris
/dev/sda3            2189        9730    60572672   83  Linux


```
Hmmmm, sda3 doesn't seem to be formatted FAT32.

---

