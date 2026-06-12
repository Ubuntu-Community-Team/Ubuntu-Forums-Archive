---
title: "How much Harddisk will support"
date: 2014-01-29
forum: Installation &amp; Upgrades
---

### Post by sunil6 on 2014-01-29
I haveubuntu 12.04.
I have 500 Gb harddisk which i formatted and using currently,
I want to get 2TB as my 500 GB is getting full. So, In ubuntu 12.04 if i attached 2 TB does ubuntu Desktop 12.04 will supports 2TB + 500GB + 2TB ?

What is the limit of storage for using ubuntu 12.04

---

### Post by tfrue on 2014-01-29
The question to be asked is, does your mother board supprt 2TB driver? If you are using an external drive, then you should be fine, but if you are using an internal HDD and want to boot from it, you need to make sure that your motherboard supports UEFI, which supports the 2TB drives.

---

### Post by oldfred on 2014-01-29
You do not need UEFI for 2TB. And you can use MBR(msdos) partitioning.

Actually 2.2TB is the max for the 30 year old MBR partition type. But I do often suggest using gpt and including an efi partition at the beginning of a drive. Then if you move drive to a new UEFI system, you do not have to reformat to add an efi partition at beginning of drive to boot in UEFI mode. 
I now use gpt on all new drives, even smaller ones and even flash drives.

       MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

 [https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

The main issue with gpt is that Windows only boots in UEFI mode from gpt partitioned drives. Both Ubuntu & Windows only boot from MBR drives with BIOS.
Both Windows after XP and Ubuntu read data from gpt drives.

I converted a smaller drive to gpt and booted in BIOS mode wtih 10.10, so gpt works well now with Ubuntu.

I do not think there are any issues on size. Some have posted with recovery issues on 4TB drives that they were using, but those were drive or format issues. I have seen several posts with 16TB or larger server type systems.

---

### Post by sunil6 on 2014-01-29
> **tfrue said:**
> The question to be asked is, does your mother board supprt 2TB driver? If you are using an external drive, then you should be fine, but if you are using an internal HDD and want to boot from it, you need to make sure that your motherboard supports UEFI, which supports the 2TB drives.

OS will be in 500 GB. I will be Connecting that another internal 2 TB as an another drive. So should i format with NTFS and use both drives ?
My is Gigabyte (GA-G41M-COMBO) Motherboard

---

### Post by sunil6 on 2014-01-29
> **oldfred said:**
> You do not need UEFI for 2TB. And you can use MBR(msdos) partitioning.

Actually 2.2TB is the max for the 30 year old MBR partition type. But I do often suggest using gpt and including an efi partition at the beginning of a drive. Then if you move drive to a new UEFI system, you do not have to reformat to add an efi partition at beginning of drive to boot in UEFI mode. 
I now use gpt on all new drives, even smaller ones and even flash drives.

       MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

 [https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

The main issue with gpt is that Windows only boots in UEFI mode from gpt partitioned drives. Both Ubuntu & Windows only boot from MBR drives with BIOS.
Both Windows after XP and Ubuntu read data from gpt drives.

I converted a smaller drive to gpt and booted in BIOS mode wtih 10.10, so gpt works well now with Ubuntu.

I do not think there are any issues on size. Some have posted with recovery issues on 4TB drives that they were using, but those were drive or format issues. I have seen several posts with 16TB or larger server type systems.


OS will be in 500 GB. I will be Connecting that another internal 2 TB as  an another drive. So should i format with NTFS and use both drives ?
My is Gigabyte (GA-G41M-COMBO) Motherboard

---

### Post by oldfred on 2014-01-29
I always suggest system partition with Windows or / (root) with Ubuntu be smaller for efficiency and data partitions be larger. Now with drives being larger, using a tiny / is not required and having some extra space is not much loss. I normally suggest 10 to 25GB for / and only use smaller size for very limited systems. My / uses about 11GB, but I do have all data in other data partitions both NTFS and Linux formatted. My / includes /home.

I think the issues with motherboard/BIOS is the newer very large drives. Some may not support over 2TiB.

I do prefer to have an operating system on every drive, so it can boot without any other system.

 Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

### Post by fantab on 2014-01-30
> **sunil6 said:**
> I haveubuntu 12.04.
I have 500 Gb harddisk which i formatted and using currently,
I want to get 2TB as my 500 GB is getting full. So, In ubuntu 12.04 if i attached 2 TB does ubuntu Desktop 12.04 will supports 2TB + 500GB + 2TB ?

What is the limit of storage for using ubuntu 12.04

No there won't be any problems.
Sometimes your Mother Board can have limitations as to how much strorage it can handle. Especially if its an OLD mobo, I haven't seen any issues with newer mobos.Check your mobo's specification guide for more details.
An Operating System has no such limitations.

Is there Windows in the picture? Are you dualbooting?
If you intend to use the new 2Tb HDD as 'SHARED' data storage between Ubuntu and Windows then format it as NTFS. 
If there is NO Windows then it should be formatted as Ext4.

---

