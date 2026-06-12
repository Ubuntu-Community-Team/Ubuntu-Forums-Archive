---
title: "boot-repair can not fix with /boot partition"
date: 2016-06-28
forum: Installation &amp; Upgrades
---

### Post by hazzapotter on 2016-06-28
I have just moved an SSD from my mac osx into a laptop. The SSD had two ubuntu partitions + mac partition (that I never used). One partition is a normal partition with everything stored under /, but the special partition has a /boot partition too. After placing the SSD into the new laptop I could boot into both partitions. I did sudo apt-get update && sudo apt-get upgrade on the special partition. I could still boot into either partition. Then upgraded the normal partition and noticed that only the normal partition + mac partitions were visible on the boot menu.

I tried to fix this using Boot-Repair, however I get an error message saying that I need an EFI-compatible version. Here is a paste from the Boot-Repair tool : [http://paste.ubuntu.com/17993991/](http://paste.ubuntu.com/17993991/)

Any help appreciated.

---

### Post by oldfred on 2016-06-28
I do not know Mac. But they use UEFI.

But you have installed Ubuntu in BIOS boot mode on a gpt partitioned drive and it looks like you have created a hybrid MBR/gpt drive, which is not recommended.

If Boot-Repair is asking for  the ESP - efi system partition, then it is trying to reinstall grub in UEFI boot mode. And your ESP is sda1 in the gpt partition, but not in BIOS/MBR.[URL="http://www.rodsbooks.com/gdisk/hybrid.html"]

http://www.rodsbooks.com/gdisk/hybrid.html[/URL]
 convert hybrid to protective MBR gdisk experts commands  p, x, n, p, w
[URL="http://askubuntu.com/questions/650194/repair-windows-boot-loader-after-installing-ubuntu-on-macbook-pro"]http://askubuntu.com/questions/650194/repair-windows-boot-loader-after-installing-ubuntu-on-macbook-pro
[/URL]
 [http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios](http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios) [URL="http://askubuntu.com/questions/650194/repair-windows-boot-loader-after-installing-ubuntu-on-macbook-pro"]
[/URL]

---

