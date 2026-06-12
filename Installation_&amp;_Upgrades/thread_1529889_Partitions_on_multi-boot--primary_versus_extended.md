---
title: "Partitions on multi-boot--primary versus extended?"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by NoHolyGrail on 2010-07-12
I'm setting up my laptop to dual boot (default Vista installation and Ubuntu).  There's also a possibility I may add XP later as a triple boot.

My laptop came with two partitions already, the second one labelled "Recovery".  I was planning on adding three partitions, one for the Ubuntu installation, one for Swap, and one for storing my files (accessible to both OSs).  However, this would be five partitions (or six, if I add XP later).

I've never had to deal with this many partitions before and just learned about the maximum of four primary partitions.  How should I handle this situation?

---

### Post by oldfred on 2010-07-13
Ubuntu can be in logical partitions. One of the primary parititions can be converted to an extended partition which can hold many logical.

[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)
[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)


If you plan on XP reserve another primary partition.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by NoHolyGrail on 2010-07-16
Thanks for this information.

I cleared some unallocated space between C: (Vista) and D: (Recovery), so I'm going to format that as an extended partition to house logical partitions for Ubuntu & Swap.

I think this should give me the flexibility to later shrink C: some more to make room for another primary partition for XP, or to expand my extended partition if necessary (for example, to add a logical partition for /home, which I don't have space for at the moment).

Does this sound like it should work?

---

### Post by oldfred on 2010-07-16
As long as you plan ahead a little it helps. If low on room then a new hard drive will probably be on your list in the near future.

---

