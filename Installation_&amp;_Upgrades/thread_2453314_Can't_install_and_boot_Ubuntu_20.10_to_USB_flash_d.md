---
title: "Can't install and boot Ubuntu 20.10 to USB flash drive (BusyBox Initramfs)"
date: 2020-11-07
forum: Installation &amp; Upgrades
---

### Post by stantonarch on 2020-11-07
I installed Ubuntu 20.10 from a USB flash drive to another USB flash drive and the installation process completed successfully, but when I boot the system, it boots into BusyBox with a initramfs prompt. I tried running the fsck command, but it doesn't exist.

The laptop is a Dell XPS 15 with secure boot disabled. I also have the internal SSD disabled, because I don't want Ubuntu touching that.

---

### Post by CelticWarrior on 2020-11-07
> [COLOR=#000000]I also have the internal SSD disabled, because I don't want Ubuntu touching that.[/COLOR]
It makes (some) sense if you want to have a "portable" installation on the USB, otherwise it doesn't make sense because the Ubuntu installer would need to install the bootloader (Grub) in the ESP (EFI System Partition).

So, now, I'm not sure whether 1) Ubuntu was booted and subsequently installed in the correct mode (UEFI mode) or 2) assuming #1 as correct, you're now selecting the correct boot order in UEFI settings.

---

### Post by oldfred on 2020-11-07
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

If internal drive disconnected then it should install boot loader to USB drive. But external devices boot from /EFI/Boot/bootx64.efi or device, not an "ubuntu" entry.
Both live installer and full install use bootx64.efi, but full install the bootx64.efi is a full copy of shimx64.efi. Installer is just to boot install media.

---

### Post by stantonarch on 2020-11-07
So, yes I'm trying to do a portable installation of Ubuntu. I should've titled my post that way. I did a search for how to do a portable installation of Ubuntu and still couldn't get it to work. So, I'm going to give up for now and maybe revisit this another time. I have done portable installations of other Linux distros with no problems. I guess Ubuntu is different.

I can still use Ubuntu in a virtual machine. It works fine there.

Thanks for your help.

---

### Post by garvinrick4 on 2020-11-08
Hard to just give up would drive me nuts not knowing what 
I am doing wrong and find the find the solution we have all
ran into problems nothing much different about installing any linux
distro really. Finish up thread and report your fix other users run into same
would help other users out. (Ubuntu I firmly believe is best distro). My thoughts anyway
for what they are worth. Have a nice day Stantonarch

---

