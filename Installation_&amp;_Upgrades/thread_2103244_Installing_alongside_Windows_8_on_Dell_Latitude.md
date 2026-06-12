---
title: "Installing alongside Windows 8 on Dell Latitude"
date: 2013-01-09
forum: Installation &amp; Upgrades
---

### Post by aarpel on 2013-01-09
I have a Dell Latitude E6430 pre-installed with Windows 8 on a 256GB SSD.  

I followed the 'Installing Ubuntu Quickly and Easily via Trial and Error' steps from [UEFI page on the community help wiki]("https://help.ubuntu.com/community/UEFI") using the Ubuntu-Secure-Remix 64bit build.

The HDD is configured (and only recognized) in legacy mode, while the USB drive was booted with UEFI.

I've run Boot-Repair twice, to no avail.  The computer continues to boot directly into Windows with no trace of GRUB.

[http://paste.ubuntu.com/1513766](http://paste.ubuntu.com/1513766)

Any and all help is greatly appreciated!

---

### Post by Rebelli0us on 2013-01-09
Why not install Linux on a USB flash drive, that way you won't risk damaging your Windows partition.

---

### Post by aarpel on 2013-01-09
I'd prefer not to have my primary OS on an external device.
 
I'll likely be using Ubuntu 80% of the time, but have to keep the Windows 8 installation available to keep the corporate IT-types satisfied.

---

### Post by aarpel on 2013-01-09
Windows 8 was installed by IT, looks like it came from the factory with Windows 7, which may explain why its in Legacy mode for the SSD.

---

### Post by oldfred on 2013-01-09
A factory install of Windows 8 has to have secure boot, UEFI and gpt partitions. You have none of that. 

If your IT reinstalled Windows 8, they just installed in BIOS/MBR mode. You just need to install grub to the MBR.

If a corporate computer are you allowed to do this?

---

