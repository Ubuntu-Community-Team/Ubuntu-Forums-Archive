---
title: "SATA Problem"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by Zonged on 2006-10-31
I just installed Edgy on my computer for the first time, and so far almost everything works great. My computer has 2 hard drives, ones an IDE and the other is a SATA that is hooked up through a pci raid card. The IDE one is partitioned for a Vista/Edgy dual boot, and the SATA has been used as a data disk for windows & is formatted using NTFS. When I was installing Edgy the SATA drive showed up in the partition manager but now its not detecting it. 

lspci detects the raid controller:
ren@ren-desktop:~$ sudo lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
        Subsystem: ASUSTeK Computer Inc. A7V8X motherboard
        Flags: bus master, 66MHz, medium devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: [80] AGP version 3.5
        Capabilities: [c0] Power Management version 2

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: ce000000-cfdfffff
        Prefetchable memory behind bridge: cff00000-dfffffff
        Capabilities: [80] Power Management version 2

00:0d.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
        Subsystem: Silicon Image, Inc. SiI 3112 SATARaid Controller
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 169
        I/O ports at d800 [size=8]
        I/O ports at d400 [size=4]
        I/O ports at d000 [size=8]
        I/O ports at b800 [size=4]
        I/O ports at b400 [size=16]
        Memory at cd800000 (32-bit, non-prefetchable) [size=512]
        [virtual] Expansion ROM at 40000000 [disabled] [size=512K]
        Capabilities: [60] Power Management version 2

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. A7V8X-X motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 177
        I/O ports at b000 [size=32]
        Capabilities: [80] Power Management version 2

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. A7V8X-X motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 177
        I/O ports at a800 [size=32]
        Capabilities: [80] Power Management version 2

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. A7V8X-X motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 177
        I/O ports at a400 [size=32]
        Capabilities: [80] Power Management version 2

00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. A7V8X-X motherboard rev 1.01
        Flags: bus master, medium devsel, latency 32, IRQ 177
        Memory at cd000000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
        Subsystem: ASUSTeK Computer Inc. A7V8X-X motherboard
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: [c0] Power Management version 2

00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. A7V8X-X motherboard rev. 1.01
        Flags: bus master, medium devsel, latency 32, IRQ 255
        I/O ports at a000 [size=16]
        Capabilities: [c0] Power Management version 2

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
        Subsystem: ASUSTeK Computer Inc. A7V8X-X Motherboard
        Flags: medium devsel, IRQ 201
        I/O ports at e000 [size=256]
        Capabilities: [c0] Power Management version 2

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
        Subsystem: ASUSTeK Computer Inc. A7V8X-X Motherboard
        Flags: bus master, stepping, medium devsel, latency 32, IRQ 185
        I/O ports at 9800 [size=256]
        Memory at cc800000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [40] Power Management version 2

00:13.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
        Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device
        Flags: bus master, stepping, medium devsel, latency 32, IRQ 193
        I/O ports at 9400 [size=256]
        Capabilities: [c0] Power Management version 2

01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1) (prog-if 00 [VGA])
        Subsystem: XFX Pine Group Inc. Unknown device 2034
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 169
        Memory at ce000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        [virtual] Expansion ROM at cffe0000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
        Capabilities: [44] AGP version 3.0



but fdisk -l doesn't show the drive:
ren@ren-desktop:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3592    28847104    7  HPFS/NTFS
/dev/hda2            3593        4803     9721405   83  Linux
/dev/hda3            4803        4867      512000   82  Linux swap / Solaris

Any help would be greatly appreciated

---

### Post by Zonged on 2006-11-02
(Bump) Any ideas?

---

### Post by dannyboy79 on 2006-11-02
you have to make sure the module is being loaded for that raid pci card. sure, lspci will show the card but now you have to have a driver or module to make it work. can't help you any further, just gogle, sata drivers and ubuntu and i am sure you'll find the answer

also, after relooking at your post, are you sure that RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02) isn't the sata raid ports built into your motherboard? maybe it isn't seeing the additional pci card? normally ubuntu lists everything in order from my experience, notice your agp card is last, so normally pci devices are going to be last and since the raid device listed in way at the top I am guessing that that raid controller is actually on your motherboard. my foxconn motherboard has a sata raid controller on it, 0000:00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA [SiS] (rev 01) (prog-if 85 [Master SecO PriO]). Just a thought but I can't tell you for sure?



I have to tell you that I am rather disappointed with your search capabilities. All I did was use the search function within this forum and found an exact thread WITH a a solution to your EXACT same problem and EXACT same pci sata card. This is the solution:
It appears that I just needed to add "irqpoll" to the boot options. Now to find that thread I saw about the performance issues.

This is the thread: [http://www.ubuntuforums.org/showthread.php?t=214669&highlight=SiI+3112+SATARaid+Controller](http://www.ubuntuforums.org/showthread.php?t=214669&highlight=SiI+3112+SATARaid+Controller)

---

### Post by Zonged on 2006-11-02
Thanks for your help Dannyboy. I tried adding  irqpoll but that didn't do anything.  Its definitely a pci card as my mobo doesn't have sata. The module sata_sil is being loaded for the card. I ran dmesg and this is the output pertaining to sata:

[17179576.100000] SCSI subsystem initialized
[17179576.104000] libata version 1.20 loaded.
[17179576.108000] sata_sil 0000:00:0d.0: version 0.9
[17179576.108000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179576.108000] ata1: SATA max UDMA/100 cmd 0xF0832080 ctl 0xF083208A bmdma 0xF0832000 irq 169
[17179576.108000] ata2: SATA max UDMA/100 cmd 0xF08320C0 ctl 0xF08320CA bmdma 0xF0832008 irq 169
[17179576.312000] ata1: SATA link down (SStatus 0)
[17179576.324000] scsi0 : sata_sil
[17179576.688000] ata2: SATA link up 1.5 Gbps (SStatus 113)
[17179576.704000] ata2: PIO error
[17179576.704000] ata2: dev 0 failed to IDENTIFY (I/O error)
[17179576.704000] scsi1 : sata_sil
[17179576.744000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[17179576.744000] ACPI: Unable to derive IRQ for device 0000:00:11.1
[17179576.744000] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
[17179576.744000] PCI: Via IRQ fixup for 0000:00:11.1, from 255 to 15

Thanks again from a newbie

---

### Post by dannyboy79 on 2006-11-02
well, did you read that thread that I posted? he posted the exact same pci card as yours so I am not sure why the irqpoll option isn;t working. i noticed that there is a failurem something about dev. i say another post about mapping a sata drive to dev or something like that, let me see if I can find it again.

check this out: [http://ubuntuforums.org/showthread.php?t=241345&highlight=SiI+3112](http://ubuntuforums.org/showthread.php?t=241345&highlight=SiI+3112)

otherwise I can't help

---

