---
title: "Won't boot after install"
date: 2013-02-19
forum: Installation &amp; Upgrades
---

### Post by sumguy on 2013-02-19
I'm trying to install Ubuntu 11.10. I've got a CD drive and an external USB 1.5TB drive for a hard disk. I go through the install process, create small boot (bootable flag), root and swap partitions on the disk, leaving my data in a big ntfs partition. The install seems to complete fine, but when I reboot, I get "Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key". The bios allows me to select the drive as the first bootable device.

Boot-repair gives me: [http://paste.ubuntu.com/1680067/](http://paste.ubuntu.com/1680067/)

Any ideas?

---

### Post by oldfred on 2013-02-20
Almost all of the tools BootInfo uses, found no hard drive at all. Is that the full report?

One listing did show a swap on sda6. If you have no internal drive then the USB drive may be sda?

Is BIOS seeing drive?

Have you unmounted external?

---

