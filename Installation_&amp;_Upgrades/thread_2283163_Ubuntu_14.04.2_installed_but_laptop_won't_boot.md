---
title: "Ubuntu 14.04.2 installed but laptop won't boot"
date: 2015-06-19
forum: Installation &amp; Upgrades
---

### Post by andrewajc on 2015-06-19
I'm having a bit of trouble with starting my laptop up (Asus N56v) after going through the installation of Ubuntu 14.04.2. It restarted at the end of the installation but then wouldn't boot anything.

The message I am getting when I turn my laptop on is:

[B]For Atheros PCIE Ethernet Controller v2.1.1.1 (12/23/11)

Check cable connection!
PXE-MOF: Exiting Intel PXE ROM

Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key

[/B]My laptop has Windows 8 on it, I opted for Ubuntu to be installed alongside the Windows 8 install. It did take me quite some time in the Bios to actually change the boot priority in order to install Ubuntu from a DVD in the first place (had to get it to boot in Legacy to be able to make the DVD drive 1st priority) I'm thinking I may need to change something in there to get it to boot?

Any suggestions?

Thanks

---

### Post by ajgreeny on 2015-06-19
I suspect that Win8 is installed using UEFI so your ubuntu in legacy mode will not boot as things stand.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You will have to reinstall or you could try running the Boot-Repair from my signature but just running the info script.  Do not at this stage accept the default repair.

I think it is possible for Boot_Repair to change the Ubuntu installation from legacy into UEFI which is apparently only a case of removing one grub package and replacing it with another, but I am no expert in dual booting, so just run the info script and post back here the pastebin URL so we can look at it and help you further.

---

### Post by andrewajc on 2015-06-20
> **ajgreeny said:**
> I suspect that Win8 is installed using UEFI so your ubuntu in legacy mode will not boot as things stand.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You will have to reinstall or you could try running the Boot-Repair from my signature but just running the info script.  Do not at this stage accept the default repair.

I think it is possible for Boot_Repair to change the Ubuntu installation from legacy into UEFI which is apparently only a case of removing one grub package and replacing it with another, but I am no expert in dual booting, so just run the info script and post back here the pastebin URL so we can look at it and help you further.
I'm posting from my laptop now, in Windows 8. I enabled 'fast boot' in the BIOS and it allowed me into Windows, and a "disk repair" was automatically performed by the laptop (took less than 30 seconds).

Thanks for the info about UEFI, I'll follow the instructions on how to install Ubuntu with it. I didn't realise there would be issues, having previously installed Ubuntu with no problems in the past on other laptops.

---

