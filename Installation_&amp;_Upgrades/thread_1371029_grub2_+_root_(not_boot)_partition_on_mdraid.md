---
title: "grub2 + root (not boot) partition on mdraid"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by fperloff on 2010-01-02
[SIZE=1]I installed Ubuntu 9.10, 64-bit on a root partition (/), with a separate /boot partition. The system boots with grub2. Now I would like to migrate the root partition to mdraid RAID 1. I created the md drive, mounted it, and copied the root file system to it. Then I modified the stanza in /boot/grub/grub.cfg to point to the md drive rather than the "un-raided" root partition. When I reboot, I am dropped to a shell, with the error message that the root partition cannot be found. 
I have tried specifying the root partition as /dev/md_d2, as the UUID that blkid reports, and with the UUID that mdadm reports (the two UUID's are different.) I'm confident that the appropriate modules are loading, since when I am dropped to the shell, my /home file system is mounted which exists on a md raid drive. Also, I can use mdraid to assemble the root md drive.
Any thoughts on how to get grub2 to use the md drive for root (/) partition?[/SIZE]

---

