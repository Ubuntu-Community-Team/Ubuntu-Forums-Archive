---
title: "Guidelines installing 10.04 64-bit server with vmware and SSD"
date: 2010-04-24
forum: Installation &amp; Upgrades
---

### Post by Erik-NA on 2010-04-24
I have just bought two SSD, Intel X25-M 80GB, to install Ubuntu 10.04 64-bit server with vmware on a computer with 8GB RAM.

I have tried to find out how to set up the system, but is somewhat confused on the setup.

The idea is to use software raid to aviod data loss if one SSD is giving up in the future.

When installing I have thought about using tree partitions.
[LIST]
[*]Swap
[*]Root
[*]Vmware vhd
[/LIST]

When reading about how to optimize vwware I found this:
>     Disks, Disks, Disks: I always attempt to put my guest OSs on their own partition and I format that partition thusly because VMWare server reads guests in huge blocks (/dev/sdb1 is the partition my guests reside on):

    mke2fs -b 4096 -R stride=8 /dev/sdb1

    Then I set the block readahead value to somewhere around 16384, but you can go as high as twice that value (in my case this is an entire disk array, so I dropped the partition indicator):

    blockdev –setra 16384 /dev/sdb

How should I setup the file system on each partition? When using an SSD, each partition should be aligned. How do I do that?
Let say I would like to have 4GB swap, 60GB root and the rest for vmware.

At last, I have fount out that full support for TRIM is supported by kernel v2.6.33. Ubuntu 10.04 is using v2.6.32? If so, for full TRIM support I must upgrade kernel to v2.6.33.

---

### Post by Katchina on 2010-05-31
Hello,

I'll start working on a similar setup (Ubuntu 10.04 + VMWare Server, running on SSD drive(s)) in a few weeks.  Have you got any feedback to share after your own experience ?

Best regards,

J.

---

