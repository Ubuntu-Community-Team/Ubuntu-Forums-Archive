---
title: "Boot repair does not repair Grub"
date: 2014-01-27
forum: Installation &amp; Upgrades
---

### Post by kanesoban2 on 2014-01-27
Hello everyone

Boot-repair tells me, that Grub was repaired successfully. When i restart my machine, Windows 7 still starts by default instead of the Grub menu appearing.
Info:
[http://paste.ubuntu.com/6826461/](http://paste.ubuntu.com/6826461/)

---

### Post by oldfred on 2014-01-27
Some of the older versions of Ubuntu had UEFI boot, but not secure boot. It says 12.04.3 but that may not be correct?
You show this, which says you have not installed the current version and will never work with secure boot on, also Windows 7 will not boot with secure boot:
>  GRUB too old for SecureBoot



New systems with new hardware work much better with the newer UEFI updates in the newest Ubuntu or 13.10 or 12.04.4 that will be out in a couple of weeks. And vendors are making fixes to UEFI, so you may want to update UEFI/BIOS if vendor has a new version.

But have you gone into UEFI menu and try to boot from ubuntu entry?
Some vendors modify UEFI to only boot Windows. Boot-Repair has a work around by backing up and renaming the Windows file to really be grub. But then you can only boot Windows from grub menu not from UEFI.

You also show dual video. Both Intel & AMD.

---

