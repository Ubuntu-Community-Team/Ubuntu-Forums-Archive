---
title: "Can't install Linux Kubuntu on HP Pavilion 15-eh1001ur laptop. Laptop wouldn't boot"
date: 2021-09-06
forum: Installation &amp; Upgrades
---

### Post by tobiasthefourth on 2021-09-06
I recently bought a HP Pavilion 15-eh1001ur laptop. It had pre installed Windows 10.

I use Linux, so I installed Kubuntu on it using a USB. I used Guided installation - use whole disk. After installation, Linux doesn't boot. It all stops at HP logo, not moving forward.

Also the live USB mode doesn't boot. I get the "Initramfs unpacking failed: Decoding failed" error.

I also have Windows 10 USB, which the BIOS simply doesn't see.

I also have HDD with Kubuntu, which I connected using SATA-USB cable. It starts booting, shows Kubuntu logo, but stops at that.

Both USB with Kubuntu, USB with Windows 10 and HDD with Kubuntu work fine on desktop PC. USB with Kubuntu also worked fine on an old laptop.

I tried disabling Secure Boot - that didn't help. I can get the grub terminal to appear, however I can't load the kernel there (see picture).

I was thinking - maybe updating BIOS would help? I can't find the exact BIOS version that I have, though, only revision number - F.04. And also I worry that updating BIOS would void the warranty.

Are there any other options?

I also tried loading shimx64.file from BIOS. I get the "ACPI Error: AE_NOT_FOUND, while resolving a named reference package element" error (see picture).

PS The Kubuntu I'm trying to install is Ubuntu 20.04.3 LTS. The uname -r command shows
5.4.0-81-generic.

---

### Post by tobiasthefourth on 2021-09-06
Figured it out. Remade USB with Etcher with Kubuntu 21.04. It installed and booted.

Meanwhile old HDD with Kubuntu 20 (don't remember how it was made) wasn't booting. So the problem was either about the version of Kubuntu or about the way USB was made. Also I've tested Archlinux, its latest version, made with Etcher booted the live USB version fine. So if anyone is seeing this post, I suggest downloading the latest Etcher and the latest stable OS version, just to be sure. And use Linux PC to make that USB.


Also Windows 10 USB made with Etcher was finally seen in BIOS. It didn't install correctly due to lack of drivers, but that was to be expected.


So I suspect it was something about how the USB was made. Looking from this tutorial [https://www.top-password.com/blog/create-uefi-or-legacy-bootable-usb-drive-for-windows-10-setup/](https://www.top-password.com/blog/create-uefi-or-legacy-bootable-usb-drive-for-windows-10-setup/) it seems important to select correct boot style when creating USB. So if your BIOS is UEFI you better make sure you make  GPT-partitioned USB.

---

### Post by mikewhatever on 2021-09-07
Hm..., not sure who wrote the title, but apparently there was no problem with the installation process at all.
Kubuntu was installed, but then wouldn't boot, and also a USB with Kubuntu wouldn't boot. Now, a boot process and an installation process are, obviously, different things.
Perhaps try a more relevant title next time.

---

