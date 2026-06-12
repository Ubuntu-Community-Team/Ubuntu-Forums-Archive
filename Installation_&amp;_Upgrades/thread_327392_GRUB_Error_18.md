---
title: "GRUB Error 18"
date: 2006-12-29
forum: Installation &amp; Upgrades
---

### Post by DistroTech on 2006-12-29
Alright, here's the situation:

Two hard drives, one 20 GB with Windows XP running on it.  The other is a 200 GB internal.  I partitioned the 200 GB internal with the Kubuntu 6.10 Alternate CD (LiveCD is always too slow).  The partition is half and half, decent amount of space for Linux.  Anyway, I went through the whole process of install, everything seemed to work fine until I got to the GRUB install part.

I had read up on differences between GRUB, Lilo, various other bootloaders and boot methods, and had heard both positives and negatives on it.  It seems that experience drives its effectiveness.  I did a test install on another computer, and GRUB worked great, so I thought I'd go for it on the main computer.

GRUB loading stage 1.5...

GRUB loading...
Error 18

That's what I'm  getting.  Upon further research, it appears the BIOS cannot handle such a big hard drive.  I have a few options available to me according to these forums and other sources, and I was wondering if anyone could tell me which one is best / safest.  Want to keep these systems intact, am willing to put in a decent amount of work to do so.

So, should I:

1.) Reinstall the system and add a /boot partition so that it boots correctly (or just tell me how to properly add a /boot parition to the current setup)
2.) Change the / from primary to logical (More details on how to do that please)
3.) Reinstall the MBR from a Windows recovery disk and pretend that Linux is just a dream  
4.) Do something else


Thanks in advance for any and all help!

Partitioning = ](*,)

---

### Post by OpsVentus on 2006-12-29
Hello DistroTech,

Reading the Grub manual the errorcode 18 tells us:
18 : Selected cylinder exceeds maximum supported by BIOS
    This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general). 

So yes, apparently 100 GB is not supported by your BIOS.

I've got 2 good options for you:

1 shrink '/' and create a '/boot' partition
2 repartition the Linux partition to a '/' and a '/home' the '/' only has to be around 3GB

I would suggest the second. Even when you chose to make a sepperate boot partition I would still suggest to make a sepperate home partition as well.

This all assuming you made one big root('/') partition.

Cheers,
Bart.

---

