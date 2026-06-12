---
title: "Can't install 18.10 on M.2 PCIe SSD - Dell Latitude 5490"
date: 2018-11-11
forum: Installation &amp; Upgrades
---

### Post by saz on 2018-11-11
I just got a Dell Latitude 5490, which came with a M.2 PCIe SSD.

At first try the installer would not detect the M.2 PCIe SSD drive; even with '*nvme_load=YES*' passed as boot argument.

I then went into the UEFI and realised that for some reason the drive was configured as RAID. This is very weird because it isn't RAID.

I changed it to AHCI ('*System Configuration > SATA Operation*') and now the drive appears in the installer. Installation proceeds without hiccups, and when it finishes I'm asked to reboot.

Once the system reboots, no bootable device is found - and that's where I'm lost.

For the record, Secure Boot is disabled and the BIOS is up-to-date.

---

### Post by pqwoerituytrueiwoq on 2018-11-11
Most M.2 SSDs are NVME does your board support NVME SSDs, assuming your SSD is NVME
M.2 slots are have different speeds based on the generation (2 and 3) and number of lanes (x1, x2 and x4)
There are also sata based M.2 SSDs, though the cost more than the 2.5" version in my experience (they have the same performance) so I personally do not see the why they need to exist, well I guess there are niche mobile use cases...

I do not know what the real effect of nvme vs not nvme is, but before i got mine i did notice something about it mattering if the board supports it, my board has a early implementation of M.2 nvme (i do not think you could buy M.2 ssds at the time the board was new)

Your bios could just have a different boot option for the M.2 slot, you may even need to use grub on a 2.5" drive to pass it to the M.2 drive if the bios does not support booting it directly

---

### Post by saz on 2018-11-11
> **pqwoerituytrueiwoq said:**
> Most M.2 SSDs are NVME does your board support NVME SSDs, assuming your SSD is NVME
...
Your bios could just have a different boot option for the M.2 slot, you may even need to use grub on a 2.5" drive to pass it to the M.2 drive if the bios does not support booting it directly

Not sure if the drive is NVME or not, but I'm sure that if it is then the board supports it - it is a **laptop**. It came with this drive from the factory, and it is the only drive. It came with Windows 10 installed and it worked, so I know for a fact it can boot from the M.2 slot.

EDIT: I just reinstalled Windows 10 and it booted perfectly (with drive in AHCI). So it really doesn't look like a BIOS problem/setting.

---

### Post by Dennis N on 2018-11-11
Possibly you installed Ubuntu in the wrong mode Legacy (BIOS) instead of UEFI, or vice-versa. Check the computer bios to see the boot mode the computer is set to use (UEFI or Legacy (bios)), you want to install Ubuntu in that same mode - Ubuntu installer should have entries for both modes in one-time boot menu (F12?) to select from.

---

### Post by oldfred on 2018-11-11
Most Dell have needed UEFI updates and many SSD have needed firmware updates.
They need the RAID or Intel SRT changed to AHCI which you already found. Normally you have to install the Windows AHCI driver first for Windows to work.

       Dell Precision 5820 with PCI NVME SSD UEFI update & SSD firmware update
[https://ubuntuforums.org/showthread.php?t=2402254](https://ubuntuforums.org/showthread.php?t=2402254)

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please attach link to the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by saz on 2018-11-12
> **Dennis N said:**
> Possibly you installed Ubuntu in the wrong mode Legacy (BIOS) instead of UEFI, or vice-versa. Check the computer bios to see the boot mode the computer is set to use (UEFI or Legacy (bios)), you want to install Ubuntu in that same mode - Ubuntu installer should have entries for both modes in one-time boot menu (F12?) to select from.

This was the problem thank you very much! For anyone else facing the problem, it seemed to be an issue with the way Rufus (v3.3) created the USB stick. When booting through UEFI mode it would fail to locate \EFI\BOOT\mmx64.efi:

```
Failed to open \EFI\BOOT\mmx64.efi - Not Found
Failed to load image \EFI\BOOT\mmx64.efi: Not Found
Failed to start MokManager: Not Fond
Something has gone seriously wrong: import_mok_state() failed
```

Upon failure, the system automatically booted the USB stick in Legacy mode -> and then Ubuntu was installed in Legacy mode -> and then I couldn't boot (no legacy mode for the internal M.2 PCIe SSD)

To fix I renamed grubx64.efi to mmx64.efi, and voila was able to boot Ubuntu live in UEFI mode, and thus install it in UEFI mode as well. Found my solution here: [https://askubuntu.com/questions/1085550/cant-install-ubuntu-18-10-on-xps-15-efi-boot-mmx-64-not-found]("https://askubuntu.com/questions/1085550/cant-install-ubuntu-18-10-on-xps-15-efi-boot-mmx-64-not-found")

For the record I've used the current version of Rufus v3.3 and followed the Ubuntu guide: [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0]("https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0") So perhaps Rufus needs an update, or the guide does.

Also, all my laptop firmware (UEFI, SSD, etc.) was already up-to-date via the *Dell Command | Update* utility. I did it before even trying to install Ubuntu.

EDIT: Might be worth noting that my aim was always a single-boot installation, which is why I wasn't so concerned about Legacy v.s. UEFI to begin with. But for some reason the system does not support Legacy boot for the internal M.2 PCIe SSD, only for external drives. :confused:

---

