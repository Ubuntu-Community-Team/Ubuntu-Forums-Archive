---
title: "Multiooting in Secureboot mode - vmlinuz invalid signature"
date: 2015-01-15
forum: Installation &amp; Upgrades
---

### Post by akashunbeatable on 2015-01-15
My system has Windows 8.1 installed by default. I installed  LinuxMint and openSUSE later. The problem is if I use openSUSE  bootloader, it is able to load windows but not linuxmint. The error  vmlinuz not signed. And when I use linuxmint bootloader (actually it  uses ubuntu bootloader), it is able to load openSUSE but not Windows.
  I want to use openSUSE bootloader.
  On openSUSE forum [https://forums.opensuse.org/showthread.php/504278-Multiooting-in-Secureboot-mode-Linuxmint-vmlinuz-invalid-signature](https://forums.opensuse.org/showthread.php/504278-Multiooting-in-Secureboot-mode-Linuxmint-vmlinuz-invalid-signature)  I was asked to get proper certificate for LinuxMint/Ubuntu bootloader  and load it with mokutil (of openSUSE) and later by MokManager.efi
  But from where can I source proper certificate for LinuxMint/Ubuntu bootloader
  And is there any other option

---

### Post by sudodus on 2015-01-15
Welcome to the Ubuntu Forums :-)

- You could [try also Ubuntu or one the the flavours Kubuntu, Lubuntu, Xubuntu, Ubuntu Gnome live]("http://ubuntuforums.org/showthread.php?t=2230389") and install what you like best and see if you have better luck concerning multi-booting.

- But I know that it is complicated with secure boot. Maybe an alternative is to ***switch off secure boot*** and try again - the computer should not be so fuzzy with signatures.

- If your computer is powerful enough to run one of the operating systems in a ***virtual machine*** (and I think it is, but please specify it*), then you can dual boot and run the third operating system in a virtual machine (for example VirtualBox). It may be difficult to install Windows into a virtual machine unless you get a full licence. So Windows should be one of the dual booters.
[HR][/HR]*) Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It makes it easier to give relevant advice.

---

### Post by Sally_Joshua on 2015-01-15
u just need to switch off secure boot

---

### Post by valmar-lp on 2015-01-15
Akashunbeatable, if you want to keep secure boot on, you have to add the public key of the other distribution to the bootloader you are using.

Please see this thread here, where I had the same problem:

[http://ubuntuforums.org/showthread.php?t=2260361](http://ubuntuforums.org/showthread.php?t=2260361)

Valerio

---

### Post by sudodus on 2015-01-15
Thanks for sharing your solution, [valmar-lp]("http://ubuntuforums.org/member.php?u=1912708") :KS

---

### Post by grahammechanical on 2015-01-15
The whole point of secure boot is to only allow executable files to run that have been signed with a key acceptable to the secure boot database. Ubuntu has such a signed kernel and has had it since the release of Ubuntu 12.10. The question is this: Does that version of Linux Mint have such a signed kernel?

Another point to consider. If Windows 8 is installed in EFI mode and it usually is, then Linux must be installed in EFI mode. We cannot mix and match. So, if Linux Mint is installed in legacy mode and Windows 8 installed in EFI mode, then the Linux Mint bootloader will not be able to load Windows 8.

Likewise, if Opensuse is installed in EFI mode but Linux Mint is installed in legacy mode, then the OpenSuse boot loader will load Windows 8 but not Linux Mint.

Regards.

---

