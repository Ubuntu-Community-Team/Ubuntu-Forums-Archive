---
title: "Dual-Boot Ubuntu Vista Stuck"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by ART_Adventures on 2008-01-07
Dear People,

I am aiming to dual boot Windows Vista and Ubuntu (latest 7.10). I have Vista installed already, and I used Vista's disk partitioner to 'shrink' myself some unallocated space, ready to install Ubuntu.

I then reboot the system, boot-up into Ubuntu live mode. Click install, pass the first few screens and then arrive at the partition section, whereupon I get stuck because I do not know what to select without worrying that I might be overwriting the Vista partition.

At the partition screen, I have two options, as follows:

Guided - Entire Disk
* SCSC11 (0,0,0) (sda) 250.GB ATA
* SCSC11 (0,0,0) (sdb) 250.GB ATA

Manual.

If I select 'Manual', It asks me to choose a partition to prepare. Those being:
/dev/sda
/dev/sdb

The problem I have is that I do not know which of these (if any) represents the unpartitioned space which I 'shrank' using the Vista Disk utility. Can anybody help?

---

### Post by ART_Adventures on 2008-01-07
In addition...

I Boot into Ubuntu Live Mode, I enter the following in a Terminal

```

sudo fdisk -l

```

and it returns:

```

Unable to seek on /dev/sda

```

BTW: I have a Dell Dimension 9200.

---

