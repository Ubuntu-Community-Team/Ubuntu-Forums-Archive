---
title: "Booting from a externel CD...."
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by realproto on 2008-01-21
This is an old project I'm finally trying out after waiting for the right linux distro to install (Ubuntu 7.10).  I'm using a Pentium II laptop (circa 1999) with 128 MB of RAM,.  The laptop, Sharp Actius A200, has a BIOS that offers no option to boot from a USB source or CD drive (just HD or floppy ).  I ran wubi-cdboot.exe from Windows 98.  I plugged into the USB port, then tried booting from a standard CD-ROM drive using a USB2-to-IDE adapter just to see what would happen.  It detected the drive and actually booted!  Although is was slow some kernel options helped.   My question is why did it work???  Here's what the default menu.lst file contains:

find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz boot=casper     find_preseed=/ubuntu/install/preseed.cfg  quiet splash ro --
# other options not important here
initrd /ubuntu/install/boot/initrd.gz
boot

Does the vmlinuz contain usbcore modules?  How did it detect the usb adapter connection to the CD drive if no usb modules are loaded yet?  This project is important to me.  Now that I discovered this works I can use a CD to install Linux on PCs that don't boot from the CD drive.  FYI: the usb-to-IDE adapter is a no-name, plug-n-play compliant and made in China.

---

### Post by wolfen69 on 2008-01-22
> My question is why did it work???
for the same reason my usb stick is recognized as a HD in the boot menu. it is not a surprize really. depending on the bios, peripherals are recognized differently.

---

