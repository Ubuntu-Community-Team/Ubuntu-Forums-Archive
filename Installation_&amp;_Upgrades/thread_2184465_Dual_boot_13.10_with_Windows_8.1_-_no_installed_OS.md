---
title: "Dual boot 13.10 with Windows 8.1 - no installed OS"
date: 2013-10-29
forum: Installation &amp; Upgrades
---

### Post by Gordonbp531 on 2013-10-29
Upgraded pre installed Windows 8 to 8.1 - now trying to dual-boot with Ubuntu 13.10. When the install routine gets to the what to do part, it says "No recognisable OS found". I hesitate to contine manually, as I don't want Ubuntu to remove the ability to boot into Windows should I require to....

Anyone come across this and is there a fix?

NB - 13.04 works as it should and detects the Windows 8.1 OS....

---

### Post by oldfred on 2013-10-29
Did you boot both 13.04 & 13.10 in UEFI mode? If so it seems like a bug.

Is fast boot off. Is secure boot on or off. Normally suggest off, but should even work with it on.

Is system an Ultrabook with Intel SRT? It uses RAID that confuses things.

        sudo parted /dev/sda unit s print
    and if a second drive.
  sudo parted /dev/sdb unit s print

---

### Post by Gordonbp531 on 2013-10-31
13.04 installs perfectly normally (ie in the install process it sees Windows 8.1) with UEFI activated, and Intel SRT still enabled.
On the same system, with no changes, 13.10 does NOT see the installed Windows 8.1. So yes, IMHO that's a bug...

---

### Post by oldfred on 2013-10-31
You are the first (I think) that installed with SRT enabled. It used to be with older versions that the installer did not work at all, then with the more recent versions, the install would work, but grub would not install as RAID (the Intel SRT) would confuse grub on where it really should install.

---

