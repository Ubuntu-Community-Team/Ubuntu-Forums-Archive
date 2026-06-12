---
title: "USB Micro SD Partition Editor"
date: 2010-12-23
forum: Installation &amp; Upgrades
---

### Post by pcsel on 2010-12-23
Hi everyone.. I have checked the forums but can't find a topic that covers this.

I have an 8Gb Micro SDHC in a micro reader that I installed 10.10 onto from the Alternate DVD. Unfortunately I neglected to set up the \swap and \home volumes and I now have a stick with all 8GB used up.

I have configured up Ubuntu to my liking and also added some applications. I would prefer not to lose this and I don't appear to be able to adjust the partition table live to now accommodate the swap and home areas.

Is there a way to do it live or can I boot from the DVD again and adjust the one partition to three such as 4 GB root, 2G Swap and 2 Gb Home?

Many Thanks in advance

Paul

---

### Post by metalf8801 on 2010-12-23
Try booting from Parted Magic and use Gparted unless the alternative DVD has gparted on it. [http://distrowatch.com/table.php?distribution=partedmagic](http://distrowatch.com/table.php?distribution=partedmagic)

I hope this helps
Dan

---

### Post by efflandt on 2010-12-23
If you do not want to lose what is on your 8 GB partition you will need to "resize" that partition down (which you can do from gparted live CD), rather than removing it.  For flash memory like that ext2 file system would make sense (ext3 or ext4 journaling adds write cycles).

And you do not necessarily need swap unless you want to hibernate, or do not have enough RAM (you do not need swap to suspend).  If you do use swap on flash RAM, you may want to set swappiness to 1 to minimize its use (scroll down to swappiness at [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) ).

---

