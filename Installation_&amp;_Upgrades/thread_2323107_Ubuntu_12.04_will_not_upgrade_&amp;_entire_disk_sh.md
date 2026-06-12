---
title: "Ubuntu 12.04 will not upgrade &amp; entire disk shows as unallocated."
date: 2016-05-02
forum: Installation &amp; Upgrades
---

### Post by Mahogan on 2016-05-02
I have a laptop with Ubuntu 12.04 and Windows 7 dual boot.  Both OS's work fine and all boots properly.  I want to upgrade, it says that 12.10 is available, but I keep getting the error: "failed to fetch. fetching the upgrade failed. Network Error."  I am connected to the internet, so am not sure why this is happening. 

 I was looking over my system for any other errors that might be related.  What I found, I am not sure if this is relevant, but it seems like a real problem. In gParted, it shows that the entire disk is unallocated.  So I put in a live CD and opened gParted to see if this gives me the same result, and yes, it is identical.  Looking online for a solution, I found similar issues and have tried several things, but nothing helps.  I was able to go to terminal, and get this result of my disk:

ubuntu@ubuntu-laptop:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xda22e49b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    25167871    12582912    7  HPFS/NTFS/exFAT
/dev/sda2   *    25167872    25372671      102400    7  HPFS/NTFS/exFAT
/dev/sda3        25372672   568508408   271567868+   7  HPFS/NTFS/exFAT
/dev/sda4       568508472   625153409    28322469    f  W95 Ext'd (LBA)
/dev/sda5       568510464   615407607    23448572   83  Linux
/dev/sda6       615409664   625141743     4866040   82  Linux swap / Solaris
ubuntu@ubuntu-laptop:~$

I don't know much about this. So, not sure what to do here, maybe these are two completely different problems? I want to upgrade to Ubuntu 16.04 LTS.  So I was hoping to fix this disk problem, then download the upgrade from the 16.04 ISO, rather than version by version through the update manager.  I am assuming this method will not delete my Ubuntu programs and files and would be much faster.  Any help would be greatly appreciated.

---

### Post by grahammechanical on 2016-05-02
Let us deal with one problem at a time.

> I want to upgrade, it says that 12.10 is available, but I keep getting  the error: "failed to fetch. fetching the upgrade failed. Network  Error."

Actually, Ubuntu 12.10 has reached end of life a long time ago. The software repositories are now closed and have been moved onto other servers. This means that the file (sources.list) that records the URLs of the repositories now has incorrect URLs and this is why Update Manager is give that network error.

It is a long time since I used 12.04 and some of the names have been changed. So, I may get the labels wrong. I think that you need to go to System Settings & open Software Sources and look for a tab on the subject of updates and set to be notified of the next LTS release. Then reload or run

```
sudo apt-get update
```

Now when you open Update Manager you should be offered an upgrade to 14.04. Before upgrading you should make sure that 12.04 is fully up to date and that you are using an open source video driver (see Additional Drivers). Also disable any PPAs and revert the desktop to as close  to default as possible. And backup any data you do not wish to lose.

Regards.

P.S, The only sensible alternative to upgrading to 14.04 and then to 16.04 is to do a fresh install using the Something Else option. I would not try upgrading 12.04 to 16.04 from the 16.04 ISO image. And because you do not have a separate /home partition or a separate data partition a fresh install will destroy what is on sda5 which is the partition for Ubuntu.

---

### Post by Mahogan on 2016-05-02
>  I think that you need to go to System Settings & open Software Sources and look for a tab on the subject of updates and set to be notified of the next LTS release. Then reload or run

Code:

sudo apt-get update

Now when you open Update Manager you should be offered an upgrade to 14.04

Thanks!  This works for upgrading, it is now in process.  I will post when completed of the results (possibly tomorrow).  Hopefully this will also fix the disk issue.

---

### Post by Mahogan on 2016-05-03
Ok, the upgrade to 14.04 worked fine.  However the unallocated disk in gparted still exists.  Should I upgrade to 16.04 LTS to see if it corrects the issue? Suggestions?

---

### Post by Mahogan on 2016-05-04
Been trying to fix the disk so that it shows up properly in gparted and found the error message: "Can't have a partition outside the disk!"  Looking around on different forum posts, I do not see a real solution as most others have a different scenario.  Here is a screenshot.  Any suggestions would be greatly appreciated, thanks.

---

### Post by Mahogan on 2016-05-04
Ok, I have been doing some more research on the unallocated disk problem. Looking at my specs, the numbers all seem to line up properly, I am not sure where the partition table is outside the disk?  

I found this post: [http://ubuntuforums.org/showthread.php?t=2201860](http://ubuntuforums.org/showthread.php?t=2201860)

Also the solution that they used: [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

My question: Based upon my disk results listed on my first post, does anyone think the Fixparts is an applicable course to try?

---

### Post by Impavidus on 2016-05-04
The numbers don't line up properly. The end of the last "real" partition is at byte 625141743×512=320072572416, which is fine, but the end of the extended partition (which is only a container) is at byte 625153409×512=320078545408. The size of your hard drive is 320072933376 bytes, so the extended partition is outside the disk. I don't know how to deal with that though.

---

### Post by Mahogan on 2016-05-04
Alright, thanks for pointing that out.  I see now that the numbers of the extended partition are wrong.  So I did find a post with a very similar problem: [http://ubuntuforums.org/showthread.php?t=2251075](http://ubuntuforums.org/showthread.php?t=2251075)

I tried to download the FixParts in Ubuntu and it gives me an error that it is a bad package and fails to install.  So I thought I would try to download the version in Windows, which I did. Then running as administrator and typing the command to start the program, it just closes.  

At this point I am in way over my head.  About to give up.   After re-reading the fixparts directions, it is beyond my grasp anyway.

---

### Post by mörgæs on 2016-05-05
Have you considered deleting the two Buntu partitions and doing a fresh install of 16.04?

---

### Post by Mahogan on 2016-05-05
> **mörgæs said:**
> Have you considered deleting the two Buntu partitions and doing a fresh install of 16.04?

I have thought of this, but in gparted, it shows the whole disk as unallocated, so there are no partitions to delete.  I did get in Windows Disk Management and see the partitions, it show them as empty, but shows the Windows partitions as fine.  I had considered deleting them from Windows, but then am concerned with the Grub boot loader may be corrupted after doing that, and then I may not be able to even access Windows after doing this?  Also right now when I boot from a Live CD the whole disk is unallocated, so after messing with the partitions in Windows, I am not sure if gparted will show that Windows still exists?

---

### Post by Dennis N on 2016-05-05
> I have thought of this, but in gparted, it shows the whole disk as unallocated, so there are no partitions to delete.

Since fdisk can detect the partitions, you might be able to use it to delete specific partitions (like 5,6, and 4) to prepare the disk for a new install of Ubuntu? Then use gparted to make new Linux partitions to replace them?

[FONT=Courier New]**sudo fdisk /dev/sda**[/FONT]

them 'm' for menu of options.

EDIT: Although fdisk might get this done, since that partition #4 was made by Windows, you should probably do any deletion using the Windows OS, based on the advice I have seen.

---

