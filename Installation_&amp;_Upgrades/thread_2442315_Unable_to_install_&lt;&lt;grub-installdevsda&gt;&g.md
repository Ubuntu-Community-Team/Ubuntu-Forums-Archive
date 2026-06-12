---
title: "Unable to install &lt;&lt;grub-install/dev/sda&gt;&gt; error. It is a fatal error"
date: 2020-05-02
forum: Installation &amp; Upgrades
---

### Post by retegi84 on 2020-05-02
Hello, while installing Ubuntu on a Lenovo machine where there were previously windows 7, I got the following error. Anyway, even though Ubuntu doesn't start, it does open a GRUB terminal. Is it a startup error? How can it be solved?
Thank you.

---

### Post by oldfred on 2020-05-02
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Windows 7 typically was BIOS/MBR, but systems since 2012 are UEFI.
So if you partitioned in advance on MBR partitioned drive, booted in UEFI boot mode, it will install in UEFI boot mode.
It can install to MBR partitioning, but UEFI highly suggests gpt partitioning. Either way you would need an ESP - efi system partition. If hardware is UEFI, use gpt & boot installer in UEFI boot mode.

---

