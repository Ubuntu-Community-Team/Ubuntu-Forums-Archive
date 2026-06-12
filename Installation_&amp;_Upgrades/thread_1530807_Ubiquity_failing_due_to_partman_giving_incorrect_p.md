---
title: "Ubiquity failing due to partman giving incorrect partition paths"
date: 2010-07-14
forum: Installation &amp; Upgrades
---

### Post by Dark_Neo on 2010-07-14
I've been trying to install Ubuntu Lucid on my new machine with an nVidia RAID 1 setup (2x 1TB SATAII drives). I've got the drives partitioned, but Ubiquity refuses to format them. I've dug around in the code to find that it's because partman thinks the partitions device nodes are named: /dev/mapped/[raid_name][partition number]

However they're actually named: /dev/mapped/[raid_name]p[partition number]

I would file a bug report for this, but I'm not sure if it would be a bug in partman, or a bug in whatever creates the device nodes for the drives (which until today I would have assumed was partman - but I don't have a great understanding of the Debian arch)

Also if anyone has any ideas on how to fix this, please let me know. I tried a quick hack of altering ubiquitys' gparted-server to add in the 'p', but then ubiquity tries to use a feature of partman to format the partition, which promptly fails due to the incorrect name. I've also tried a last ditch attempt to create symlinks for the device nodes, unsurprisingly this caused a segfault in partman.

I've also tried manually formatting the partition, but ubiquity still fails to install, although I've yet to thoroughly investigate why that is (it complains about not being able to remove system folders - that don't actually exist, so the same naming problem is cropping up somewhere else).

---

### Post by phillw on 2010-07-14
Hi,

I don't have RAID, but do have empathy for those installing it. HowToForge are a good site for instructions, so I can recommend you have a look at [http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub2-configuration-ubuntu-10.04](http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub2-configuration-ubuntu-10.04)

As it is a clean installation you are wanting, those instructions should be fine for you they are excellent step by step instructions.

Regards,

Phill.

---

