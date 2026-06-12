---
title: "Installing a GNU/Linux distribution on an extended partition"
date: 2013-10-27
forum: Installation &amp; Upgrades
---

### Post by Canaryguy on 2013-10-27
Hello,

A friend asked me to install in his computer Ubuntu. His hard drive already had three primary NTFS partions and oen partition free. In order to install Ubuntu I created an extended partition to create a logical partition for Ubuntu and another for the Swap space. But when I was going to initiate the installation the system told me that I couldn't install Ubuntu outside the disk. So I didn't create a Swap and I installed Ubuntu in the fourth primary partition.

Is it required that at least one distribution be installed on a primary partition? In other occasions I had installed distributions in a logical partition but I had also one on a primary partition too at that time.

---

### Post by metalf8801 on 2013-10-27
I'm using logical partitions for both my / boot partition and swap partition. Does that answer your question?

---

### Post by oldfred on 2013-10-27
An outside of disk error is usually something in partition table is wrong or last partition is beyond end of drive. Installer or gparted should not let that happen. 

Unless you only had / inside the extended then tried to create swap outside the extended as primary? Both needed to be created as logical.

---

### Post by Canaryguy on 2013-10-28
> **oldfred said:**
> An outside of disk error is usually something in partition table is wrong or last partition is beyond end of drive. Installer or gparted should not let that happen. 

Unless you only had / inside the extended then tried to create swap outside the extended as primary? Both needed to be created as logical.

After I created an extended partition I put both / and swap in logical partitions but the installer indicated me something like I could not installed the system outside the disk.

As I said, there were three primary partitions used (NTFS) and an unallocated space. I resized the third of the NTFS partitions to get more free space and finally I set the extended partition with / and swap logical. All of this using GParted.

Well, my friend's computer has enough RAM (I think it was 4 Gb) so I think it is not crucial to have a swap in this case. Ubuntu is installed as a primary partition and everything seems to be working well.

Maybe something happened when the NTFS partitions were created. According to Metalf8801 there shouldn't be any problem if a person wants to install a Linux distributions only in a logical partition. So I don't know what the problem was.

---

