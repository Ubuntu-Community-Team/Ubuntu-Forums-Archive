---
title: "partitioning"
date: 2005-05-13
forum: Installation &amp; Upgrades
---

### Post by mdinkens on 2005-05-13
I used partition magic to make another primary partition but can't find out how to boot the install disk to that partition.  who can give me some advice?  My goal is to dual boot as I need my windows 98 for business.

---

### Post by nad on 2005-05-13
The install disk boots its' own operating system.

During the install process, you will be asked where you wish to install to when you get to the 'partition disks' menu. Here you will have to manually select your chosen partition and tell the installer to use it as the / (root) of the ubuntu filesystem. You will also need to tell the installer to use the ext3 type filesystem and format it before the installer will continue.

Please read the menus carefully and note that no changes are made until you choose 'write partition information to disk'.

There is more information here regarding installation in a dual boot environment. You may wish to research this to become more familiar with what you are about to do. Ubuntu will co-habitate with win98 without problems.

---

### Post by exile on 2005-05-13
Do you mean that you want to know what the new partition would be called when you are doing an ubuntu install? I'm going to assume that you can boot from the CD already.

I usually keep a pen and paper around when I work with partitions. When I repartition I note the size, types (for unix/linux resizes), and position (is it a master or a slave hdd or is there only one etc?) of the partitions. Then when I go to install I use the size as a guideline.

For example:

A single hard disked (non SATA drive) windows machine would have the partition called C: which would equate to /dev/hda1

If after the resize you made the windows partition 40Gb and the new partition 20Gb
then I'd expect to see /dev/hda1 40Gb and /dev/hda2 20Gb.

When installing select the second partition.

SATA hard drives are a different beast that I can't really help you with.

If I've misunderstood and you've already installed Ubuntu but having trouble booting post install then that is probably something going on with the boot loader.

Good luck!

---

