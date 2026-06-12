---
title: "Dell Inspiron 3500 laptop install problem"
date: 2005-02-01
forum: Installation &amp; Upgrades
---

### Post by johnallengreen on 2005-02-01
Summary:
Are there any special boot arguments (or module parameters) required to install on Dell Inspiron 3500 Laptop?

Gory details:

I checked the ISO image MD5SUM, and I also tested the CD against md5sum.txt on the same machine where I'm trying to install Ubuntu. (Machine currently has FC3 installed.) All files on the CD MD5SUM check out OK - the CD and CD drive are fine.

I can run Ubuntu live, it only requires the boot argument "nodma".

I have also tried: nodma noscsi noapic nolapic aic7xxx=no_reset

- Select language, location, keyboard OK
- Detect and mount CD-ROM OK
- Unable to load some modules: agpgart, 3c59x, ide-mod, ide-probe-mod, ide-detect, ide-floppy
- I tried PCMCIA parameter: exclude port 0x800-0x8ff
- Detect and mount CD-ROM: hdparm to tune CD-ROM drive parameters (I leave blank - I wonder if I need something here?)
- Scanning CD-ROM - successful
- Load installer: There were problems reading data from the CDROM.

If I try to "Check the CD-ROM integrity", it doesn't even touch the CD before coming back with a report that the disk is not valid.

Thanks in advance,
John

---

### Post by johnallengreen on 2005-02-02
I got through this problem. Here's my workaround:

Boot with expert mode. Step through, but BEFORE "Detect and mount CD-ROM", switch to console with Alt-F2, and enter these two commands:
umount /cdrom
mount /dev/cdroms/cdrom0 /cdrom
Switch back with Alt-F1, and continue installation.

Actually, I used:
mount -r -t iso9660 /dev/cdroms/cdrom0 /cdrom -o nojoliet
...but I don't think any of that extra stuff made any difference.

The problem was that the first time the CD was mounted by the installer, the symbolic links in /dists were not there - as if the CD was being viewed under Windows. There were just a bunch of zero-length files there. Remounting the CD at the right time gets the symbolic links there.

I'm not sure what's going on in the installer to cause the CD to be mounted incorrectly. Here is some of the install log (copied by hand), in case it is helpful for the Ubuntu team:

cdrom-detect: Searching for Ubuntu installation media...
ide-cd: cmd 0x28 timed out
hdc: DMA interrupt recovery
hdc: lost interrupt
hdc: status error: status=0x58 { Drive Ready SeekComplete DataRequest }
hdc: status error: error=0x00
hdc: drive not ready for command
ide-cd: cmd 0x28 timed out
hdc: DMA interrupt recovery
hdc: lost interrupt
hdc: status timeout: status=0x00 { Busy }
hdc: status timeout: error=0x04Aborted Command
hdc: DMA disabled
hdc: drive not ready for command
hdc: ATAPI reset complete
ISO 9660 Extensions: Microsoft Joliet Level 3
cdrom-detect: Detected CD 'Ubuntu 4.10 "Warty Warthog" - Preview i386 Binary-1 (20041020)'

Regards,
John

---

### Post by Lord C on 2005-03-03
[QUOTE=johnallengreen]I got through this problem. Here's my workaround:

Boot with expert mode. Step through, but BEFORE "Detect and mount CD-ROM", switch to console with Alt-F2, and enter these two commands:
umount /cdrom
mount /dev/cdroms/cdrom0 /cdrom
Switch back with Alt-F1, and continue installation.
[/QUOTE]
 Unfortunetly this work-around doesn't work for me.
I still get the following error:

Unable to load some modules: amd76xrom ide-mod ide-probe-mod ide-detect ide-floppy

---

