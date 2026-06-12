---
title: "help! install without cd-writer"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by unixguru on 2006-10-30
Ok here's the deal. I wanted to upgrade from dapper to edgy with the alternate install cd but the danm thing screwed up the system, in frustration i formatted the whole thing from windows only to find the grub error(how dumb](*,) ). I have only two bootable linux cd's hoary live, hoary install and dsl, so i installed dsl to hd with grub bootloader. I want to install edgy without cd-writer and using the alternate iso i already have. I tried debootstrap from hoary livecd but for the install i deleted the dsl partition and to my utter amazement found that i could'nt install grub after chrooting into the new environment. So back to square one and no grub, so again installed dsl but this time grub refuses to install in mbr so i use lilo. I also tried booting from the netboot kernel in edgy cd but that's just downloading the whole thing from net. The solution i propose is to use grub for NT to boot the edgy iso which i extracted to hda3(fat32) and pass the parameter INSTALL_MEDIA_dev=/dev/hda3 to select install media source as the extracted iso. will this work? Also, in expert mode there is a option of loading a module which allows the use of iso image for installation, what must i pass to the kernel to access this option?

---

### Post by unixguru on 2006-10-30
Bump

---

