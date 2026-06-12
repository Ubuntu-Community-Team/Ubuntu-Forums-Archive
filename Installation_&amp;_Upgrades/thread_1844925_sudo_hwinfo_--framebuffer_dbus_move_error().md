---
title: "sudo hwinfo --framebuffer dbus_move_error()"
date: 2011-09-16
forum: Installation &amp; Upgrades
---

### Post by miroi on 2011-09-16
On my Ubuntu 11.04, this command give error message first:

[EMAIL="ilias@miro_ilias_desktop:%7E/.sudo"]ilias@miro_ilias_desktop:~/.sudo[/EMAIL] hwinfo --framebuffer
> hal.1: read hal dataprocess 2108: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.FLoTMpm0mi1
  Hardware Class: framebuffer
  Model: "NVIDIA G92 Board - 03930004"
  Vendor: "NVIDIA Corporation"
  Device: "G92 Board - 03930004"
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 14 MB
  Memory Range: 0xf9000000-0xf9dfffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
.
.
.
Version:
[EMAIL="ilias@miro_ilias_desktop:%7E/.sudo"]ilias@miro_ilias_desktop:~/.sudo[/EMAIL] hwinfo --version
16.0

---

