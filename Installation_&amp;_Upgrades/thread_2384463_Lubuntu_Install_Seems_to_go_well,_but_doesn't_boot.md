---
title: "Lubuntu Install Seems to go well, but doesn't boot"
date: 2018-02-07
forum: Installation &amp; Upgrades
---

### Post by kannak2 on 2018-02-07
I'm trying to install Lubuntu 17.10.1 on my Acer laptop (Aspire E5-575, model number N16Q2), which used to have Win10 installed by OEM. I chose to erase and install Lubuntu the first time, then tried some other things later. The install usually seems to go well, but it won't boot. It boots to my usb if I have it in, or says no bootable device otherwise. I tried boot-repair (edit: after doing an automatic partition install) and here is the result:

[https://paste.ubuntu.com/26535913/](https://paste.ubuntu.com/26535913/)

I've tried plain Ubuntu as well. I've tried letting the installer automatically decide partitions as well as tried to follow guides on how to manually do it, but nothing works.

---

### Post by oldfred on 2018-02-07
Acer has an unique requirement of setting an UEFI password and enabling "trust" on the .efi boot files. Only Windows works by default.
Make sure you have newest UEFI from Acer. Some older threads mentioning downgrading UEFI as trust setting was missing. But newer threads say newest UEFI works.

 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

### Post by kannak2 on 2018-02-07
Thanks oldfred!

I chose to set it to trusted using this guide linked by you [http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
Acer only provides bios updates designed for windows, so it would have been much more time consuming to do than the steps in this guide

---

### Post by oldfred on 2018-02-07
UEFI/BIOS is really only one configuration. 
I have only seen one or two that even mention anything other than Windows.
And if you call just about any vendor they know only Windows.

---

