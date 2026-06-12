---
title: "What is Fdisk Telling Me?"
date: 2007-03-25
forum: Installation &amp; Upgrades
---

### Post by Holzmann on 2007-03-25
This is what I did during installation:

#1 primary 98.6GB B F ext3 /
#3 primary 400.0GB f ext3 /home
#5 logial 1.5GB F swap swap

This is what fdisk reports:

Disk /dev/sda: 500.1 GB, 500106813440 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11987    96285546   83  Linux
**/dev/sda2           60614       60801     1510110    5  Extended**
/dev/sda3           11988       60613   390588345   83  Linux
/dev/sda5           60614       60801     1510078+  82  Linux swap / Solaris

A couple of questions:

How can I get fdisk to report the partition sizes in GB? (Yes, I have read the MAN page on fdsik.)

Where did sda2 come from?

How can I confirm that /home was truly mounted on sda3?

---

### Post by bulldog on 2007-03-25
To create a logical partition you have to have an extended partition.

You can have only four primary partitions,but you can make multiple partitions in an extended partition.
To create an extended you have to give a primary in,so you can have three primary''s,one extended and even thirty logicals if you want.

Your swap is a logical partition,so you must have an extended partition.

---

### Post by taurus on 2007-03-25
```
df -h
```

---

### Post by Holzmann on 2007-03-25
Hmmm. I don't know if that answers my questions though.

---

### Post by Holzmann on 2007-03-25
Okay, that did it. Thanks.

---

### Post by souki on 2007-03-25
to get the size in GB, you have to calculate yourself, nb_blocks/1024/1024
to list mounted partitions, you can use the "df" command :
```
 df -h
```

---

