---
title: "Slow boot 10.10 maverick"
date: 2011-01-22
forum: Installation &amp; Upgrades
---

### Post by JohnReid on 2011-01-22
Hi,

Since upgrading from lucid my boot has been much slower. Looking at dmesg I can see this:

```
[    2.396712] EXT4-fs (sda1): orphan cleanup on readonly fs
[    2.396721] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 124
[    2.396746] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 93
[    2.396752] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 81
[    2.396757] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 80
[    2.396763] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 70
[    2.396767] EXT4-fs (sda1): 5 orphan inodes deleted
[    2.396768] EXT4-fs (sda1): recovery complete
[    2.904650] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   22.524338] udev[387]: starting version 163
[   22.550341] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[   22.551534] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
[   22.604799] lp: driver loaded but no devices found
[   22.663618] usbcore: deregistering interface driver usbhid
[   22.663636] Adding 11285624k swap on /dev/sda5.  Priority:-1 extents:1 across:11285624k 
[   22.678818] parport_pc 00:03: reported by Plug and Play ACPI
[   22.678940] parport0: PC-style at 0x378 (0x778), irq 5, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   22.683131] saa7164 driver loaded
[   22.683172] saa7164 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.685018] CORE saa7164[0]: subsystem: 0070:8940, board: Hauppauge WinTV-HVR2200 [card=4,insmod option]
[   22.685025] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfb800000
[   22.685032] saa7164 0000:02:00.0: setting latency timer to 64
[   22.703527] ppdev: user-space parallel port driver
[   22.706245] IR NEC protocol handler initialized
[   22.706490] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   22.708772] IR RC5(x) protocol handler initialized
[   22.711488] IR RC6 protocol handler initialized
[   22.713834] IR JVC protocol handler initialized
[   22.716150] IR Sony protocol handler initialized
[   22.720336] lirc_dev: IR Remote Control driver registered, major 250 

```Can anyone who knows more about such things let me know if this 20 second delay is normal? Could there be something funny going on with the saa7164, usb or graphics drivers?

Thanks,
John.

---

