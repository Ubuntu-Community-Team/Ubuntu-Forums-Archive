---
title: "RAID1  &amp; lvm boot problem"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by g0ng on 2008-11-28
Hello, 

let me describe what I did and tell you my problem.

I had a running system where I put on 2x500 SATA disks. I made two equally sized partitions in each disk. The first is for /boot. the other was made linux autoraid type and made a /dev/md0 device with them. I also made an lvm and splitted it in three partitions.

then I copied my entire system in one of the lvms and the /boot partition to the first partitions of the two disks. I enabled in initramfs modules the appropriate modules for raid and ext3. I also installed grub on the MBR of the disks.

The I boot from this disk. The problem is that while the kernel loads it cannot find / in the lvm I have told it to through UUID. The reason is that it cannot find /dev/md0. I get in a initramfs prompt.

If I write : 
mdadm --assemble /dev/md0 /dev/sdb2 /dev/sdd2 and exit the prompt it continues loading OK from the raid.

so the problem is how to make this permanent.

I tried (from the new system in the RAID) to update-initramfs -u but still booting doesn't recognize the md0. I also tried to unzip|cpio the initrd image put in /etc/mdadm/mdadm.conf the line ARRAY=... for the md0,then  make the image again but with no luck.

Any solution to this? Any help is appreciated

---

