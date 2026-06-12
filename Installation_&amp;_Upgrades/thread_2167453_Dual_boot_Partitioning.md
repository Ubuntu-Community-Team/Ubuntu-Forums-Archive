---
title: "Dual boot Partitioning"
date: 2013-08-13
forum: Installation &amp; Upgrades
---

### Post by urban-suhadolnik on 2013-08-13
3 moths ago i started using ubuntu when i first came to this forum and ask for help. I had a similar problem with partitioning a got all the help i needed. (partitioning is a scary thing :))
But after 2 months unity stopt working and win7 just slowed down to the point where it is unusable. So I decided to do a fresh install of both ubuntu and win7. (first time I just installed ubuntu in my last partition)

I would like to have an "advanced" partition scheme
I have 1,5 TB hard drive
And I will use win7 only for occasional gaming (and LAN party)

I would like to partition like this:
win7 system 100MB -- win7os 150GB -- ? -- extended partition everything else

Which partition should be in ? primary partition? (boot? root? swap?)

If i buy an 120GB SSD would be good if I partition like this:
SSD:  boot 500 MB -- root 
HDD: win7system 100MB -- win7os 150GB -- swap 4GB -- home (or extended if I decide to try other distros)

Which partition should not be on SSD?
Should I use GUID Partition Table in SSD?
If I use this partition scheme can I get rid of GRUB to boot as fast as I can? (or turn off waiting in GRUB)

Do I need boot partition?
Should I use btrfs filesystem?
Should I leave some space in extended partition to try other distros from time to time?

Thank you in advance
Urban120

P.s. How can I get my old username back?

---

### Post by oldfred on 2013-08-13
Post a request in the Resolution Center for name change. But you will need to know old e-mail as the Admin has to privately confirm that with you.
[http://ubuntuforums.org/showthread.php?t=2164369](http://ubuntuforums.org/showthread.php?t=2164369)

There is no thing as perfect partitioning. It is based on your very individual needs. My own optimal partitioning is obsolete in a year or so.

My suggestion is generally to keep system partitions smaller and have large data partitions. If thinking of other installs either leave some unallocated space in the extended partition or create 10 to 25GB extra partitions.

Windows only boots from gpt partitioned drives with UEFI. So if ever installing Windows on a gpt partitioned drive you need a UEFI system.
Ubuntu can boot in BIOS or UEFI from gpt partitioned drives if you have the correct partitions. With BIOS you need a bios_grub 1MB unformatted partition or with UEFI you need a 250 to 300MB FAT32 partition with the boot flag (to make it the efi partition). 

Desktops do not normally need a separate /boot partition, but a few BIOS do have issues booting from beyond a 100GB on new very large drives. If you BIOS is one of those you may need the separate /boot. Seems to be more common with external large drives and may be BIOS and USB port related.

You have to have grub to boot. You can set auto boot delay to 1 second. Those who change timeout to 0 can never get to other boot entries and often have major issues later.

---

### Post by urban-suhadolnik on 2013-08-14
Thank you for your answer
I would still like to know:
If I should use btrfs?
What to put in the last available primary partition? (it is marked as ? in my scenario)
Which partitions should not be on SSD to extend live time? (swap? tmp?)
what's the down side of logical partitions?

Thank you in advance for your answers
Urban120

---

### Post by oldfred on 2013-08-14
I prefer to stay with default recommendations on formats or ext4. Also most tools work well. If using one of the alternative formats best to be a very advanced user and only use it on a second install for testing.

 10-Way Linux File-System Comparison On Linux 3.10
[http://www.phoronix.com/scan.php?page=article&item=linux_310_10fs&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_310_10fs&num=1)
BTRFS, not ready for prime time
[http://ubuntuforums.org/showthread.php?t=2111487](http://ubuntuforums.org/showthread.php?t=2111487)
Linux 3.11 File-System Performance: EXT4, Btrfs, XFS, F2FS
[http://www.phoronix.com/scan.php?page=article&item=linux_311_filesystems&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_311_filesystems&num=1)

You do not have to use all primary partitions. Some may want to install another copy of Windows later, so I usually suggest leaving one primary as Windows can be directly booted from a primary.

I think if it is a new SSD the live issue is not an issue anymore. Hard drives do not last forever either. If you have lots of RAM you will never use swap so that does not really matter. I just like to have some swap as a just in case something runs away. Some recommend some of the temp files be loaded into RAM, to reduce writes & improve performance when you have lots of RAM. When RAM was more expensive you could not really do that.

There is no real downside of logical. It just is that MBR(msdos) has been around for over 30 years and has had to have many modifications to work with newer systems. Logical will work for Linux but not for direct booting of Windows as it only boots from primary partitions.
Actually gpt has been around for 10 years but not really used until drives went over 2TB which was the maximum that MBR could support. And UEFI used gpt. You cannot boot from MBR drives with UEFI. 

      
 GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

---

### Post by urban-suhadolnik on 2013-08-15
Thank you for your help i am now writing from my new ubuntu install at the end i went with EXT4 and i couldn't wait for an ssd so i instaled all on HDD

Urban120

---

### Post by oldfred on 2013-08-15
Glad it worked.

I like to have an install on every drive anyway. That way you have another to test changes that you may not be sure you want or test the next version.

---

