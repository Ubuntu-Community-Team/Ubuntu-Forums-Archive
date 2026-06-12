---
title: "Ubuntu 11.10 crashes after installation on HP Pro 3400"
date: 2012-02-08
forum: Installation &amp; Upgrades
---

### Post by floppp on 2012-02-08
Hello,

I have a HP Pro 3400 (Intel H61 express, Geforce GT520) and I am trying to get Ubuntu 11.10 working.
I tried successfully to install Ubuntu 11.04 but with the 11.10 it stops working a few seconds after the boot menu (after beeping). I can use the kernel magic keys (to sync and reboot), but I don't have any terminal access (using Ctrl-Alt-F1). If I remove quiet and splash from the boot option, I don't see anything more

With a live CD and chroot+bind programs, I updated all the package using apt-get update, apt-get upgrade, apt-get dist-upgrade, tried to reinstall nvidia and xorg but it changes nothing.

I don't find any relevant error in the log message (see attachment)

While booting, I removed acpi with noacpi option (also tried nomodeset). I tried in recovery mode, but Ubuntu freeze when the recovery menu appears...

Thanks in advance for the help,

Florian

---

