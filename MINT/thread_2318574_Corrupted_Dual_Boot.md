---
title: "Corrupted Dual Boot"
date: 2016-03-27
forum: MINT
---

### Post by MintyMike on 2016-03-27
Hi everybody

I have posted this in both the Mint and Linuxquestions forums with no solution

Perhaps there may be somebody here who has the answers


-------------------------------------------

Is there anybody here expert in booting and in particular dual booting?

 My aim is to dump MS

 I started out having a dual-boot  Windows 7 / Linux Mint system with a view to ditching MS in favour of Linux

 Something went wrong, I think MS tried forcing an update on me.

 on trying to boot I got the message "Operating System Not Found"

 I used the Rescue Disk which eventually told me that it had fixed the boot partition

 report at [http://paste.ubuntu.com/15502896/](http://paste.ubuntu.com/15502896/)

 On trying to boot I got:-

 Linux Mint 17.3 Cinnamon 64 bit
 Advanced Options for Linux Mint 17.3 Cinnamon 64 bit
 Memory Test (memtest86+)
 Memory Test (memtest86+, serial console 115200)
 Windows 7 (loader) (on /dev/sda1)
 Windows 7 (loader) (on /dev/sda2)

 I have tried all combinations with no joy

 I loaded a Mint system from CD (same one as loaded original system) and put the disk into an attached caddy
 I can load and navigate the 455 GB volume which has the entire file system and data of my Windows 7 system
 I can load and navigate the 41GB volume which has the entire file system and data from my Mint system

 results from 'disks' command from accessories:- 

 500 GB Hard Drive
 /dev/sda
 Partitioning Master Boot Record

 Volumes
 Partition 1                      105 Meg  -  /dev/sda1    -   HPFS/NTFS(Bootable)      contents NTFS-Mounted 

 Partition 2 Filesystem           455GB    -  /dev/sda2    -   HPFS/NTFS                contents NTFS- Not Mounted 

 Partition 3 Extended Partition   45 GB    -  /dev/sda3    -   Extended                 Extended Partition
 Partition 5 Filesystem           41GB     -  /dev/sda5    -   Linux                    Ext4 (version 1.0) - Mounted
 Partition 6 swap                 4.2 GB   -  /dev/sda6    -   linux Swap               Swap (version 2) - Active   
                             1.1 Meg  -  /dev/sda     -   Unallocated Swap

 results from disk check

 fsck /dev/sda1
 fsck: fsck.ntfs: not found
 fsck: error 2 while executing fsck.ntfs for /dev/sda1

 fsck /dev/sda2
 fsck: fsck.ntfs: not found
 fsck: error 2 while executing fsck.ntfs for /dev/sda2

 fsck /dev/sda3
 fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda3
 Could this be a zero-length partition?

 fsck /dev/sda5
 /dev/sda5: clean, 217501/2506752 files, 3946730/10016256 blocks

 fsck /dev/sda6
 fsck from util-linux 2.20.1
 fsck: fsck.swap: not found
 fsck: error 2 while executing fsck.swap for /dev/sda6

 contents of /etc/fstab
 #
 # Use 'blkid' to print the universally unique identifier for a
 # device; this may be used with UUID= as a more robust way to name devices
 # that works even if disks are added and removed. See fstab(5).
 #
 # <file system> <mount point> <type> <options> <dump> <pass>
 # / was on /dev/sda5 during installation
 UUID=f5f2eab8-e23a-4e99-807c-ab570a342d79 / ext4 errors=remount-ro 0 1
 # swap was on /dev/sda6 during installation
 UUID=702fadb0-363c-4819-8e79-ceca327a022b none swap sw 0 0

 grub.cfg file attached as grubcfg.txt

 If I put the disk in a caddy and connect it to a windows 8.1 machine I get a System Reserved disk with 69.5 MB free out of 99.9 and a
 'disk' (un-openable and size unknown)and MS Disk Manager hangs when the caddy is attached.

 Is there somebody who knows the intricacies of linux and windows booting who could help me restore my boot

 This is really frustrating as I can see every scrap of files and data on both the Mint and Windows installations but just can not 
 load either system. I have lost no data

 My plan is to restore my windows system on this disk and then load Linux onto its own PC, so it doesn't matter if the Mint gets wiped 
 out, as long as I can boot into windows for now so that I can gradually migrate to Linux and then dump windows for good.


 Thanks very much in advance for any help that this forum can give me

---

### Post by howefield on 2016-03-27
Thread moved to the "*MINT*" sub forum.

---

### Post by Bucky Ball on 2016-03-27
Tried [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair")?

Post the bootinfo output from that (option when you launch it or after repair).

---

### Post by MintyMike on 2016-03-27
@howefield
According to the distributors of Mint, it is based on Ubuntu and that my problem with booting and Grub and the like is common to all Ubuntu distros therefore I posted it into forum with most readership hoping that I would find somebody who knows about Grub2 and dual booting, which unfortunately nobody seems to. 

Are you saying that the Mint Grub is different to that of Ubuntu?   If not, could we get this question back to the main forum please as it is about a Ubuntu based installation

@Bucky Bell
...and yes, thanks Bucky Ball, the rescue disk I mentioned in my original post is the same as Boot Repair Disk

---

### Post by Bucky Ball on 2016-03-27
My mistake.

***Mint*** is not one of the Ubuntu official flavours, is not officially supported by Canonical nor do we give support for it anywhere here but in this sub-forum. That's why you're here.

They have a vibrant forum community of their own, as you have discovered, but not so vibrant for you by the sounds of it. :|

---

### Post by MintyMike on 2016-03-28
I noticed your use of 'we' and did some 'Googling'   I hadn't realised that Conical had bought out this forum and unfortunately "Other Discussions and Support - Other OS Support and Projects - Other Operating Systems - Mint"   is not what I would have guessed at to find discussions on Grub problems !. 

That's why I posted where I did as I had a problem that is common to all Ubuntu 'flavours' (and possibly all Linux flavours ) and the rescue disk sent its results to Ubuntu.com (perhaps the disk should now be changed to only do that for Ubuntu installations)

The reason I chose Mint was that it is an easier visual transition from Windows 7 than other releases of Linux and as it is the third most installed system after MS Windows and Apple OS I figured it would have a bit of support. But as Linux support seems a bit thin on the ground and with an 'us and them' attitude to the various releases then perhaps I will have to stick to Windows

But thanks for attention anyway

---

