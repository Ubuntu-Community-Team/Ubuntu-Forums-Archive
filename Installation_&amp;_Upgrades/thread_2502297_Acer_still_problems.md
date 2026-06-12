---
title: "Acer still problems?"
date: 2024-11-08
forum: Installation &amp; Upgrades
---

### Post by freedom1984 on 2024-11-08
Hello!
I'm thinking of buying an Acer notebook as it offers the best deal for the money, but in the past Acer has often caused problems with the bios etc. for inexperienced Linux users.
[https://wiki.ubuntuusers.de/EFI_Problembehebung/#Acer-Rechner](https://wiki.ubuntuusers.de/EFI_Problembehebung/#Acer-Rechner)
Chat-GPT claims that Acer is accommodating to Linux users on newer machines, but it's still a budget model (I'm dirt poor).
What is your experience?
Can you say anything about this model?
[https://www.notebooksbilliger.de/acer+aspire+15+a15+41m+r4an+851447](https://www.notebooksbilliger.de/acer+aspire+15+a15+41m+r4an+851447) 

I'm constantly messing up my Ubuntu system anyway.

On the one hand, it would be better to switch to Windows, on the other hand, since I want to learn descriptive statistics with Python and R, I could start right away with Ubuntu Command and teach myself.

But now I still have a Thinkpad E540, which I could use for Ubuntu, and the Acer for Windows.

I'm undecided...or I'll wait for a better deal.

---

### Post by oldfred on 2024-11-09
Acer is the only one that requires you to go back into UEFI System settings and enable "trust" on the unknown(ubuntu) entry in UEFI boot.
Many new systems are UEFI only, my Dell says "BIOS" but once in BIOS it says UEFI only.

Models with similar issues:
Aspire V 15 Nitro Trust settings required. 2024
[https://askubuntu.com/questions/1518065/dual-boot-windows-ubuntu-in-acer-no-grub-showing-up](https://askubuntu.com/questions/1518065/dual-boot-windows-ubuntu-in-acer-no-grub-showing-up)
Trust
[https://askubuntu.com/questions/908854/installed-ubuntu-17-04-and-now-cant-boot-at-all-failed-to-open-efi-boot-grubx](https://askubuntu.com/questions/908854/installed-ubuntu-17-04-and-now-cant-boot-at-all-failed-to-open-efi-boot-grubx)

ACER sf514 laptop UEFI Class 3 (UEFI only) "SATA" mode for drives
[https://unix.stackexchange.com/questions/615603/in-uefi-class-3-how-install-centos-8](https://unix.stackexchange.com/questions/615603/in-uefi-class-3-how-install-centos-8)
Acer Aspire 5 Model A515-54-5649  Intel Core i5-10210U Install Tutorial
[https://ubuntuforums.org/showthread.php?t=2437702](https://ubuntuforums.org/showthread.php?t=2437702)
Acer Aspire A515-54G Newer Acer -  CTRL S on the main Tab in BIOS to get the option to change SATA to AHCI
[https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected](https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected)

If newer model, it will need 24.04.1 LTS or maybe the short term support version 24.10 to have latest kernel & drivers.

---

