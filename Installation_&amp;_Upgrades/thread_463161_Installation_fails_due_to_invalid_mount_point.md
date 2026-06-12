---
title: "Installation fails due to invalid mount point"
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by liberalist on 2007-06-03
I have 5 partitions, two of them are used by Mac OS X. My computer is an Intel Core 2 Duo iMac (2 GHz with 1024 MB ram)

The other ones are set up as follows: 
200 MB EFI partition
18 GB ext3 file system
1.5 GB Linux swap partition

What mountpoints do these have (I thought /boot, /, swap respectively, but this did not work). Please help me, because I am stuck. Ubuntu refuses to install due to invalid mountpoint (my guess is the EFI partition).

I have installed [rEFIt]("http://refit.sourceforge.net/") and initially the EFI partition was set to /media/rEFIt. This mount point did not work as well.

Furthermore, I can choose from the following options:
swap
/
/home
/boot
/usr
/var

---

### Post by confused57 on 2007-06-03
> **liberalist said:**
> I have 5 partitions, two of them are used by Mac OS X. My computer is an Intel Core 2 Duo iMac (2 GHz with 1024 MB ram)

The other ones are set up as follows: 
200 MB EFI partition
18 GB ext3 file system
1.5 GB Linux swap partition

What mountpoints do these have (I thought /boot, /, /swap respectively, but this did not work). Please help me, because I am stuck. Ubuntu refuses to install due to invalid mountpoint (my guess is the EFI partition).

I'm not sure, but I think your swap mountpoint should just be "swap", not "/swap"...don't know about the EFI partition.

---

### Post by liberalist on 2007-06-03
> **confused57 said:**
> I'm not sure, but I think your swap mountpoint should just be "swap", not "/swap"...don't know about the EFI partition.

That is true, I made a mistake in my first post. However, my system still refuses to install.

---

### Post by Cool Surfer on 2007-06-03
swap partition willaccept swap. Other two two would take ext3 and ext2 partitins.

Make sure you format the ext partition after which installation will be real cool.

I also spent some time at that point. :popcorn:

---

