---
title: "Installing Ubuntu on a Windows 8 Disk Without Dual Boot and UEFI"
date: 2013-05-17
forum: Installation &amp; Upgrades
---

### Post by aginzuj on 2013-05-17
I seem to be trying to do the reverse of what many people are doing (trying to dual boot Windows 8 and Ubuntu).  I have a disk drive that came out of a new computer that came with Windows 8 pre-installed on it.  I removed it from the new computer because I already had an Ubuntu installation on another disk drive that I was able to install and boot up (after turning on CSM mode) on the new computer.  

I now want to use the Windows 8 drive from the new computer to run Ubuntu 12.04 on my old computer, so I booted Windows 8 (on the new computer) and reduced it's partition size to leave space for the Ubuntu installation.  I don't need dual boot (Windows 8 probably won't run on the old computer anyway) but I don't want to completely eliminate Windows 8 from the disk drive either since I may someday want to sell the new computer that the drive came out of and may want to be able to re-enable Windows 8 on it.  The drive is a Seagate 1TB, 7200 RPM.

When I move the drive with Windows 8 and the resized partition to the old computer the BIOS won't even come up.  The computer just freezes at the manufacturer (Acer) splash screen.  If I unplug the disk drive I can enter the BIOS and boot Ubuntu from CD-ROM.  I even tried booting up Ubuntu from CD-ROM then hot plugging in the SATA cable after it came up, but the disk drive doesn't seem to be accessible once Ubuntu comes up.

The old computer does not have UEFI.  I suspect that there is something UEFI based on the drive that doesn't allow it to be accessed from a non-UEFI BIOS.  If so, is there a way to remove that restriction without removing the entire Windows 8 installation?  My new machine, that the drive came from, is a Lenovo H430 that has a Windows recovery partition on it.  I wouldn't mind removing the bootable Windows partition if the recovery partition can stay there so that I can reinstall Windows 8 if needed.  This UEFI stuff is a pain!

Any help would be appreciated.

---

### Post by fantab on 2013-05-17
There could be multiple reasons: 
Windows 8 pre-installed has UEFI boot, your older computer is probably BIOS only and does not know how to handle UEFI boot. Windows8 on disk could have "Secure Boot" entries and your older computer BIOS is clueless what to do with it.... Your OEM Windows8 licence key will be applicable on its native computer only, Windows8 hardware configuration is with your "new computer" and will not work with any other machine. etc, etc.

In short the disk with Windows8 is useless on any other computer. So you either remove windows8 completely or restore everything on that Disk to its factory condition and lock it away (so that you can later re-sell it with your "new computer" later).

---

### Post by aginzuj on 2013-05-18
I was just trying to boot from CD with the disk drive attached, but I guess with UEFI the BIOS gets hung just trying to locate the drive.  In any case, I have decided to make a recovery set of the Window 8 drive so I can re-create it if needed.  That way I can wipe the drive and start over with a fresh Ubuntu install without Windows 8 on the drive.

---

