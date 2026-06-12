---
title: "Sata hard drives (raid 0) not detected"
date: 2006-11-19
forum: Installation &amp; Upgrades
---

### Post by blackspawn on 2006-11-19
Hello let's see if some of you kind souls can help me with my problem. I have two sata2 drives configured as a Raid 0 (using Intel Matrix Storage controller). The problem is Ubuntu's installer doesn't recognize my hard drives, "No devices detected" so says GParted... I've seen people with problems where Ubuntu detected individual drives instead of a raid array but I can't even get it to recognize that there are 2 HDs there. ](*,) 

Is there any incompatibility with sata2 hard drives? (my HDs are 2 Western Digital 250Gb Sata2 16Mb cache) 

My motherboard is an Asus P5B Deluxe with a Core 2 Duo E6600, both my dvd and dvdrw drives are sata so Jmicro controller is disabled in the BIOS (so is the HD audio controller)

This is what "dmesg | grep ata" gives me:
```
[17179569.184000]  BIOS-e820: 000000007ffa0000 - 000000007ffae000 (ACPI data)
[17179569.184000] Memory: 2068932k/2096768k available (1910k kernel code, 26584k reserved, 1070k data, 308k init, 1179264k highmem)
[17179571.592000] libata version 1.20 loaded.
[17179575.864000] ata1: SATA max UDMA/133 cmd 0xF885C900 ctl 0x0 bmdma 0x0 irq 201
[17179575.864000] ata2: SATA max UDMA/133 cmd 0xF885C980 ctl 0x0 bmdma 0x0 irq 201
[17179575.864000] ata3: SATA max UDMA/133 cmd 0xF885CA00 ctl 0x0 bmdma 0x0 irq 201
[17179575.864000] ata4: SATA max UDMA/133 cmd 0xF885CA80 ctl 0x0 bmdma 0x0 irq 201
[17179575.864000] ata5: SATA max UDMA/133 cmd 0xF885CB00 ctl 0x0 bmdma 0x0 irq 201
[17179575.864000] ata6: SATA max UDMA/133 cmd 0xF885CB80 ctl 0x0 bmdma 0x0 irq 201
[17179583.112000] ata1 is slow to respond, please be patient
[17179606.072000] ata1 failed to respond (30 secs)
[17179606.788000] ata1: SATA link up 3.0 Gbps (SStatus 123)
[17179636.788000] ata1: qc timeout (cmd 0xec)
[17179636.788000] ata1: dev 0 failed to IDENTIFY (I/O error)
[17179643.996000] ata2 is slow to respond, please be patient
[17179655.632000] ata2: SATA link down (SStatus 0)
[17179685.656000] ata2: qc timeout (cmd 0xec)
[17179685.656000] ata2: dev 0 failed to IDENTIFY (I/O error)
[17179686.576000] ata3: SATA link down (SStatus 0)
[17179687.496000] ata4: SATA link down (SStatus 0)
[17179687.872000] ata5: SATA link up 1.5 Gbps (SStatus 113)
[17179688.044000] ata5: dev 0 cfg 49:0f00 82:0210 83:4011 84:4000 85:0000 86:0001 87:4000 88:0407
[17179688.044000] ata5: dev 0 ATAPI, max UDMA/33
[17179688.216000] ata5: dev 0 configured for UDMA/33
[17179688.592000] ata6: SATA link up 1.5 Gbps (SStatus 113)
[17179688.752000] ata6: dev 0 cfg 49:0f00 82:0000 83:4000 84:4000 85:0000 86:0000 87:4000 88:0407
[17179688.752000] ata6: dev 0 ATAPI, max UDMA/33
[17179688.912000] ata6: dev 0 configured for UDMA/33
```

As you can see my HDs are connected to sata ports 1 & 2 and my DVD drives to 5 & 6, could those errors be related to the fact that the HD are in Raid 0 configuration? Because I already have windows installed I can't really afford to go messing around with the raid array to see if it's the problem... edit: oh I'm using edgy desktop cd, I tried the alternative version but after the initial boot menu all I get is a blinking cursor on a black screen.

Any help is appreciated.

---

### Post by blackspawn on 2006-11-23
Anyone?

---

