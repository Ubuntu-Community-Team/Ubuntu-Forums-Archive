---
title: "Installing Ubuntu with Bootable DVD"
date: 2013-03-27
forum: Installation &amp; Upgrades
---

### Post by Exp3rt on 2013-03-27
Hello all,
I wanna install Ubuntu from Bootable DVD. How is it's installation with Windows 8?:confused:
It means installing Ubuntu and Windows 8 together without remove my windows and other hard drives.

---

### Post by darkod on 2013-03-27
If you don't have unallocated space on the disk you will first have to shrink or delete some of the ntfs partitions. Do this with windows Disk Management, not the ubuntu installer.

If your machine uses uefi boot and has Secure Boot enabled, in most cases you need to go into bios and siable secure boot (for ubuntu 12.04.2 and 12.10 you don't need to do this), and then make sure you boot the ubuntu dvd in uefi mode, not legacy mode (you need to boot the optical device that says like UEFI: DVD-ROM....). Booting the dvd in uefi mode makes ubuntu install in uefi mode which is necessary to make uefi dual boot.

There are still some issues making an uefi dual boot, the uefi boot technology is still new and MS makes it harder to install linux, so many people have seen issues trying to make it to work. Personally I don't use uefi and don't plan to for as long as I can avoid it. :)

---

