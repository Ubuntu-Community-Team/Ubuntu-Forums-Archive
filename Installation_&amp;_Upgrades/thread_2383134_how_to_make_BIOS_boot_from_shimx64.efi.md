---
title: "how to make BIOS boot from shimx64.efi??"
date: 2018-01-21
forum: Installation &amp; Upgrades
---

### Post by fatemeh1998 on 2018-01-21
I've just installed Ubuntu alone on my acer aspire laptop. it installed successfully but it fails to boot. I tried boot-repair and here is the [link]("http://paste.ubuntu.com/26431088/"). in boot-repair message also there is sentence which says:
please do not forget to make your BIOS boot on sdb1/EFI/ubuntu/shimx64.efi file!"

I have problem with this sentence, how should I do this??
.

note: I have installed it in UEFI mode and windows boot manager is removed. secure boot is disabled

---

### Post by oldfred on 2018-01-21
Acer has an unique requirement of setting UEFI password and enabling "trust" on the .efi boot files from within UEFI.
Also old threads mention downgrading UEFI, newer say to upgrade. So make sure you have newest UEFI from Acer.

Several users posted what they did. Read several as some explain better than others.
 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)

---

