---
title: "Unable to boot ubuntu after windows upgrade (dual boot)"
date: 2024-02-14
forum: Installation &amp; Upgrades
---

### Post by nadav7679 on 2024-02-14
Hi guys,

I have a Lenovo laptop with dual boot - Ubuntu 22.04 and Windows 10.
After annoying windows updates, I'm suddenly unable to boot into ubuntu (am able to boot into recovery mode). 
Grub seems to work and windows as well.

I tried doing the recommended repairs using boot-repair but still no luck. Here is the pastebin:
[https://pastebin.ubuntu.com/p/SHD4kSSpXs/](https://pastebin.ubuntu.com/p/SHD4kSSpXs/)

Would appreciate any help!

---

### Post by oldfred on 2024-02-14
Did Windows update also update UEFI firmware. That may not have been obvious as part of Windows updates.
UEFI firmware update can reset some settings to defaults. Report shows UEFI Secure boot is now on. Did you install Ubuntu with Secure boot on.
With Secure boot on, you have to provide a MOK machine owner key to authorize the nVidia binary blob that you believe is secure. Ubuntu cannot automatically approve it as it is just a binary blob. 

If you did not create MOK you can just turn UEFI Secure boot off.
Windows updates may have also turned on Windows fast startup. Then grub may not boot Windows. You can turn fast startup off, or Boot Windows directly from UEFI boot menu.

---

