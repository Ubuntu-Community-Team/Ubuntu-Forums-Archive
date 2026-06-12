---
title: "Partition/Dual-Boot Installation Assistance"
date: 2011-12-15
forum: Installation &amp; Upgrades
---

### Post by randomname9438 on 2011-12-15
Hello,

I know this matter has been covered a million times and I apologize for one-million-and-one, but, I thought I followed the steps I found while trying to create my desired installation setup but I encountered errors. 

I've attached a screenshot of the partition layout that I am using. After my errors, I deleted all the partitions and re-created them. At this time, Windows boots directly into Windows. I made sure to fix my MBR just in case (though, I am not sure anything was wrong with it, I did this just in case). My questions are as follows:

1. Is this the correct type of partition layout (including 'types' of partitions for each area, i.e. primary/extended)? 

2. Where should I be telling the installer to place the bootloader? 

3. Which partitions should have which mount points? Note, that the 180.62GB NTFS partition is going to be the area each operating system uses for my personal files. I found one guide which said to make it /home but the installer only gave me options for /dos, and /windows. 

4. Any I missing anything else that I haven't asked, but is clearly obvious to those "in the know?" 

Also, in case anyone is wondering, the 16GB partition at the end is for swap. I have 8GB of RAM in my laptop and while I understand that swap may not be needed at all, I wanted to create it just in case. 

THANKS IN ADVANCE!

---

### Post by critin on 2011-12-15
Ubuntu normally formats itself to an ext4.  (sometimes ext3)  I would question using ext2 unless installing an older version of linux.  I  also wonder what the tiny 1.4 g partition is for--grub?  I've not seen a separate partition like this on any of mine--but I'm not an expert.  lol   

You don't say what the errors were and why you changed the layout.  Guess it doesn't matter really, since you're starting new.  

I will watch and learn from the answers you receive.  Good luck.

---

### Post by randomname9438 on 2011-12-15
Well, I can change the ext2 to ext4 easily (nothing is installed on those partitions yet)... that's no problem. 

Windows is already installed and running. That's the first two NTFS partitions. The third NTFS should be the storage space, and the last two are for Ubuntu 11.10 (OS/Swap). 

The errors I received were regarding error in the placement of the bootloader. Originally I had set it to install the the file on the same partition that Ubuntu would be, because I swear I saw instruction to place it there. 

I also was unable to set the shared storage space as /home. I was wondering if Ubuntu had to be installed BEFORE setting that space as /home? 

I can make any changes I need too. I'm just looking for someone to help me figure out what I've done wrong, and what needs to be changed (i.e. where to place the bootloader and mount points for each area).

---

### Post by oldfred on 2011-12-15
Linux has permissions & ownership that improve security, but NTFS does not support those, so you cannot use NTFS (or FAT) for any Linux system partitions including /home.

If you want a separate /home you should split the current partition into 20GB for / (root) and 30GB for /home. The advantage is that your user settings and Linux data will be preserved if you do a clean install. But since you will probably be storing most of your data in the shared NTFS partition and then your /home will be smaller and easy to backup for a new install (but it should be backed up regularly anyway.).

Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition older:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by fantab on 2011-12-15
> **brandon.castleman said:**
> 
1. Is this the correct type of partition layout (including 'types' of partitions for each area, i.e. primary/extended)? 

2. Where should I be telling the installer to place the bootloader? 

3. Which partitions should have which mount points? Note, that the 180.62GB NTFS partition is going to be the area each operating system uses for my personal files. I found one guide which said to make it /home but the installer only gave me options for /dos, and /windows. 

4. Any I missing anything else that I haven't asked, but is clearly obvious to those "in the know?" 

Also, in case anyone is wondering, the 16GB partition at the end is for swap. I have 8GB of RAM in my laptop and while I understand that swap may not be needed at all, I wanted to create it just in case. 


[LIST=1]
[*]Yes, it is OKAY, except use **EXT4**.
[*]GRUB- Boot Loader must be installed to **/dev/sda ONLY**.
[*]On your EXT4 partition use "** /** "** mount point** only. Or use **oldfred's** advice.
[*]You have enough memory and as such you don't need 16GB memory, IMO 2-4GB is plenty than enough.
[/LIST]

---

### Post by randomname9438 on 2011-12-16
**SOLVED**

To those who replied and offered help, I say thank you. I was able to get everything up and running like I wanted. I'm not sure I understand exactly what oldfred was talking about in regards to the NTFS issues, but I will sit down and dig through that material when I have a few extra minutes.

---

### Post by oldfred on 2011-12-16
Glad it is solved.

Oldfred is known for overdoing info.:) But all that is if you want to permanently mount the NTFS partition rather than just using Nautilus to browse it. A permanent mount has a standard location and you can control the ownership & permissions (just not at the level Linux offers). I use my shared NTFS for Firefox & Thunderbird profiles, so I have the same bookmarks & emails in both XP  & several Ubuntu installs. I just use XP very little now.

---

