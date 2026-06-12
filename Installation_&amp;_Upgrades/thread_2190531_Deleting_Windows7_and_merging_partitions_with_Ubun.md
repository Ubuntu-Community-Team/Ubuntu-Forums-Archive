---
title: "Deleting Windows7 and merging partitions with Ubuntu"
date: 2013-11-27
forum: Installation &amp; Upgrades
---

### Post by dimitri6 on 2013-11-27
Hi All,

My system is currently configured for dual-boot: Windows 7 and Ubuntu 13.10, via GRUB.
When I boot on Ubuntu I can see my "C, D, E and F" NTFS partitions and access my Win7 files. [each NTFS partition is displayed as separate drive in Ubuntu]
I almost always use Ubuntu Linux, and very rarely Windows 7.
Long story short, my Win7 is severely corrupted and unusable, and since now I'm very comfortable with Unity desktop and rarely boot to windows, I decided to completely make the switch and not re-install windows.

My question is:

How can I go about

- wiping my "c (NTFS) partition and assign it to Ubuntu's partition(s)?
- re-map my "D,E and F" NTFS widows partitions to my ext4 Ubuntu home folder? (without erasing anything - I have lots of documents, saved work and video files in these NTFS partitions)
- Remove the Windows7 dual-boot from GRUB and make it single-boot? (boot directly to Ubuntu without the "Windows 7" option).

Simply put, I wish to completely get rid of Win7 and give all HD space to Ubuntu.

Thanks for any suggestions.

Dimitri Papadopoulos

---

### Post by fantab on 2013-11-27
For now, you can BACK UP any data you have on NTFS C: and using 'Disks' or 'Gparted'... reformat that partition as EXT4 and use it to save your personal data. No need to merge this with your /home for now. It will be unnecessarily complicated.
After reformatting the C: partition run:
```
sudo update-grub
```
Your Windows entries will be gone.

Keep using the remaining NTFS 'D', 'E' and 'F' as they are. Since Ubuntu/Linux can read-write from NTFS, no issues there. You don't have to do anything to these partitions. There are good.

However, in future, after doing a good BACKUP of your important DATA to an external device, you can reformat the entire HDD accordingly to use with Linux only.

---

### Post by Mark Phelps on 2013-11-28
> re-map my "D,E and F" NTFS widows partitions to my ext4 Ubuntu home folder? (without erasing anything 

Sorry -- but this simply can NOT be done.  Changing the filesystem of a partition automatically removes the former partition table, and while that does not actually "wipe" all the files from that partition, it does "erase" them -- making recovery of them very difficult.  

To change the filesystems of these partitions, you would have to do the following:
1) Copy the files and directories to an external drive
2) Erase the partitions
3) Recreate the partitions using the new filetype
4) Restore the files from the external drive

---

### Post by dimitri6 on 2013-11-28
Thanks for your replies.

That's what I initially thought doing but I asked in case there's a tool or something that helps with the switchover.

as you suggested, I will backup everything to an external drive, re-initialize my main drive with dban (sort of a "low-level format"), start fresh with Ubuntu and bring things over.

Thanks again.

---

