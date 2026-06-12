---
title: "Multiple OS's on a disk with LVM setup."
date: 2010-03-27
forum: Installation &amp; Upgrades
---

### Post by neilevan814 on 2010-03-27
I want to be able to install multiple operating systems on a disk setup with LVM.  I am uncertain as to how to go about this.  

I read somewhere that you can do it, but that only one /boot partition should used for all systems(they are all linux).  

Can anyone explain how to get going on this?  Do I boot from an installation disk and follow that path some how...or is there some other method I should be following? And how do I use one boot partition for all OS's?  I had a problem with this once before..so need to ask, especially with the LVM thrown in the mix.

[IMG]http://lh4.ggpht.com/_rXW4XqYLz5U/S67uJoPbuaI/AAAAAAAABok/0Itvhwc6_3s/s800/Screenshot.png[/IMG]

[IMG]http://picasaweb.google.com/lh/photo/tVEGK7WSTjgPPrO2Xbz1tA?feat=directlink[/IMG]

---

### Post by stlsaint on 2010-03-27
Not to sound mean or high and mighty but i suggest that you do some serious reading/studying on how LVM works. As having multiple os all working of lvm can get very difficult and can result in loss data or damaged installs. Based off the type of questions you are asking it seems that you are fairly new lvm and dual booting or triple booting. Also sharing a /boot will cause you to have a partition probably in an extended volume outside your lvm which then causes you to manually mount that it. Here is a good guide to start with. [LVM ]("http://www.howtoforge.com/linux_lvm")

---

### Post by srs5694 on 2010-03-27
To some extent I agree with stlsaint, in that neilevan814 should read up on LVM basics; however, I disagree that it's really all that dangerous. I put codes in my logical volume names to distinguish which distribution each one belongs to (e.g., "ubuntu9_root" or "gentoo_usr"). Personally, I find LVM to be a great tool for installing multiple Linux distributions on one computer, particularly over time. That is, as one distribution ages I can upgrade it while keeping the old one temporarily in place, then delete the old one and re-use its space in whatever way is convenient (say, to upgrade the second distribution).

Although I've tried sharing a single /boot partition, I find that I have fewer problems if I use separate /boot partitions for each distribution. My current practice is to set aside three ~200MB partitions for use as /boot partitions. These can be either primary or logical partitions in an MBR configuration, although I prefer GPT these days. (One minor benefit of GPT for this is that I can label each partition in the partition table, so I can identify which /boot partition goes with which distribution.)

Unfortunately, the last I checked the standard Ubuntu desktop installer doesn't support LVM, so to use Ubuntu with LVM you've got to use the alternate or server installer.

---

### Post by neilevan814 on 2010-03-27
Thanks to both of you for your suggested readings and advice.  I have ubuntu studio amd64 installed and it did come with the lvm partitioning option, so it is as ubuntu studio set it up.  My intentions with this disk is to do what srs5694 has done.  I am always experimenting with programs and distributions and constantly changing operating systems.

I will definitely continue studying LVM and the best /boot method to use.

---

### Post by stlsaint on 2010-03-27
> **srs5694 said:**
> To some extent I agree with stlsaint, in that neilevan814 should read up on LVM basics; however, I disagree that it's really all that dangerous. I put codes in my logical volume names to distinguish which distribution each one belongs to (e.g., "ubuntu9_root" or "gentoo_usr"). Personally, I find LVM to be a great tool for installing multiple Linux distributions on one computer, particularly over time. That is, as one distribution ages I can upgrade it while keeping the old one temporarily in place, then delete the old one and re-use its space in whatever way is convenient (say, to upgrade the second distribution).

Although I've tried sharing a single /boot partition, I find that I have fewer problems if I use separate /boot partitions for each distribution. My current practice is to set aside three ~200MB partitions for use as /boot partitions. These can be either primary or logical partitions in an MBR configuration, although I prefer GPT these days. (One minor benefit of GPT for this is that I can label each partition in the partition table, so I can identify which /boot partition goes with which distribution.)

Unfortunately, the last I checked the standard Ubuntu desktop installer doesn't support LVM, so to use Ubuntu with LVM you've got to use the alternate or server installer.

I really was meaning that it can become a bit troublesome when you start dealing with removing broken hdd and adding new LVM groups/fixing LVM groups, etc. Not so much that its prone to destruction. Just giving a warning to do plenty of research and ask as many questions as you need before putting lvm into full swing on a production system.

---

### Post by srs5694 on 2010-03-27
> **stlsaint said:**
> I really was meaning that it can become a bit troublesome when you start dealing with removing broken hdd and adding new LVM groups/fixing LVM groups, etc. Not so much that its prone to destruction. Just giving a warning to do plenty of research and ask as many questions as you need before putting lvm into full swing on a production system.

True, if a hard disk fails catastrophically and completely, it may be difficult or impossible to recover any data from *either* drive, especially if you use an LVM striping system. If a disk is just starting to show signs of impending failure (SMART warnings, say), adding a new one isn't too hard. I recently replaced an 80GB drive with a 500GB unit to get more disk space and it went pretty smoothly. I added the new disk to the volume group, issued the commands to remove and deactivate the old disk, and it was done. Of course, it took a while to copy the data, but the system continued to function during all this, so it was pretty painless.

---

### Post by neilevan814 on 2010-03-28
[IMG]http://picasaweb.google.com/lh/photo/tVEGK7WSTjgPPrO2Xbz1tA?feat=directlink[/IMG]I have started reading some of the links given by Stlsaint.  I really should have a better understanding of grub and that will most likely help in deciding what to do next before installing another distribution to a new partition.  I have included a snapshot of my fdisk -l of sda my lvm drive and sdb a larger storage drive not with lvm.  
It appaears to me that the mbr was installed to sda1, a partition fixed with lvm?  I have read in other places that people seem to use an ext3 partition for boot and then begin a volume group.
If I am installing to a new logical partition in this hdd volume group, when the install asks where to install grub, what would I say?

[IMG]http://lh4.ggpht.com/_rXW4XqYLz5U/S67uJoPbuaI/AAAAAAAABok/0Itvhwc6_3s/s800/Screenshot.png[/IMG]

---

### Post by srs5694 on 2010-03-28
> **neilevan814 said:**
> [IMG]http://picasaweb.google.com/lh/photo/tVEGK7WSTjgPPrO2Xbz1tA?feat=directlink[/IMG]I have started reading some of the links given by Stlsaint.  I really should have a better understanding of grub and that will most likely help in deciding what to do next before installing another distribution to a new partition.  I have included a snapshot of my fdisk -l of sda my lvm drive and sdb a larger storage drive not with lvm.  
It appaears to me that the mbr was installed to sda1, a partition fixed with lvm?

No. The Master Boot Record (MBR) is the first sector on a hard disk. Period. In most partitioning systems, including the like-named MBR partitioning system and the newer GUID Partition Table (GPT) partitioning system, the MBR does not reside in any partition. The MBR is not "installed to" anywhere; it simply is.

You're probably thinking of installing the GRUB boot loader. That can be installed to the MBR or to a partition. GRUB is not normally installed to an LVM partition. I don't know offhand if it's even possible to do so. In an LVM configuration, you'd normally install GRUB either to the MBR or to the boot sector of your /boot partition (probably /dev/sda5 in your case -- but see below).

> I have read in other places that people seem to use an ext3 partition for boot and then begin a volume group.

Personally, I prefer ext2 for the /boot partition, since a journal doesn't improve the fsck time all that much on such a small partition, but it does consume a significant amount of space on such a small partition.

> If I am installing to a new logical partition in this hdd volume group, when the install asks where to install grub, what would I say?

What do you mean by "installing to a new logical partition in this hdd volume group?" I think you mean "logical volume," not "logical partition." A logical partition is a partition that resides within an extended partition in the MBR partitioning system. Logical partitions have partition numbers of 5 and above in Linux's partition numbering scheme. A logical volume, OTOH, is an LVM data structure. Both can be used to hold filesystems or data structures, but they're very different in how they're managed and in their capabilities.

As I wrote above, GRUB normally goes in the MBR or in a /boot partition's boot sector. If the /boot partition is a logical partition and you put GRUB there, whatever boot loader goes in the MBR must be able to redirect the boot process to a logical partition. (Not all boot loaders can do this.) You do not normally install GRUB in a logical volume. Since your only non-LVM partitions are extended partitions (which are placeholders for logical partitions) or logical partitions, it's probably best for you to install GRUB to the MBR.

---

