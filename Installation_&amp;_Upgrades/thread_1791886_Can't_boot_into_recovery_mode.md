---
title: "Can't boot into recovery mode"
date: 2011-06-27
forum: Installation &amp; Upgrades
---

### Post by TiberiusT on 2011-06-27
10.04x32

I am trying to update my nvidia driver, I have previously done this by booting into recovery mode, but holding [shift] doesn't work anymore - no matter what/how/why i press/hold etc etc the PC just boots as usual. I have done sudo update-grub

/etc/default/grub looks lie this, I have messed abt with it since this problem surfaced...

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=10
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="

alternatively, sudo /etc/init.d/gdm stop just gives me a black screen with a blinking cursor - is there a command I should type to get a prompt?

Tks

---

### Post by TiberiusT on 2011-11-03
Sorted. The 'peasants edition' Asrock P4i65G Mobo, or it's accompanying BIOS that I was using obviously had issues firing up a USB Keyboard prior to the OS. I swapped the USB Keyboard for an PS/2 plug one and I was able to get into Grub. Not the first time I've had this problem, I've found my antique PS/2 keyboard very useful quite a few times for getting into GRUB.

T

---

