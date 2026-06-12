---
title: "installing on an AMD64 laptop"
date: 2006-03-06
forum: Installation &amp; Upgrades
---

### Post by jamzen on 2006-03-06
The laptop is a Winbook A730.  The first part of the installation went fine.  When I reboot, the system hangs at "* Starting hotplug subsystem".  Examining the console output, I find

[114.518045] PCI: Cannot allocate resource region 0 of device 0000:00:11.0

The boot commandline is
"kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro pnpbios=off acpi=off noapic nolapic quiet splash"

-- I've tried downloading and booting the AMD64 build of ubuntu05.10 as well.  Similar hangup.  Anybody seen this before?  Any advice?

---

### Post by jamzen on 2006-03-07
Following a suggestion on another thread dealing with installation problems, I installed dapper drake flight 4 and experienced no problems.  I'll play with this a little more and then see whether I can install an amd64 version of dapper.

---

