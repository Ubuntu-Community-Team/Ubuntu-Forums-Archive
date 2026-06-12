---
title: "Dual boot install ok but now Windows option doesnt appear in grub menu"
date: 2022-10-28
forum: Installation &amp; Upgrades
---

### Post by jethrot on 2022-10-28
How can I get Windows to appear in the grub boot option after installing Ubuntu please?7

---

### Post by yancek on 2022-10-28
Have you tried running:  sudo update-grub?
Are both Ubuntu and windows (version?) installed in the same mode, both UEFI or both Legacy?  Grub installed Legacy won't boot a windows UEFI.  Check the directory /boot to see if you have an efi/EFI directory with ubuntu in it.

---

### Post by bsniadajewski on 2022-10-28
You can also check if "GRUB_DISABLE_OS_PROBER="false"" is present in the /etc/default/grub file.  If not, enter it in there, save it (will require password), and then run "sudo update-grub".

---

