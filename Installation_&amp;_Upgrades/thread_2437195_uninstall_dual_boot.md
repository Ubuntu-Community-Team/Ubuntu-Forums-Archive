---
title: "uninstall dual boot"
date: 2020-02-19
forum: Installation &amp; Upgrades
---

### Post by roberthleeii on 2020-02-19
I set my HP laptop up to dual boot ubuntu and windows 10 and want to remove ubuntu. Can I simply use my recovery USB drive I made from windows before I installed ubuntu and wipe everything and start over? I am unsure how that affects the boot process that ubuntu installed on my computer.

Thanks in advance,

Robert

---

### Post by mikewhatever on 2020-02-20
If that is what the recovery USB would do - wipe everything and start over, then likely yes. It is an overkill solution, but, since everything gets wiped, you should not have to worry about Ubuntu boot files.

---

### Post by yancek on 2020-02-20
Does your recovery usb set to factory defaults?  I would expect it will so I would investigate that before doing anything as any software you have installed on windows and any data will be deleted/overwritten.

Windows 10 should be an EFI install.  You need to verify that first.  If it is, you can simply format the partition on which you have Ubuntu from windows Disk Management then check the BIOS firmware and verify that windows boot manager is set to first boot priority and then remove the ubuntu entry from the EFI partition.  This is only if you are using the default EFI install for windows 10 which you haven't indicated.

---

