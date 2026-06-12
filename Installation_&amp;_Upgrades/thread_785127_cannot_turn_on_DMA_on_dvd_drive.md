---
title: "cannot turn on DMA on dvd drive"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by wizzleteet on 2008-05-07
Hi all,

I updated from edgy to hardy over a week's time and I now I notice that I cannot turn on the dma on my dvd drive.
I used to be able to and now I can't.

I have an OLD asus bp6 board with hpt366 and intel chipsets.

I have edited my /etc/modules to read like this:
ata-piix
hpt366
ide-core
ide-cd

I run update-initramfs and reboot, find this in my dmesg, note that I really only have one DVD drive, the pioneer one, the second message is puzzling:
[...]
[   52.060050] Probing IDE interface ide0...
[   52.642506] hdb: IRQ probe failed (0xfffffcfc)
[   52.938435] hdb: IRQ probe failed (0xfffffcfc)
[   53.850202] hda: PIONEER DVD-RW DVR-110D, ATAPI CD/DVD-ROM drive
[..]
[   55.744836] Probing IDE interface ide3...
[   56.356914] hda: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache
[   56.356947] Uniform CD-ROM driver Revision: 3.20

Also, this might be of interrest:

[...]
[   60.517409] libata version 3.00 loaded.
[   60.597294] PCI: Unable to reserve I/O region #1:8@1f0 for device 0000:00:07.
1
[   60.597321] pata_acpi 0000:00:07.1: failed to request/iomap BARs for port 0 (
errno=-16)
[   60.597339] PCI: Unable to reserve I/O region #3:8@170 for device 0000:00:07.
1
[   60.597352] pata_acpi 0000:00:07.1: failed to request/iomap BARs for port 1 (
errno=-16)
[   60.597365] pata_acpi 0000:00:07.1: no available native port
[   60.702568] ata_piix 0000:00:07.1: version 2.12
[   60.702753] PCI: Unable to reserve I/O region #1:8@1f0 for device 0000:00:07.
1
[   60.702769] ata_piix 0000:00:07.1: failed to request/iomap BARs for port 0 (e
rrno=-16)
[   60.702786] PCI: Unable to reserve I/O region #3:8@170 for device 0000:00:07.
1
[   60.702799] ata_piix 0000:00:07.1: failed to request/iomap BARs for port 1 (e
rrno=-16)
[   60.702812] ata_piix 0000:00:07.1: no available native port
[   60.914130] PCI: Unable to reserve I/O region #5:100@ec00 for device 0000:00:
13.1
[   60.914150] pata_hpt366 0000:00:13.1: failed to request/iomap BAR4
[   60.914171] Bad IO access at port 0x0 ()
[   60.914182] WARNING: at /build/buildd/linux-2.6.24/lib/iomap.c:44 bad_io_acce
ss()
[   60.914199] Pid: 1891, comm: modprobe Not tainted 2.6.24-16-generic #1



Help is very much appreciated.

kind regards,

wzzl

---

### Post by wizzleteet on 2008-05-08
I solved my problems.

I returned to the kernel that loves me: 2.6.17

Quick, responsive, dma, oh joy.


I had to go hunting for the debs though, is it an idea to have kernel backports of at least two releases ?


grtz wzzl

---

