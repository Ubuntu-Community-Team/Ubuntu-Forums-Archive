---
title: "CD ROM Problems after upgrade to 6.06"
date: 2006-07-06
forum: Installation &amp; Upgrades
---

### Post by jerunamuck on 2006-07-06
PROBLEM:
Music CD ejects after ~1 minute no matter what I do or don't do.
Sound Jiucer opens on CD insert and populates title/track/artist but can't play.  Rips dead air until CD ejects then hangs as if it does not know media is no longer available.

XMMS sees tracks but plays nothing (dead air - static) until disk ejects of own accord then stops.
XMMS et al have no problem playing any of my existing MP3 / OGG / FLAC media on /dev/sda1

GRIP ripes dead air until CD ejects of own accord then complains media is unavailable......

While I can access a data CD and copy files from it I must complete the transaction before the media ejects of own accord.

HISTORY:
All these worked fine under BB but when I updated to DD via update manager it stopped working.  At first I thought it was the gstream0.8 vs gstream0.10 issue and unloaded all my gstreamer0.8 stuff to no avail.  Also tried setting DMA off for /dev/hda but that did not matter (was on - don't know status prior to update.  did not alter hdparm.config).

CONFIG:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0    1
/dev/sda1       /boot           ext3    defaults        0       2
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


jerome@muck:~$ sudo hdparm -I /dev/hda
Password:

/dev/hda:

ATAPI CD-ROM, with removable media
        Model Number:       Hewlett-Packard CD-Writer Plus 8000
        Serial Number:
        Firmware Revision:  2.5C
Standards:
        Likely used CD-ROM ATAPI-1
Configuration:
        DRQ response: 50us.
        Packet size: 12 bytes
Capabilities:
        LBA, IORDY(can be disabled)
        DMA: sdma0 sdma1 mdma0 *mdma1
             Cycle time: min=180ns recommended=180ns
        PIO: pio0 pio1 pio2 pio3
             Cycle time: no flow control=240ns  IORDY flow control=180ns
jerome@muck:~$


0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)

---

### Post by jerunamuck on 2006-07-08
curioser and curioser.

So just for fun I rebuilt my system from the Ubuntu 6.06 ALT CD.  
(Well that was painless)

The good news is that Sound Juicer can now play the Audio CD.
The bad news is that the CD ejects for no apparent reason after about 30 seconds or so.

Conclusions:
Looks like I hosed my gstreamer config while messing about.
Unfortunately, the CD eject problem persists and appears to be related to 6.06.  These were some posts in the bug list regarding 6.06 and DMA for CD devices, not sure if this is the case. 

I may (time permitting) install Breezy Badger and confirm the behavior stops.  This was not an issue until I updated to Dapper.  For now I'm calling this a repeatable BUG.

BUMP!
Would definately like some feed back on this for any user and/or developer.

Please!!!

](*,)

---

### Post by jerunamuck on 2006-07-11
Rolled back to Breezy Badger and the CD stopped ejecting.  This does not bode well for tht HP drive support in Dapper Drake.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Results for hdparm -I unchanged ( as if I expected something different )
Ditto lspci

---

### Post by jerunamuck on 2006-07-11
Ash-Fox suggested I review syslog for messages.  Also suggested mount verbose and see what I get.  Rebuilding to Dapper from the alt CD...

---

### Post by jerunamuck on 2006-07-11
Oh yea, forgot to check DMA settings under BB
sudo hdparm  /dev/hda
Password:

/dev/hda:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

Interesting, I remember seeing "using_dma = 1 (on)" under DD.  I followed a procedure in the wiki to turn it off but that did not matter.  Something else I'll need to re-investigate.

---

### Post by jerunamuck on 2006-07-11
For those of you following along at home.....

Forgot that VIA has problems honoring changes in dma settings without reboot.  So... altered hdparm.conf to disable dma for /dev/hda and rebooted in Dapper.  
Verified that the change took.
Jul 11 19:51:08 muck kernel: [4294673.556000]     ide0: BM-DMA at 0xa800-0xa807, BIOS settings: hda:DMA, hdb:pio
Jul 11 19:51:08 muck kernel: [4294674.350000] hda: Hewlett-Packard CD-Writer Plus 8000, ATAPI CD/DVD-ROM drive
Jul 11 19:51:08 muck kernel: [4294675.189000] hda: ATAPI 20X CD-ROM CD-R/RW drive, 2048kB Cache, DMA
Jul 11 19:51:08 muck kernel: [4294681.951000] hda: DMA disabled

Repeated music cd test and sure enough it ejected it self within about a minute or less. found this interesting tidbit in syslog corresponding to the time the disk ejected.
Jul 11 19:53:29 muck kernel: [4294839.642000] cdrom: dropping to single frame dma

---

### Post by jerunamuck on 2006-07-12
The good news is that the UPS dude arrived with my new video and DVD/RW
The bad news is that I never figured out what was with that HP CD Writer drive ejecting.

Installed the new IDVD186DL and the problem stopped happening.

Case Closed

---

### Post by floundered on 2007-02-07
See related issue at Launchpad:

[https://answers.launchpad.net/ubuntu/+ticket/3385](https://answers.launchpad.net/ubuntu/+ticket/3385)

---

