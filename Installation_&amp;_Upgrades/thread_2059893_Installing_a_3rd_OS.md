---
title: "Installing a 3rd OS"
date: 2012-09-19
forum: Installation &amp; Upgrades
---

### Post by ccm.vslam on 2012-09-19
Hi, right now my computer has  dual boot Windows7 and Ubuntu 11.10.

I want to install Ubuntu 12.04 without deleting Ubuntu 11.10. 
I'm really confused with how to partitioning and the install process. It would be nice to have someone show a step-by-step walkthrough on how to do this.

 I have already downloaded the iso file and prepared a bootable usb. just need to know how to partition before installation and what to click during installation.

Thanks in advance

---

### Post by darkod on 2012-09-19
It is difficult to have a walkthrough covering every possible situation. Especially since this is a triple boot, not dual boot.

General walkthrough:
1. Take a look at your disk(s) partitions. To add another OS you need unpartitioned space not belonging to any partition. Do you have any? If not, you will have to think about shrinking one of the partitions where you have free space, so you can make unpartitioned space on the disk.

2. After you make the unpartitioned space, you only need to create a root partition and optionally /home partition. It can use the same existing swap partition. Use the manual install method (Something Else) and create the root partition from the unpartitioned space (or both the root and /home partitions if that was your decision). Make it ext4 with mount points / and /home respectively.

3. For bootloader (grub2) install location select a MBR of a disk. If you have only one hdd it would be /dev/sda. If you have more, you can decide where to install it but always on the MBR, not on a partition. You also need to make sure in BIOS you are booting from that disk if you have more than one.

That's it.

It's good practice to have a full backup before starting the shrinking procedure mentioned above. Any disk repartitioning can go wrong, so you need to have a backup of everything important to you.

---

