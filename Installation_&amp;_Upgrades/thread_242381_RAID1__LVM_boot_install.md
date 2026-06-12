---
title: "RAID1 / LVM boot install"
date: 2006-08-23
forum: Installation &amp; Upgrades
---

### Post by waltsjc on 2006-08-23
OK, I'm going nuts here.

I've been trying to setup a raid1 /boot, LVM root system. I have both the standard install and alternative ISO's for "server".

First, I can't get it to use grub. It insists on using lilo. Grub works AWESOME with raid / lvm on Centos, so I can't understand the why dapper won't use it. 

That said, I go through the install, creating 2 raid1 mirrors, the first for /boot, and the second for LVM where root (and a couple other partitions) lives.

For some bizzare reason, it is NOT using the /boot partition, but instead creating /boot inside the LVM root partition.

Anyway, during boot it finds my LVM partitions (4 logical volume(s) in group "main" now active) and gets to running /scripts/local-premount, then starts having problems. It prints a modprobe usage message (like it was called with no parameters) and then "Can't read /etc/fstab: No such file or directory". Then I'm dumped into a busybox shell.

I can see my partitions in /dev/mapper/*, and can manually mount them.

So it looks like either lilo or some script is borked and NOT mounting the root fs at all. The lilo config all looks good, with the right "root=" line and everything.

It would be Very helpful if the installer was smart enough to do RAID / LVM out of the box with grub like Centos can, but even just a good "dapper" version of the howto would be cool.

Any ideas?

---

### Post by zitch on 2006-08-23
I was working on such a [how-to]("https://help.ubuntu.com/community/FileServerOnLVMOnRAID1?highlight=%28lvm%29") a while back.  I was trying to figure out how to do LVM on a RAID1 while providing screenshots.  Unfortunately, I did the mistake of including the /boot partition in the screenshots, so I was hoping to redo them but I haven't had time to do so yet.

Did you notice the error when setting up LVM after you've setup the RAID arrays?  There's a workaround in the bugs section, but I've also observed that you may have issues unless you wait for the sync process finishes after setting up the raid arrays before continuing on to LVM.  You can check this by Alt-F2 and running "cat /proc/mdstat" until it indicates that the syncing is finished.

ADD: Also, when setting up the partitions, be sure the /boot section is setup properly after you've setup LVM.  I've found that the partitioner seems to forget that you want that /boot partition after setting up the LVM.

Please update here if you find out anymore info.

---

