---
title: "Ubuntu Fails to Detect Hard Drives"
date: 2007-10-14
forum: Installation &amp; Upgrades
---

### Post by zachsandberg on 2007-10-14
Hello everyone, I am trying to install Ubuntu 7.04 on an IBM Intellistation A Pro.  Currently Installed in the Intellistation are four Seagate Cheetah 36.7GB disks running independently with no raid.  The SCSI controller is an Adaptec® AIC7902W / dual channel Ultra320 SCSI controller.  I cannot for the life of me get Ubuntu to discover and use this card.  I am having the same issue with Fedora Core 6 (my backup diagnostic OS)  The frustrating part about this is that Ubuntu gives me no error reports, and in the GNOME Hardware Information program even lists the device correctly as an AIC79xxx SCSI controller.  I have switched around the cabling in the case to no avail, and have scoured the web for any information that could point me in the right direction.  Some other forum noted that the driver was broken in an older kernel, however I have tried numerous kernels to no avail.

The way I have the drives set up I believe are correct.  I have a 3 connector cable coming from the motherboard, the first hard drive is connected to the last connector (closest to the terminator) while the third drive is closest to the MoBo.  I have the last drive running off of a separate channel (and works fine in windows)

Fedora gives a message that says "Domain Validation failure" "dropping back", and repeats the message in a loop.  Ubuntu will load the live CD but not detect any drives to install on.

I really appreciate any advice on this one!:)

Zach

---

### Post by zachsandberg on 2007-10-18
After hours of diagnostics, it turned out to be a bad SCSI cable.  Works like a charm, thanks all!

---

