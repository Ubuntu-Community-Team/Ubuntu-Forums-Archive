---
title: "Error when Erasing Ubuntu 16.04.5 LTS and reinstall"
date: 2019-06-12
forum: Installation &amp; Upgrades
---

### Post by austincibulka on 2019-06-12
Hi all,

Last year I downloaded Ubuntu 16.04.5 on a bootable flash drive. I successfully used this to run ubuntu on my laptop. I ran into some problems and decided to erase my current version of Ubuntu and reinstall it. To do this, I re-inserted the flash drive and chose 'Install Ubuntu'. I go through the installer and select 'Erase Ubuntu 16.04.5 LTS and reinstall' as the installation type. I then get a decision to ‘Go Back” or ‘Continue in UEFI mode’.
When I continue in UEFI mode, the installation stops at the following error:

**The 'grub-efi-amd64-signed' package failed to install into /target/ . Without the GRUB boot loader, the installed system will not boot.**

When I choose 'Go Back' instead of 'Continue in UEFI mode', I get the following error:

**Executing 'grub-install/dev/sda' failed.**

**[B]This is a fatal error.**[/B]

No matter what, I am forced to end the installation. Then, when I restart my computer, I am no longer able to run Ubuntu unless my flash drive is inserted. I get another error on my laptop if my bootable flash drive is not in the computer:

[ATTACH=CONFIG]283423[/ATTACH]
 
I attempted to run boot-repair, using [these instructions]("https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/"), with no success. I no longer have anything on the computer which is of value to me. I just want a clean slate with Ubuntu as the operating system.

 
Can someone guide me through the errors I am getting to reach this clean slate?
 
Thank you.

---

### Post by Xian on 2019-06-12
> **austincibulka said:**
> 
**The 'grub-efi-amd64-signed' package failed to install into /target/ . Without the GRUB boot loader, the installed system will not boot.**


There is a lot of good information on this error:

[https://askubuntu.com/questions/789998/16-04-new-installation-gives-grub-efi-amd64-signed-failed-installation-target](https://askubuntu.com/questions/789998/16-04-new-installation-gives-grub-efi-amd64-signed-failed-installation-target)

---

### Post by oldfred on 2019-06-13
It sounds like you have a newer UEFI based system, but originally installed in the now 35 year old BIOS with MBR partitioning.
But this time you booted in UEFI boot mode and do not have gpt partitioning with the ESP - efi system partition for grub to install. The target in BIOS installs is just the MBR, if gpt and still BIOS, you also have to have a bios_grub partition. And if UEFI you need an ESP.

       Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Do you have your data in /home all well backed up?

Post this, if MBR usually BIOS, and if gpt usually UEFI:
sudo parted -l

---

