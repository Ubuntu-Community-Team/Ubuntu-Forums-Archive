---
title: "blank screen when trying to install ubuntu 12.04 on a hp envy"
date: 2014-01-08
forum: Installation &amp; Upgrades
---

### Post by surfer on 2014-01-08
i'm trying to install ubuntu 12.04 on a brand new "HP ENVY h8-1550ez Desktop-PC". i manage to boot the bootloader on the flash drive where the ubuntu installer is located. on the drive i have an extracted ubuntu-12.04.3-alternate-amd64.iso . i see the grub menu and can select "Install Ubuntu" but then the screen goes blank and nothing happens.

i tried to change the grub boot lines: i changed "set gfxpayload=keep" to "set gfxpayload=text" and added "nomodeset" to the kernel line. still no luck. the screen stays blank and there is no indication that the computer is doing anything.

the graphics card is a "NVIDIA GeForce GTX 645". may this be the issue?

any help would be greatly appreciated!

---

### Post by surfer on 2014-01-09
ups, my mistake. forgot to switch off "Secure Boot" in the UEFI BIOS configuration... SOLVED.

---

