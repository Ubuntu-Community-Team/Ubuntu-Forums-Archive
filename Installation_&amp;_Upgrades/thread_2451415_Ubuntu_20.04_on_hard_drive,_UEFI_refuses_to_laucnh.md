---
title: "Ubuntu 20.04 on hard drive, UEFI refuses to laucnh live Ubuntu from USB stick"
date: 2020-10-04
forum: Installation &amp; Upgrades
---

### Post by aimo-ella on 2020-10-04
I have only Ubuntu 20.04 on my laptop, and I have the USB stick that I used for installing it (I created it with Etcher). So far I have been able to use the live stick to perform some management activities such as disk checking. But now, after the latest Grub2 updates in the Ubuntu installation on my hard drive, UEFI on my laptop refuses to start live Ubuntu from the stick. More precisely, I don't even get the question whether to launch installer or Ubuntu. UEFI just says something like it cannot find signature. I am not sure of the exact message, because I know that UEFI uses timer for everything, so taking notes or a photo of it is so tricky that I haven't tried it yet.

Anyway, this seems related to "boothole", but is it? If I create a new live stick, does it matter which Ubuntu ISO file I choose? Does it matter which software I use to create the stick?

Please do not advice me to use BIOS or some such workarounds. I will not accept workarounds until I know what the actual problem is.

---

### Post by CelticWarrior on 2020-10-04
Welcome.

That the installation/live media doesn't boot due to the installed OS is a common misconception.

---

### Post by oldfred on 2020-10-04
Signature is related to UEFI Secure Boot.

Generally you can turn Secure Boot off in UEFI, but if on, you have to boot USB flash drive in UEFI Secure Boot mode. And if you need proprietary drivers, you have to provide  your own secure boot key as Ubuntu cannot verify third party drivers, but a user can if he believes it is secure (reliable third party).

Torvalds clarifies Linux's Windows 8 Secure Boot position
[http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

---

### Post by aimo-ella on 2020-10-04
I downloaded Ubuntu 20.04.1, created a new stick with Etcher and now I can get into live Ubuntu with UEFI and Secure Boot. Problem solved. It was caused by the recent update to secureboot-db (not grub) in the Ubuntu I have on hard drive.

---

### Post by CelticWarrior on 2020-10-04
> **aimo-ella said:**
> I downloaded Ubuntu 20.04.1, created a new stick with Etcher and now I can get into live Ubuntu with UEFI and Secure Boot. Problem solved. It was caused by the recent update to secureboot-db (not grub) in the Ubuntu I have on hard drive.

No, it was likely caused by corrupt media that was correct by redoing it.

---

