---
title: "Grub didn't install."
date: 2011-11-29
forum: Installation &amp; Upgrades
---

### Post by dagoth_pie on 2011-11-29
I've just installed 11.10 on my new laptop, it was meant to be a dual boot with Windows Seven Home Premium. The installation completed without error, but on rebooting, it booted straight into the windows bootloader, Grub doesn't seem to have installed. 

Does this resemble any known issues, maybe an oem lock on the boot sector or something? I installed off a usb stick if that makes any difference.

---

### Post by oldfred on 2011-11-29
Some computers do have security on the MBR set in BIOS. Some very new computers are now UEFI not BIOS.

Download this and post the boot_info_script link it creates. I do not think it can repair UEFI but can make minor repairs to BIOS based systems.

Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

