---
title: "Multiboot with UEFI"
date: 2014-03-09
forum: Installation &amp; Upgrades
---

### Post by 2477426-5 on 2014-03-09
How to create a multiboot system with UEFI, from scratch? I have got a GPT capable hdd and UEFI boot enabled in BIOS? Which are the steps I must take for best results? I wnat to install Ubuntu, Linux Mint and openSUSE. Thank youvery much!

---

### Post by oldfred on 2014-03-09
Each should install its own boot files in separate folders in the efi partition.
It is somewhat like having multiple MBR's but all in one drive.
But you still have to choose one as default boot and then that one should have chain entries in grub menu back to the others in the efi partition.

---

