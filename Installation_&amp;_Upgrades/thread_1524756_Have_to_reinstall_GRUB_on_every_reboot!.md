---
title: "Have to reinstall GRUB on every reboot!"
date: 2010-07-05
forum: Installation &amp; Upgrades
---

### Post by Jason_X2 on 2010-07-05
I just installed Ubuntu 10.04 Server (64 bit) on a system with an Intel D975XBX motherboard. Installation went OK, but now every time the system reboots, the motherboard can't find any boot device. If I boot with a USB stick and use the recovery function to write a new GRUB installation to /dev/sda (the internal SATA drive where Ubuntu is installed) then removing the USB stick and rebooting works from the internal SATA drive. However, once I shut down or reboot, the same thing happens (can't find boot device). So, I have to recover AGAIN from the USB stick, and write a new GRUB installation to /dev/sda AGAIN. Then, it works for the next reboot cycle.

I have tried this with the internal SATA controller set to both AHCI and IDE. It doesn't make a difference, but this shouldn't even matter since the Intel board will still check for a bootloader.

Any help would be appreciated!

---

### Post by darkod on 2010-07-05
Are you talking about EFI boot by any chance?

If you are, I saw it mentioned in a thread few days ago but I don't know if they made it work. I only know it was a lot of hassle and didn't accept any fix we threw at it.

If your board is using EFI by default and there is a way to disable that, it sounds like much better choice.

---

### Post by Jason_X2 on 2010-07-05
> **darkod said:**
> If your board is using EFI by default and there is a way to disable that, it sounds like much better choice.
Ah, good call. Yes, I believe the D975XBX has an EFI BIOS. I looked into this, and there's an option in the "Boot" section of the BIOS setup that lets you choose between "Normal" and "Advanced." It was set to Advanced. I changed it to "Normal" and now it seems to be working OK. Thanks!

---

