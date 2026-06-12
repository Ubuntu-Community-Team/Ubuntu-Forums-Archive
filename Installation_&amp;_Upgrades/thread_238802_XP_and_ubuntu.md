---
title: "XP and ubuntu"
date: 2006-08-18
forum: Installation &amp; Upgrades
---

### Post by Intruder on 2006-08-18
Hi guys first post, had a look around but cant really find my awnser, I have Ubuntu Server running for a while now so i thought i would have a look @ the desktop version.  My quetion is I have a laptop running XP harddrive has 2 partions first with XP on what i wanted to do was keep my install of XP and install Ubuntu on the second partion, is this possible? as when i tryed to install it it did not seen to give me that option it just wanted to re-partion it??  Any help would be great....
Thx all

Int

---

### Post by louis_nichols on 2006-08-18
It IS possible. But I suspect that both your partitions are formatted as NTFS, and Ubuntu can't be installed on NTFS.

So you need to re-format the space where you want Ubuntu with one of several supported file systems, of which ext3 is the most used.

---

### Post by Intruder on 2006-08-18
cheers for the quick reply buddy 
ahh i thought that too m8 hence i re-formated it FAT32

Int

---

### Post by louis_nichols on 2006-08-18
FAT32 is good in the sense that Linux can safely write on it but, while there are distros out there that can be installed on FAT32, Ubuntu can't. I would just make a small partition, of 5Gigs or so to install Ubuntu on. You don't need more, since storage can be made on the FAT32 space and, unlike another OS we know out there, it is pretty unlikely that Ubuntu will reach 5 gigs.

EDIT: typos

---

### Post by givré on 2006-08-18
linux (and unix in general) cant be install in FAT32, since it don't support file permission.
But while running the installer, you will have a small apps to partition your  HD, and it will automatcaly choose ext3 for the base system.

---

