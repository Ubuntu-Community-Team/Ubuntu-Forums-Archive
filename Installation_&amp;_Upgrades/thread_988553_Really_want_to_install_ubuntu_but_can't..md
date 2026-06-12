---
title: "Really want to install ubuntu but can't."
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by eviesdad on 2008-11-20
Hi,

I am a newb to linux who would love to install ubuntu through wubi onto my main pc.

**I have installed it with very little on my laptop but it will just not install on my pc.**

When booting ubuntu it gives me a 'kernel panic killing init message'.

I have tried all of the boot options including Live CD and get the same message. 

I have also tried to load Knoppix and that just hangs on a black screen.

I am beginning to believe I must have a hardware problem. Are there any obvious issues I should know about? I have tried looking theough the forums but there is such a glut of info it is impossible.

My system details are as follows:

Operating System 	  	System Model
Windows XP Professional Service Pack 3 (build 2600) 	  	Enclosure Type: Desktop
Processor a 	  	Main Circuit Board b
2.65 gigahertz Intel Core Duo
64 kilobyte primary memory cache
1024 kilobyte secondary memory cache 	  	Board: 2Core1333-2.66G
Bus Clock: 333 megahertz
BIOS: American Megatrends Inc. P1.00 07/16/2007
Drives 	  	Memory Modules c,d
329.55 Gigabytes Usable Hard Drive Capacity
155.04 Gigabytes Hard Drive Free Space

_NEC DVD_RW ND-3520A [CD-ROM drive]
Generic DVD-ROM SCSI CdRom Device [CD-ROM drive]
Generic DVD-ROM SCSI CdRom Device [CD-ROM drive]
3.5" format removeable media [Floppy drive]

MAXTOR STM3250310AS [Hard drive] (250.06 GB) -- drive 1
WDC WD800JB-00CRA1 [Hard drive] (80.02 GB) -- drive 0 	  	2040 Megabytes Installed Memory

Slot 'DIMM0' has 1024 MB
Slot 'DIMM1' has 1024 MB
  	Local Drive Volumes
  	
		
c: (NTFS on drive 1) 	223.84 GB 	106.21 GB free
e: (NTFS on drive 0) 	79.50 GB 	48.43 GB free
h: (NTFS on drive 1) 	26.21 GB 	400 MB free

Many thanks

Eviesdad

---

### Post by adaptr on 2008-11-20
> 2040 Megabytes Installed Memory
You have on-board video - is this necessary, or unused ?

Anyway, the way to get around those kernel panic messages (it means Ubuntu could not start because something crashed the kernel) is to closely examine all your BIOS options, specifically those pertaining to power saving modes (ACPI), and try to lower or disable them.
You can also force Ubuntu to ignore ACPI by editing the boot menu and adding "acpi=off" at the end of the "kernel=" line.

---

### Post by eviesdad on 2008-11-20
Thank you adaptr.

I will have a play around with the bios settings and see what happens.

Eviesdad

---

### Post by kerry_s on 2008-11-20
> When booting ubuntu it gives me a 'kernel panic killing init message'.

most common cause bad cd, make sure you burn the image slow 4x if possible or what ever is the slowest yours can go at.

---

### Post by eviesdad on 2008-11-20
Thanks kerry_s


I've tried that already. No luck there either.


Eviesdad

---

