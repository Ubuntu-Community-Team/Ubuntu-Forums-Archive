---
title: "enhanced ide mode in bios P4C800-E (875PE), can't find /root"
date: 2006-08-19
forum: Installation &amp; Upgrades
---

### Post by cafemartin on 2006-08-19
hello there,

I'm trying to make the switch from windows to linux and ubuntu seemed like the distribution that suits my needs and that i really like, but I have a hard time making a dual-boot with windows. I've been googling and reading many pages that might be related, about hardware-issues, grub, super grub disk, mbr, mft, very handy sites like this one: [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)
but I haven't yet been able to make all my harddrives appear in dapper.

my system:
P4C800-E Deluxe (875PE chipset, ICH5)
PIV 2,4C
2048MB DDR400
matrox g450
pioneer dvr-108
1 x WD740GD (sata)
2 x WD2500JB (pata)
3 X WD1600JB (pata)

In the bios (latest version (1023)) is an option to run ide on enhanced and compatible mode. options:
enhanced pata + sata
enhanced sata
compatible primary pata + primary sata
compatible secondary pata + sata

The only way I knew to make dapper properly mount the dvr-108 while booting for installation, was running the installation in compatible mode. This means also that some of my harddrives are not enabled. Besdides that, this installation, a dual-boot with windows, went fine.

After installation I've tried re-enabling the enhanced ide mode, but is giving problems I'm trying to understand. Choosing the recovery mode in grub results in the following:

hdc: DMA interrupt recovery
hdc: lost interrupt
DONE
begin waiting for root filesystem
irq 177: nobody cared (try booting with the irqpoll option)
disabling irq 177
DONE
ALERT! /dev/sda2 does not exist. dropping to a shell.
busybox
/bin/sh" can't access tty: job control turned off.
#

Does this mean that with all the drives enables the whole partition table is changed, because of which grub no longer refers to the proper partition for dapper (and that changing this referrer would help)? (the super grub disk couldn't find the right partition automatically and neither could I manually. the one it chose didn't work).

I have read as much as I could find on this bios option with this type of motherboard, but didn't find a working solution. Is there perhaps a boot option that would help (if i'd reinstall dapper), through which the cdrom is properly mounted in enhanced mode. Or should i modify the kernel? (wouldn't know where to begin). I'd love being able to have all my harddrives available under dapper.

Hope someone has an idea!

---

### Post by cafemartin on 2006-08-20
Ok, I found out about the renaming of the root path in fstab and menu.lst.
If I also use the irqpoll boot parameter, it actually boots and sees all my harddrives (yay!)

next thing is to make it boot properly, because this irqpoll-option brings my screen resolution to 640x480 at 60Hz, which is no fun. I also wonder what else is not working now.

when dapper does it's regular boot, it partly shows the same message:

irq 177: nobody cared (try booting with the irqpoll option)
disabling irq 177
busybox
/bin/sh" can't access tty: job control turned off.
#

what I could find on IRQ #177:

syslog:
PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 177
Aug 20 21:39:44 daulagiri kernel: [17179573.248000] ICH5: 100%% native mode on irq 177
----
Aug 20 22:06:42 daulagiri kernel: [17179576.968000] Probing IDE interface ide0...
Aug 20 22:06:42 daulagiri kernel: [17179577.708000] hda: PIONEER DVD-RW DVR-108, ATAPI CD/DVD-ROM drive
Aug 20 22:06:42 daulagiri kernel: [17179578.380000] ide0 at 0xefe0-0xefe7,0xefae on irq 177

dmesg:
[17179576.684000] ide1 at 0xefa0-0xefa7,0xefaa on irq 177
[17179576.776000] hda: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[17179576.892000] Uniform CD-ROM driver Revision: 3.20
[17179577.720000] ata4: PATA max UDMA/133 cmd 0xEF88 ctl 0xEF86 bmdma 0xEE60 irq 177

kern.log
Aug 18 21:42:31 daulagiri kernel: [17179576.228000] ide1: I/O resource 0x170-0x177 not free.
Aug 18 21:42:31 daulagiri kernel: [17179576.228000] ide1: ports already in use, skipping probe
Aug 20 21:39:44 daulagiri kernel: [17179578.876000] handlers:
Aug 20 21:39:44 daulagiri kernel: [17179578.876000] [ide_intr+0/512] (ide_intr+0x0/0x200)
Aug 20 21:39:44 daulagiri kernel: [17179578.876000] [ide_intr+0/512] (ide_intr+0x0/0x200)
Aug 20 21:39:44 daulagiri kernel: [17179578.876000] [pg0+944391184/1069368320] (ata_interrupt+0x0/0x150 [libata])
Aug 20 21:39:44 daulagiri kernel: [17179578.876000] Disabling IRQ #177
Aug 20 21:39:44 daulagiri kernel: [17179579.448000] uhci_hcd 0000:00:1d.2: irq 177, io base 0x0000ef20

:confused:

---

