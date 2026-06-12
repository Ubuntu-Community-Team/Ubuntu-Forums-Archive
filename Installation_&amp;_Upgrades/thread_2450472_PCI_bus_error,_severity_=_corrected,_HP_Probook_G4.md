---
title: "PCI bus error, severity = corrected, HP Probook G4"
date: 2020-09-14
forum: Installation &amp; Upgrades
---

### Post by webmanoffesto on 2020-09-14
I'm having a terrible time trying to get Ubuntu 20 installed. This is an erase-all fresh install.

After installation is completed I sometimes can't even reboot or maybe I can reboot a few times, but then I get the dreaded neverending scroll of "PCI bus error, severity = corrected,"

This laptop has UEFI. On reboot, to live DVD of Ubuntu 20, I can choose UEFI DVD or Legacy DVD.

My HD is GPT.
/dev/sda1, biosgrub or efi boot, 1 GB
/dev/sda2, ext4, /, 40 GB
/dev/sda3, ext4, /home, 900 GB
/dev/sda4, swap 

With my disk already partitioned, I let Ubuntu do it's install (not "something else"), I successfully booted into Ubuntu. Then on about the 3rd reboot "pci bus errror".

Some forum posts say I need "Method nomodeset" 
[https://ubuntuforums.org/showthread.php?t=2381339](https://ubuntuforums.org/showthread.php?t=2381339)

But how would I do that.
Also, once I see the "pci bus error" I can no longer do anything to repair it.

Is this related: When I am able to boot into Ubuntu 20 I then get a warning that my root partition is nearly full (only 650MB available).

Laptop: HP ProBook 450 G3

---

### Post by webmanoffesto on 2020-09-14
I followed the instructions on the below two pages. I've rebooted 4 times and ... so far, so good :-)

[https://ahelpme.com/tag/pcie-bus-error/](https://ahelpme.com/tag/pcie-bus-error/)
Under Ubuntu you can add in the file
/etc/default/grub
the following line
[B]GRUB_CMDLINE_LINUX="pcie_aspm=off"
[/B]
[https://itsfoss.com/pcie-bus-error-severity-corrected/](https://itsfoss.com/pcie-bus-error-severity-corrected/)
Add pci=noaer in this line. AER stands for Advanced Error Reporting  and &#8216;noaer&#8217; asks the kernel to not use/log Advanced Error Reporting. The  changed line should look like this:
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=noaer"**

---

### Post by CelticWarrior on 2020-09-14
I'm glad you solved it.

This is an unrelated comment pertaining to your installation mode and partitioning only.

1. You want UEFI mode, period. So, I hope sda1 is the ESP (EFI System Partition). Anyway, it can't be both.
2. 1GB for ESP is absolutely insane*. Less than half of that is enough to boot 10-12 different OSes. 1GB is a waste of space.
3. Since many releases ago Ubuntu doesn't use a swap partition by default. It uses a swapfile. A separated swap partition isn't needed. And very likely another huge waste of space if anything bigger than 2GB for normal usage without hibernation which you shouldn't use anyway and not even enabled by default, same as Windows.


* In my current installation with Ubuntu standalone **only 9MB **of the 537MB ESP (installer default) is used.

---

