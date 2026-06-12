---
title: "Boot-Repair Summary Review"
date: 2018-03-22
forum: Installation &amp; Upgrades
---

### Post by mclemore on 2018-03-22
Here is the link: [http://paste.ubuntu.com/p/yQDcbKQ7WW](http://paste.ubuntu.com/p/yQDcbKQ7WW)

I'm trying to install Ubuntu on a new disk I have, so that I can stop dual booting off of just one disk, but after installing Ubuntu on the new disk I can't get into either installation. Instead, I'm just automatically booted into Windows.

---

### Post by oldfred on 2018-03-22
Windows works?
Script is not showing the files in the main install partition. 

It does look like Ubuntu/grub did install to the ESP - efi system partition on sdb.

If an Acer you must set "Trust" in UEFI. Some also have to upgrade UEFI to have trust settings.

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

### Post by mclemore on 2018-03-22
That worked perfectly. I just had to mark the EFI file as trusted and then change boot order for it to be checked first. Thank you!

---

