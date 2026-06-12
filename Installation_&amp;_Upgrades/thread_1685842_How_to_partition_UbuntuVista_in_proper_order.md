---
title: "How to partition Ubuntu/Vista in proper order"
date: 2011-02-11
forum: Installation &amp; Upgrades
---

### Post by F8M on 2011-02-11
Please refer to post #6 b/c I have rearranged my partition.

---

### Post by KeLa on 2011-02-11
If you don't get any other better advice then do this:
1. Start from fresh.
2. Install windows vista
3. Install ubuntu.
After that everything should be ok.
But as you know this is the so called easy fix.

---

### Post by F8M on 2011-02-11
The only problem I will have with this setup is with the important data I need in Ubuntu. How can I do this without losing the data in Ubuntu.
Thanks for the quick reply

---

### Post by KeLa on 2011-02-11
If your important data is in your home directory then you can try following:
1. Connect external usb disk to your computer.
2. Open terminal (it will open to your home directory)
3. Execute following command:
rsync -rit --del . /media/yourusbdisk/backupfolder/
That will copy everything from your home directory to the usb disk.
I have extra internal disk on my ubuntu box and its mounted as /media/data
and i use command rsync -rit --del /home/username /media/data/username
as a backup system.
It will copy everything (including hidden files and folders)

---

### Post by P4man on 2011-02-11
AFAIK, its not a problem that they are not in order. However, windows doesnt like being installed to anything other than the first primary partition. You may have to move your linux partition, so you can install windows "before" ubuntu, on sda1, or rather, on the first partition. You can do that from a livecd, delete the ntfs partition, move your ext4 partition, then install windows upon the empty space. You will have to reinstall grub, but you will have to do that anyway after installing windows.

---

### Post by F8M on 2011-02-11
Ok, I changed the order of the partition as shown below and I selected Vista(/dev/sda3) to boot from.

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x69664f0a
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12162    97682420    7  HPFS/NTFS

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00012bcc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           27967       38164    81915435   83  Linux
/dev/sda2           38165       38914     6013953    5  Extended
/dev/sda3   *           1       27966   224636863+   7  HPFS/NTFS
/dev/sda5           38165       38914     6013952   82  Linux swap / Solaris
Partition table entries are not in disk order

But after installing Vista & rebooting OK, I reinstalled Grub2 for Ubuntu and reboot with only Ubuntu showing up. It did NOT give me the option of either booting from Windows or Ubuntu. PLEASE help, thanks.

---

### Post by F8M on 2011-02-11
I need help in getting my bootmgr to boot with both Windows & Ubuntu. Thanks

---

### Post by presence1960 on 2011-02-12
> **F8M said:**
> When I type in "sudo fdisk -l" command, it say that my partition is not in order.

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x69664f0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12162    97682420    7  HPFS/NTFS
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00012bcc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10199    81922443+  83  Linux
/dev/sda2           38165       38914     6013953    5  Extended
/dev/sda3           10200       38164   224628862+   7  HPFS/NTFS
/dev/sda5           38165       38914     6013952   82  Linux swap / Solaris
Partition table entries are not in disk order

The following is what my partition looks like in the Gparted:

Partition------File_System---Size
unallocated--unallocated---1.0  MB
/dev/sda1------ext 4--------78.13 GB
/dev/sda3-------ntfs--------214.22 GB
unallocated--unallocated---4.49 MB
/dev/sda2-----extended-----5.74 GB
/dev/sda5----linux-swap----5.74 GB

How to I go about putting partition in right order so I coulde install Vista? Please help, Thank you.


It can be fixed this way:

Code:

```
sudo fdisk /dev/sda
x
f
w

```

---

### Post by F8M on 2011-02-12
The following is done w/the live CD.

When I type in the command 'sudo fdisk /dev/sda', I get the following warning:
WARNING: DOS-compatible mode is deprecated. It's strongly recommended to switch off the mode (command 'c') and change display units to  sectors (command 'u').

Command (m for help): 


Here is the result of 'sudo fdisk -l' after rearranging my partition.

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x69664f0a
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12162    97682420    7  HPFS/NTFS

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00012bcc
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           27967       38164    81915435   83  Linux
/dev/sda2           38165       38914     6013953    5  Extended
/dev/sda3   *           1       27966   224636863+   7  HPFS/NTFS
/dev/sda5           38165       38914     6013952   82  Linux swap / Solaris

Partition table entries are not in disk order


I don't know why, but every time I boot from the live CD I have to go into Gparted to uncheck '/dev/sdb1'.
Here is another question. Knowing that you can only boot from one source(either sda1 or sda3), that it matter which one you choose - what's the difference?
Thank you.

---

### Post by presence1960 on 2011-02-12
> **F8M said:**
> The following is done w/the live CD.

When I type in the command 'sudo fdisk /dev/sda', I get the following warning:
WARNING: DOS-compatible mode is deprecated. It's strongly recommended to switch off the mode (command 'c') and change display units to  sectors (command 'u').

Command (m for help): 


Here is the result of 'sudo fdisk -l' after rearranging my partition.

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x69664f0a
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12162    97682420    7  HPFS/NTFS

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00012bcc
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           27967       38164    81915435   83  Linux
/dev/sda2           38165       38914     6013953    5  Extended
/dev/sda3   *           1       27966   224636863+   7  HPFS/NTFS
/dev/sda5           38165       38914     6013952   82  Linux swap / Solaris

Partition table entries are not in disk order


I don't know why, but every time I boot from the live CD I have to go into Gparted to uncheck '/dev/sdb1'.
Here is another question. Knowing that you can only boot from one source(either sda1 or sda3), that it matter which one you choose - what's the difference?
Thank you.

Go ahead and run the commands. That is a standard warning that appears.

---

### Post by F8M on 2011-02-12
After going ahead, I received the following:

Command (m for help): x

Expert command (m for help): f
Nothing to do. Ordering is correct already.

Expert command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table. The new table will be used at
the next reboot or after you run partprobe(8) or kpartx(8)
Syncing disks.

After doing this with my computer still using the Live CD, I checked my partition in Gparted and noticed that there was a problem with the /dev/sda1 (Vista).

Partition---------File-System--------Label---------Size--------Flags
/dev/sda1(WARNING)-ntfs-----------Vista-------214.23GB-----boot-
/dev/sda2-----------ext4------------Ubuntu---------78.12GB---------
unallocated------unallocated------------------------4.49GB---------
/dev/sda3--(key)--extended--------------------------5.74GB---------
/dev/sda5--(key)--linuxswap-------------------------5.74GB---------

Now because of the WARNING in ntfs, should I still go ahead and reboot or should I first fix the ntfs file.

---

### Post by F8M on 2011-02-12
Sorry about the inconvenience, but post#11 was repeated 3 times.
Please help me - - - Thank you.

---

### Post by F8M on 2011-02-12
Sorry about the inconvenience, but post#11 was repeated 3 times.
Please help me - - - Thank you.

---

### Post by F8M on 2011-02-12
After repairing the ntfs file by deleting it and installing a brand new one, the error did not show up in the Gparted.

So after putting your commands, the following is the message I got:

ubuntu@ubuntu:~$ sudo fdisk /dev/sda
WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): x

Expert command (m for help): f
Nothing to do. Ordering is correct already.


Expert command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table. The new table will be used at
the next reboot or after you run partprobe(8) or kpartx(8)
Syncing disks.

After all this work, it eliminated the boot-up command from showing up in the /dev/sdb1. But still, once I rebooted without the CD, it did not dual boot but went to the Ubuntu. My real question is (out of frustration), how do you dual-boot without losing my Ubuntu data files. Thank you

---

