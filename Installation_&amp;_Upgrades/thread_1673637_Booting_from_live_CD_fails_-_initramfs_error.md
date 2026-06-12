---
title: "Booting from live CD fails - initramfs error"
date: 2011-01-22
forum: Installation &amp; Upgrades
---

### Post by ill_switch on 2011-01-22
Hello forum,

Put together a PC using the following:

Foxconn M61PMP-K AM3 NVIDIA MCP61P Micro ATX AMD Motherboard
AMD Athlon II X2 240 Regor 2.8GHz Socket AM3 65W Dual-Core Processor ADX240OCGQBOX
Patriot 2GB 240-Pin DDR3 SDRAM DDR3 1333 (PC3 10600) Desktop Memory Model PSD32G13332
HITACHI Deskstar 7K1000.C HDS721010CLA332 (0F10383) 1TB 7200 RPM SATA 3.0Gb/s 3.5" Internal Hard Drive -Bare Drive

Plus an old case and PSU and an old 18gb IDE drive, and an old CD-RW drive

I put the CD in and boot the machine. The initial Ubuntu screen comes up ("Ubuntu" with the line of dots below it) for a few seconds, and then it disappears and I see this text:

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

At that point it hangs and will proceed no further. I've tried this with the latest Mythbuntu Live CD and the latest Ubuntu Desktop Edition Live CD. Both were x64 versions.

Any thoughts? I searched on this error and found some suggestions that the boot CD may be corrupt, but since I've seen the problem with two different boot CDs I'm not sure that's the case here.

---

### Post by ill_switch on 2011-01-23
Problem solved. It WAS an issue with the CD. I checked MD5 and it was fine. I burnt on a mac mini using the internal superdrive and Disk Utility app, I even used Disk Utility to verify the media. Everything LOOKED fine for both disks. But I was getting this error.

Anyways I burned another disk, this time putting the burn speed on the slowest setting (8x) and - it worked!

---

