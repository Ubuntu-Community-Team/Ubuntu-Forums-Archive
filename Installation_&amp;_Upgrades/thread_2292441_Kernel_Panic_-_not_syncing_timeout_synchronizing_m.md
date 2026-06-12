---
title: "Kernel Panic - not syncing: timeout synchronizing machine check over cpus"
date: 2015-08-28
forum: Installation &amp; Upgrades
---

### Post by Nathan_Martini on 2015-08-28
I'm attempting to install ***Xubuntu 15.04 x64*** on a brand new high end laptop. These forums have already helped me fix a problem with the Nvidia cards and needing to set ***nomodeset*** on boot but now I get this one kernel panic at all different run levels and at different times. It doesn't seem to have any apparent pattern or logic to it.

[IMG]http://i.stack.imgur.com/w6Uu0.jpg[/IMG]

This happens during boot of the installation media and can happen almost instantly or shortly after fully booting into the desktop environment to start installation. Does anyone know what this is and how I can fix it?

Laptop specs and config (***MSI GT80 Titan***):


[LIST]
[*]Intel i7 5th gen processor
[*]32 gigs system ram
[*]2x Nvidia GeForce 980M with 8 gigs each
[*]Intel Wireless AC 7260
[*]Mostly SSDs configured in RAID 0 (Stripe)
[*]Secure Boot Enabled
[*]Fast Boot Disabled
[*]UEFI Enabled
[*]Windows 10 installed (was installed with UEFI enabled)
[*]Windows 10 Fast Startup is disabled
[*]Windows Boot Manager has lowest priority on boot
[/LIST]

I thought it might have been the wireless card but I tried removing the ***iwlwifi ***module and it still had a kernel panic. I've also tried using ***acpi=off***, ***nolapic***, and ***pci=noacpi*** but they don't help at all.

---

### Post by dino99 on 2015-08-28
*** conflicting device   /dev/mapper/ ..... ******
is your uefi settings has a dmraid activated ?

if you can watch the logs, then run 'journalctl' to know what is happening and when (mostly the red lines)

---

### Post by Nathan_Martini on 2015-08-28
The system has raid but I'm not sure if it's dmraid. The raid is configured in the BIOS since it's UEFI but when booting in legacy mode there is a display for raid configuration and an option to press ctrl+i to configure the raid. That sounds like an actual raid controller and not fake software dmraid... right?

---

### Post by Nathan_Martini on 2015-08-28
booting with **nomodeset **into runlevel 4, journalctl shows the following red lines:

ACPI probe failed
[/lib/systemd/system/casper.service:10] Failed to parse input specifier, ignoring: force-tty
iwlwifi 0000:05:00.0: Unsupported splx structure
conflicting device node '...' found, link to '...' will not be created
Device dev-disk-by\... appeard twice with different sysfs paths ...
name server cannot be used: Temporary failure in name resolution (-3)
DIS cannot start: GATT is disabled
Failed to init deviceinfo plugin
Failed to init proximity plugin
Failed to init time plugin
Failed to init alert plugin
Failed to init thermometer plugin
Failed to init gatt_example plugin
Unknown command complete for opcode 19
nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
dbud: failed to construct signal

Doing some research, I did find out that it is a "fakeraid" controller and dmraid is being used on the linux side. I'm not convinced that the errors you see in my screenshot are a problem. If I boot to runlevel 2, I can list all volumes in the raid sets with dmraid and I can even mount both ***/dev/mapper/isw_jibeadicf_Volume1p1*** and ***/dev/dm-1*** with no problems at all. Plus, it's an intermittent and sporadic problem appearing seemingly at  random at different points during the boot process and at different  points while in the desktop environment. If I can make it through a boot  to any run level from 1 to 4 and get a terminal, it will not ever  kernel panic, it will only kernel panic during boot or when in the  desktop environment.

---

### Post by gonzalez.rod.a on 2015-09-25
I'm having the same problem trying to install Kubuntu on a SSD. I don't know if Ubuntu's spins because Ubuntu with unity it's OK.

---

