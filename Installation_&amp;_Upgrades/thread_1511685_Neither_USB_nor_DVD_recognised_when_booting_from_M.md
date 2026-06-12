---
title: "Neither USB nor DVD recognised when booting from Macbook"
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by alexmoon on 2010-06-17
Hi,

I'm trying to install Lucid on a Macbook 4,1. I've got both a DVD and a USB (created using Ubuntu instructions and USB Startup Disk Creator) with ubuntu-10.04-desktop-i386.iso on them. (Is this the wrong version to use, maybe?)

There are three different ways I've come across to boot from a USB or DVD, and none of them work:
1) System Preferences > Startup Disk: when I do this, only the Mac's harddrive and 'Network Startup' are available as options for booting. Even when the USB and/or DVD are inserted and are showing up on the desktop, they aren't available as options in Startup Disk.
2) Hold down 'C' when the computer is booting up to boot from a disk: this doesn't seem to do anything.
3) Hold down 'alt/option' when the computer is booting up to get a list of boot options: a list appears, but the computer's hard drive is the only option. Neither the DVD nor the USB show up.

Any ideas on what to try next? 

Thank you!
sky.

---

### Post by lechien73 on 2010-06-17
From what I was reading, you need to install rEFIt - a separate boot manager for Intel-based Macs.

The project is located here: [http://refit.sourceforge.net/](http://refit.sourceforge.net/)

You should then be able to boot from different media, including from USB.

---

### Post by alexmoon on 2010-06-17
Thank you. I installed Refit, and after two reboots it gave me the menu. Unfortunately, it keeps asking me to insert a bootable device, even when my USB is inserted. But at least I'm a step closer now!

---

### Post by alexmoon on 2010-06-17
In the end I re-burnt the DVD using the Mac. Once I'd done that, it showed up in the boot menu of refit and I could install.

---

