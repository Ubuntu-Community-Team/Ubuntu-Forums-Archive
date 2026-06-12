---
title: "Issues installing Windows Xp and Ubuntu"
date: 2006-06-30
forum: Installation &amp; Upgrades
---

### Post by oakey_99 on 2006-06-30
Hey All,

I have a LP LS50a laptop which is currently running windows xp. I wanted to use UBUNTU for obvious reasons. Due to the current windows install running slower than can be imagined, i decided to reformatt.

I formatted the HDD, set up 2 partitions (NTFS file system for windows and unallocated space) using the windows setup. I then continued to install windows onto the NTFS partition. Complete fine and windows loaded all ok.

I then put in the UBUNTU live cd that i have, (downloaded from ubuntu.com) and booted into the live version. From here i run the install of UBUNTU. Complete fine, reboot and recieved the options of which OS i wanted to load.

Select UBUNTU ... all fine.
Select Windows XP, and i get the welcome to Windows XP screen, then blue screen of death for half a second and it reboots.

I have read other posts on here about people having the same issue and was wondering if and how they resolved it. 

I have tried all different ways, installed windows then UBUNTU, other way around, using Windows to partition, using UBUNTU to partition, creating 1 NTFS and 1 ext3 partition, creating 1 NTFS and unallocated space, created 1 ext3 and unallocated space.

No matter how i try it, windows always seems to be killed. :( 

Easy enough to say the hell with windows, but its needs for other users of the laptop.

Any help appreciated.
Regards.
Oakey

---

### Post by ajgreeny on 2006-06-30
What does your /boot/grub/menu.lst file look like at the bottom where it has the entry for windows?  It should look something like this, depending on the disk identification of your windows partition.  I assume you could get into windows after reinstalling before you added ubuntu to the disk.

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

If it looks completely different then that may be your problem, and an edit of that file may be needed.

---

### Post by Herman on 2006-06-30
I have a couple of ideas, but I'm not sure how they'll work, okay?
One is to give this old solution from 'Warty' a try. It's supposed to be a safe procedure, so even if it doesn't work it shouldn't hurt, but it might just work. [*Click Here.*]("http://ubuntuforums.org/showthread.php?t=2689")

Another idea is, if it seems to be the writing of GRUB to MBR that may be causing the problem, try installing with the Ubuntu Dapper 'Alternate' install CD rather than the 'Desktop' live/Install CD. The 'Alternate' CD allows you to choose a different location to install GRUB (for example to the first sector of your Ubuntu partition rather than to MBR.
When you install GRUB to your first sector of your Ubuntu partition, GRUB will need some other bootloader or bootloader manager to boot it.
I suggest GAG Boot Manager, it's free, open source easy to use, and only a small download. GAG Boot Manager can be installed and run from either a CD or floppy disk. If you do it that way, you won't need to disturb your Windows IPL in your MBR at all. GAG can be installed to MBR later from the CD or floppy if you like, but then if it's a Windows problem, you might end up back where you started again.
[GAG Boot Manager How-to,]("http://users.bigpond.net.au/hermanzone/p12.htm")          [GAG Boot Manager Home Page]("http://gag.sourceforge.net/")
If you plan on trying that idea, you will need to make your GAG CD or CD-RW beforehand, prior to beginning your Ubuntu install, so you can re-boot from it during the install.
Regards, Herman

---

### Post by oakey_99 on 2006-07-02
i got it all working guys.

I wasn't partitioning correctly ...

I installed XP on the whole disk, then run UBUNTU install from live cd ... used UBUNTU's partitioner, resized the XP partition, then created an extended partition with size as the remainder of the disk. Then created a partition for / and a partition for swap.

All good ... only issue is wont play MP3 files now on UBUNTU ... any ideas ?

---

