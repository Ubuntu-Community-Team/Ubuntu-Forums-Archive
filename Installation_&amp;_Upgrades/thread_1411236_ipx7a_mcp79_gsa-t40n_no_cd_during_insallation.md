---
title: "ipx7a mcp79 gsa-t40n no cd during insallation"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by Emilianio on 2010-02-19
Hi, 

my dvdrom LG hl-dt-st GSA-T40N is not recognized during installation (motherboard prestigio ion nvidia mcp79 chipset). The last version that I was able to install using cdrom was 8.04 with boot option all_generic_ide. The cdrom works slowly!, but there was no driver for the graphic chipset (nv9400) for this old kernel version (nvidia 185 needed). So I updated to newer version.
I tried 8.10, 9.04, 9.10, alternate cd, dvd, burning with slow speed, changing the sata cable, changing the bios settings (sata ->ahci), boot options like all_generic_ide, ... everything that I found and all the combination. gsa-t40n still not working

The actual status is:

sudo lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.10
Release:    9.10
Codename:    karmic

sudo lshw
 *-cdrom
                description: SCSI CD-ROM
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio
                configuration: status=nodisc

dmesg |tail    with no media inserted
[ 4566.100294] ata2.00: status: { DRDY ERR }
[ 4566.102822] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 4566.102834] ata2.00: irq_stat 0x40000001
[ 4566.102861] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 4566.102865]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 4566.102869]          res 51/24:03:00:00:00/00:00:00:00:00/a0 Emask 0x1 (device error)
[ 4566.102880] ata2.00: status: { DRDY ERR }

dmesg |tail    with inserted media (ubuntu live CD)
[ 4680.398027] sr0: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[ 4680.398049] sr: Sense Key : Aborted Command [current] [descriptor]
[ 4680.398058] sr: Add. Sense: No additional sense information

sudo lshw with inserted cd
*-cdrom
                description: SCSI CD-ROM
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio
                configuration: status=ready

ready but no cd or dvd is working, not even simple audio, can't read contents on it, can't mount.

uname 
Linux desktop 2.6.31-20-generic

I updated to 9.10 using network (from 8.04), everything is working perfect (nvidia 185 graphic driver is fine, full HD ok), but the cdrom. The cdrom is working with microsoft vista (installed and removed), so it is probably not a hardware problem. I also tried pre-release 10.04 , and 2.6.32 in 9.10, no change. The computer is: prestigio ion ipx7a nv9400 mcp79

if there is some way to install some driver, patch, enable modules or so, please help me to find it
Why is the only one capability of the cdrom: audio ?

Thanks for your time
Emilianio

---

