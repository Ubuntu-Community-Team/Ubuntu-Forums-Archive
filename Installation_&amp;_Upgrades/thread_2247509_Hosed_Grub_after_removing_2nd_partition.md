---
title: "Hosed Grub after removing 2nd partition"
date: 2014-10-08
forum: Installation &amp; Upgrades
---

### Post by DVD-R on 2014-10-08
Hi all!
I divided my hard-drive into two partitions and one Linux swap space.
I had Ubuntu 12.04 on both partitions.... Studio, in the first one, and MATE in the second one.
I needed more room for the Studio system and decided to remove the MATE files and expand the Studio install so that it uses all of the HD except the swap.
I booted up on CD Gparted, but my guess is that Gparted saw the swap partition and decided to use it on the GParted install.
So this essentially block my ability to resize the partitions.
Resizing often times requires turning off the swap, which can typically be linked to the extended partition one needs to resize.
So I pulled the hard drive, re-booted into Gparted and accessed the Hard drive via a external USB hard-drive cradle.
And then I was able to deleted the MATE system and resize the Studio so have all of the HD except swap.

However, in the process I must have messed up boot-loader as all I get now at boot-up is the word "GRUB"
I tried mounting the folders that grub accesses using the mount --bind commands, and then updating GRUB.
But no luck.
I wonder if I'm going to have to copy the HOME folder off the Studio into a thumb-drive and re-install it?
I wonder if there is a GRUB rescue ISO I can download and use to restore GRUB settings to the system without doing a full re-install?
Any suggestions are most welcome!!  :-]
Thanks,
got_ubuntu!

---

### Post by zvacet on 2014-10-08
Try [Boot repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by yancek on 2014-10-08
The boot-repair should fix the problem.  It would seem that you had the Ubuntu Mate Grub installed to the master boot record which would explain the problem you are having.  You could have avoided that problem by booting into Studio and doing:  sudo grub-install /dev/sda, that is if it is on sda and you only have the one drive.

---

