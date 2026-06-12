---
title: "wtf? installation"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by SABOT00 on 2008-03-14
first i used disk management in vista to shrink my C: partition and created a new one with NTFS, then i tried installing ubuntu, then i used partition manager in liveCD to reformat the NTFS into a FAT32, i completed that then when i try to install the guiled only has use entire disk option so i used manuall install. im trying to install ubuntu to my ~34gb FAT32 partition 
but it says no root file system is defined. i haven't created a swap partition seeing as i have 4gb memory. how do i get ubuntu to install on my 34gb FAT32 partition??!! HELP!
btw im a total newb at ubuntu.

---

### Post by taurus on 2008-03-14
If you highlight the partition you want to install Ubuntu to, look at the first option below, left side, and says something about edit partition.  You need to change the mount point from something like /media/sda2 to / and format that partition to ext3, by putting a check mark on the small square window.

---

### Post by Afkpuz on 2008-03-14
What you should do is leave a space on your hard drive empty.  Then, during install, pick "Use largest continuous free space."

---

