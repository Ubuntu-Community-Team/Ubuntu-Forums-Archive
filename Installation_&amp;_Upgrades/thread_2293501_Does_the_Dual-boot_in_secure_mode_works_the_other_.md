---
title: "Does the Dual-boot in secure mode works the other way?"
date: 2015-09-05
forum: Installation &amp; Upgrades
---

### Post by hoveringfalcon on 2015-09-05
Its a common error that users can't boot into Windows through Grub  while using Secure-boot. Some "image not found" error comes up. Disabing  secure-boot works though. That is when when we install ubuntu after Windows.
Does this happen even if we install Windows later than Ubuntu & use Windows loader to get into Ubuntu?

---

### Post by grahammechanical on 2015-09-05
I am not sure that you are correct. Perhaps you are thinking of what happens when Windows is installed in EFI mode and we install Ubuntu in legacy mode. In that situation I think I am correct in saying that even though Windows appears in the Linux boot menu (Grub) Windows will not load.

Two things I am certain of and they are, 1) Install Windows after Ubuntu and the Windows installer will overwrite the Linux boot loader with the Windows boot loader; 2) The Windows boot loader menu will only dual boot Windows OSes. It will not recognise a Linux OS.

Regards.

---

### Post by hoveringfalcon on 2015-09-05
I am correct. When you install Ubuntu after Windows in Secure-boot mode, the grub will not be able to boot Windows, it will show some "image not found" when you click Windows.
Its happening to everyone who want to use Ubuntu to dual boot with Windows in secure mode.
Although, grub boots Windows successfully if we disable the secure mode even when we are using UEFI.

---

### Post by hoveringfalcon on 2015-09-05
> **grahammechanical said:**
> I am not sure that you are correct. Perhaps you are thinking of what happens when Windows is installed in EFI mode and we install Ubuntu in legacy mode. In that situation I think I am correct in saying that even though Windows appears in the Linux boot menu (Grub) Windows will not load.

Two things I am certain of and they are, 1) Install Windows after Ubuntu and the Windows installer will overwrite the Linux boot loader with the Windows boot loader; 2) The Windows boot loader menu will only dual boot Windows OSes. It will not recognise a Linux OS.

Regards.

Thi issue has been since 2012 and Ubuntu didn't correct it yet, check it out yourself - that's why people are not so sure about Linux yet - [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)

---

