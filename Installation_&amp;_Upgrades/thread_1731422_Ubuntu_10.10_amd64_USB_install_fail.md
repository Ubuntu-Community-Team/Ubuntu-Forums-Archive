---
title: "Ubuntu 10.10 amd64 USB install fail"
date: 2011-04-17
forum: Installation &amp; Upgrades
---

### Post by morten49 on 2011-04-17
This applies to USB install sticks for Ubuntu Server 64-bit made with both Universal USB Installer and UNetbootin (only tested from Windows).

Both applications extracts, expands and rearranges installation files from the .iso to folders on a USB drive. Unfortunately, when copying files from  ubuntu-10.10-server-amd64.iso some of the filenames are too long for the extraction part of the app to handle. This means that some filenames are shortened.

The effect is that the installation starts, gets to detecting and mounting the CDROM but fails with 'No Common CDROM' and/or some files not found check the integrity of your CD.

Solution:
Manually edit the affected filenames. 
For me it was a number of files in: <usb-drive>:\pool\main\l\linux\
The only extensions (file types) that should be there are .udeb or .deb. If any of the files have extensions like .u or .ude etc, change them to .udeb

This fixed it for me.

Ref: [https://bugs.launchpad.net/unetbootin/+bug/672978](https://bugs.launchpad.net/unetbootin/+bug/672978) (thanks to dEUS101)

---

