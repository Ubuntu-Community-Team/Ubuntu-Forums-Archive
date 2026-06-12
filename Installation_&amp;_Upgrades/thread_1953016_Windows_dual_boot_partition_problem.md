---
title: "Windows dual boot partition problem"
date: 2012-04-05
forum: Installation &amp; Upgrades
---

### Post by raysa on 2012-04-05
I went to instal Ubunutu 11.10 on a new computer. Chose the "instal alongside Windows" option and adjusted the partitions so that Windows had a very small share (I hardly ever use it), leaving the bulk of the spare space for Ubunutu.

But it seemed to start installing onto my external harddisk - where all my back-up data is kept, so I panicked and turned off the external disk. The installation ground to a halt and I turned everything off and started again (with the external disk turned off this time).

The installation started as before but this time the "install alongside Windows" option is missing - leaving me with only two choices - "replacing Windows" or "something else".

I'd rather keep Windows but I don't understand the stuff in "something else".

For the 500GB internal disk it lists:
dev/sd1 ntfs Windows recovery environment (loader) 17 GB
dev/sd2 ntfs Windows 7 (loader) 104 MB
dev/sd3 ntfs 241 GB
dev/sd4 ntfs 248 GB

How can I go from here to having about 100 GB for Windows and 400 GB for Ubuntu?

Thanks for any help,
Ray

---

### Post by sudodus on 2012-04-05
I seems your internal drive /dev/sda already has 4 primary partitions. This means you cannot make a new one for Ubuntu. I think this is why it started to install into your external drive (probably) /dev/sdb.

One solution is to edit the partitions with ***gparted*** run from a live session booted from your Ubuntu install CD or USB drive.

But first be sure to have a ***fresh backup*** of your personal data.

It seems that at least one of your partitions maybe /dev/sda4 is a data partition. If it is you can delete that partition and instead create an extended partition using that disk space. And then, make logical partitions for Ubuntu root (/), swap and a common data partition inside the extended partition.

For example:
[FONT="Courier New"][SIZE="3"]
ext4 partition to be mounted as /,...size 32 GB
swap partition, size = size of RAM....(say 4 GB)
ntfs data partition, size 248-32-4 GB =..212 GB
------------------------------------------------
extended partition,size .................248 GB[/SIZE][/FONT]

---

### Post by Mark Phelps on 2012-04-05
If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. Since you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

### Post by raysa on 2012-04-05
Thanks folks. Reading the comments and thinking about it I came to the conclusion that my initial aborted attempt to instal Ubuntu and change the partitions created dev/sd4, so I deleted it to give some unallocated space.

Then I started the instal again and this time the option to instal "alongside Windows" returned, so that's what I've done, and so far it seems to have worked.

Thanks again,
Ray

---

