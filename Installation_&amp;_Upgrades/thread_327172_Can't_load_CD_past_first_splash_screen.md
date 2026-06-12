---
title: "Can't load CD past first splash screen"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by gene02 on 2006-12-28
I'm trying to install Ubuntu (6.10-server-amd64) on a Dell Dimension E521.  The boot process stalls after the initial splash screen, regardless of which option I choose on that screen.  Initially, I was getting a freeze after these lines:

[ 341.195032] megaraid cmm: 2.20.2.6 (Release Date:  Mon Mar 7 00:01:03 EST 2005)
[ 341.196393] megaraid: 2.20.4.8 (Release Date: Mon Apr 11 12:27:22 EST 2006)

So I tried disconnecting the Megaraid card (the installation is not going onto the RAID system, but a standard drive).  Without the megaraid, I get a freeze after these lines:

[  55.963282] SCSI subsystem initialized
[  55.967232] libata version 1.20 loaded.

I've been beating my head on this all day, but I'm not getting anywhere.  Any help would be greatly appreciated!

---

### Post by gene02 on 2006-12-28
...a follow-up:  "pci=noacpi" allowed me to get past the freeze.  Hopefully the rest of the install will work now.

---

### Post by gene02 on 2006-12-28
...more follow-up:  I was able to complete the installation once I used the pci=noacpi, but the installed system freezes during boot.  I tried adding the noacpi option to grub, but that didn't help.  The system freezes after these lines:

[  47.283869] PCI: Setting latency timer of device 000:00:0e.0 to 64
[  47.284001] ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xE000 irq 209
[  47.284070] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xBF2 bmdma 0xE000 irq 209


Help, please!

---

### Post by phatlip on 2006-12-28
Do you get a blinking underscore in the top left hand corner, then a message "cannot access tty;"?

---

### Post by gene02 on 2007-01-10
No, I just see the message I pasted in above.
I have figured it out, though, I have to add this to grub to get it to boot:

pci=noacpi noacpi noapci nolapic

I haven't tried these individually, but together they work.

---

### Post by magicfab on 2007-01-24
This is a known issue solved by upgrading to the latest BIOS from Dell.
See: [https://wiki.ubuntu.com/HardwareSupportMachinesDesktopsDellnSeries](https://wiki.ubuntu.com/HardwareSupportMachinesDesktopsDellnSeries)

---

