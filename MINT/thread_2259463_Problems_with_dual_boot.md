---
title: "Problems with dual boot"
date: 2015-01-04
forum: MINT
---

### Post by dani_elo on 2015-01-04
Hi,
I am a Win 8.1 user, I was trying to add Linux Mint to my computer for the first time ever as a dual boot and I have broken everything.

My boot repair code is [http://paste2.org/247f7Jm9](http://paste2.org/247f7Jm9)

---

### Post by howefield on 2015-01-04
Thread moved to the "*MINT*" section of the forum.

---

### Post by dani_elo on 2015-01-05
Any help?

---

### Post by JohnMorrow on 2015-01-07
Dani_elo:

Some 5 months ago I installed Mint 17 on my new Windows 8.1 laptop. I can tell you it was much harder than it used to be now that PCs have the UEFI BIOS. I hosed my system once in the process and had to restore from backup. The instructions that worked for me are here: [http://www.linuxbsdos.com/2014/06/11/how-to-dual-boot-linux-mint-17-and-windows-8-on-a-pc-with-uefi-firmware/]("http://www.linuxbsdos.com/2014/06/11/how-to-dual-boot-linux-mint-17-and-windows-8-on-a-pc-with-uefi-firmware/").  In my case, the linchpin to the whole business was finding the partition marked as efi and marking it as the location for the boot loader.

The above instructions leave out an important first step, to create a recovery drive from Windows. After my unsuccessful first attempt to install Mint 17, my laptop would not boot, so I reinstalled the factory installed software (Windows and everything else) from the recovery USB stick.  [http://windows.microsoft.com/en-us/windows-8/create-usb-recovery-drive]("http://windows.microsoft.com/en-us/windows-8/create-usb-recovery-drive").

Good luck!
John

---

