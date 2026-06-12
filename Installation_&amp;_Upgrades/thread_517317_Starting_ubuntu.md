---
title: "Starting ubuntu"
date: 2007-08-04
forum: Installation &amp; Upgrades
---

### Post by caver_w on 2007-08-04
Problem loading ubuntu from the cd:
unbuntu start screen comes up OK.
When I try to start ubuntu it reports that the kernel is loaded.
Gets to statement "kernel direct mapping to tables . . . "
At this point the monitor goes into power saving mode but the cd continues to run for about 1 minute.
I have waited as long as 30 minutes but nothing else happens.

ubuntu version is 7.04 DVD for 64 bit PC
Also have tried  loading ubuntu 6.06 - same problem.

System is AMD64X2 5000+ socket AM2
Mother board is Gigabyte GA-M57SLI-34 Rev 2.0 (I tried flashing to latest bios but didn't help)
Video is Sparkle Ge force 8600 Gt 512 MB
2048 MB PC6400 DDR2 800 MHz Dual Channel Memory
Seagate 500 GB SATA HD


Planned system is for a dual boot Windows XP Professional and unbuntu. (Can't totally get away from software that runs on MS windows.)
[B]
Note[/B]: When I first completed assembling the computer I tried starting ubuntu 7.04 64-bit. It took a long - long time but it did start.  After the initial starting of ubuntu I loaded Windows XP with the intent of partitioning the hard drive. XP loaded OK.

After installing XP I could not start ubuntu from the CD. Problem stated above.

I tried returning the bios to default set up and clearing the CMOS - same problem.

Next I tried installing SUSE 10.2 64 bit.  It stops loading  at "Activating usb devices ..._" At this point the cursor goes away and nothing else happens.( No usb devices are connected to the computer.)

Installing XP must have changed something in the computer but I have not determined what.

Does anyone have some suggestions?

Thanks much,
Bill Walden
[email]wdwalden@hughes.net[/email]

---

### Post by lgambett on 2007-08-04
Try installing from the alternate CD (ie text install). This usually solves problems due to hardware not recognised by the installer. This generally solves the problem.

---

### Post by caver_w on 2007-08-04
Just tried starting ubuntu in text startup.  It still hangs after the startup file lines:

start_kernel+0x24a/-x260
_sinittext+0x163/0x170

Any thoughts?

Best regards,
Bill Walden

---

### Post by tzeentch on 2007-09-04
> **caver_w said:**
> Just tried starting ubuntu in text startup.  It still hangs after the startup file lines:

start_kernel+0x24a/-x260
_sinittext+0x163/0x170

Any thoughts?

Best regards,
Bill Walden
I'm getting the same thing basically.  Kernel hangs just after loading with the call trace displayed ending with the same text as above.
I've found that on my hardware this is caused by/because of a SCSI controller (Domex DMX3194UP) - when I disconnect the controller the kernel loads ok.  Generally this is a problem with the 2.6.20 kernel - the controler worked ok in edgy.
BTW, I'm on amd64.
Don't know if you're issue is similar.  No solution as of yet though, but there is a bug filled in on launchpad somewhere about something similar.

---

### Post by caver_w on 2007-09-04
Thank you for the suggestion.  I do have an older SCSI controller installed and the computer is based on a dual core AMD64. I'll try removing the SCSI controller and see if UBUNTU will install OK.  I've been running SUSE 10.2 OK but would like to try UBUNTU.

Best regards,
Bill Walden

---

### Post by caver_w on 2007-09-04
The SCSI card was apparently the problem. My SCSI is SIIG SCS1360P. Removing the card from the computer allowed the 64 byte version of UBUNTU 7.04 to boot and load.

Thank you ever-so-much,
Bill Walden

---

