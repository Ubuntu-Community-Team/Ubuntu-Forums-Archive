---
title: "The creation of swap space in partition #5 of SCSI1 (0,0,0) (sda) failed."
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by tiroon on 2008-01-13
Hi! I'm new to Ubuntu, and when I tried installing I got this error msg:
The creation of swap space in partition #5 of SCSI1 (0,0,0) (sda) failed.

I tried creating partitions manually, but I get the same error. The reason I'm trying Ubuntu is because Vista wasn't working properly after I formatted it. Anyways, here are the partitions that were going to be installed:

The partition tables of the following devices are changed:
 SCSI1 (0,0,0) (sda)

The following partitions are going to be formatted:
 partition #1 of SCSI1 (0,0,0) (sda) as ext3
 partition #5 of SCSI1 (0,0,0) (sda) as swap


Atm, I'm running firefox through the installation dvd, so the hd is clean (afaik).


Hope someone have time to help.

tiroon

---

### Post by Perpetual on 2008-01-13
How big was the swap and what is in partitions 2, 3, and 4?  Was partition 1 your / partition?  How big is the drive?

---

### Post by smurf47172 on 2008-02-05
> **Perpetual said:**
> How big was the swap and what is in partitions 2, 3, and 4?  Was partition 1 your / partition?  How big is the drive?

Partitions 2, 3, and 4 do not matter.  The default for the automatic partitioning is 1 for the / partition and 5 for the swap.  Now the drive size question is very good.  If it is below the recommended you will get this message.  However, I have received this message when I am installing Ubuntu 7.10 in Virtual Box.  What I did to resolve this is reboot the system after I received the message and try again.  It worked fine the second time for some reason.  I do not know if this is the case for normal installs, but it is worth a shot.

Smurf

---

