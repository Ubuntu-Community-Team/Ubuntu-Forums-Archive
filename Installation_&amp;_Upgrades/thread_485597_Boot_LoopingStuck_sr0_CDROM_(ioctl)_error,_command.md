---
title: "Boot Looping/Stuck sr0: CDROM (ioctl) error, command: &lt;6&gt;Test Unit Ready"
date: 2007-06-27
forum: Installation &amp; Upgrades
---

### Post by transltr on 2007-06-27
Hi All,

The laptop is an IBM R51, the dvd/cd drive does not work anymore. Installed kubuntu from a USB live, everything was fine until i updated and tried installing beryl and 3d desktop. Now during boot this keeps coming up, and doesn't stop
sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00

I can get to recovery mode,
tried adding cdrom from /modprobe/blacklist
adding # the cdrom line from fstab
disabling from BIOS
removing the drive <- this stops the message but just hangs

please help

Thanks guys

---

### Post by transltr on 2007-06-29
Anyone ?? please help really annoying .... as i can't use the laptop

---

### Post by Akre on 2007-07-02
I've had very similar problem with Toshiba s9150 laptop (dead cd - hardware failure). When not in X mode this message keeps poping out, console is not usable.

For me it helped to unload sr_mod:
sudo modprobe -r sr_mod
sudo modprobe -r cdrom

Blacklisting those modules doesn't seem to have effect, they are still loading at startup. I still do not understand how those modules keep starting.
EDIT:
They are loading by initramfs on kernel startup by alias. Blaklisting there should help.

I will investigate fruther, for now i suggest append this lines to startup config (rc.local)

Hope this help.

Problem did not occur in Ubuntu 6.10
Wheter it is reggression or feature I don't know

---

