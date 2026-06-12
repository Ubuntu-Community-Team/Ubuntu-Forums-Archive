---
title: "Multiboot with Windows"
date: 2012-08-16
forum: Installation &amp; Upgrades
---

### Post by matkobrcko on 2012-08-16
I am trying to install ubuntu on a pc already running windows7 os. I have got 3 volumes on my hard disk. 1st C drive is where windows is installed, second drive A is where I want to install ubuntu and 3rd is used for backup. 
When I run installation from my USB it gives my options 1. Windows installation detected install then side by side chosing between them at start#up.
2.Use entire hard drive
3.Specify partitions manually (advanced)
I went for 3rd option but when I selected A drive it wouldnt let me go further.
Does anybody know how could I possibly install ubuntu on my A drive only. I dont want two different OS running on the same volume.
Can anybody help please???

---

### Post by darkod on 2012-08-16
If the destination is a ntfs partition, linux doesn't install on ntfs. You will need to delete that partition, and create the ubuntu partitions into that unallocated space.

You can create the standard root + swap partitions, or also a separate /home partition if you want to.

---

### Post by ajgreeny on 2012-08-16
Using the live CD or USB that you are going to install from, can we see the output of ```
sudo fdisk -l
``` please.  That will tell us what partitions you already have, and give us some idea of how best to proceed.

---

### Post by smartboyhw on 2012-08-16
Please, use Windows to get rid of the Ubuntu partition, and then use the first option to install. It will give you an option to choose how big the disk is and helps you to multiboot easily.

---

### Post by matkobrcko on 2012-08-16
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x89d7bd46

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       15201   121993216    7  HPFS/NTFS
/dev/sda3           15201       30401   122096640    f  W95 Ext'd (LBA)
/dev/sda4           30401       60802   244192256    7  HPFS/NTFS
/dev/sda5           15201       30401   122095616    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       16619   133487050+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x584c9ad4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488384032+   7  HPFS/NTFS

Disk /dev/sdd: 16.1 GB, 16131293184 bytes
255 heads, 63 sectors/track, 1961 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        1961    15751701    c  W95 FAT32 (LBA)

---

### Post by matkobrcko on 2012-08-16
how do I do that?? I ve been trying to do that but it still says that no root partition has been defined. Can you help please

---

### Post by darkod on 2012-08-16
> **matkobrcko said:**
> how do I do that?? I ve been trying to do that but it still says that no root partition has been defined. Can you help please

That's because you are not setting mount point / to any partition. You have to tell the installer what partition you want to use as what, otherwise how can it know.

You start with unallocated space (maybe you will need to delete one ntfs partition to create the unallocated space first). In that unallocated space you create new primary or logical partition, in the Use As select ext4, mount point /.
For the small swap partition, the Use As is swap area and it doesn't use mount point.
If you decide to create separate / home, make another ext4 partition with mount point /home.
For the bootloader destination select the MBR of the disk, like /dev/sda, /dev/sdb, etc, without any number in it.

That's it.

After it installs and you restart, go into BIOS and make sure you are booting the disk with ubuntu as first option.

---

### Post by ajgreeny on 2012-08-16
OK, do you want to install Ubuntu to the 160GB disk, /dev/sdc?  It will be easy to do so if you delete the ntfs partition on that disk either with the ubuntu installer, or with windows disk management, it does not matter which.

Then when you install ubuntu I suggest you choose the "Something Else" option and follow the instructions at [Separate home at install.]("http://www.psychocats.net/ubuntu/installseparatehome").

---

### Post by matkobrcko on 2012-08-16
Thanks a lot problem solved

---

