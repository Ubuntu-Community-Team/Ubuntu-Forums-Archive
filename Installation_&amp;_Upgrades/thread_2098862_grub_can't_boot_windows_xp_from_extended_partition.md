---
title: "grub can't boot windows xp from extended partition"
date: 2012-12-27
forum: Installation &amp; Upgrades
---

### Post by jarnoldorocketpower on 2012-12-27
HI, I had install ubuntu 12.04 on my laptop with windows xp, the installation was ok but when i restarted the laptop the grub menu doesn't show, i use sudo update-grub but it's the same problem. then i use boot-repair and i got this:
[http://paste.ubuntu.com/1471486/](http://paste.ubuntu.com/1471486/)
 but when i select windows it doesn't boot.
Can anyone help me?
Sorry for my english i speak spanish as my mother language.

---

### Post by oldfred on 2012-12-28
Windows only officially boots from a primary partition. I have seen work arounds for XP only but in your case it would be better to make Windows a primary partition and make a new extended partition for swap.

Windows NTFS partition have to also have partition start & size info as well as what boot loader in the PBR - partition boot sector. Yours says it starts at sector 63.

       To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sda or sdb, sdc if more than one etc.
sudo sfdisk -d /dev/sda > parts.txt

Not sure if fixparts will work with all 4 primary already used. You may have to delete current swap and then recreate it in a new extended. If you create new swap also update fstab with new UUID.

---

