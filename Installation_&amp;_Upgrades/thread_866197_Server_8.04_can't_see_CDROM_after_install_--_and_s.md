---
title: "Server 8.04 can't see CDROM after install -- and solution!"
date: 2008-07-21
forum: Installation &amp; Upgrades
---

### Post by Flash303 on 2008-07-21
After installing Ubuntu Server 8.04 from CDROM, I could not
access the CDROM/DVD after rebooting.   It turned out to be an
error in /etc/fstab which I think was caused by the motherboard
configuration.

Symptoms: "apt-cdrom add" could not find the CD/DVD drive.

Configuration:
  Gigabyte GA-MA69VM-S2 motherboard with four SATA connections
  and one IDE connection.
  Three SATA drives installed (in a RAID-1 configuration)
  One IDE CD/DVD drive: Lite-on DH-20A4P-04OEM 20x DVD Burner
  Ubuntu 8.04 32-bit Server Edition (CD from On-Disk.com)

Incorrect line from /etc/fstab:
  /dev/scd0  /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
  (Note the incorrect use of scd0, which is the unused fourth
  SATA port), not the IDE port.)

Corrected line from /etc/fstab:
  /dev/cdrom  /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

After making this correction "apt-cdrom add" worked OK.
I tried using /dev/hda but it didn't seem to work.  I don't know
why.

It appears that the installer is getting confused about where the
CD/DVD drive is located when there are SATA ports.   It shouldn't
be, as it is doing the install *from* that drive!   :-)

I hope that someone can forward this to the correct people to
fix this.   (Or let me know how to contact them!)   I would be
happy to provide any additional information if it would help
track down this problem (I kept a detailed log).

---

