---
title: "Possible to Convert Single Boot to Dual Boot?"
date: 2020-11-21
forum: Installation &amp; Upgrades
---

### Post by rebeltaz on 2020-11-21
I have Ubuntu 18.04 on a 500gb SSD in my laptop. I have a desktop with a 2tb harddrive with Windows 10 pre-installed. Is it possible to somehow move the linux partition from my laptop to a new partition on the desktop and have the ability to dual-boot?

---

### Post by oldfred on 2020-11-21
Just do a new install to Desktop system.
If you want same configuration & data, restore your /home, list of apps and any server type apps in / (root) from your normal backup of your laptop.

Is desktop UEFI?
If so lots of details in link below in my signature.

Shows live installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen 20.10 uses grub for both
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Shows Windows screens
[https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi)

---

### Post by rebeltaz on 2020-11-21
I haven't actually got the desktop yet - it'll be here in a few days - so not sure if it's UEFI or not. I will check out those pages though. Thanks.

---

### Post by Impavidus on 2020-11-22
If it has Windows 10 preinstalled from an official retailer, it must be uefi. Pretty much every computer from the past 8 years is.

Cloning your existing system from your laptop to your desktop is hard. There are many details you have to get right: UUIDs of partitions, proprietary drivers (if any), bootloader configuration, ... Just easier to do a fresh install.

---

### Post by rebeltaz on 2020-11-22
> **Impavidus said:**
>  Just easier to do a fresh install.

Yeah, I was afraid you'd say that.

---

