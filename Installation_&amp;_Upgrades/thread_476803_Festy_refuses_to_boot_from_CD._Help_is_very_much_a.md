---
title: "Festy refuses to boot from CD. Help is very much appreciated!"
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by tyler_o_melvin on 2007-06-17
Hi all,

I've been having some issues with attempting to install Festy. When I boot from the CD I get the error message:
```
[      34.412000] ata3: port failed to respond (30 secs, Status 0x80)
```
and then I'm in sh. I think this may be related to an annoyance I've been experiencing with Edgy for some time now. When mid-boot, the kernel appears to hang for about a minute while running /scripts/local-top before completely loading the OS. Inspection of dmesg output reveals:

```
...
[17179577.016000] SCSI subsystem initialized
[17179577.020000] libata version 1.20 loaded.
[17179577.020000] ahci 0000:00:1f.2: version 1.2
[17179577.020000] ACPI: PCI Interrupt 0000:00:1f.2[D] -> GSI 16 (level, low) -> IRQ 169
[17179582.840000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179582.840000] ahci 0000:00:1f.2: AHCI 0001.0000 32 slots 4 ports 1.5 Gbps 0x5 impl IDE mode
[17179582.840000] ahci 0000:00:1f.2: flags: 64bit stag led pmp 
[17179582.840000] ata1: SATA max UDMA/133 cmd 0xF8844100 ctl 0x0 bmdma 0x0 irq 169
[17179582.840000] ata2: SATA max UDMA/133 cmd 0xF8844180 ctl 0x0 bmdma 0x0 irq 169
[17179582.840000] ata3: SATA max UDMA/133 cmd 0xF8844200 ctl 0x0 bmdma 0x0 irq 169
[17179582.840000] ata4: SATA max UDMA/133 cmd 0xF8844280 ctl 0x0 bmdma 0x0 irq 169
[B][17179590.044000] ata1 is slow to respond, please be patient
[17179613.060000] ata1 failed to respond (30 secs)
[17179620.776000] ata1 is slow to respond, please be patient
[17179643.792000] ata1 failed to respond (30 secs)
[17179643.792000] ata1: reset failed (errno=-5)[/B]
[17179643.792000] scsi0 : ahci
[17179643.996000] ata2: SATA link down (SStatus 0)
[17179643.996000] scsi1 : ahci
[17179644.200000] ata3: SATA link down (SStatus 0)
[17179644.200000] scsi2 : ahci
[17179644.404000] ata4: SATA link down (SStatus 0)
[17179644.404000] scsi3 : ahci
[17179644.488000] Probing IDE interface ide1...
[17179644.524000] usbcore: registered new driver usbfs
...
```

System Specs:
Linux version 2.6.17-11-generic (root@terranova) 
(gcc version 4.1.2 20060928 (prerelease)(Ubuntu 4.1.1-13ubuntu5)) #2 SMP
Thu Feb 1 19:52:28 UTC 2007 (Ubuntu 2.6.17-11.35-generic)

Fujitsu LifeBook N6210 Notebook
Intel Pentium M 750 1.86 GHz
1GB DDR2-535 RAM
ATI Mobility RADEON X600 w/ 128MB
Intel 915PM audio
60GB 7200RPM ultra-DMA 100 HD
Intel PRO/Wireless 2915ABG


How can I fix this? I really want to install Festy! Will this entail modifying the ISO?
Thanks a ton.

-Tyler

P.S.- For what I think are obvious reasons, I really don't want to try any other installation method before I am able to boot off the CD.

---

### Post by tyler_o_melvin on 2007-06-19
Anyone? Someone out there must have seen this problem before.

-Tyler

---

### Post by information_entropy on 2007-06-19
Your problem may be related to this bug in launchpad.
Some possible solutions discussed there


[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/64587]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/64587")

---

### Post by tyler_o_melvin on 2007-06-20
Thanks for the help. It certainly doesn't look like it will be an easy problem to fix. I'll have to search around a bit, see if I can find anyone who is having this problem at boot.

Again, thanks for the link.
](*,)
-Tyler

---

