---
title: "Computer will not boot, boot repair ideas requested"
date: 2016-05-19
forum: MINT
---

### Post by liam31 on 2016-05-19
Hello.  If anyone out there can help me evaluate a boot problem, it would be greatly appreciated.  I have four disk drives on my desktop, a Samsung 250gb SSD is my boot drive.  I am running Linux Mint 17 without dual boot.

The error message I get is odd; the computer puts up four green dots on the screen, then finally tells me that one of my drives (iTunes Drive) is not ready or not present.  Here is my Disk Repair file... [http://paste2.org/2gUUFc64](http://paste2.org/2gUUFc64)

Any help would be greatly appreciated.

liam

---

### Post by oldfred on 2016-05-19
Moved to Mint sub-forum, since not Ubuntu.

Best not to run Boot-Repair's auto fix with multiple drives. Use advanced mode and only install grub to same drive as your install.

You also show Windows on sdd2, but no bootmgr nor /Boot/BCD. Windows uses boot flag to find those files to know which partition. But grub2's os-prober looks for those files. You need to repair Windows and best to reinstall Windows boot loader into MBR of sdd, so from BIOS you can directly boot Windows. Grub only boots working Windows and you may need to get into repair console or safe mode to fix Windows. Probably even better to make the Windows repair flash drive.

If you left Windows hibernated or needing chkdsk then Linux NTFS driver will not mount it, to prevent damage that chkdsk may then not be able to fix. If now really Windows 8 or 10 then it is hibernated if the fast start up is on.

Once I started using Linux I stopped using spaces. So I use CamelCase, under_score or justonename. Then you can avoid all the \040 issue. Not sure if , (comma) allowed either, some special characters should be avoided.

Use of labels should be ok, if label is valid, typical entry using UUID:
 UUID=44332FD360AA9657 /mnt/shared ntfs-3g defaults,uid=1000,nls=utf8,windows_names 0 0 
   Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problem as well:

---

### Post by liam31 on 2016-05-22
OldFred.  Thank you for your thoughtful reply.  I tried to look at the mess that I created with multiple drive and multiple names, all renamed since I loaded the operating system.  Since I did not have that much invested in the overall installation, I reloaded the operating system from scratch.  The third install of Mint.  Now, I will be much more careful when setting up drive naming. 

Also, I should mention that the Windows that I have stashed on one of the drives is simply a backup and I should completely delete the associated files and folders.  In your reply, were you thinking that the Windows on sdd2 was cause for the machine to not boot?

 Again, thanks for your review.

---

### Post by oldfred on 2016-05-22
The issue on Windows was just on booting that copy of Windows. Windows 7 or later in BIOS mode normally installs in two partitions. A 100MB boot partition with bootmgr & BCD and main install.  If backing up Windows you need both partitions. Or you can install/repair bootmgr & BCD into main install partition to make it directly bootable. Not sure if f8 for recovery/safe  mode then works or if that file is just in boot partition.

With multiple drives, I like to to have a full install of Ubuntu on every drive, that can boot without any other drive. Even if primarily a data drive.
       Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and keep a current testing one on every drive.

---

