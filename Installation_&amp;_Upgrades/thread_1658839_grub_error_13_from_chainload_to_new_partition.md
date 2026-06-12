---
title: "grub error 13 from chainload to new partition"
date: 2011-01-03
forum: Installation &amp; Upgrades
---

### Post by hgu on 2011-01-03
Hi,

I tried to find an answer to this but failed, any help appreciated. I have a machine with two disc but only one is involved in the boot. It is hd0 / sda. On this I have several partitions, first I have a partion (sda1) with grub-legacy and a menu.lst file that boot by chainloading my ubuntu 10.04 on partition sda4 (with ext4 and grub 2). This works without any problems. Today I was doing a larger upgrade of my mythtv install so I first copied sda4 to sda3, did all the neccessary changes in /etc/fstab and a grub-mkconfig (so that the grub.cfg on sda4 also included sda3 kernel). The chainload manage to nicely chainload to sda4 and when I select the newly copied kernel on sda3 it boots. Now inside the booted kernel/ubuntu on sda3 I again do the grub-mkconfig so I get a correct grub menu. I add a new chainload to menu.lst on sda1 so that I can go direct from that to my new partition.

Here comes the problem, when I chainload to the sda3 (hd0,2) partition I get grub-legacy error 13 invalid or unsupported executable format. No grub2 menu from sda3 shows up and the boot halts. The grub.cfg files on sda3 and sda4 are identical besides the uuid and hd0,3/4 references.

Any ideas?

/Harald

---

### Post by hgu on 2011-01-03
Manage to solve it. I always forget that I need to install on the partitions boot sector, since I only did a copy on file system level and not disc level.

Anyway with grub2 I did

grub-install --force /dev/sda3

Use force since otherwise grub refuses due to it thinks it is a bad idea that is unreliable to install to a partition and not the MBR. Anyway it worked for me.

---

