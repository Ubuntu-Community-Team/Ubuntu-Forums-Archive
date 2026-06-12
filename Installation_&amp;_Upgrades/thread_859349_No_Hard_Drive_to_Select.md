---
title: "No Hard Drive to Select"
date: 2008-07-14
forum: Installation &amp; Upgrades
---

### Post by charlesbw on 2008-07-14
I am trying to install ubuntu, but when i get to the partitioner part.  Where I choose what hard drive i want to install ubuntu on, no hard drive is listed.  Is there a solution to this problem...or do i have to accept the fact that the live cd doesn't work on my system?

---

### Post by cmnorton on 2008-07-14
We would need to know a little more about the hardware. 

Can you boot from the live CD?

Is there another OS (Windows?) on this PC already? In other words, what are the circumstances of your installing Ubuntu on this system?

---

### Post by charlesbw on 2008-07-14
i have two hard drives, i have window vista installed on the first one and the second is completely clean (as in nothing in it).  The drives are both western digital, the vista drive is 500 GB and the one i want to install ubuntu in is 320 GB.  I have a 8800 GT, 4 gigs of RAM, E6750 core 2 duo, AC-1 Barracuda Sound Card, Haupper TV Tuner, Zonet wireless card.  Please let me know if you need further information.

---

### Post by logos34 on 2008-07-14
Are they sata or ide drives?

On the live cd desktop go to system>admin>partition editor (Gparted)

Do the drives show up?

Run this command in a terminal (apps>accessories>terminal) and post it:

**sudo fdisk -l**

What about your Bios settings?  If the 320 is a sata drive, maybe try changing the sata mode between ide emulation and ahci

---

### Post by charlesbw on 2008-07-14
I tried the partition editor and the drives didn't show up

I tried the command and nothing was spit out, am gonna restart now and try editing the modes.

---

### Post by charlesbw on 2008-07-14
i dont see any options to change the sata mode between IDE emulation and ahci in my bios.  

I did try to strip my hardware down to just hard drive, video card and other bare minimums and nothing changed during installation.  Still cannot detect the drives.

Although i keep getting this error during boot up:

> buffer error on device fd0 - logical block 0

and 
> 
ata4.00: revalidation failed (errno=-5)

---

### Post by charlesbw on 2008-07-15
i decided to take a tip from a thread i read and post this as well

> [    0.000000]  BIOS-e820: 00000000bfee3000 - 00000000bfef0000 (ACPI data)
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[   30.848906] Memory: 4041776k/5242880k available (2466k kernel code, 150988k reserved, 1309k data, 316k init)
[   33.475475] libata version 3.00 loaded.
[   34.300880] scsi0 : pata_jmicron
[   34.300908] scsi1 : pata_jmicron
[   34.301066] ata1: PATA max UDMA/100 cmd 0xcf00 ctl 0xce00 bmdma 0xcb00 irq 17
[   34.301068] ata2: PATA max UDMA/100 cmd 0xcd00 ctl 0xcc00 bmdma 0xcb08 irq 17
[   34.968174] ata1.00: ATAPI: CD-ROM  F565E,  1.07, max UDMA/66
[   34.968185] ata1.01: ATAPI: LITE-ON DVDRW LH-20A1P, KL0G, max UDMA/66
[   34.968191] ata1.00: limited to UDMA/33 due to 40-wire cable
[   34.968192] ata1.01: limited to UDMA/33 due to 40-wire cable
[   35.132315] ata1.00: configured for UDMA/33
[   35.319898] ata1.01: configured for UDMA/33
[   35.476866] ata_piix 0000:00:1f.2: version 2.12
[   35.476871] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[   35.477357] scsi2 : ata_piix
[   35.477594] scsi3 : ata_piix
[   35.477968] ata3: SATA max UDMA/133 cmd 0xf900 ctl 0xf800 bmdma 0xf500 irq 19
[   35.477970] ata4: SATA max UDMA/133 cmd 0xf700 ctl 0xf600 bmdma 0xf508 irq 19
[   65.576501] ata3.00: qc timeout (cmd 0x27)
[   65.576505] ata3.00: failed to read native max address (err_mask=0x4)
[   65.576507] ata3: failed to recover some devices, retrying in 5 secs
[  100.667471] ata3.00: qc timeout (cmd 0x27)
[  100.667475] ata3.00: failed to read native max address (err_mask=0x4)
[  100.667478] ata3.00: revalidation failed (errno=-5)
[  100.667480] ata3: failed to recover some devices, retrying in 5 secs
[  135.758436] ata3.00: qc timeout (cmd 0x27)
[  135.758440] ata3.00: failed to read native max address (err_mask=0x4)
[  135.758443] ata3.00: revalidation failed (errno=-5)
[  135.758446] ata3.00: disabled
[  136.261325] ata3: soft resetting link
[  136.417504] ata3: EH complete
[  166.514909] ata4.00: qc timeout (cmd 0x27)
[  166.514913] ata4.00: failed to read native max address (err_mask=0x4)
[  166.514915] ata4: failed to recover some devices, retrying in 5 secs
[  201.605937] ata4.00: qc timeout (cmd 0x27)
[  201.605940] ata4.00: failed to read native max address (err_mask=0x4)
[  201.605942] ata4.00: revalidation failed (errno=-5)
[  201.605979] ata4: failed to recover some devices, retrying in 5 secs
[  236.697332] ata4.00: qc timeout (cmd 0x27)
[  236.697337] ata4.00: failed to read native max address (err_mask=0x4)
[  236.697339] ata4.00: revalidation failed (errno=-5)
[  236.697377] ata4.00: disabled
[  237.199749] ata4: soft resetting link
[  237.355924] ata4: EH complete
[  237.355952] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[  237.356027] scsi4 : ata_piix
[  237.356295] scsi5 : ata_piix
[  237.356481] ata5: SATA max UDMA/133 cmd 0xf200 ctl 0xf100 bmdma 0xee00 irq 19
[  237.356483] ata6: SATA max UDMA/133 cmd 0xf000 ctl 0xef00 bmdma 0xee08 irq 19


---

### Post by cmnorton on 2008-07-15
This story may only be slightly related, but might be of help.

I don't know how old your hardware is, but I have a perfectly good "Chembro" battleship server from four years ago, with Intel motherboard, SATA drives, and Adaptec SATA controllers. Linux installed fine. I kept returning RAM to the SMART memory people, because I'd get kernel panics about reading bad memory. (The SMART people were quite nice, by the way.) It turns out the problem was bad I/O because of the adapters.

Can you resolve this problem with an adapter that works with your hardware or some other combination of hardware changes?

---

### Post by charlesbw on 2008-07-15
i tried multiple hardware configurations and nothing has worked so far.  What does I/O mean?  
I also tried the alternate disk for hardy and that got the same results.

---

### Post by cmnorton on 2008-07-15
> **charlesbw said:**
> i tried multiple hardware configurations and nothing has worked so far.  What does I/O mean?  
I also tried the alternate disk for hardy and that got the same results.

I/O = input/output

---

