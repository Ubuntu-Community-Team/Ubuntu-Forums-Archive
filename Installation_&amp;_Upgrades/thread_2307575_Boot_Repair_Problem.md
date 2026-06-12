---
title: "Boot Repair Problem"
date: 2015-12-26
forum: Installation &amp; Upgrades
---

### Post by klarchen on 2015-12-26
[http://paste.ubuntu.com/14192358/](http://paste.ubuntu.com/14192358/)
Hi I am new to Ubuntu. I've installed it through a USB in Legacy mode. The installation was indeed successful but when I took off the usb and tried to boot it, it wouldn't boot. So I went to try Ubuntu mode and used boot repair. Still nothing and that's why I am here.

---

### Post by oldfred on 2015-12-26
There are 3 modes to boot once installed from UEFI boot menu. UEFI with secure boot, UEFI and CSM/BIOS/Legacy. 
There are 3 modes to boot install DVD or flash drive. If system has secure boot on, only that will show. But if secure boot is off, then you can boot flash drive in UEFI:ame of flash or name of flash(BIOS). And how you boot install media is how it installs.
But then system must also be set to boot in that same mode.

It looks like your install is CSM/BIOS, but you booted Boot-Repair in UEFI mode. You also have the ESP - efi system partition for UEFI boot and the bios_grub partition for BIOS boot. (I normally have both also).

It looks like you have AMD graphics which I do not know about. But it also need nomodeset.
If BIOS you hold shift key from vendor logo until grub menu appears. With UEFI you press escape key (sometimes several trys required) during UEFI/vendor logo boot.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

    But then how you boot install, depends on how you repair grub, BIOS or UEFI and then settings in UEFI to boot in that same mode. Check that you have BIOS/CSM/Legacy as UEFI setting to boot.

If you want UEFI boot later, you can change that be reinstalling grub in UEFI mode and change UEFI setting to boot in UEFI mode.

---

