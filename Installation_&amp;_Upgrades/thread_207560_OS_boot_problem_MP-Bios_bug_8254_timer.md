---
title: "OS boot problem: MP-Bios bug 8254 timer"
date: 2006-07-02
forum: Installation &amp; Upgrades
---

### Post by afbase on 2006-07-02
NOTICE: I AM A linux NOOB

Okay, i installed ubuntu and i got error when it boots:
[42949376.2000] MP-Bios bug: 8254 timer not connected to IO-APIC
[42949376.290000] 0:0:0:0 Write buffer failure on 80002
[42949376.290000] 0:0:0:0 Write buffer failure on 80002
[42949376.290000] 0:0:0:0 Write buffer failure on 80002
[42949376.290000] 0:0:0:0 Write buffer failure on 80002
[42949376.290000] 0:0:0:0 Write buffer failure on 80002 reverting back to asynchronous

-----------------------------------------
Any clues as to what problem is?  I've noticed on some other threads about USB problems so i've already disabled those through the BIOS.  While i was in the bios i noticed in one of the logs i have is a number of CMOS checksum errors.  Not sure if that is related to this problem but just an FYI.

once it finishes the boot it goes directly to command prompt asking me for my user name and password.  Now i'm not sure if that is the standard procedure for booting.  From what i'm initially reading on the forums is that once a regular boot process is complete on ubuntu it loads into a GUI (gnome?? i'm guessing).  


Any suggestions as to what i need to do?


---------------Hardware--------------
-2 Intel Xeon processors (800 mhz each)
-18.3 gb scsi hard drive (western digital - i think 40 pin, not sure;i've never worked with SCSI before)
-Super Motherboard (thats as far as i know, and yes it really is a super mobo)
-CDRW
-Floppy drive

---

