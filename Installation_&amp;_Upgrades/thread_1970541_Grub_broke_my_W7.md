---
title: "Grub broke my W7"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by Znerox on 2012-05-01
I installed Ubuntu Server to an empty disk, and installed Grub, thinking it would work fine. Whenever I try to boot Windows 7 "Windows 7 (loader) (on /dev/sda1)", it starts loading, but right when the login screen is about to pop up the computer reboots with no error messages, and I get the Grub menu again. I've tried repairing it with the install CD but it's not working. How can I fix this?

---

### Post by darkod on 2012-05-01
Did you shrink the win7 partition with the installer? Since you said you installed on empty disk, I guess not.

Grub2 will only pass booting to the win7 boot files when you select to boot win7. From there on, it's up to windows to boot itself.

You can try running the boot info script from the link in my signature, and post the results as explained there. They will have more details. You can do all that from live mode (Try Ubuntu with the cd).

---

### Post by Znerox on 2012-05-01
I didn't touch the Windows disk. Even if i remove the Ubuntu disk, Grub still starts. I've tried rebuilding boot records and all that, but there's no change.

---

### Post by darkod on 2012-05-01
When you say rebuilding boot records, did you reinstall windows bootloader on the windows disk? And still you have the same problem?

If yes, then it's not grub related.

The win7 dvd should help you reinstall windows bootloader on the windows disk.

---

### Post by Znerox on 2012-05-01
I tried running "bootrec /fixboot" and "bootrec /fix fixmbr" but with no change. I also tried removing the Ubuntu disk and booting with only W7, but that just gives me Grub recovery, where I can't continue due to the Ubuntu disk missing. This is what windows recovery (from install usb/disk) shows after trying a restore.

[IMG]https://lh3.googleusercontent.com/-11o49htu6zM/T6AKD9C_zXI/AAAAAAAAJfo/cd4XJBIrOOQ/s1280/IMAG0082.jpg[/IMG]

---

### Post by Znerox on 2012-05-01
It appears I removed Grub and installed the default W7 bootloader. But I still have the same problem, and now Ubuntu won't start either...

---

### Post by Znerox on 2012-05-01
Oh wow, i found the problem. The issue wasn't Grub at all, it was that SATA was set to AHCI mode instead of IDE in BIOS, which somehow made the computer reboot while loading Windows. Thanks for your help anyway :)

---

