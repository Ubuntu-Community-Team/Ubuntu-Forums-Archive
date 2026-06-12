---
title: "hotplug subsystem hang up.."
date: 2006-02-19
forum: Installation &amp; Upgrades
---

### Post by mlmpihl on 2006-02-19
Hi there.

When I  install ubuntu, in 2.stage, after the cdrom install, when the machine boots to finnish installing, the computer comes to a halt during "Starting hotplug subsystem"

I can't seem to get around it?

My computer is a laptop with intell centrino cpu, ati graphichs radion 700, brand: Fujitsu/Siemens, model Amilo M1437G

Anyone that can help?

Regards Kenneth

---

### Post by Sublime10 on 2006-03-28
I had the same problem and this is what someone recommended me to do for my computer. I don't know anything past that because I only did this yesterday night and haven't had time to work with it. Hope it helps a little.

[QUOTE=dcstar]Try booting into Recover mode - or with the install CD - and try any mount your drive and edit the following files (you may need to do a forum search for exact details on how to do this):

/etc/default/bootlogd
```
BOOTLOGD_ENABLE=Yes
```
/etc/default/rcS
```
VERBOSE=yes
```
The first should enable you to see the boot messages in a log file, the second should increase the level of detail so you may see exactly what part of the hotplug subsystem is freezing your system.[/QUOTE]

---

### Post by Mustard on 2006-03-28
Another method you might try is to use the special install options on the install.  When you get to the Boot prompt on the install, press the function keys for some explanations of the options.  I would suggest trying noapic, nolapic, apci=off, vga=771 (any, some or all of these options can attempted).

---

