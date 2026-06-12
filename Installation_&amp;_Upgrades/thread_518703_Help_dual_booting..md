---
title: "Help dual booting."
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by Ikith on 2007-08-06
Ok so I want to dual boot Ubuntu on my Gateway MX8711 which came preinstalled with windows vista. But I want to do it without damaging the current boot platform (sorry new to this) I love ubuntu and would like to try it after testing it on VMWare. Please help me out I know there are some good people out there willing to help a noob... :-)! Thanks!

Ikith

---

### Post by henriette_holm on 2007-08-06
Hi.

Assuming that you have ine hard drive. If your Windows partition takes up your whole drive you'll have to change the size of it during installation. One piece of advice would be to create the following partitions:

part 1 - Windows
part 2 - /
part 3 - swap
part 4 - /home

Also consider making a 5th partition (fat32) if you want to be able to share files between Windows and Linux.

After installation - when you boot your computer - you'll have a boot menu where you can choose between Windows and Linux.

More reading:

[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p3](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p3)

/Henriette

---

### Post by Ikith on 2007-08-06
> **henriette_holm said:**
> Hi.

Assuming that you have ine hard drive. If your Windows partition takes up your whole drive you'll have to change the size of it during installation. One piece of advice would be to create the following partitions:

part 1 - Windows
part 2 - /
part 3 - swap
part 4 - /home

Also consider making a 5th partition (fat32) if you want to be able to share files between Windows and Linux.

After installation - when you boot your computer - you'll have a boot menu where you can choose between Windows and Linux.

More reading:

[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p3](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p3)

/Henriette

Its running a serial ata since when I was trying to install XP over vista it wouldn't pick it up without text based drivers.

---

### Post by henriette_holm on 2007-08-07
I'm not sure I understand what you mean. Did you already try to install Ubuntu and it didn't work? Or did you try to install XP instead of Vista but couldn't?

/Henriette

---

### Post by logos34 on 2007-08-07
> **Ikith said:**
> Ok so I want to dual boot Ubuntu on my Gateway MX8711 which came preinstalled with windows vista. But I want to do it without damaging the current boot platform (sorry new to this) I love ubuntu and would like to try it after testing it on VMWare. Please help me out I know there are some good people out there willing to help a noob... :-)! Thanks!

Ikith

It won't (shouldn't) damage vista in any way, but linux will overwrite the vista boot loader with it's own--Grub.  I would encourage you to use it.  But if you prefer not to, you can use[ EasyBCD]("http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home") to add linux to your vista boot loader.

Consider making a separate /home partition, as Henriette_Holm suggested.  But you really don't need a fat32 partition to share files, since the fs-driver will allow you to read+write to ext3 linux from your windows/NTFS partition.  (and get NTFS-3g driver on the linux side to write to windows).

---

### Post by Computer Guru on 2007-08-09
EasyBCD will work fine for adding Linux to the Vista Bootloader - but don't use the ext3 driver on Vista - it really doesn't work too well with chronic BSODs and worse.

---

