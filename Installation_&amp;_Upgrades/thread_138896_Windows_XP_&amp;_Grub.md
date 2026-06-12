---
title: "Windows XP &amp; Grub"
date: 2006-03-02
forum: Installation &amp; Upgrades
---

### Post by someusernoob on 2006-03-02
A generel question about the install of Windows XP and what about Grub.

My setting:
Hard disk:
Partition 1 (with bootflag) Windows XP (ntfs)
Partition 2 Ubuntu Dapper Drake (ext3) /root ,(+ a little swap partition)
Partition 3 data (vfat)
Grub: on the master boot record (both OS are shown in Grub, it works perfect)

I want to re-install (the same version of) Windows XP tomorrow on the 1st partition, and i was wondering, after i do a full format on the 1st partition, and install XP, will Grub be still there (will windows write a new mbr)?  Or will Grub recognize it as a 2nd XP installation? Or will Grub be just the same as it is now?

Just want to know for sure before things are getting messed up.

Thnx.

---

### Post by Sutekh on 2006-03-02
Sorry to say; that if GRUB is on the MBR, Windows XP will remove it and replace with its own one.

I would make a backup of the menu.lst, and once WinXP is re-installed, use this link to get GRUB back

[Ubuntu Wiki - Recovering Ubuntu After Installing Windows]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows")

---

### Post by someusernoob on 2006-03-02
Thanx, that is a very clear answer. :D Thank you very very much.

---

### Post by someusernoob on 2006-03-02
Well, didnt quite work out well.

I installed Windows XP, got in it, missed my vfat partition, checked the diskmanagement-tool, and got BSOD's out of the system.

If i turn on the pc again i got a BSOD after the Win logo.
If i put in the Win Xp install cd i got a BSOD while scanning disks, if i put in the Ubuntu install cd my hdd is all blank. And now im using Knoppix to find out that i can reach my Win & Ubuntu partition, but not my vfat partition, its just gone. I think the Win install really messed up my partition lay-out.

Hope i can get some data back when i plug it in my neighbours computer, cant wake them up now (4:18am).

Just to let you now :)

Ah, and btw, i didn't delete or format the partition myself, have done a million of Windows installations, so about that im sure.

\\:D/

---

