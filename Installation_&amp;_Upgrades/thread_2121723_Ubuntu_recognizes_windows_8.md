---
title: "Ubuntu recognizes windows 8"
date: 2013-03-02
forum: Installation &amp; Upgrades
---

### Post by Andrewknowslinux on 2013-03-02
On my pc when i go click to install ubuntu (im using an live usb, not wubi.) the installer recognizes windows 8 and gives me an option to run along side windows. Now my PC does not have an UEFI bios it just has a normal bios. Anyway i just want to know if i select this option will this screw up the boot loaders? will it work normally? I have done this with windows 7 and older before but never on 8.

---

### Post by bcbc on 2013-03-02
It should work the same as with Windows 7, but Windows 8 has this thing called Fast-start which is hibernating the system session quietly in the background. So if you do a normal shutdown then the installer may find the windows partition 'hibernated' and it won't mount it. The way around this is to do a Restart, not a Shutdown from Windows.

The other thing is you can shrink the windows partition (if required) from Windows before running the installer. This will give you the free space without having to worry about the hibernated partition.

---

