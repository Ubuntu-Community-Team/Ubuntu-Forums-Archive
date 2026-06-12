---
title: "Will I delete my efi partition?"
date: 2014-02-25
forum: Installation &amp; Upgrades
---

### Post by random417 on 2014-02-25
OK, this UEFI thing is new to me, but I got a new computer with Windows 8. (8.1 I believe, if it makes a difference). I believe I've gotten all the steps in place, and I'm ready to go, just one minor thing...

I don't feel the need to keep my Windows install, but when I went to install xubuntu, it didn't read that windows existed on it at all. My question is this: I understand that what the install will do in this case is overwrite my Windows. I'm alright with that, but I understand that UEFI uses a partition as part of the boot process. Is it possible that I would wipe out my boot process? Should I worry about not being able to get to the "BIOS menu"? It's probably a stupid question, but I'd rather check than screw it up, right?

EDIT: Apologies, I did forget to add the computer stuff:

It's a ASUS X551M, out of the box.

---

### Post by oldfred on 2014-02-25
Some Asus have worked better than others best to make a full image backup of your Windows. And make sure your live installer works.

You do need to have the always on hibernation off or fast boot. Often best to have secure boot off also.

       You will need to use the 64 bit version of 13.10 or 12.04.4 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode. You will also need Boot-Repair for several work arounds for Vendor UEFI issues and grub bugs.
Systems need Windows  fast start up (hibernation) and UEFI/BIOS fast boot quick boot UEFI settings. Vital for some systems.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive. Reboot after shrink so it can run its repairs to its new size.
Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

