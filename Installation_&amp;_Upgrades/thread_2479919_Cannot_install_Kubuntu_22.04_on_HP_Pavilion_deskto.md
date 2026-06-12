---
title: "Cannot install Kubuntu 22.04 on HP Pavilion desktop"
date: 2022-10-13
forum: Installation &amp; Upgrades
---

### Post by pwabrahams2 on 2022-10-13
I'm trying to install Kubuntu 22.04 on my HP Pavilion desktop from a USB stick, but I can barely get started. I've turned off Secure Boot, so that's not the problem. I get the initial boot menu with "Try or install Kubuntu". When I select that, I get a burst of USB activity, and then -- nothing.   The machine just sits there, with the USB stick illuminated. I've checked the  boot medium by booting from it on a different machine, and it works.  I've also tried starting with "e" and adding **nomodeset**; it makes no difference.

I suspect a BIOS setting problem, bu I don't know what that might be.  What can I do?

---

### Post by yancek on 2022-10-13
Do you currently have another OS currently installed on this computer?  If so, what is it and which version?  Is this an EFI capable machine?  Are you booting in EFI mode?

---

### Post by pwabrahams2 on 2022-10-13
The machine, like most HP machines, came with Windows11 installed, and  it's working.  The machine is a a Pavilion Desktop TP01-2XX, according  to the BIOS.  I have no idea if it has EFI installed.  Is that the same  as UEFI?  I know it has UEFI because the BIOS indicates the UEFI boot  order.

---

### Post by pwabrahams2 on 2022-10-13
The machine, an HP Pavilion Desktop TP01, apparently supports UEFI; I have no idea what EFI is. How do I know what mode I'm booting in?

---

### Post by oldfred on 2022-10-13
EFI is UEFI.
Technically efi became UEFI v1 when Intel turned it over to the UEFI Forum and v2 released. Current standard is now  UEFI 2.9.
UEFI still uses an ESP - efi system partition for its boot files. So names often used interchangeably. 

Very new machines now only boot in UEFI mode. I believe Windows 11 is UEFI/gpt only. So if dual booting you must use UEFI.
Best to use Windows to shrink its NTFS partition & reboot, so it can run chkdsk. And make sure Windows fast start up is off. Often other UEFI settings may be required and vary both by vendor & model.

Older machines booted in Legacy/BIOS/CSM or UEFI and various brands of UEFI had somewhat different settings to choose.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

And booting a USB required an UEFI configured flash drive and correct choice in UEFI boot menu. Most flash drives can be booted in either mode and UEFI boot menu will give two choices, one clearly UEFI:xxxx and other just xxxx where that is the BIOS option.

Legacy boot mode is also only available with Secure Boot off and then you may also have to turn on an allow USB boot setting as allowing USB is not considered secure (but required if you have to repair system, so not sure why so restricted). 

Seems that HP used TP-01 for many models.
What are exact specs? What video card/chip?

---

### Post by tea for one on 2022-10-14
Some suggestions:-
In UEFI settings, temporarily disable TPM
Also disable Optane (If it exists)

Try a different USB port

Add the grub parameter acpi=off before booting the live session
[https://askubuntu.com/questions/1374545/booting-ubuntu-studio-sticks-at-different-points-hp-pavilion-desktop-pc](https://askubuntu.com/questions/1374545/booting-ubuntu-studio-sticks-at-different-points-hp-pavilion-desktop-pc)

---

### Post by pwabrahams2 on 2022-10-14
The magic incantation is **acpi=off**. Almost everything else is a distraction.  After the "Try Kubuntu" prompt, type **e** to edit, then insert it before **quiet** and exit with F10.

---

### Post by pwabrahams2 on 2022-10-15
There seems to be something in the HP version of Windows 11 that interacts badly with Ubuntu 22.04 and is disabled by **acpi-off**.  Turning off ACPI  is a workaround for an HP software defect.

It's asking a lot of end-users to understand the exotica of HP's software.

---

