---
title: "Boot Repair Failed..."
date: 2014-04-29
forum: Installation &amp; Upgrades
---

### Post by manu-27993 on 2014-04-29
Hi.. 
I tried doing a dual-boot of ubuntu 14.04 trusty tahr with windows 8 on my HP Pavilion g6 using a live USB stick...
Both Secure Boot and Fast Boot options were disabled before installation.
Ubiquity did not show "Install alongside Windows" option...
I chose "Something else"
Installation went smoothly..
But on startup, it took me to Windows 8 directly...
I restarted and ran the live usb again to install boot repair... 
boot repair showed errors..
It resulted in this report.. [http://paste.ubuntu.com/7360029/](http://paste.ubuntu.com/7360029/)

Please advice me what to do next... I want Ubuntu on this laptop as soon as possible...

---

### Post by doug12 on 2014-04-29
Run [COLOR=#000000]boot repair twice, then do a cold boot, eg switch off, wait and then switch on again ...[/COLOR]

---

### Post by oldfred on 2014-04-29
Boot-Repair says you still have secure boot on?

Can you boot ubuntu entry from UEFI? 
Many HPs cannot it seems. HP seems to have modified UEFI to only boot Windows.

UEFI shows ubuntu entry:

BootOrder: 0002,3001,3002,3003,2001,2002,2003
Boot0000* USB Hard Drive (UEFI) - JetFlashTranscend 2GB
Boot0001* Windows Boot Manager
Boot2001* USB Drive (UEFI)
Boot2002* Internal CD/DVD ROM Drive (UEFI)
Boot3001* Internal Hard Disk or Solid State Disk
Boot3002* Internal Hard Disk or Solid State Disk
Boot3003* Internal Hard Disk or Solid State Disk
Boot0002* [COLOR=#ff0000]ubuntu.[/COLOR]

---

