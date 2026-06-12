---
title: "install problem with SATA controller in Edgy."
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by boulderadan on 2007-04-06
Laptop Sony S580 with
[LIST]
[*] Pentium M 1.7 Ghz
[*] SDRAM PC2-4200 1.5 GB
[*] HDD 80 GB SATA
[*] Video on board Intel 915GM
[/LIST]

I tried to dual-boot winXP and Ubuntu with the following partition
sda1 Sony recovery partition 6 GB
sda2 Win XP Home 50 GB
sda3 Ubuntu
sda4 Linux Swap

The liveCD Ubuntu 6.10 works fine but the installation always hang at 15%. Fedora core 6 and openSuse 10.2 give the same installation hang but more detail about SATA controller. Some people also report this bug at launchpad.net e.g. #38760, #62576  and few more.

This bug report ([https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/72631](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/72631)) points out that there's a bug in SATA driver . The poster later said that it's fixed in 2.6.20 kernel.

Problem is I am a beginner linux user and I don't know how to install Feisty 2.6.20 kernel from scratch. I found a daily built 2.6.20 kernel but it's not like a one-liveCD-do-it-all. ([https://launchpad.net/ubuntu/+source/linux-source-2.6.20/2.6.20-14.22](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/2.6.20-14.22))

Questions:
1. Is there a liveCD for Feisty right now? If so, where to get it?
2. Is it such a risk and hassle for a newbie to install daily-built Feisty now and later upgrade to a stable version?
3. Is there a way to use Ubuntu 6.10 installation and fix the SATA controller problem?

Here's my lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:05.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
06:05.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
06:05.3 Mass storage controller: <pci_lookup_name: buffer too small>
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)
06:0b.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)

A snippet from dmesg about scsi
========================
[17179583.764000] SCSI subsystem initialized
[17179583.768000] libata version 1.20 loaded.
[17179583.768000] ahci 0000:00:1f.2: version 1.2
[17179583.768000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 18 (level, low) -> IRQ 177
[17179696.592000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179696.592000] ahci 0000:00:1f.2: AHCI 0001.0000 32 slots 4 ports 1.5 Gbps 0x5 impl IDE mode
[17179696.592000] ahci 0000:00:1f.2: flags: 64bit ncq pm led pmp slum part 
[17179696.592000] ata1: SATA max UDMA/133 cmd 0xF884C500 ctl 0x0 bmdma 0x0 irq 177
[17179696.592000] ata2: SATA max UDMA/133 cmd 0xF884C580 ctl 0x0 bmdma 0x0 irq 177
[17179696.592000] ata3: SATA max UDMA/133 cmd 0xF884C600 ctl 0x0 bmdma 0x0 irq 177
[17179696.592000] ata4: SATA max UDMA/133 cmd 0xF884C680 ctl 0x0 bmdma 0x0 irq 177
[17179698.040000] ata1: SATA link up 1.5 Gbps (SStatus 113)
[17179698.040000] ata1: dev 0 cfg 49:0f00 82:746b 83:7f69 84:4063 85:f469 86:3f49 87:4063 88:203f
[17179698.040000] ata1: dev 0 ATA-7, max UDMA/100, 156301488 sectors: LBA48
[17179698.040000] ata1: dev 0 configured for UDMA/100
[17179698.040000] scsi0 : ahci
[17179699.136000] ata2: SATA link down (SStatus 0)
[17179699.136000] scsi1 : ahci
[17179700.984000] ata3: SATA link down (SStatus 0)
[17179700.984000] scsi2 : ahci
[17179702.100000] ata4: SATA link down (SStatus 0)
[17179702.100000] scsi3 : ahci
[17179702.100000]   Vendor: ATA       Model: HTS541080G9SA00   Rev: MB4O
[17179702.100000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179702.108000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17179702.108000] sda: Write Protect is off
[17179702.108000] sda: Mode Sense: 00 3a 00 00
[17179702.108000] SCSI device sda: drive cache: write back
[17179702.108000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17179702.108000] sda: Write Protect is off
[17179702.108000] sda: Mode Sense: 00 3a 00 00
[17179702.108000] SCSI device sda: drive cache: write back
[17179702.108000]  sda: sda1 sda2 sda3 sda4 < sda5 >
[17179702.512000] sd 0:0:0:0: Attached scsi disk sda
========================

If anyone wants to take a look at the full dmesg, I can post it later.

P.S. Desperately need help here 'coz I don't want to use other linux distro.:popcorn:

---

### Post by p1r0 on 2007-04-07
I had a similar problem on my Intel mobo (it was kinda worse, nothing happened when I chose install) and installing Ubuntu 7.04 solved it.

You can find the live/install cd here [http://www.ubuntu.com/news/Ubuntu704Beta]("http://www.ubuntu.com/news/Ubuntu704Beta")

Best wishes

---

