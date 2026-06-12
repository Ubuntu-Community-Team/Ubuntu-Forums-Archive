---
title: "A lot of errors in /var/log/messages: ata1: PIO error"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by HarryElFuerte on 2006-06-16
Here are the messages:

Jun 16 18:18:09 localhost syslogd 1.4.1#17ubuntu7: restart.
Jun 16 18:18:11 localhost kernel: [4295077.205000] ata1: PIO error
Jun 16 18:18:11 localhost kernel: [4295077.208000] ata1: PIO error
Jun 16 18:18:11 localhost kernel: [4295077.211000] ata1: PIO error
Jun 16 18:18:11 localhost kernel: [4295077.211000] sr: Current [descriptor]: sense key: Aborted Command
Jun 16 18:18:11 localhost kernel: [4295077.211000]     Additional sense: No additional sense information
Jun 16 18:18:11 localhost kernel: [4295077.214000] ata1: PIO error
Jun 16 18:18:11 localhost kernel: [4295077.217000] ata1: PIO error
Jun 16 18:18:11 localhost kernel: [4295077.220000] ata1: PIO error
Jun 16 18:18:11 localhost kernel: [4295077.220000] sr: Current [descriptor]: sense key: Aborted Command
Jun 16 18:18:11 localhost kernel: [4295077.220000]     Additional sense: No additional sense information
Jun 16 18:18:11 localhost kernel: [4295077.223000] ata1: PIO error
Jun 16 18:18:11 localhost kernel: [4295077.226000] ata1: PIO error
Jun 16 18:18:11 localhost kernel: [4295077.229000] ata1: PIO error
Jun 16 18:18:11 localhost kernel: [4295077.232000] ata1: PIO error
Jun 16 18:18:11 localhost kernel: [4295077.235000] ata1: PIO error
Jun 16 18:18:11 localhost kernel: [4295077.238000] ata1: PIO error
Jun 16 18:18:11 localhost kernel: [4295077.241000] ata1: PIO error
Jun 16 18:18:11 localhost kernel: [4295077.244000] ata1: PIO error
Jun 16 18:18:11 localhost kernel: [4295077.247000] ata1: PIO error
Jun 16 18:18:11 localhost kernel: [4295077.269000] ata1: PIO error
Jun 16 18:18:11 localhost kernel: [4295077.269000] ata1: no sense translation for error 0x20
Jun 16 18:18:11 localhost kernel: [4295077.269000] ata1: no sense translation for status: 0x51
Jun 16 18:18:11 localhost kernel: [4295077.272000] ata1: PIO error
Jun 16 18:18:11 localhost kernel: [4295077.275000] ata1: PIO error
Jun 16 18:18:11 localhost kernel: [4295077.275000] ata1: no sense translation for error 0x20
Jun 16 18:18:11 localhost kernel: [4295077.275000] ata1: no sense translation for status: 0x51
Jun 16 18:18:11 localhost kernel: [4295077.278000] ata1: PIO error
Jun 16 18:18:11 localhost kernel: [4295077.281000] ata1: PIO error
Jun 16 18:18:11 localhost kernel: [4295077.281000] ata1: no sense translation for error 0x20
Jun 16 18:18:11 localhost kernel: [4295077.281000] ata1: no sense translation for status: 0x51
Jun 16 18:18:11 localhost kernel: [4295077.281000] sr: Current [descriptor]: sense key: Medium Error
Jun 16 18:18:11 localhost kernel: [4295077.281000]     Additional sense: Unrecovered read error - auto reallocate 

And so on. Starting System Log Viewer hangs, because those errors come so frequently.

I had Ubuntu 5.10 installed and it worked fine. I upgraded to 6.06 and then I got these problems. I had problems with video (ATI monitor resolution) and audio as well, but now this seems the be the only remaining problem.

Thanks, Harri

---

### Post by HarryElFuerte on 2006-06-16
/var/log/kern.log says:

Jun 16 22:39:34 localhost kernel: [17184215.856000] ata1: PIO error
Jun 16 22:39:34 localhost kernel: [17184215.856000] ata1: no sense translation for error 0x20
Jun 16 22:39:34 localhost kernel: [17184215.856000] ata1: no sense translation for status: 0x51
Jun 16 22:39:34 localhost kernel: [17184215.856000] ata1: translated ATA stat/err 0x51/20 to SCSI SK/ASC/ASCQ 0x3/11/04
Jun 16 22:39:34 localhost kernel: [17184215.864000] ata1: PIO error
Jun 16 22:39:34 localhost kernel: [17184215.864000] ata1: no sense translation for error 0x20
Jun 16 22:39:34 localhost kernel: [17184215.864000] ata1: no sense translation for status: 0x51
Jun 16 22:39:34 localhost kernel: [17184215.864000] ata1: translated ATA stat/err 0x51/20 to SCSI SK/ASC/ASCQ 0x3/11/04
Jun 16 22:39:34 localhost kernel: [17184215.884000] sr0: CDROM (ioctl) error, command: <6>Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 00
Jun 16 22:39:34 localhost kernel: [17184215.884000] sr: Current [descriptor]: sense key: Medium Error
Jun 16 22:39:34 localhost kernel: [17184215.884000]     Additional sense: Unrecovered read error - auto reallocate failed
Jun 16 22:39:34 localhost kernel: [17184215.892000] ata1: PIO error
Jun 16 22:39:34 localhost kernel: [17184215.892000] ata1: no sense translation for error 0x20
Jun 16 22:39:34 localhost kernel: [17184215.892000] ata1: no sense translation for status: 0x51
Jun 16 22:39:34 localhost kernel: [17184215.892000] ata1: translated ATA stat/err 0x51/20 to SCSI SK/ASC/ASCQ 0x3/11/04
Jun 16 22:39:34 localhost kernel: [17184215.900000] ata1: PIO error
Jun 16 22:39:34 localhost kernel: [17184215.900000] ata1: no sense translation for error 0x20
Jun 16 22:39:34 localhost kernel: [17184215.900000] ata1: no sense translation for status: 0x51
Jun 16 22:39:34 localhost kernel: [17184215.900000] ata1: translated ATA stat/err 0x51/20 to SCSI SK/ASC/ASCQ 0x3/11/04

and so on.

---

### Post by HarryElFuerte on 2006-06-16
I found some evidence that kernel has a bug, which has been fixed in 2.6.17 or 2.6.16. Unfortunately 2.6.15 seems to be the latest for Ubuntu.

[http://lkml.org/lkml/2006/4/20/143](http://lkml.org/lkml/2006/4/20/143)

Is there any unofficial way to get 2.6.17 kernel for Ubuntu (without compiling it myself)?

---

### Post by bartuela on 2006-09-28
I confirm. Using 2.6.17 or 2.6.18 hand compiled th problem disappears.
I'll wait for a new kernel in Ubuntu if I would be certain that my data are kept safe on hard drive, but I'm not sure what those errors would imply.

I have a 
RAID bus controller: Intel Corporation 82801HR/HO/HH (ICH8R/DO/DH) SATA RAID Controller
and a WDC WD3200KS-75P sata 320GB hard drive

---

