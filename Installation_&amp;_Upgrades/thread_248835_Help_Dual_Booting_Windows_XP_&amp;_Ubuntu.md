---
title: "Help Dual Booting Windows XP &amp; Ubuntu"
date: 2006-09-01
forum: Installation &amp; Upgrades
---

### Post by dal2k5 on 2006-09-01
Hey, i downloaded grub and i'm lost:confused: ........ i'm afriad of ubuntu will get rid 
of my Windows OS ppl HELP ME!!!!!

---

### Post by tatimmer on 2006-09-01
order the Ubuntu cd, its free, boot up the install cd, it can partition, and install itself on free space and it can leave your vfat or ntfs partition alone.

---

### Post by orb9220 on 2006-09-01
You did not download grub it is a utility within linux. Do you mean the iso for ubuntu?

---

### Post by dal2k5 on 2006-09-01
> **tatimmer said:**
> order the Ubuntu cd, its free, boot up the install cd, it can partition, and install itself on free space and it can leave your vfat or ntfs partition alone.
thnx soo i dont need grub?

---

### Post by orb9220 on 2006-09-02
Grub is a builtin command used by linux to build a boot-loader and write it to the mbr of your hd. And if you have xp installed first then during the install the partitioning software should see your xp partition and leave it alone.

---

### Post by cotcot on 2006-09-03
If you are afraid for installing a dual boot you can install the bootloader on a floppy instead of MBR. With the bios looking for the floppy first you will have your windows as before when the floppy is out.

---

### Post by confused57 on 2006-09-03
cotcot is right, you can install grub to floppy during installation, but you have to use the Dapper alternate cd.

The Desktop live cd automatically installs grub to your Windows mbr.

---

