---
title: "On the Edge of SATA"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by Thangalin on 2007-03-14
Hi,

I am running Kubuntu 6.10 (32-bit) and am looking to install Kubuntu 6.10 (64-bit), as I have recently upgraded to an Intel Core 2 Duo CPU. However, when I boot with the Kubuntu 6.10 (64-bit) DVD, I receive the infamous "BusyBox" error ([details here]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84964")).

I am booting (Kubuntu 64-bit) from an IDE-based LITEON DVD-R/W, which is connected to an ASUS P5B motherboard via SIIG's [Serial ATA-to-Ultra ATA Adapter]("http://onlinestore.siig.com/shopexd.asp?id=192"). Two IDE drives are connected via the only IDE channel.

Kubuntu 6.10 (32-bit) works fine, however there is no **/dev/sd*** available to mount.

The **lspci** command reveals:
[INDENT]00:1f.2 IDE interface: Intel Corporation SATA Controller 1 IDE (rev 02)
00:1f.3 SMBus: Intel Corporation SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation SATA Controller 2 IDE (rev 02)
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
02:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
[/INDENT]

The **dmesg** command reveals:
[INDENT][17179571.532000] ata1: SATA max UDMA/133 cmd 0xEC00 ctl 0xE882 bmdma 0xE400 irq 177
[17179571.852000] ata1: dev 0 cfg 49:0b00 82:0210 83:1000 84:0000 85:0000 86:0000 87:0000 88:0407
[17179571.852000] ata1: dev 0 ATAPI, max UDMA/33
[17179572.008000] ata1: PIO error
[17179572.008000] ata1: dev 1 failed to IDENTIFY (I/O error)
[17179572.172000] ata1: dev 0 configured for UDMA/33
[17179577.836000] ata1: command 0xa0 timeout, stat 0xd8 host_stat 0x21
[17179577.836000] ata1: translated ATA stat/err 0xd8/00 to SCSI SK/ASC/ASCQ 0xb/47/00
[/INDENT]

In **/var/log/messages**, I see:
[INDENT]Mar 14 14:52:31 jaguar kernel: [17179571.532000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 177
Mar 14 14:52:31 jaguar kernel: [17179571.532000] ata1: SATA max UDMA/133 cmd 0xEC00 ctl 0xE882 bmdma 0xE400 irq 177
Mar 14 14:52:31 jaguar kernel: [17179571.532000] ata2: SATA max UDMA/133 cmd 0xE800 ctl 0xE482 bmdma 0xE408 irq 177
Mar 14 14:52:31 jaguar kernel: [17179571.852000] ata1: dev 0 ATAPI, max UDMA/33
Mar 14 14:52:31 jaguar kernel: [17179572.008000] ata1: PIO error
Mar 14 14:52:31 jaguar kernel: [17179572.008000] ata1: dev 1 failed to IDENTIFY (I/O error)                                                                    
Mar 14 14:52:31 jaguar kernel: [17179572.172000] ata1: dev 0 configured for UDMA/33
Mar 14 14:52:31 jaguar kernel: [17179572.172000] scsi0 : ata_piix
Mar 14 14:52:31 jaguar kernel: [17179572.336000] scsi1 : ata_piix
Mar 14 14:52:31 jaguar kernel: [17179577.836000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 177
[/INDENT]

In **/etc/initramfs-tools/modules**, I have:

[INDENT]libata
pata_jmicron
ata_piix
ahci
ata_generic
[/INDENT]

Since I want to use the DVD to perform the new installation, I cannot disable JMicron from the BIOS. Which leaves me with a conundrum of questions:

[LIST=1][*]Is it possible to install Kubuntu 6.10 (64-bit) using the hardware's current configuration?
[*]If so, how?
[*]How do I make the DVD player mountable under the current 6.10 (32-bit) installation?[/LIST]
Many, many thanks for any help.

---

