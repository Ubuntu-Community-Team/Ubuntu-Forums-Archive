---
title: "Install fails on IBM p5"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by robmoore on 2008-11-18
I'm trying to install Intrepid server on a IBM 9115-505 (P5 series) using the PowerPC image and am not getting very far (see below) as the install hangs. I'm curious if anyone has had success install Ubuntu on such a machine. It's currently running AIX but I was hoping to convert it over to Ubuntu.

```
Welcome to Ubuntu Server 8.10 (Intrepid Ibex)!

This is an Ubuntu Server installation CDROM,
built on 20081030.

The default option is 'install'. For maximum
control, you can use the 'expert' option.

If the system fails to boot at all (the typical
symptom is a white screen which doesn't go away),
use 'install video=ofonly' or 'expert video=ofonly'.

Press the tab key for a list of options, or type
'help' for help.

************************************
If in doubt, just press Enter, and if that
doesn't work, type 'install video=ofonly'.
************************************
Welcome to yaboot version 1.3.13
Enter "help" to get some basic usage information
boot: install video=ofonly
Please wait, loading kernel...
   Elf32 kernel loaded...
Loading ramdisk...
Claim failed for initrd memory at 01e00000 rc=ffffffff
ramdisk loaded at 01a00000, size: 4096 Kbytes
OF stdout device is: /vdevice/vty@30000000
command line: ro ramdisk_size=8192 file=/cdrom/preseed/ubuntu-server.seed quiet
-- video=ofonly
memory layout at init:
  alloc_bottom : 01e00000
  alloc_top    : 08000000
  alloc_top_hi : 08000000
  rmo_top      : 08000000
  ram_top      : 08000000
Looking for displays
instantiating rtas at 0x076a4000 ... done
00000002 : starting cpu hw idx 00000002... done
WARNING: maximum CPUs (1) exceeded: ignoring extras
copying OF device tree ...
Building dt strings...
Building dt structure...
Device tree strings 0x01e01000 -> 0x01e02335
Device tree struct  0x01e03000 -> 0x01e11000
```

The install hangs after the last line above.

---

