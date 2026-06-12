---
title: "System won't boot off of server or alternate CD"
date: 2007-12-21
forum: Installation &amp; Upgrades
---

### Post by goldenfri on 2007-12-21
I am having a major problem trying to install ubuntu server on my system.

I have been running Knoppmyth on it for years and have done many upgrades, but no longer use mythtv so I want to install ubuntu on it instead.

The problem is that when I try and boot from the server or alternate cds I get a crc error and Kernel panic. I have tried many diffrent CDs and dvds burned from diffrent computers. The wierd thing is that the normal desktop CD will boot up fine but I don't want gnome and all that. I want the server version.

The exact error is:
crc error
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(104,1)

I have tried:
acpi=off
acpi=force
pci=off
etc

nothing works and its really starting to annoy me and I'm about to goto another distro.

Any suggestions?

System Info:
Athlon XP 1800+
512MB RAM
Soyo Dragon Plus motherboard (KT266a chipset)

---

### Post by anregen on 2007-12-27
I have a very similar problem only I had this trouble with the desktop CD (I didn't try server).

My solution was to hit F6 at the menu to bring up the boot options, then ADD (I didn't delete anything) acpi=off

I had a similar problem on this machine when I was running FreeBSD where I had to disable acpi.

I'm on a Dell optiplex gx270

Let us know if that helps you?

---

