---
title: "Via C3 Machine - Boot Troubles"
date: 2007-02-22
forum: Installation &amp; Upgrades
---

### Post by jbs398 on 2007-02-22
So, I've got an Asus Terminator C3, and I'm trying to set it up as a NAS.  I've gotten FreeNAS to install OK, but raid 5 performance is a little on the slow side and I wanted to try Ubuntu.  The install for Ubuntu Server goes OK with 6.10, but after reboot, I can't get the system to boot from the hard drive (which FreeNAS has booted from, so the drive's not bad), grub loads, does the short countdown, then it sits with a flashing cursor for a second, then I see a flicker of "Starting Up..." and then the system reboots.

Any ideas?  I've tried noapic, acpi=off and tweaking various BIOS settings.  I'm at somewhat of a loss...

---

### Post by panthar on 2007-04-25
I am having this same issue.  I got the latest Debian installed without a hitch on this machine. And it also boots fine from an external drive that has Feisty installed.  It just will not boot from the internal drive with the kernel that Feisty installs.  And since the machine reboots almost instantly after it moves from GRUB to loading the kernel, I'm having a hard time figuring what is causing this to fail.

---

