---
title: "Problems upgrading to 2.6.14"
date: 2005-11-29
forum: Installation &amp; Upgrades
---

### Post by plengnom on 2005-11-29
I got an Aopen mz915 with the 915-chipset. Since the default kernel just stops loading (don't remember the exact error here) when the sound card (intel hda) is enabled, I decided to upgrade to 2.6.14. Shouldnt have been much of a problem, but I end up with this message during boot:

[4294669.701000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[4294669.701000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[4294669.719000] PCI: Device 0000:00:1c.0 not available because of resource colisions
[4294669.720000] PCI: Device 0000:00:1c.0 not available because of resource colisions
[4295671.589000] ata1: disabling port
[4294678.155000] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
[4294678.155000]

.. and there it stops. The default kernel boots up nice (when soundcard is disabled), except it also gives the ata-message, but there its "ata2: disabling port", and not ata1. 

I'm guessing that i'm missing something when setting up the kernel, but what? Any ideas? :confused:

---

### Post by ranf on 2005-11-30
[QUOTE=plengnom]
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
[/QUOTE]
You either make an initrd for your kernel
Or compile IDE drivers and file system drivers statically into the kernel.

Can't help with the other errors.

---

### Post by plengnom on 2005-11-30
Weird stuff. Suddenly it started to work. The errors (except that last one) are still there, but everything, except sound, seems to work fine.

---

