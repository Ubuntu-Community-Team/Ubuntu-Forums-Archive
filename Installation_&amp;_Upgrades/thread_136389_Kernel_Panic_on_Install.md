---
title: "Kernel Panic on Install"
date: 2006-02-25
forum: Installation &amp; Upgrades
---

### Post by jjm on 2006-02-25
My rig:

new ECS NFORCE3-A
new Sempron 3100+
new 512 MB RAM
CD-ROM
new 200 GB Maxtor HD (unformatted)

Ubuntu Live CD works fine.  I am typing this while on ubuntu Live.

When I try to install ubuntu onto the HD using the install CD, I get this:

RAM disk driver initialized: 16 RAM disks of 16384K size 1024 blocksize
EISA: Probing bus 0 at eisa.0
Cannot allocate resource for EISA slot 4
EISA: Detected 0 cards.
Net: Registered protocol family 2
IP: routing cache hash table of 4096 buckets, 32Kbytes
TCP established hash table entries: 32768 (order: 5, 131072 bytes )
TCP: Hash tables configured (established 32768 bind 32768 )
NET: Registered protocol family 8
NET: Registered protocol family 20
ACPI wakeup devices:
SLPB HUB0 HUB1 USB0 USB1 USB2 F139 MMAC MMCI VAR1
ACPI: (supports S0 S3 S4 S5)
RAMDISK: compressed image found at block 0
input: AT Translated Set 2 keyboard on isa0060/serio0
incomplete distance tree
invalid compressed format (err=1)
VFS: Mounted root (ext filesystem).
Freeing unused kernel memory: 224k freed
Kernel panic - not syncing: No init found. Try passing init= option to kernel.

The Live and install CDs were both obtained from ubuntu.  Version 5.10.  I have 5 copies of each, and the same thing happens each time.

I have tried different HD and CD drive cables, putting CD drive as slave on the same cable as HD, putting CD drive (set to master) on secondary IDE alone, and using different CD drives.  And I tried using an old 20 GB HD before putting in the new 200 GB drive too.  The result is always the same.

Getting pretty frustrated.  I am a Linux newbie Any suggestions?

---

### Post by jjm on 2006-02-26
Just hoping someone might be able to help.

---

