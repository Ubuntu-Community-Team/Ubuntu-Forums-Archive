---
title: "ubuntu Bootloader fix after update"
date: 2022-11-17
forum: Installation &amp; Upgrades
---

### Post by shehzadgypsy on 2022-11-17
Hi,

I am a new Ubuntu user. Today during the critical update the progress stopped with the message that the rest of the installation will complete after reboot. This was in the middle of the installation and very puzzling. Instead of cancelling the update I rebooted the computer (mistake). Now the Ubuntu desktop don't boot up. I tried the Boot Repair from the Ubuntu live-usb with the instructions at here: [Boot-Repair - Community Help Wiki (ubuntu.com)]("https://help.ubuntu.com/community/Boot-Repair"). Here is the pastebin report: [Ubuntu Pastebin]("https://paste.ubuntu.com/p/dVMWxDmW6h/") ([https://paste.ubuntu.com/p/dVMWxDmW6h](https://paste.ubuntu.com/p/dVMWxDmW6h)). I did the recommended repair but that did not fix the issue.  Kindly help!

-shaan-4378

---

### Post by oldfred on 2022-11-17
You have UEFI system with UEFI install of Windows on gpt partitioned drives.
But show a bios_grub partition and grub in gpt's protective MBR which is used for BIOS/Legacy/CSM boot.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

Not sure why you do not have UEFI booting of Ubuntu.
Only real difference with BIOS & UEFI installs is the version of grub. BIOS uses grub-pc and UEFI grub-efi-amd64.
How you boot install media UEFI or BIOS is then how it installs or repairs.
You probably had settings to reinstall grub in BIOS mode, but something was not correct.

Did you reinstall grub in UEFI boot mode? The recommended repair?
Or did you get an error message?
And then system must be set in UEFI settings to use UEFI as default boot mode.

---

### Post by tea for one on 2022-11-18
The boot-repair report shows that you have three disks.
As a new Ubuntu user, have you considered installing each OS on separate disks?

---

