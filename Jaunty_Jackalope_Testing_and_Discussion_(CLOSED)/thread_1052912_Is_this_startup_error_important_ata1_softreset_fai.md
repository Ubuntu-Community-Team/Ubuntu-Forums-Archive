---
title: "Is this startup error important: ata1: softreset failed (device not ready)"
date: 2009-01-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-01-28
ata1: softreset failed (device not ready)
ata3: softreset failed (device not ready)

Get this every boot.

---

### Post by Gina on 2009-01-28
I get odd messages on startup but things work anyway so I don't worry.  Maybe I should take note and report back but I always seem to forget. 

Your errors look like drives not ready and not getting reset. Do you get any problems once the system is up and running?  What devices do you have on ata1 and ata3?

---

### Post by inportb on 2009-01-28
Confirmed. But I don't know what it means as things tend to work smoothly anyway.

---

### Post by philinux on 2009-01-28
> **Gina said:**
> I get odd messages on startup but things work anyway so I don't worry.  Maybe I should take note and report back but I always seem to forget. 

Your errors look like drives not ready and not getting reset. Do you get any problems once the system is up and running?  What devices do you have on ata1 and ata3?

All works fine. I've got two HD's. sda1 running intrepid and sdb1 running jaunty. Both with /, /swap and /home.

On intrepid these message appear after suspend. On Jaunty they always appear at boot up.

---

### Post by bpl07 on 2009-01-28
Me too.

---

### Post by loser72555 on 2009-02-22
This is evidently not an error confined to Ubuntu.  I run Mepis and get the same error.  Googled on it and it pushed me to this forum.  My only ata drive is a cd rom/dvd burner.  The rest of the stuff is sata.  So far it causes no problems with the system running, but the error msg repeats each boot.

---

### Post by tawmas on 2009-02-22
I got a lot of these from a device (a dvd reader) that turned out to be in the process of getting broken... :-(

EDIT: What I mean, is that this could be hardware-related.

---

### Post by philinux on 2009-02-23
I've got two sata drives both running Jaunty. I update one, test it and if it breaks I wait till it gets fixed before I update the other. I've always got a running system this way. 

Drive 1 shows the two ata errors on boot the other does not. So I would say it's a software thing. Drive 1 was a clean install drive 2 was an intrepid update to Jaunty.

---

### Post by Archmage on 2009-02-23
I got this, too. For my harddrive and my cd-rom. Both a brand new.

---

### Post by philinux on 2009-03-29
This is back again on a clean beta install. It slows the boot process up.

Is there a fix? Nothing in messages.log but this in dmesg.
```
 ata1: SATA max UDMA/133 abar m1024@0xf7fff800 port 0xf7fff900 irq 2300
[    1.086547] ata2: SATA max UDMA/133 abar m1024@0xf7fff800 port 0xf7fff980 irq 2300
[    1.086550] ata3: SATA max UDMA/133 abar m1024@0xf7fff800 port 0xf7fffa00 irq 2300
[    1.086553] ata4: SATA max UDMA/133 abar m1024@0xf7fff800 port 0xf7fffa80 irq 2300
[    1.568015] ata1: softreset failed (device not ready)
[    1.568066] ata1: failed due to HW bug, retry pmp=0
[    1.732028] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.732589] ata1.00: ATA-7: MAXTOR STM3250310AS, 3.AAC, max UDMA/133
[    1.732590] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.733272] ata1.00: configured for UDMA/133
[    2.068031] ata2: SATA link down (SStatus 0 SControl 300)
[    2.568013] ata3: softreset failed (device not ready)
[    2.568061] ata3: failed due to HW bug, retry pmp=0
[    2.732025] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.732589] ata3.00: ATA-7: MAXTOR STM3250310AS, 3.AAC, max UDMA/133
[    2.732591] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.733290] ata3.00: configured for UDMA/133
[    3.068030] ata4: SATA link down (SStatus 0 SControl 300)
[    3.084108] scsi 0:0:0:0: Direct-Access     ATA      MAXTOR STM325031 3.AA PQ: 0 ANSI: 5
```

---

### Post by todak on 2009-03-29
It might be a bug related to SATA drives. I have two IDE hard drives and two IDE DVD burners and do not see the message.

---

### Post by philinux on 2009-03-29
Strange thing is it dont appear on my alpha install, which is obviously now the beat. But it appears on the beta clean install. Did not appear on 64 bit intrepid.

---

### Post by Reiger on 2009-03-29
Oh this message is something I'm used to seeing in Hardy/Intrepid. I figured, you cause it yourself, by having one (possibly failed, I've had quite a few of 'em fail on me in Hardy/Intrepid) attempt to let your PC **hibernate**. Seems like the system wishes to make good on its earlier failures to hibernate by doing this now and settle its debt...

Obviously, any attempt to hibernate isn't going to work right at the very first beginnings of a boot-up procedure, though. ;)

I don't get this error, for instance, on my desktop which *never* hibernates (a shutdown is just as convenient). (But does have funny error messages at shutdown: can't enumerate IDE devices.)

---

### Post by philinux on 2009-03-29
> **Reiger said:**
> Oh this message is something I'm used to seeing in Hardy/Intrepid. I figured, you cause it yourself, by having one (possibly failed, I've had quite a few of 'em fail on me in Hardy/Intrepid) attempt to let your PC **hibernate**. Seems like the system wishes to make good on its earlier failures to hibernate by doing this now and settle its debt...

Obviously, any attempt to hibernate isn't going to work right at the very first beginnings of a boot-up procedure, though. ;)

I don't get this error, for instance, on my desktop which *never* hibernates (a shutdown is just as convenient). (But does have funny error messages at shutdown: can't enumerate IDE devices.)

Thats probably it. I've had a failed suspend on this drive but not the other. This message appears at every boot now though. 

How do you get rid of it?

---

### Post by philinux on 2009-03-29
SOLVED but not sure how.

I installed startupmanager and that did it's thing but I also booted into recovery to see all messages.

After that no errors at startup although they still appear in dmesg. Boot up is faster too.

---

### Post by pig-flower on 2009-03-30
same here. but all thing is good work. i just wonder what means this messages...

```
dmesg | grep ata
[    0.000000]  BIOS-e820: 00000000bfee3000 - 00000000bfef0000 (ACPI data)
[    0.000000]  modified: 00000000bfee3000 - 00000000bfef0000 (ACPI data)
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.004000] Memory: 3087304k/3144576k available (4127k kernel code, 55944k reserved, 2208k data, 532k init, 2239368k highmem)
[    0.004000]       .data : 0xc0507dff - 0xc072fe60   (2208 kB)
[    0.469315] libata version 3.00 loaded.
[    1.591535] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
[    1.591538] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
[    1.591542] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
[    1.591546] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
[    2.072018] ata1:[COLOR="Red"] softreset failed (device not ready)[/COLOR]
[    2.072062] ata1:[COLOR="Blue"] failed due to HW bug, retry pmp=0[/COLOR]
[    2.236028] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.239331] ata1.00: ATA-7: SAMSUNG SP2504C, VT100-59, max UDMA7
[    2.239333] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.239351] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    2.242709] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    2.242712] ata1.00: configured for UDMA/133
[    2.724017] ata2:[COLOR="Red"] softreset failed (device not ready)[/COLOR]
[    2.724057] ata2:[COLOR="Blue"] failed due to HW bug, retry pmp=0[/COLOR]
[    2.888027] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.893388] ata2.00: ATA-7: SAMSUNG HD250HJ, FH100-06, max UDMA7
[    2.893391] ata2.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.893407] ata2.00: SB600 AHCI: limiting to 255 sectors per cmd
[    2.898793] ata2.00: SB600 AHCI: limiting to 255 sectors per cmd
[    2.898795] ata2.00: configured for UDMA/133
[    3.216032] ata3: SATA link down (SStatus 0 SControl 300)
[    3.536031] ata4: SATA link down (SStatus 0 SControl 300)
[    3.563104] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.563217] scsi4 : pata_atiixp
[    3.563282] scsi5 : pata_atiixp
[    3.564235] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf900 irq 14
[    3.564237] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf908 irq 15
[    3.728485] ata5.01: ATAPI: HL-DT-ST RW/DVD GCC-4480B, 1.02, max UDMA/33
[    3.744435] ata5.01: configured for UDMA/33
[    4.417745] Write protecting the kernel read-only data: 1532k
[    4.895990] EXT3-fs: mounted filesystem with ordered data mode.
[   11.430271] EXT3-fs: mounted filesystem with ordered data mode.
[  761.433209] EXT3-fs: mounted filesystem with ordered data mode.
[  867.396602] EXT3-fs: mounted filesystem with ordered data mode.
```

---

### Post by flurl on 2009-03-31
I wouldn't worry about the messages, as long as you have an AMD motherboard and you get after the "softreset failed" message another one like "failed due to HW bug, retry pmp=0".
This message is due to a workaround for a hardware bug in AMD chipsets - if i interpret the comment on [http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.26.y.git;a=blob_plain;f=drivers/ata/ahci.c;hb=HEAD]("http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.26.y.git;a=blob_plain;f=drivers/ata/ahci.c;hb=HEAD") the right way (search for the function "ahci_sb600_softreset").

---

### Post by zika on 2009-04-01
> **flurl said:**
> I wouldn't worry about the messages, as long as you have an AMD motherboard and you get after the "softreset failed" message another one like "failed due to HW bug, retry pmp=0".
This message is due to a workaround for a hardware bug in AMD chipsets - if i interpret the comment on [http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.26.y.git;a=blob_plain;f=drivers/ata/ahci.c;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.26.y.git;a=blob_plain;f=drivers/ata/ahci.c;hb=HEAD) the right way (search for the function "ahci_sb600_softreset").
same here:```
[    1.408439] ata1: SATA max UDMA/133 irq_stat 0x00400000, PHY RDY changed irq 22
[    1.408490] ata2: SATA max UDMA/133 abar m1024@0xfe9ff800 port 0xfe9ff980 irq 22
[    1.408541] ata3: SATA max UDMA/133 abar m1024@0xfe9ff800 port 0xfe9ffa00 irq 22
[    1.408592] ata4: SATA max UDMA/133 abar m1024@0xfe9ff800 port 0xfe9ffa80 irq 22
[    2.292054] ata1: softreset failed (device not ready)
[    2.292103] ata1: failed due to HW bug, retry pmp=0
[    2.456052] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.456918] ata1.00: ATA-8: ExcelStor Technology J9250S, GM2OA52A, max UDMA/133
[    2.456968] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.457037] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    2.458081] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    2.458132] ata1.00: configured for UDMA/133
[    2.792030] ata2: SATA link down (SStatus 0 SControl 300)
[    3.128027] ata3: SATA link down (SStatus 0 SControl 300)
[    3.464027] ata4: SATA link down (SStatus 0 SControl 300)
[    3.480040] isa bounce pool size: 16 pages
[    3.480152] scsi 0:0:0:0: Direct-Access     ATA      ExcelStor Techno GM2O PQ: 0 ANSI: 5
[    3.480280] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    3.480926] sd 0:0:0:0: [sda] Write Protect is off
[    3.480971] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.480993] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.481105] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    3.481169] sd 0:0:0:0: [sda] Write Protect is off
[    3.481218] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.481235] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.481290]  sda: sda1 sda2 sda3
[    3.540225] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.540313] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.540569] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.540642] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    3.540714] scsi4 : pata_atiixp
[    3.540810] scsi5 : pata_atiixp
[    3.542076] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    3.542125] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    3.704517] ata5.00: ATAPI: Optiarc DVD RW AD-5200A, 1.05, max UDMA/66
[    3.720455] ata5.00: configured for UDMA/66
```

looks like a bad choice of words for a warning ...

---

