---
title: "Getting NON-RAID SATA Drives to appear - Sil3112"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by Rob_Quads on 2007-03-26
I have a working Ubuntu 6.10 System running a 2.6.20 kernel, recompiled to enable RAID5.

I currently have a single 20GB drive on the onboard IDE
I have a PCI IDE card with 4 300GB drives configured in a RAID5 array.

I now have a PCI SATA Card I want to plug in along with 2 250GB Drives (currently NTFS but will move over to ext3 once sorted). These drives are independantly configured. There are no raid arrays on the board.

It appears that the system is just not picking up the SATA card.

In Dmesg I can see the existing IDE stuff being defected but then it appears to go on to the USB stuff

....
[   61.538195] ACPI: Fan [FAN] (on)
[   61.554454] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   61.554477] ACPI: Processor [CPU0] (supports 2 throttling states)
[   61.559385] ACPI: Thermal Zone [THRM] (22 C)
[   63.407205] VP_IDE: IDE controller at PCI slot 0000:00:07.1
[   63.407263] VP_IDE: chipset revision 6
[   63.407272] VP_IDE: not 100% native mode: will probe irqs later
[   63.407303] VP_IDE: VIA vt82c596b (rev 12) IDE UDMA66 controller on pci0000:00:07.1
[   63.407331]     ide0: BM-DMA at 0xa000-0xa007, BIOS settings: hda:DMA, hdb:pio
[   63.407375]     ide1: BM-DMA at 0xa008-0xa00f, BIOS settings: hdc:pio, hdd:pio
[   63.407404] Probing IDE interface ide0...
[    6.416000] Time: acpi_pm clocksource has been installed.
[    6.768000] hda: WDC WD200BB-23DEA0, ATA DISK drive
[    7.440000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    7.440000] Probing IDE interface ide1...
[    8.036000] hda: max request size: 128KiB
[    8.052000] hda: 39876480 sectors (20416 MB) w/2048KiB Cache, CHS=39560/16/63, UDMA(66)
[    8.052000] hda: cache flushes not supported
[    8.052000]  hda: hda1 hda2 < hda5 >
[    8.424000] IT8212: IDE controller at PCI slot 0000:00:09.0
[    8.428000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 7
[    8.428000] PCI: setting IRQ 7 as level-triggered
[    8.428000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[    8.428000] IT8212: chipset revision 19
[    8.428000] it821x: controller in pass through mode.
[    8.428000] IT8212: 100% native mode on irq 7
[    8.428000]     ide2: BM-DMA at 0xcc00-0xcc07, BIOS settings: hde:pio, hdf:pio
[    8.428000]     ide3: BM-DMA at 0xcc08-0xcc0f, BIOS settings: hdg:pio, hdh:pio
[    8.428000] Probing IDE interface ide2...
[    8.716000] hde: ST3300831A, ATA DISK drive
[    8.996000] hdf: ST3300831A, ATA DISK drive
[    9.052000] ide2 at 0xbc00-0xbc07,0xc002 on irq 7
[    9.052000] hde: max request size: 512KiB
[    9.052000] hde: 586072368 sectors (300069 MB) w/8192KiB Cache, CHS=36481/255/63, UDMA(100)
[    9.052000] hde: cache flushes supported
[    9.052000]  hde: unknown partition table
[    9.076000] hdf: max request size: 512KiB
[    9.076000] hdf: 586072368 sectors (300069 MB) w/8192KiB Cache, CHS=36481/255/63, UDMA(100)
[    9.076000] hdf: cache flushes supported
[    9.076000]  hdf: unknown partition table
[    9.092000] Probing IDE interface ide3...
[    9.380000] hdg: Maxtor 6L300R0, ATA DISK drive
[    9.660000] hdh: Maxtor 6B300R0, ATA DISK drive
[    9.716000] ide3 at 0xc400-0xc407,0xc802 on irq 7
[    9.716000] hdg: max request size: 512KiB
[    9.740000] hdg: 586114704 sectors (300090 MB) w/16384KiB Cache, CHS=36483/255/63, UDMA(133)
[    9.740000] hdg: cache flushes supported
[    9.740000]  hdg: unknown partition table
[    9.748000] hdh: max request size: 512KiB
[    9.772000] hdh: 586114704 sectors (300090 MB) w/16384KiB Cache, CHS=36483/255/63, UDMA(133)
[    9.772000] hdh: cache flushes supported
[    9.772000]  hdh: unknown partition table
[   10.164000] Probing IDE interface ide1...
[   10.320000] usbcore: registered new interface driver usbfs
[   10.324000] usbcore: registered new interface driver hub
[   10.324000] usbcore: registered new device driver usb
[   10.332000] USB Universal Host Controller Interface driver v3.0
[   10.336000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[   10.336000] PCI: setting IRQ 10 as level-triggered
[   10.336000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   10.336000] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   10.336000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   10.336000] uhci_hcd 0000:00:07.2: irq 10, io base 0x0000a400
....

Anyone have any ideas on how to get the SATA card picked up??

---

### Post by Rob_Quads on 2007-03-27
After looking around some more it appears that the card is recognised by Ubuntu as lspci lists the card but it does not appear do anything more than that.

00:08.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)

I have recompiled the kernel with the SATA drivers selected but that appears to make no difference. Nothing gets loded

---

### Post by Rob_Quads on 2007-03-27
I have now switched out the SATA card I am using for another one. This time its an ALi M5283. Like before I am getting no-where. Its obviously picked up properly as I have noticed that my other IDE card has had all its drives moved i.e.

/dev/hde -> /dev/hdi
/dev/hde -> /dev/hdj
/dev/hde -> /dev/hdk
/dev/hde -> /dev/hdl

Why is raid with linux soo dodgy

---

