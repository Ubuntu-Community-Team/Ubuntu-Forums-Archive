---
title: "Problems Installing Ubuntu 7.10 &quot;modprobe&quot; error"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by Sir Skillz on 2007-11-03
I just got my Ubuntu 7.10 Live CD from Shipit.  When installing I get this error

--------
udevd-event[1730]: run_program: '/sbin/modprobe' abnormal exit


BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _

-------

Thinking it's a live CD problem I downloaded the Alt. Install Disk and still get the same error.  Then I tried to remove some of the add-on hardware* for my computer, disable the floppy drive, added some the boot commands, but still the same error comes up.  The Alt. install disk do "try" to install by leaving the setup at the error, but in the text install it hangs at the floppy detect (even with it disabled
:confused:).
This never happened with the early versions of Ubuntu I used (got 7.04 running right now, but the update broke the nvidia driver).

My Hardware.
Athlon XP 2400+
VIA Motherboard
Geforce Ti 4600
512MB DDR ram
Soundblaster Live! -> removed
Belkin 5xUSB PCI -> removed
Ethernet card PCI -> removed

PS: Both Live and Alt. Disks work on my 'Compaq Presario V6000' laptop using "noapic irqpoll noirqdebug" command.

---

