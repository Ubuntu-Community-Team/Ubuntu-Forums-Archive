---
title: "Deives on a Secondary PCI SATA Controller Don't Show Up as Devices"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by swilleke on 2008-02-25
I'm having trouble getting two 500GB drives to appear as devices (under /dev) that are attached to a PCI SATA controller. The drives appear in the card's bios fine. I have an Intel motherboard with a built-in SATA controller already. The drive on this controller works fine. The PCI SATA controller was bought under the name SIIG and appears via lspc as "02:04.0 SATA controller: Initio Corporation INI-1623 PCI SATA-II Controller (rev 02)".  Under Gnome's "Device Manager" the controller appears similarly, but neither drive appears under it.

I think the drivers are correct, at least by running lsmod | grep sata, I see the following:
sata_inic162x          12932  0 
libata                125168  3 ata_generic,sata_inic162x,ata_piix

...From what I've read this appears to be correct.

sudo fdisk -l shows the following:
Disk /dev/sda: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf79cf79c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14030   112695943+  83  Linux
/dev/sda2           14031       14596     4546395    5  Extended
/dev/sda5           14031       14596     4546363+  82  Linux swap / Solaris


Which is only my boot drive (which is SATA plugged into the motherboard's built-in controller).

What am I missing? I will be greatful if someone can help or point me in the right direction.

Thanks!

---

### Post by mrsteveman1 on 2008-02-25
When the kernel loads its modules at boot time, it should be listing that controller in the kernel log, and it should tell you without a doubt if the kernel driver can see the attached drives on the card.

Run through the kernel log one screen at a time using dmesg and more:

```
sudo dmesg | more
```

You'll have to look through it carefully but it should be there. If the kernel module isn't recognizing the drives in the first place there is something wrong for sure.

---

### Post by swilleke on 2008-02-29
Thanks Steve. I've gone through the log in detail and I think I've found relevant portions but I'm not sure what to do next. Below is the log. If I understand correctly, the samsung is my boot drive (ata3?) and it works fine. It seems ata5 & ata6 are the drives I'm unable to use. Please correct me if I misunderstood and help me understand what to do next:

[   31.246029] ata_piix 0000:00:1f.1: version 2.11
[   31.246055] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   31.246067] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   31.246124] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   31.246260] scsi0 : ata_piix
[   31.246367] scsi1 : ata_piix
[   31.246570] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   31.246578] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   31.328125] usb 1-1: configuration #1 chosen from 1 choice
[   31.331017] hub 1-1:1.0: USB hub found
[   31.333944] hub 1-1:1.0: 4 ports detected
[   31.680282] usb 1-2: new low speed USB device using uhci_hcd and address 3
[   31.696438] ata1.01: ATAPI: LITE-ON DVDRW LDW-811S, HS0K, max UDMA/33
[   31.862858] usb 1-2: configuration #1 chosen from 1 choice
[   31.868098] ata1.01: configured for UDMA/33
[   32.024472] scsi 0:0:1:0: CD-ROM            LITE-ON  DVDRW LDW-811S   HS0K PQ: 0 ANSI: 5
[   32.024583] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[   32.024616] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
[   32.024673] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   32.024742] scsi2 : ata_piix
[   32.024818] scsi3 : ata_piix
[   32.024966] ata3: SATA max UDMA/133 cmd 0x0001ec00 ctl 0x0001e802 bmdma 0x0001dc00 irq 18
[   32.024972] ata4: SATA max UDMA/133 cmd 0x0001e400 ctl 0x0001e002 bmdma 0x0001dc08 irq 18
[   32.103383] usb 4-2: new full speed USB device using uhci_hcd and address 2
[   32.187494] ata3.00: ATA-7: SAMSUNG SP1213C, SV100-27, max UDMA7
[   32.187499] ata3.00: 234493056 sectors, multi 16: LBA48 
[   32.195472] ata3.00: configured for UDMA/133
[   32.291276] usb 4-2: configuration #1 chosen from 1 choice
[   32.361730] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG SP1213C  SV10 PQ: 0 ANSI: 5
...
[   32.519941] sd 2:0:0:0: [sda] 234493056 512-byte hardware sectors (120060 MB)
[   32.519961] sd 2:0:0:0: [sda] Write Protect is off
[   32.519965] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   32.519992] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.520080] sd 2:0:0:0: [sda] 234493056 512-byte hardware sectors (120060 MB)
[   32.520096] sd 2:0:0:0: [sda] Write Protect is off
[   32.520100] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   32.520125] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.520132]  sda:<6>ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 21
[   32.551224] e100: eth0: e100_probe: addr 0xff9fd000, irq 21, MAC addr 00:07:E9:64:8A:2A
[   32.551275] sata_inic162x 0000:02:04.0: version 0.2
[   32.551331] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 18 (level, low) -> IRQ 18
[   32.553171]  sda1 sda2 <sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   32.560429] Uniform CD-ROM driver Revision: 3.20
[   32.560509] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   32.574454] scsi4 : sata_inic162x
[   32.574536] scsi5 : sata_inic162x
[   32.574589] ata5: SATA max UDMA/133 cmd 0x0001b800 ctl 0x0001b402 bmdma 0x00000000 irq 18
[   32.574596] ata6: SATA max UDMA/133 cmd 0x0001b000 ctl 0x0001a802 bmdma 0x00000000 irq 18
[   32.574873]  sda5 >
[   32.575015] sd 2:0:0:0: [sda] Attached SCSI disk
[   32.581573] sr 0:0:1:0: Attached scsi generic sg0 type 5
[   32.581612] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   32.582409] usb 1-2: USB disconnect, address 3
[   32.799363] Attempting manual resume
[   32.799368] swsusp: Resume From Partition 8:5
[   32.799370] PM: Checking swsusp image.
[   32.799602] PM: Resume from disk failed.
[   32.837032] kjournald starting.  Commit interval 5 seconds
[   32.837045] EXT3-fs: mounted filesystem with ordered data mode.
[   33.065349] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   33.080046] ata5.00: Host Protected Area detected:
[   33.080048]  current size: 976773168 sectors
[   33.080049]  native size: 61985760239664 sectors
[   33.080253] ata5.00: native size increased to 61985760239664 sectors
[   33.080259] ata5.00: ATA-8: WDC WD5000AAKS-00YGA0, 12.01C02, max UDMA/133
[   33.080263] ata5.00: 61985760239664 sectors, multi 0: LBA48 NCQ (depth 0/32)
[   33.080267] ata5.00: ERROR: This driver doesn't support LBA48 yet and may cause
[   33.080268]                 data corruption on such devices.  Disabling.
[   33.080272] ata5.00: disabled
[   33.372731] usb 4-2: USB disconnect, address 2
[   33.568281] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   33.592375] ata6.00: Host Protected Area detected:
[   33.592378]  current size: 976773168 sectors
[   33.592379]  native size: 61985760239664 sectors
[   33.592567] ata6.00: native size increased to 61985760239664 sectors
[   33.592574] ata6.00: ATA-8: WDC WD5000AAKS-00YGA0, 12.01C02, max UDMA/133
[   33.592577] ata6.00: 61985760239664 sectors, multi 0: LBA48 NCQ (depth 0/32)
[   33.592581] ata6.00: ERROR: This driver doesn't support LBA48 yet and may cause
[   33.592583]                 data corruption on such devices.  Disabling.
[   33.592587] ata6.00: disabled

[   32.799363] Attempting manual resume
[   32.799368] swsusp: Resume From Partition 8:5
[   32.799370] PM: Checking swsusp image.
[   32.799602] PM: Resume from disk failed.
[   32.837032] kjournald starting.  Commit interval 5 seconds
[   32.837045] EXT3-fs: mounted filesystem with ordered data mode.
[   33.065349] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   33.080046] ata5.00: Host Protected Area detected:
[   33.080048]  current size: 976773168 sectors
[   33.080049]  native size: 61985760239664 sectors
[   33.080253] ata5.00: native size increased to 61985760239664 sectors
[   33.080259] ata5.00: ATA-8: WDC WD5000AAKS-00YGA0, 12.01C02, max UDMA/133
[   33.080263] ata5.00: 61985760239664 sectors, multi 0: LBA48 NCQ (depth 0/32)
[   33.080267] ata5.00: ERROR: This driver doesn't support LBA48 yet and may cause
[   33.080268]                 data corruption on such devices.  Disabling.
[   33.080272] ata5.00: disabled
[   33.372731] usb 4-2: USB disconnect, address 2
[   33.568281] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   33.592375] ata6.00: Host Protected Area detected:
[   33.592378]  current size: 976773168 sectors
[   33.592379]  native size: 61985760239664 sectors
[   33.592567] ata6.00: native size increased to 61985760239664 sectors
[   33.592574] ata6.00: ATA-8: WDC WD5000AAKS-00YGA0, 12.01C02, max UDMA/133
[   33.592577] ata6.00: 61985760239664 sectors, multi 0: LBA48 NCQ (depth 0/32)
[   33.592581] ata6.00: ERROR: This driver doesn't support LBA48 yet and may cause
[   33.592583]                 data corruption on such devices.  Disabling.
[   33.592587] ata6.00: disabled

---

### Post by mrsteveman1 on 2008-02-29
Found your problem :D There are multiple entries in the kernel log for each drive on the new pci card, but here is an example: 

```
[ 33.080259] ata5.00: ATA-8: WDC WD5000AAKS-00YGA0, 12.01C02, max UDMA/133

[ 33.080263] ata5.00: 61985760239664 sectors, multi 0: LBA48 NCQ (depth 0/32)

[ 33.080267] ata5.00: ERROR: This driver doesn't support LBA48 yet and may cause

[ 33.080268] data corruption on such devices. Disabling.

[ 33.080272] ata5.00: disabled
```


The kernel found the card, found the drives, but disabled them because the driver currently doesn't support LBA48 addressing for some reason. LBA48 is needed because this is a 500gb hard drive. It's trying to protect the drive because the driver can't safely write to drives this large, as for why, i have no clue.

Which version of ubuntu is this? I'll see if the kernel drivers have been improved recently for this chipset.

---

### Post by swilleke on 2008-02-29
Great, at least I understand now. I saw that entry but didn't know what LBA48 was. I'm on Ubuntu 7.10 Gutsy GIbbon. uname -a says: 
Linux media 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

If we can't find a better drive I don't mind buying another controller if it is necessary but I'd sure like someone's suggestion on one that will work with these drives. The controller is a SIIG SATA-II 150.

Thanks so much for all you're help. It's been very helpful so far.

---

### Post by mrsteveman1 on 2008-02-29
In this case, the driver for your specific chipset isn't very good at the moment, i think because the manufacturer isn't providing any support. The drives aren't the problem.


If you just need an SATA card there are some good ones that use Promise chipsets, which are well supported on Linux.

If you want a real hardware raid card, 3ware is very well supported.

---

### Post by swilleke on 2008-02-29
Thanks again. I'll go try and pick up a promise card and use it then. I don't need hardware raid.

---

