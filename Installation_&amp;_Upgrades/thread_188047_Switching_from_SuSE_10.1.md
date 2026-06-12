---
title: "Switching from SuSE 10.1"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by Mr_Cynical on 2006-06-03
I'm a Linux n00b and I recently (as in this morning) set up a WinXP/SuSE 10.1 dual boot. Thanks to the SuSE graphical installer I was able to easily set up the following:

37.5Gb NTFS (this was my existing Windows partition, it didn't change)
2Gb linux-swap (2x my RAM)
root partition (I think it's called root, it's the program-installing partition anyway) - reiserfs
home partition (separate, I read this was a good idea) - reiserfs
share partition - 5gb (for transferring files between Windows and SuSE) - fat32

Unfortunately, SuSE seems to hate my wifi card (which the Ubuntu 5.10 LiveCD recognised no problem, an Atheros 5005GS, as ath0) so I was going to switch to the new version of Ubuntu.

How do I uninstall SuSE? Presumably, I'll need to delete the contents of all the partitions except NTFS and FAT32 (well, if the FAT32 one gets wiped it's no problem because there's nothing in it), but keep the partitions themselves. Can this be done with Gparted, which is on my 5.10 LiveCD (and presumably will be on the new combined install/LiveCD)?

I'll also need to remove SuSE from Grub (without removing Grub itself or hosing my MBR). How do I do this, or does Grub do it automatically if I remove SuSE?)

When installing Ubuntu, I'll want it to use the same configuration (ie use the root and home partitions as appropriate, mount the ntfs as read-only [non-essential], mount the fat32 as read-write). Can this be done using the Ubuntu installer?

---

### Post by dglock on 2006-06-03
As to suse 10.1, search yast for the drivers for your card, it is supported.

  You can format the suse partiton at the same time you install ubuntu.

  You may have to edit your menu.list to remove the suse entry.

don

---

### Post by Mr_Cynical on 2006-06-03
As far as I am aware, the drivers ARE installed, but for some unknown reason SuSE simply will not detect the card (I've run all the appropriate information commands e.g. iwconfig and it doesn't even show up as an 'unknown device'), whereas even the Ubuntu 5.10 LiveCD detects it as 'ath0'.

---

### Post by Lux Perpetua on 2006-06-03
Mr_Cynical, there is no need to "uninstall" Suse explicitly. With that partitioning setup, you should format your Suse root partition and make it / for your Ubuntu during the Ubuntu installation. Don't format anything else, and mount your home partition as /home again. The benefit of having a separate /home partition is that your personal files remain intact even when you reinstall the operating system. 

About grub, it should be fine if you install it to the MBR when asked, but if you already have grub there, you shouldn't need to install a new bootloader at all. If you use the standard "desktop" install disk, then I've heard that it will write its own grub to the MBR without prompting you. That should not cause any problems.

edit: and everything you describe can be done with the Ubuntu installer. It can certainly be done with the "alternate" disk (I have a similar setup), but someone else will have to talk about the "desktop" installer.

---

### Post by Mr_Cynical on 2006-06-03
OK, I'm not all that bothered about my 'home' partition anyway, since all my data is still on my Windows partition since I haven't got SuSE working properly yet. Presumably re-installing grub with the Ubuntu installer will automatically fix the menu.list file dglock talked about?

---

### Post by Lux Perpetua on 2006-06-03
That shouldn't even come up, since you'll be formatting the old installation and the old menu.lst will be replaced by a new one. You might have to worry about menu.lst if you had a separate /boot partition that you weren't formatting, but you don't have that. 

The Ubuntu installer will probably tell you it recognizes Windows on your disk, which is good; it will then be able to set up the bootloader to let you choose between Windows and Ubuntu during boot. (If it doesn't, for whatever reason, then that can be fixed after the fact.)

---

### Post by Mr_Cynical on 2006-06-04
One more question - do I have to format 'root' BEFORE Ubuntu installation, or is this done as part of the Ubuntu installation program?

---

### Post by .t. on 2006-06-04
Ubuntu will do all the partitioning and formating for you, like YaST did, so you don't need to worry.

---

