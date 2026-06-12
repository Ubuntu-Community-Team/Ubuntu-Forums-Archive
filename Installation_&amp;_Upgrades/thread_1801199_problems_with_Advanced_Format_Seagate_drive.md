---
title: "problems with Advanced Format Seagate drive"
date: 2011-07-10
forum: Installation &amp; Upgrades
---

### Post by kingofspades8 on 2011-07-10
I normally am able to install Ubuntu without any trouble, but I was using a new hard drive with 4k blocks and 11.04 kept installing and making misaligned partitions.  So I learned how to use GNU Parted, since Seagate said in their documentation that it was supported as of version 2.x.  I made all the partitions, which according to both Parted and Ubuntu's Disk Utility are aligned fine.  But when I try to install Ubuntu AND format the drives it tells me that they're misaligned and refuses to format them (and by extension, refuses to install)

After some tinkering I found that you have to:

1.  use parted to make the partitions, 
2.  then Disk Utility to format them
3.  install ubuntu using Ubuntu's partition manager (DON'T do erase entire disk) - 
4. you'll have to set one of the partitions as / in the custom partition manager that the installer provides and then you'll be set.

Well, actually that didn't quite work, as Ubuntu appeared to install fine but then would be unable to boot.  If instead I let Ubuquity set the partitions, then Ubuntu installs and boots just fine.  Only thing is: Disk Utility is complaining that the partition is misaligned by 2560 bytes, and suggests repartitioning.

So I don't know which program is the buggy one...Ubuquity or disk utility

---

### Post by kingofspades8 on 2011-07-11
I finally got Ubuntu to install!  I've reported the bug to the Ubiquity developers:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/583790](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/583790)

Basically the solution is to make and format the partitions with Parted and/or Ubuntu's Disk Utility (palimpsest) and then manually set the mount points for Ubuntu from the alternate install CD.  See the launchpad bug report for more details.

---

### Post by Luke M on 2011-07-11
You can check the alignment with:

sudo fdisk -u -l /dev/sda

It's possible that different programs have their own idea of what "aligned" is. Some might be satisfied with 4K alignment (adequate for all current drives), while others might be unhappy with less than 1MB (I think the drive makers suggest partitioning software use 1MB alignment for future compatibility).

---

