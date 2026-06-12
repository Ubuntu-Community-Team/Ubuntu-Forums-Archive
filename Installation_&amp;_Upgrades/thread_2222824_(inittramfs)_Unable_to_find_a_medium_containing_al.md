---
title: "(inittramfs) Unable to find a medium containing alive file system"
date: 2014-05-08
forum: Installation &amp; Upgrades
---

### Post by fernandojosecabral on 2014-05-08
Scenario: Toshiba Satellite 105.
CD-ROM unit? Yes, but never recognized (did not work even when the machine was new)
USB? Yes, four. They work once any sytem is running, but is not recognized by the BIOS during cold boot.
I have ubuntu running on it (it took me more than one day to install it piece by piece using wubi and several different tricks)

Goal: I want switch either to Zorin or Linux Mint

Problem: cannot boot from usb or cd-rom
I am trying grub2 (several different ways I found on the Internet). It seems to work up to a point. Then it
halts with the message:

```

BusyBox v1.20.2 (ubuntu 1:1.20.0-8.1ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(inittramfs) Unable to find a medium containing alive file system


```

It happens both with zorin and mint. Also happens when I use grub2 with or without explicit use of memdisk

Any hints? Or perhaps an easer way to switch from ubuntu 14.4 to linuxmint 16 (or zorin) using the harddisk only. Or perhaps using the usb WHEN ubuntu
is running (because usb works normally ubuntu is running. It only does not work as a boot device).

---

