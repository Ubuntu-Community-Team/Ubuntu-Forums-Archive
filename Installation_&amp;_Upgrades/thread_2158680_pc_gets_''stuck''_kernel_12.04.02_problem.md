---
title: "pc gets ''stuck'' kernel 12.04.02 problem?"
date: 2013-06-30
forum: Installation &amp; Upgrades
---

### Post by spiridonios on 2013-06-30
actually this thread is kinda the continue of this one [http://ubuntuforums.org/showthread.php?t=2155252&page=2](http://ubuntuforums.org/showthread.php?t=2155252&page=2), but since the nature of the issue seems to have changed, I thought of redirecting it here.

Ok, so here' s the situation:

As long asmy new built machine works, it's really fast and as far as I can tell, everything seems to work preety good. I got decent temperatures (the same as I stated at the previous post, about 40C at the cpu and typing to terminal acpi -t  I get
Thermal 0: ok, 29.8 degrees C
Thermal 1: ok, 27.8 degrees C
which seem preety ok (even if i m not sure to what part they 're refering to..)

Having adjusted at the top bar the system load monitor, it seems really unloaded during the soft applications I 've been running so far. web browsing, chating and music listening basically. The cpu is almost always at 0 to 4% , ram 300 to 700 mb used from 8 gb and of the 8 gb swap usually 0%

I did the ''check the cd for defects'' before installing ubuntu and after also, I did memtest twice.

the first time using an older version of memtest86+ v.4.00 which recognized cpu as
intel i7 at 3392 mhz
L1 cache : Unknown
L2 Cache : Unknown
L3 Cache : None
memory : 8082 M
Chipset : Core IMC (ECC : Direct/ correct)
scrubt / Blck : )mhz
triple channel channel
settings ram : 0 Mhz (DDR3 - )  / CAS : 19-15-15-31
I let it run for 36 hours, no errors found

the second time i used the dvd from which i installed ubuntu studio. memtest86 v4.20 and i got
intel core gen2 3403 mhz
settings : ram : 800 Mhz (DDR3-1601) / CAS : 8-8-8-24 / dual channel
I let it pass the first test and half an hour more, no errors found

so basically its been recognized differently.
At some time after the first memtest i changed the ram frequency in the bios from the auto function, in which it was running at 1300 mhz, to 1600 mhz. this is the only bios change that i ve done so far. everything else is still set to default.

The problem is, that while the pc is normally running, suddenly (usually while i 'm moving the mouse around to do some click anywhere) the mouse stops responding, if any sound is being played it gets stuck and keeps looping the past half second that was going on while the pc was functioning, the restart button is not working either. ctr,alt,delete or ctr.alt,backspace dont work. so I have to keep pressed the shut down button from the box till it shuts down. then i repress it, it opens again and I it works till it crushes again..

I had a crash report a couple of days ago that was refering to the sensors pluggin that i installed at the top bar,

sorry, ubuntu 12.04 has experienced an internal error.
if you notice further problems, try restarting the computer.

Executable path
   /usr/lib/xfce4-sensors-plugin/xfce4/panel-plugins/xfce4-sensors-plugin

Package
   xfce4-sensors-plugin 1.2.3-2
problemType
   Crash
Title
   xfce4-sensors-plugin crashed with SIGSEGV in free()
ApportVersion
   2.0.1-0ubuntu17.3
Architecture
   amd64
CoreDump
   (binary data)
Date
   Thu Jun 27 02:18:20 2013
Dependencies
   adduser 3.113ubuntu2
   base-passwd 3.5.24
   busybox-initramfs 1:1.18.5-1ubuntu4.1
   ...
SegvAnalysis
  Segfault happened at: 0x7ff8d284459c <free+60>: mov (%rax),%rdi
  PC(0x7ff8d284459c) ok
  source"(%rax)"(0x7ff8d4000000) in non-readable VMA region: 0x7ff8d41c5000      ---  p /usr/lib/libxfce4util.so.4.1.1
  destination"%rdi"ok

   so i completelly removed it, but the problem keeps going on.



First of all, I guess that my machine should be compatible with the 64 bit ubuntu version, since its so new. but could it be incompatible?

Does anyone know of any incompatibillity between the parts of my pc, or could this be the problem?


running  less /var/log/syslog i find these (from all day) errors:

Jun 29 23:36:58 spiridonios-To-be-filled-by-O-E-M kernel: [   15.861146] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 17000000, was 12060000

Jun 29 23:36:57 spiridonios-To-be-filled-by-O-E-M kernel: [    9.168339] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
Jun 29 23:36:57 spiridonios-To-be-filled-by-O-E-M kernel: [    9.168343] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT0._GTF] (Node ffff8802118a2050),
 AE_NOT_FOUND (20110623/psparse-536)
Jun 29 23:36:57 spiridonios-To-be-filled-by-O-E-M kernel: [    9.172304] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
Jun 29 23:36:57 spiridonios-To-be-filled-by-O-E-M kernel: [    9.172308] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT0._GTF] (Node ffff8802118a2050),
 AE_NOT_FOUND (20110623/psparse-536)

Jun 29 23:36:57 spiridonios-To-be-filled-by-O-E-M kernel: [    1.284704] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
Jun 29 23:36:57 spiridonios-To-be-filled-by-O-E-M kernel: [    1.284708] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT1._GTF] (Node ffff8802118a20c8),
 AE_NOT_FOUND (20110623/psparse-536)
Jun 29 23:36:57 spiridonios-To-be-filled-by-O-E-M kernel: [    1.284882] ata2.00: configured for UDMA/133
Jun 29 23:36:57 spiridonios-To-be-filled-by-O-E-M kernel: [    1.286097] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
Jun 29 23:36:57 spiridonios-To-be-filled-by-O-E-M kernel: [    1.286101] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT0._GTF] (Node ffff8802118a2050),
 AE_NOT_FOUND (20110623/psparse-536)
Jun 29 23:36:57 spiridonios-To-be-filled-by-O-E-M kernel: [    1.286108] ata1.00: ATAPI: HL-DT-ST DVDRAM GH22LS50, TL02, max UDMA/100
Jun 29 23:36:57 spiridonios-To-be-filled-by-O-E-M kernel: [    1.289971] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
Jun 29 23:36:57 spiridonios-To-be-filled-by-O-E-M kernel: [    1.289976] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT0._GTF] (Node ffff8802118a2050),
 AE_NOT_FOUND (20110623/psparse-536)

Jun 29 23:36:57 spiridonios-To-be-filled-by-O-E-M kernel: [    1.284278] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
Jun 29 23:36:57 spiridonios-To-be-filled-by-O-E-M kernel: [    1.284282] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT1._GTF] (Node ffff8802118a20c8),
 AE_NOT_FOUND (20110623/psparse-536)



Jun 29 21:42:48 spiridonios-To-be-filled-by-O-E-M kernel: [   15.621093] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected
 17000000, was 12060000

also Jun 29 21:42:47 spiridonios-To-be-filled-by-O-E-M kernel: [    1.284919] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
Jun 29 21:42:47 spiridonios-To-be-filled-by-O-E-M kernel: [    1.284924] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT1._GTF] (Node ffff8802118a20c8),
 AE_NOT_FOUND (20110623/psparse-536)
Jun 29 21:42:47 spiridonios-To-be-filled-by-O-E-M kernel: [    1.285189] ata2.00: configured for UDMA/133
Jun 29 21:42:47 spiridonios-To-be-filled-by-O-E-M kernel: [    1.288053] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
Jun 29 21:42:47 spiridonios-To-be-filled-by-O-E-M kernel: [    1.288057] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT0._GTF] (Node ffff8802118a2050),
 AE_NOT_FOUND (20110623/psparse-536)
Jun 29 21:42:47 spiridonios-To-be-filled-by-O-E-M kernel: [    1.288064] ata1.00: ATAPI: HL-DT-ST DVDRAM GH22LS50, TL02, max UDMA/100
Jun 29 21:42:47 spiridonios-To-be-filled-by-O-E-M kernel: [    1.291927] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
Jun 29 21:42:47 spiridonios-To-be-filled-by-O-E-M kernel: [    1.291931] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT0._GTF] (Node ffff8802118a2050),
 AE_NOT_FOUND (20110623/psparse-536)

Jun 29 20:51:24 spiridonios-To-be-filled-by-O-E-M kernel: [    1.290159] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
Jun 29 20:51:24 spiridonios-To-be-filled-by-O-E-M kernel: [    1.290164] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT1._GTF] (Node ffff8802118a20c8),
 AE_NOT_FOUND (20110623/psparse-536)

Jun 29 16:31:04 spiridonios-To-be-filled-by-O-E-M kernel: [ 3132.509953] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected
 00070000, was 17000000

Jun 29 15:38:57 spiridonios-To-be-filled-by-O-E-M kernel: [   15.372398] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected
 17000000, was 12060000

Jun 29 15:38:57 spiridonios-To-be-filled-by-O-E-M kernel: [    1.286258] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT0._GTF] (Node ffff8802118a2050),
 AE_NOT_FOUND (20110623/psparse-536)

Jun 29 15:38:57 spiridonios-To-be-filled-by-O-E-M kernel: [    1.286254] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)

Jun 29 15:38:57 spiridonios-To-be-filled-by-O-E-M kernel: [    1.281160] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
Jun 29 15:38:57 spiridonios-To-be-filled-by-O-E-M kernel: [    1.281164] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT0._GTF] (Node ffff8802118a2050),
 AE_NOT_FOUND (20110623/psparse-536)

Jun 29 15:38:57 spiridonios-To-be-filled-by-O-E-M kernel: [    1.278936] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
Jun 29 15:38:57 spiridonios-To-be-filled-by-O-E-M kernel: [    1.278940] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT1._GTF] (Node ffff8802118a20c8),
 AE_NOT_FOUND (20110623/psparse-536)

Jun 29 14:21:34 spiridonios-To-be-filled-by-O-E-M kernel: [    1.289490] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
Jun 29 14:21:34 spiridonios-To-be-filled-by-O-E-M kernel: [    1.289494] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT0._GTF] (Node ffff8802118a2050),
 AE_NOT_FOUND (20110623/psparse-536)
Jun 29 14:21:34 spiridonios-To-be-filled-by-O-E-M kernel: [    1.289500] ata1.00: ATAPI: HL-DT-ST DVDRAM GH22LS50, TL02, max UDMA/100
Jun 29 14:21:34 spiridonios-To-be-filled-by-O-E-M kernel: [    1.293709] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
Jun 29 14:21:34 spiridonios-To-be-filled-by-O-E-M kernel: [    1.293713] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT0._GTF] (Node ffff8802118a2050),
 AE_NOT_FOUND (20110623/psparse-536)

Jun 29 14:21:34 spiridonios-To-be-filled-by-O-E-M kernel: [    1.286512] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
Jun 29 14:21:34 spiridonios-To-be-filled-by-O-E-M kernel: [    1.286516] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT1._GTF] (Node ffff8802118a20c8),
 AE_NOT_FOUND (20110623/psparse-536)

Jun 29 12:09:54 spiridonios-To-be-filled-by-O-E-M kernel: [    1.289472] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
Jun 29 12:09:54 spiridonios-To-be-filled-by-O-E-M kernel: [    1.289476] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT1._GTF] (Node ffff8802118a20c8),
 AE_NOT_FOUND (20110623/psparse-536)
Jun 29 12:09:54 spiridonios-To-be-filled-by-O-E-M kernel: [    1.289645] ata2.00: configured for UDMA/133
Jun 29 12:09:54 spiridonios-To-be-filled-by-O-E-M kernel: [    1.291293] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
Jun 29 12:09:54 spiridonios-To-be-filled-by-O-E-M kernel: [    1.291297] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT0._GTF] (Node ffff8802118a2050),
 AE_NOT_FOUND (20110623/psparse-536)
Jun 29 12:09:54 spiridonios-To-be-filled-by-O-E-M kernel: [    1.291304] ata1.00: ATAPI: HL-DT-ST DVDRAM GH22LS50, TL02, max UDMA/100
Jun 29 12:09:54 spiridonios-To-be-filled-by-O-E-M kernel: [    1.295156] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
Jun 29 12:09:54 spiridonios-To-be-filled-by-O-E-M kernel: [    1.295160] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT0._GTF] (Node ffff8802118a2050),
 
Jun 29 12:09:54 spiridonios-To-be-filled-by-O-E-M kernel: [    1.289122] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT1._GTF] (Node ffff8802118a20c8),
 AE_NOT_FOUND (20110623/psparse-536)

Jun 29 12:09:54 spiridonios-To-be-filled-by-O-E-M kernel: [    1.289118] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20110623/psargs-359)
:


In this thread, [http://ubuntuforums.org/showthread.php?t=2135522](http://ubuntuforums.org/showthread.php?t=2135522), i see that some people that been having the same (*ERROR* Power management discrepancy) problem seem to have solved it installing kernal 3.3.6. Maybe I should try installing it too? ( I 've never actually tried to install a kernel out of synaptic, so any advice how to will be really helpfull..)
 
I don't find what the acpi errors are about...

Any advice welcome :)

---

### Post by dino99 on 2013-06-30
your main problem is related to acpi; you need to dig around
[https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)

---

### Post by spiridonios on 2013-07-01
so it looks like a software related problem. Not like something going wrong with some part of the hardware. Or a compliance issue..
I m worrying cause I have to leave for work for a couple of months, and because I just bought the hardware, it would be better to report a misbehavior to the dealer soon, if there was some. ( of course almost everything has about 3 years of warranty..)
So probably even installing some other linux distro wouldn't give the same bugs..

---

### Post by spiridonios on 2013-07-09
so seems like it was a software problem. I installed ubuntu studio 13.04 and the machine 's been running almost 24 hours now :)

---

### Post by spiridonios on 2013-07-14
yeap.
after 4 days and everything works fine. just fine :)

---

