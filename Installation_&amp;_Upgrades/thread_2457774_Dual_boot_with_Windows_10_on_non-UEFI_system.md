---
title: "Dual boot with Windows 10 on non-UEFI system"
date: 2021-02-08
forum: Installation &amp; Upgrades
---

### Post by danhinsley on 2021-02-08
I'm trying to install Ubuntu 20.10 on an older system that already has Windows 10 installed.  This machine is pre-UEFI, and the problem is having is the install worked fine, but I can't get the dual boot menu to come up, so it always boots into Windows.  This is a Dell XPS 435 MT with bios 1.1.14.  I've read a lot of posts, but just can't figure out what I need to do to make this work.

Thanks.

---

### Post by CelticWarrior on 2021-02-08
Welcome.

Please check [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) and boot from the same USB installer you used, then install Boot Repair using the 2nd option.
Use the Create a Bootinfo summary buuton and post it here. Do NOT try any repairs before your summary is checked by more experimented users here.

---

### Post by danhinsley on 2021-02-08
Awesome!  Quick, accurate response.  One minor issue is that on the last cut and paste command, using the -y without another parm (something about allow-purge-essential) wouldn't work.  But once I fixed that it worked like a champ.

Thanks so much for the help.

---

### Post by wpadiver on 2021-02-25
I have a similar problem but not quite. I had Ubuntu 20.10 running on my old PC when my Windows drive gave up. Did a new install of Win10 but neglected to disconnect my Ubuntu drive and so lost GRUB. Tried Disk repair from my USB Ubuntu and got this message:

[IMG]https://ubuntuforums.org/blob:https://ubuntuforums.org/ca169379-f338-484c-b8c9-3124c77c5062[/IMG][ATTACH=CONFIG]288006[/ATTACH]

I don't really comprehend what this is trying to tell me but I'm pretty sure I don't have UEFI firmware.

This is the URL Disk Repair gave me:
[https://past.ubuntu.com/p/3xPFY4Xy26/](https://past.ubuntu.com/p/3xPFY4Xy26/)

Thanks
Jim

---

### Post by yancek on 2021-02-25
Your output shows sda1 as /boot/efi and as a vfat filesystem.  If you have windows installed in Legacy mode, there is no reason to have an efi partition.  A default install of windows on a Legacy machine will not have a vfat filesystem unless it is an efi install which it is not.  Windows during its install has overwritten the Grub files in the MBR so you need to reinstall Grub.  Take a look at the link below, particularly Section 2.2 on reinstalling Grub.

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by wpadiver on 2021-02-25
Following section 2.3 Purging and reinstalling Grub via terminal commands I was able to get things working again. Thanks for the pointer. Although the only efi partition I could see was on my USB stick sdb.

---

### Post by yancek on 2021-02-25
Line 77 shows sda1 as esp, line 90 shows it as a vfat filesystem and sda is your 279GB drive.  Line 97 shows an EFI partition on sdb2.  Line 107 shows a FAT32 (vfat) partition on partition one of sda.  A windows boot partition will be an ntfs filesystem on recent versions of windows, except for EFI installs.  Same info on line 117.  Line 160 also shows shows boot/efi for UUID 9C8A-7BC3 which is sda1

---

