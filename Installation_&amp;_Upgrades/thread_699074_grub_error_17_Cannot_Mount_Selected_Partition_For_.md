---
title: "grub error 17: Cannot Mount Selected Partition For Raid 0: USING FAKERAID HOWTO"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by AverageJoeSSU on 2008-02-17
Hello,

I am almost finished with installing Ubuntu on my RAID 0 and i am running into a problem setting up grub. I am following the RAID HOWTO exactly as far as i can tell.

here is some info....

partition table: msdos

Disk /dev/mapper/nvidia_ddebcejd

(parted print results)

2  ... ext3 /boot
1 .... reiserfs /
3 .... linux swap 

my /boot/grub/ folder has the e2fs_stage1_5, stage1, stage2, and fat... folders.

i get to the part where i need to run grub....

grub> device (hd0) /dev/mapper/nvidia_ddebcejd

grub> root (hd0, 1)

grub> setup (hd0)

Error 17: Cannot mount selected Partition

grub>


Any help would be greatly appricated.... 

dmraid recognizes the partitions as well... so that isnt the problem

---

### Post by Pumalite on 2008-02-17
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by AverageJoeSSU on 2008-02-17
Fixed, there were flags set on the partitoins (by parted) that screwed up grub... one step closer! i think im almost done haha

---

### Post by Schnapphase on 2008-04-04
Hello,

I've got the same problem with my Ubuntu 7.10 installation on a fakeraid0. grub only reads my NTFS-partitions and ignores the ext3-partitions, so that I can't mount my /boot partition.

Which flags do you mean and how can I fix this problem?

---

