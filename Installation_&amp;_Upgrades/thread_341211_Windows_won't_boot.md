---
title: "Windows won't boot?"
date: 2007-01-18
forum: Installation &amp; Upgrades
---

### Post by xmrcivicboix on 2007-01-18
Hi guys, I new to Linux and installed KButunu last night. I installed it on an external hard drive and everything is working fine. However, when I unplug my external hard drive, nothing will boot. The message says "Grub Loading....." then error. I was wondering if there is a work around. to boot windows without my external hard drive installed.

Thanks

---

### Post by Theimon on 2007-01-18
Unplug your external disk, boot your system with a Windows bootdisk and at the command prompt /fixboot or /fixmbr. It will repair your Windows boot. However, when you plug in your external again, Kubuntu will not boot. Apparently you installed Grub on you Windows harddisk.
Next time, install Grub on your external harddisk and when you want to use your Kubuntu installation, adjust your BIOS settings to let the system boot from the external harddisk.

---

