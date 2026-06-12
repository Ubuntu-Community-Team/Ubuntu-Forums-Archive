---
title: "Latest Ubuntu and Secure Boot"
date: 2017-01-07
forum: Installation &amp; Upgrades
---

### Post by ubuntini2 on 2017-01-07
Hi
Can anyone tell me whether it is necessary, or even recommended to disable Secure Boot in UEFI before doing a fresh Ubuntu installation?

Ditto for CSM or Legacy Boot(BIOS) mode.

I leave both untouched from their defaults(enabled) and only disabled Fast Boot in UEFI before my most recent install (Ubuntu-mate 16.04).

CSM enabled in my ASUS UEFI-BIOS means UEFI+Legacy Oprom are supported, which I assume means attempt UEFI first and fall back to BIOS Legacy if UEFI isn't supported.

Although I had to boot a couple times before my new Linux install was recognized by UEFI, didn't seem to have any other issues.
Just wondering is the 'disable Secure Boot' only applies to older versions of Ubuntu, or if there is some other advantage to doing so?

---

### Post by oldfred on 2017-01-07
If you have UEFI Secure boot on:
You can only dual boot from UEFI, grub will not chain load to Windows.
You will not be able to install any proprietary drivers that are integrated into Kernel as then kernel loses its signed capability. 
You may have to separately turn on allow USB boot as that is not secure. But most systems seem to need that to be on anyway.

CSM/BIOS is not Secure boot. So if Secure boot is on then you cannot boot in the 35 year old BIOS mode. That is more for compatibility with older systems/drives.

Most systems are either UEFI or CSM, but a few can have both settings on or need both on, but still give you the choice which way to boot.
My Asus motherboard would not boot flash drive in UEFI mode unless I had it set to UEFI only. Even a UEFI or BIOS setting would only boot in BIOS mode.

I normally turn off UEFI Secure boot, but if in future it is needed then would change.

---

