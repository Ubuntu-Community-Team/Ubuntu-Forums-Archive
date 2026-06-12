---
title: "Ubuntu Hangs on blank screen  after login"
date: 2018-05-09
forum: Installation &amp; Upgrades
---

### Post by simon114 on 2018-05-09
Good Morning, After logging in I will get a blank screen and I have to hard restart the computer, If I then login again after a restart, it will open up the desktop no problem.
Thes are the entries from the Important section of logs

```

Applications         [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out (service_start_timeout=25000ms
Applications         Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
Other                   Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
Other                   bgscan simple: Failed to enable signal strength monitoring
Other                   io/hpmud/pp.c 627: unable to read device-id ret=-1   (two entries for this)
Other                   dbus: Failed to construct signal
Other                   dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
Other                   io/hpmud/pp.c 627: unable to read device-id ret=-1
Other                   io/hpmud/musb.c 2101: Invalid usb_open: Permission denied      (this entry 3 times)
System                ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT4._GTF, AE_NOT_FOUND (20170831/psparse-550)   (this entry 2 times)
System                ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)             (this entry 2 times)
System                ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT5._GTF, AE_NOT_FOUND (20170831/psparse-550)
System                ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170831/psargs-364)
System                Couldn't get size: 0x800000000000000e     (this entry 2 times)
System                MODSIGN: Couldn't get UEFI db list
System                Couldn't get size: 0x800000000000000e
System                [Firmware Bug]: TSC_DEADLINE disabled due to Errata; please update microcode to version: 0x22 (or later)

```

So it seems that an hp might be a problem so im going to re enable the hp to start at boot see if that resolves some issues, also I think I may have enabled on sata, 
only boot drives on start up in the bios so im going to change that to all sata drives and see what happens

Any more advice anyone can give please,

Thankyou

---

### Post by dino99 on 2018-05-09
Maybe an 'apparmor' right refused:
- remove 'quiet splash'  from /etc/default/grub, then run 'sudo update-grub'; this will let you see what happen when booting
- 'blank screen' is usually related to 'video' or 'greeter (aka gdm/lightdm/...) ; you can grab and post the output of 'journalctl -b | grep video > video.txt' , 'journalctl -b | grep greeter > greeter.txt'

---

