---
title: "Ubuntu 18.04 LTS on Acer Switch Alpha 12"
date: 2018-04-29
forum: Installation &amp; Upgrades
---

### Post by leona on 2018-04-29
Ok, so I have got myself an acer switch alpha 12 2 in 1.
It comes with windows 10.
I put ubuntu 18.04LTS onto a usb stick and booted it.
All went well, in fact I was impressed that everything worked, wifi, sounds, video, screen, pen, all good.
So I thought, go ahead and install.
I made a 64gb space on the internal drive to install it.
Going through the install process and selected 'something else' for the install and setup mount points.
All went well until I rebooted.
I don't get the Grub boot loader, I get the Windows one.
Ubuntu doesn't show up in the boot list.
Turned off EFI then doesn't boot anything!
What do I have to do to get this to dual boot?
What am I missing?

---

### Post by oldfred on 2018-04-29
Edited title to be Acer since others may search on title info to find details.

All Acer have a unique requirement of setting "trust" on .efi boot files from within UEFI. Some Acer also have needed updates to newest UEFI from Acer.

Users with Acer have posted details, some explain better than others.

       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[URL="http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392"]http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392

[/URL]
 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141) 

[URL="http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392"]
[/URL]

---

### Post by leona on 2018-04-29
Amazing, thank you, will check these links out, shame it has to be soooo hard!

Anyway, the first link did it, added the files as trusted, (I incorrectly did the fw one which caused it to crash (rather boot loop)) but once I removed (or rather down as it wouldn't delete), it booed to grub with no issue, can boot Ubuntu and Windows now, lovely!  Thanks so much.

---

