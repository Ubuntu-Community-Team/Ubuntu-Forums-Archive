---
title: "Looking for Dual Boot Installation Instructions/Tutorial"
date: 2005-10-12
forum: Installation &amp; Upgrades
---

### Post by WildcatRay on 2005-10-12
I am looking for (hopefully) step by step instructions on setting up a dual boot installation of ubuntu and Windows 2000 Pro. I am intending to start with a brand new HDD, but have not decided if I will partition it or use 2 HDDs.

For a 2 HDD setup, which disk should have Windows and which ubuntu?

Thanks,
Ray

---

### Post by Pablo_Escobar on 2005-10-12
[https://wiki.ubuntu.com/WindowsDualBootHowTo]("https://wiki.ubuntu.com/WindowsDualBootHowTo")

Here You go :)

---

### Post by aysiu on 2005-10-12
You may find this helpful as well:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by WildcatRay on 2005-10-12
Thanks! I just found the second reference.

Does the file system for GRUB need to be FAT32? That is what I have read in the past.

Again, thanks,
Ray

---

### Post by aysiu on 2005-10-12
[QUOTE=WildcatRay]Thanks! I just found the second reference.

Does the file system for GRUB need to be FAT32? That is what I have read in the past.

Again, thanks,
Ray[/QUOTE] Grub is a bootloader, not a filesystem. FAT32 is for sharing files between Windows and Linux because both operating systems can read from *and* write to it. Windows XP and 2000 are generally NTFS, and Linux is usually EXT3 or reiserfs.

Grub should be on the MBR, though, if you want a simple dual boot. To make Windows' boot loader on the MBR and dual boot to Linux is tricky.

---

### Post by WildcatRay on 2005-10-13
[QUOTE=aysiu]Grub is a bootloader, not a filesystem. FAT32 is for sharing files between Windows and Linux because both operating systems can read from *and* write to it. Windows XP and 2000 are generally NTFS, and Linux is usually EXT3 or reiserfs.

Grub should be on the MBR, though, if you want a simple dual boot. To make Windows' boot loader on the MBR and dual boot to Linux is tricky.[/QUOTE]
Sorry that I did not make myself clear.

I am asking how the HDD should be formatted for GRUB. My previous investigations found that the HDD needed to be FAT32 for where the bootloader resides. (I'm assuming that is because Linux cannot write to NTFS-formatted HDDs/partitions.)

---

