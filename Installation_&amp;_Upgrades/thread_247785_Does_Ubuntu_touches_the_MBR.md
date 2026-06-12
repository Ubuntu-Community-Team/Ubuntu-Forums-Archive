---
title: "Does Ubuntu touches the MBR ?"
date: 2006-08-31
forum: Installation &amp; Upgrades
---

### Post by ravinsp on 2006-08-31
I have WinXP on the first partition of my hard disk. I have several other extented partitions including a 50MB partition, 3GB partition and 500MB partition.

I'm going to install Ubuntu with following mount points:
50MB : /boot
3GB : /
500MB : Linux-Swap

Will GRUB leave the MBR as it is if i do this? (So I can later add an entry to boot.ini to load GRUB from windows boot loader.)

---

### Post by kerry_s on 2006-08-31
Yes, it will want to install grub to the MBR, if you select no it won't install grub there. Using grub is alot easier then setting up windows. Also i would make your boot a little bigger in case of kerenel updates or just not use a seperate boot partion at all. Swap should be at least 2x your ram. Make sure you try everything from the live cd first so you no that everything works when installed, take your time before you install get the feel of linux with the live cd.

---

### Post by leftwing on 2006-09-02
> **ravinsp said:**
> I have WinXP on the first partition of my hard disk. I have several other extented partitions including a 50MB partition, 3GB partition and 500MB partition.

I'm going to install Ubuntu with following mount points:
50MB : /boot
3GB : /
500MB : Linux-Swap

Will GRUB leave the MBR as it is if i do this? (So I can later add an entry to boot.ini to load GRUB from windows boot loader.)

Be careful !! 

If you use the standard Ubuntu Desktop CD, it will install GRUB on the MBR without asking anything!

If you want to install GRUB on another location, make sure you use the Alternate CD.

---

