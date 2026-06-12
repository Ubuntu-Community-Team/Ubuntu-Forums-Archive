---
title: "Replace Suse with Ubuntu, Keep XP Pro"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by Alan Drabke on 2010-07-27
I am running Windows XP pro and Suse Linux in a dual boot arrangement on a HP 6730s KS079UT laptop. I would like to replace Suse with Ubuntu 10.04. So far, I have not been able to delete the Suse partitions and replace them one for one with Ubuntu partitions. I get error messages like: "No root file system is defined. Please correct this from the partitioning menus." The Ubuntu installer will allow me to delete the Suse spaces and create a swap file and one other partition. But then it balks and tells me the rest of the space is unusable. Seems to me I need a swap file, a partition for my programs, and a partition for my files. How do I get there? 
 
Should I install Ubuntu next to Windows XP Pro and Suse in a triple boot? Can I shrink the Suse partitions during install? Can I shrink the Suse partitions after the install and then finally delete them? :)

---

### Post by kooia on 2010-07-27
Well, triple boot *might* work, but it'd slow down XP and Suse down a lot.  From how Ubuntu is set up, I don't think you can delete the partitions because Ubuntu takes over XP and puts it in Ubuntu, like this:

Ubuntu -------Ubuntu-------Ubuntu-------Ubuntu
------------------------------Windows ---- Windows

---

### Post by oldfred on 2010-07-27
I am not sure why you are having issues. Are you trying to create more than 4 primary partitions? Your last primary should be an extended where you can put in additional logical partitions.

I suggest:

20 GB for / (root)
2GB for swap but if you want to hibernate then make it slightly larger than RAM
The rest you want to use for Ubuntu as /home

All or some of above partitions can be in the extended. Only windows requires primary partitions.

---

### Post by efflandt on 2010-07-27
If you want to use existing SuSE partitions, it should be a no brainer.  Just use the advanced mode when you get to partitioning the Ubuntu installation, and select your swap, root (/), and whatever other partition and where you want to mount it.  And check each of those to format (except the data partition if you want to use that as is).  However, if you use an existing data partition as is, you may need to change ownership and/or permission of directories or files on it before you can use them afterwards.

If you want to change partitions, just boot to a live system from the CD (or iso on bootable USB flash) and use gparted to set up the partitions how you want them, then do the above.  That is what I did when my desktop had an old SuSE version on it (multiple boot w/WinXP Home and expired 64-bit WinXP beta that I intended to remove).  Although, I did not realized that Ubuntu would pub grub in the mbr, so I later restored the Windows mbr and put grub on a Linux primary partition (with that marked as boot in partition table).

Note that you can only have 4 primary or extended partitions and any additional partitions would have to be logical partitions within an extended partition.

---

### Post by Alan Drabke on 2010-07-27
Gentlemen-
What I have now is two partitions for Windows XP Pro (NTFS and fat32) and three partitions for Suse (swap (2 gigs), programs (20gigs), and files (80 gigs)). You seem to agree that I can have at best just 4 partitions. Is that a rule under Ubuntu but not a rule under Suse? 
 
My goal is to replace Suse with Ubuntu. Once and forever. How do I do this? Should I allow a triple boot and then delete the Suse partitions with Acronis Disk Director once the Ubuntu boot loader takes hold? In Ubuntu, is the swap partition a primary or a logical partition? Which do I choose? In Ubuntu, am I only allowed one more partition in addition to the swap file? How do I format the extra partition (ext2, ext3)? what do I put in the mount window?

---

### Post by wilee-nilee on 2010-07-27
You seem to be a little confused on partitioning here is a link that might help.
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by oldfred on 2010-07-27
You can only have 4 primary partitions. One primary can be converted to an extended partition that can hold multiple logical partitions. This is the standard for all MBR or msdos style PC systems since IBM released the first PC. Apple now uses a newer system gpt and Ubuntu will work with that also.

If you already have 5 partitions one must be an extended partition to hold the additional logical.

As efflandt says this should be easy, use manual install and reuse your existing Suse partitions. Just do the install first then worry about mounting any additional data partitions after the install is complete.

---

### Post by Alan Drabke on 2010-07-28
Gentlemen, here is what my partitioning table looks like right now:
/dev/sda1   ntfs           141474 MB           51161 MB (used)
/dev/sda2   fat32            1077 MB                33 MB (used)
/dev/sda5   swap            2154 MB                  0 MB
/dev/sda6   ext4           21476 MB             5289 MB (used)
/dev/sda7   ext3           83873 MB             3013 MB (used)
 
In plain english, one step at a time, how do I replace the swap, ext4 and ext3 partitions (now occupied by Suse) with a full install of Ubuntu 10.04? You 
gentlemen are talking Ubuntu insiders jargon to a noob who barely 
understands Suse Linux.

---

### Post by wojox on 2010-07-28
Start with Swap - turn it off (Right Click)

Then delete dev/sda7

Then delete dev/sda6

You have to go in order from highest to lowest. 

Do this with a live_CD and Gparted.

I ran OpenSUSE kde for a few months dual booting with Ubuntu.

---

### Post by Alan Drabke on 2010-07-28
Dear Wojox (Ubuntu afficianados)-
 
After I follow your instructions for deleting my Suse partitions. What do I type into the little boxes in the partition file to set things up for an Ubuntu 10.04 install?

---

### Post by wojox on 2010-08-02
> **Alan Drabke said:**
> Dear Wojox (Ubuntu afficianados)-
 
After I follow your instructions for deleting my Suse partitions. What do I type into the little boxes in the partition file to set things up for an Ubuntu 10.04 install?

You shouldn't need to type anything. Do it with the Ubuntu CD installer.

---

