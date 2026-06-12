---
title: "Installing ubuntu 13.10 in an old PC"
date: 2013-12-31
forum: Installation &amp; Upgrades
---

### Post by Ski_HolmaNM on 2013-12-31
I am rennovating an old pc by removing windows xp and installing ubuntu 11.10. I am encountering an issue due to the fact that there is no f2 for boot options or anything like that, Only the SCSI setup utility. How do I install ubuntu on the computer?
specs: Intel pentium 4 cpu and
two scsi hard discs.

Screenshots below of the whole scsi setup:
*could not get screenshot of the first display, reads as follows:
press ctrl-a for SCSISelect utility

No SCSI boot device found!

BIOS not installed!

*then it boots windows. I can take screenshots if needed.

Thanks in advance :)

---

### Post by mörgæs on 2014-01-01
[http://ubuntuforums.org/showthread.php?t=2130640](http://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by sudodus on 2014-01-01
> **mörgæs said:**
> [http://ubuntuforums.org/showthread.php?t=2130640](http://ubuntuforums.org/showthread.php?t=2130640)

+1

And please notice that Ubuntu 11.10 has passed end of life. It will receive no security updates, so please use a newer distro/flavour/version, that is still supported.

---

### Post by grahammechanical on 2014-01-01
Scsi is a method for interfacing a hard drive to a motherboard. The same as IDE and SATA are ways of interfacing hard drives to motherboards. What I find strange is the two messages: "no scsi boot device found" and "then it boots Windows." To me that seems to be a contradiction. Unless you are telling it boot from a SCSI hard disk that does not have an OS so the system loads the OS that is on the other SCSI hard disk. That would make sense.

You could try disconnecting both hard disks and then seeing if the machine will boot from the optical drive. It occurs to me that the optical drive may actually be the second SCSI device that you mention. If this is the case, then I ask: Do you have a Ubuntu install disk in the optical drive? Is it suitable for your CPU? 32bit or 64bit CPU? 32bit or 64bit Ubuntu?

Regards.

---

### Post by Ski_HolmaNM on 2014-01-01
Many thanks :) That worked perfectly.

---

