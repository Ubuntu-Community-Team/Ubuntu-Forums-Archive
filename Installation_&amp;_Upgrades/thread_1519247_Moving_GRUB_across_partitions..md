---
title: "Moving GRUB across partitions."
date: 2010-06-27
forum: Installation &amp; Upgrades
---

### Post by BeigeFennec on 2010-06-27
Okay, my situation is an interesting one.  I have two "Ubuntu" installations, for the record.  My HDD is laid out like so:
PRIMARY - First Ubuntu
PRIMARY - Second Ubuntu [XBMC Live]
4GB Free
14GB LOGICAL
    -4GB Free
    -10GB Swap

Now, GRUB is currently on XBMC Live.  I have terminal and root access if needed, and a "Live CD" ready to use.  What I want to know is how I can move GRUB, preferably on its own partition but it can go back the the first partition.

---

### Post by wilee-nilee on 2010-06-27
I don't think your going to get much help on the UF, I hope so, but your question moving grub makes no sense. I'm not sure many are familiar with this platform. Here is a forum though that probably is if needed.
[http://forum.xbmc.org/index.php?](http://forum.xbmc.org/index.php?)

---

### Post by BeigeFennec on 2010-06-27
> **wilee-nilee said:**
> I don't think your going to get much help on the UF, I hope so, but your question moving grub makes no sense. I'm not sure many are familiar with this platform. Here is a forum though that probably is if needed.
[http://forum.xbmc.org/index.php?](http://forum.xbmc.org/index.php?)

It runs on top of a Ubuntu Kernel and it's terminal uses the typical Ubuntu commands.
The better thing may be "Restoring" GRUB, but on a partition of it's own.  Also, would the "/boot" partition need to be primary or could it be logical?

---

### Post by wilee-nilee on 2010-06-27
> **BeigeFennec said:**
> It runs on top of a Ubuntu Kernel and it's terminal uses the typical Ubuntu commands.
The better thing may be "Restoring" GRUB, but on a partition of it's own.  Also, would the "/boot" partition need to be primary or could it be logical?

I think you misunderstand grub.

It sounds like your trying to boot this I don't think it's set to be a bootable setup, but I'm not sure. There might be a gui interface though, but I don't know anything about it.

I would look through the forum I linked for information, I have only seen one other reference to this on the UF and it was a while back and they were having problems with it.

---

### Post by BeigeFennec on 2010-06-27
> **wilee-nilee said:**
> I think you misunderstand grub.

It sounds like your trying to boot this I don't think it's set to be a bootable setup, but I'm not sure. There might be a gui interface though, but I don't know anything about it.

I would look through the forum I linked for information, I have only seen one other reference to this on the UF and it was a while back and they were having problems with it.

It's bootable, just trying to get grub in a different spot, but I found some things on restoring grub, so I'm just going to follow those.

---

### Post by oldfred on 2010-06-27
I have old grub in a partition and my first install of Karmic beta I installed grub2 to that partition. But grub2 does not consider installs to a partition reliable due to block lists. I also installed grub2 to my USB flash drive to directly boot ISO files via loopmount.

If you have multiple installs you probably do not want /boot partitions. 

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition)
old grub partition
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_)
Grub2 version:
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)

---

