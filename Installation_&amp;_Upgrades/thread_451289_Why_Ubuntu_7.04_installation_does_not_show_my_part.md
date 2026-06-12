---
title: "Why Ubuntu 7.04 installation does not show my partitions?"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by Osvaldas on 2007-05-22
Hi there,

I have been using Ubuntu 7.04 64bit architecture version for few days. There was one but basic problem: some of x86 software simply do not work on 64bit version. So I decided to remove this and install 32bit Ubuntu version.

Successfully booted CD with NOAPIC option (it's because of my AMD 64bit X2 processor). Then, I passed 3 steps of installation. On the 4th step (partitioning) I was stopped - in the list of available partitions I saw only one entry: */dev/sda/*, while I am having four partitions on my hard drive: *NTFS*, *FAT32*, *Swap* and *Ext3*. BUT, I had no such a problem with 64bit version installation.
This is some kind of insane!

Any ways to sort it out?

Thanks for any kinda help!

---

### Post by taurus on 2007-05-22
You can always try the alternate CD version.

---

### Post by Osvaldas on 2007-05-22
It's ok now. Problem is solved. There was a conflict among partitions. Partition Magic was a magic tool ;-)

---

