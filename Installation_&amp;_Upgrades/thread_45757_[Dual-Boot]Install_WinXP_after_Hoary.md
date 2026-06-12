---
title: "[Dual-Boot]Install WinXP after Hoary"
date: 2005-07-01
forum: Installation &amp; Upgrades
---

### Post by Matthi86 on 2005-07-01
Hi, this is my current situation:
I have Ubuntu Hoary Hedgehog installed on a 80gb disk, I let the installer do the partitioning for me (so i gues i have a ext2 and a swap partition). Now i really need to set-up a duaboot because i need WinXp to run certain programs (yeah i used wine btw:p). So what i need to do is resize the ext2 partition and create a NTFS partition so i can install windows. I haven't found a tool to resize my partition so thats problem one.
Secondly i'll have to install windows and edit my GRUB config i gues:) So how should i do this?
So my main question is how should I proceed to solve this problem without losing any of my data or much of my time:p.
Any help would be greatly appreciated! Tnx:)

---

### Post by not_yet on 2005-07-01
I think you need to install windows first :???: 

if you can back up your disk, I think that is the preferred route

then use the hoary install disk to resize your disk and make some free space for ubuntu

---

### Post by Seti on 2005-07-01
You CAN install windows after already having linux installed, but bear in mind that windows HAS to be installed in a Primary partition, at the front of the disc. (/dev/hda1)
So you can have Ubuntu already located at, say, /dev/hda5, and then install Windows. Its important to have /dev/hda1 already formatted as NTFS or at least FAT32, so that the windows installer will sellect the correct partition to format.
Once you have Windows installed, its a simple matter of restoring GRUB to the MBR and making sure it has an entry for Windows.

---

### Post by mingus on 2005-07-01
Post #10 at [http://ubuntuforums.org/showthread.php?t=45089](http://ubuntuforums.org/showthread.php?t=45089) may also be useful.  Whether you can resize your existing Ubuntu partition depends upon the tool you use and the filesystem - sometimes resizing can only be done from the end of the partition.  This is academic of course if you decide you must boot W$ from the hard disk, because you will have to pull Ubuntu off to create a first partition for XP, and recreate a new Ubuntu partition.  But if you are not using W$ heavily, consider the boot floppy option, which would allow you to install W$ after Ubuntu on the disk.  Also, if you are using ext2 for Ubuntu, you should consider converting it to ext3 because ext2 is not journaled and therefore has the same vulnerabilities and requires the same maintenance as FAT32 does.

---

