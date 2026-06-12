---
title: "problem with partitioning"
date: 2004-12-16
forum: Installation &amp; Upgrades
---

### Post by makaveli on 2004-12-16
i was using gentoo but then decided to come and try this.  I used windows xp's disk management to erase the old gentoo system. When i go to install ubuntu i go to the partioning section and then i automatically configure the free space and change to file type to ReiserFS everytime i get an error that says:

Failed to create a file system and the ReiserFS file system creation in partition #2 of IDE2 master (hdc) failed. 

I dunno what to do this won't work.

Can somebody please help me out i really want to try this distro but i can't get the disk to partion.

---

### Post by makaveli on 2004-12-16
yeah i really need to get this fixed as fast as possible i have a paper to write and i can't get on my computer no more since i had dual boot set up with xp and gentoo but since i deleted the gentoo files i can no longer get into windows xp.

---

### Post by Xian on 2004-12-17
I honestly don't know what the partitioning issue is about, but if you already have WinXP installed you only need your XP install disk to reset the MBR and thereby boot into Windows. The process is simple:

- Boot from the WinXP CD
- Press the "R" key in the setup
- Select your WinXP installation from the list
- Enter the Admin password (if you have one)
- Enter the command "FIXMBR" at the input prompt
- Confirm with "y"
- Exit and reboot

---

### Post by p!=f on 2004-12-17
Removing Unix partitions under Windows... I would be scared to death. :)
Try to repartition the disk manually.

---

### Post by alainhenry on 2004-12-17
Just an idea, but have you tried another file systems (I mean ext3 instead of ReiserFS for example)
Alain

---

### Post by makaveli on 2004-12-17
yeah i tried a different filesystem and i don't have an xp pro disk mine is trashed because my little brother got a hold of it. If you know an ftp site where i can download it that would be great. But other than that i don't know what to do.

---

