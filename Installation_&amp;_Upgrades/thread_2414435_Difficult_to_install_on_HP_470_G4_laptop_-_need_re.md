---
title: "Difficult to install on HP 470 G4 laptop - need rescue mode to reinstall grub"
date: 2019-03-10
forum: Installation &amp; Upgrades
---

### Post by dgh3 on 2019-03-10
I've been using Debian 8.x and 9.x on this laptop for over a year,.
Its difficult to get the grub installed with the laptop's UEFI.
The technique works with Debian testing (buster) but I don't normally use it.

What works:
a) boot into firmware, turn off secure boot
b) use hardwired ethernet because wifi firmware is proprietary
c) boot install media in UEFI mode. I use the Debian stock install dvd. I have also used a flash drive.
d) make room for the install. I removed windows that came with the machine.
e) perform the install. I use a small /boot partition and an encrypted LVM

Installer has a problem installing grub-efi-amd64/

f) finish the install.and shut down the laptop.

Fix up grub:
a) boot in rescue mode off the install media, unlock the encrypted LVM
b) open up a shell, perform the following:
    apt-get install --reinstall grub-efi-amd64
    update-grub
c) after this fixup I can then reboot using firmware off the HDD

I don't know why the grub fixup step is needed, but it works.

The final step needed is to install the proprietary wifi driver on the running system:
a) boot as root or with sudo installed and hardwired ethernet
b) modify /etc/apt/sources.list file to include contrib and non-free
c) sudo apt-get update
d) Install wifi firmware
  (what worked for me was iwlwifi for the intel daughter card)
    see [https://wiki.debian.org/iwlwifi](https://wiki.debian.org/iwlwifi)

If anyone knows an easier way, please let me know.
HP advertises ubuntu 16.x on this system, but mine came with Windows installed.

---

