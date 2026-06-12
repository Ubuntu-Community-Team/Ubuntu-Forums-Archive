---
title: "Making Ubuntu complete system restore DVD's?  For Dual boot system?"
date: 2008-07-27
forum: Installation &amp; Upgrades
---

### Post by LazyEngineer on 2008-07-27
Is there a way to make complete system restore disks for a PC that is currently dual boot Ubuntu/WinXP?  

In my case, I have a 160 GB HDD that has multiple partitions: NTSF with WinXP on it, and EXT3 with Ubuntu on it, and the little 4GB Linux Swap drive.  I'd like to be able to run a program that generates a boot DVD that I can just drop into the drive and will completely restore my HDD to it's current configuration. 

I.e. it'll wipe the HDD, repartition it, put my WinXP and all files back onto the NTFS one, and Ubuntu and all my files back on the EXT3 one.  That would be amazingly useful!

---

### Post by LazyEngineer on 2008-07-31
I take it that's a negative?

---

### Post by Potatoj316 on 2008-07-31
I dont think you can do exactly what you want to but you might want to check into clonezilla.  It can create a backup image of your HD to an external drive and restore it later if you ever want to.  I belive it is suposed to be able to install so I guess that is what you want.  Its just not all one once DVD

---

### Post by willieboy on 2008-07-31
I don't know if you can do it from Linux, but there are commercial Windows imaging programs that will clone a drive.

Acronis True Image 11, it also makes Linux images and restores them
as I found out when I tried it to see if it worked.

O&O Disk Image  and probably others.

---

### Post by LazyEngineer on 2008-08-04
> **Potatoj316 said:**
> I dont think you can do exactly what you want to but you might want to check into clonezilla.  It can create a backup image of your HD to an external drive and restore it later if you ever want to.  I belive it is suposed to be able to install so I guess that is what you want.  Its just not all one once DVD

Thank you, I tried clonezilla and it seemed to work well enough to make an image of my XP partition for me. 

The only thing that made me nervous is that it's from China - a country somewhat infamous for putting spyware into things to sniff for secrets/data.  We'll see!

---

