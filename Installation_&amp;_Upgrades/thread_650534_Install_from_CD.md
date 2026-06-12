---
title: "Install from CD"
date: 2007-12-26
forum: Installation &amp; Upgrades
---

### Post by iClou on 2007-12-26
Hi

I tried to install Ubuntu 7.10 from CD.
Unfortunately I can not burn the ISO image to a 700MB CD because I get the error not enough space.
Is there a smaller image around or what else can I do?
--
Thanks for any hint
Best regards,
Mike

---

### Post by Pumalite on 2007-12-26
Install ImBurn: [http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)
Go to Mode>ISO
Stick a DVD and burn

---

### Post by iClou on 2007-12-27
Again
I need an image which I can burn on a CD for installing Ubuntu from it (not a DVD).

Although the official image is less than 700 MB I always get the error to less space on CD.
I use K3B.
Any idea how to install Ubuntu from a CD?
--
Thanks,
Mike

---

### Post by Pumalite on 2007-12-27
Thats very rare. Images are around 695 MB and they fit perfectly in a CD
Download from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Burn the iso to a CD as 'image'.
It should fit.

---

### Post by iClou on 2007-12-27
I did that but it does not fit on a CD (700MB, 80min).
Find following the output of ls -a

-rw-r--r--  1 <user> <user> 726663168 2007-12-26 17:20 ubuntu-7.10-alternate-i386.iso
-rw-r--r--  1 <user> <user> 729608192 2007-12-26 16:15 ubuntu-7.10-desktop-i386.iso

This explains why the image does not fit on a CD.
How can I burn that on a CD?
--
Any help is very much appreciated.
Thanks,
Mike

---

### Post by anregen on 2007-12-27
pumalite is right.  You must be sure to burn as ISO.  If you attempt to burn as data or similar, the OS will add additional info and put you over the 700MB limit.

also: 1,048,576 Bytes per MByte
729608192 Bytes / 1048576 ~= 696MB so it will fit.

using [FONT="Courier New"]ls -lh[/FONT] will display sizes in a more intuitive manner than just a pile of bytes.

---

### Post by iClou on 2007-12-29
I tried to burn it with K3B as CD ISO image but I always get the error message it does not fit on the CD.
I tried it with several CDs, but all from the same vendor: TDK CD-RW 16x-24x, 700 MB, 80MIN.

ls -lh:
-rw-r--r--  1 <user> <user> 693M 2007-12-26 17:20 ubuntu-7.10-alternate-i386.iso
-rw-r--r--  1 <user> <user> 696M 2007-12-26 16:15 ubuntu-7.10-desktop-i386.iso

Find following the debug output:
System
-----------------------
K3b Version: 1.0.3

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
PHILIPS DVD+-RW SDVD8412 LX07 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R16, RAW/R96R, Restricted Overwrite]

Used versions
-----------------------
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PHILIPS '
Identification : 'DVD+-RW SDVD8412'
Revision       : 'LX07'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x000A (CD-RW)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) (current)
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R16 RAW/R96R
Drive buf size : 1073152 = 1048 KB
FIFO size      : 12582912 = 12288 KB
Errno: 5 (Input/output error), start/stop unit scsi sendcmd: no error
CDB:  1B 00 00 00 01 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0B 00 00 00 00 09 01 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x09 Qual 0x01 (tracking servo failure) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 3.001s timeout 40s
Errno: 5 (Input/output error), start/stop unit scsi sendcmd: no error
CDB:  1B 00 00 00 01 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0B 00 00 00 00 09 01 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x09 Qual 0x01 (tracking servo failure) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 3.005s timeout 40s
/usr/bin/wodim: Cannot get next writable address for 'invisible' track.
/usr/bin/wodim: This means that we are checking recorded media.
/usr/bin/wodim: This media cannot be written in streaming mode anymore.
/usr/bin/wodim: If you like to write to 'preformatted' RW media, try to blank the media first.
/usr/bin/wodim: WARNING: Data may not fit on current disk.
/usr/bin/wodim: Notice: Use -overburn option to write more than the official disk capacity.
/usr/bin/wodim: Notice: Most CD-writers do overburning only on SAO or RAW mode.
Track 01: data   693 MB        
Total size:      795 MB (78:50.90) = 354818 sectors
Lout start:      796 MB (78:52/68) = 354818 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 0
  Reference speed: 0
  Is unrestricted
  Is erasable
  ATIP start of lead in:  -3150 (99:20/00)
  ATIP start of lead out: 299850 (66:40/00)
Disk type:    unknown dye (reserved id code)
Manuf. index: -1
Manufacturer: unknown (not in table)
Blocks total: 299852 Blocks current: 299852 Blocks remaining: -54966

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=24 -tao driveropts=burnfree -eject -multi -xa -tsize=354816s - 

Any idea what is wrong here?
--
Now I will buy other CDs;-)
Thanks,
Mike

---

### Post by Partyboi2 on 2007-12-29
what happens if you use another program to burn the iso to disk?

---

### Post by oldsoundguy on 2007-12-29
trust the other posters .. it DOES fit on a cd.  Using ANY burning program that allows BURNING OF AN IMAGE.  IF you try and burn it as data disk (ISO) it will NOT fit.

---

### Post by oldsoundguy on 2007-12-29
and it appears you may be trying to burn BOTH programs to ONE disk .. there is the ALTERNATE and the LIVE and they live on separate disks.

---

### Post by iClou on 2007-12-29
hey no.... I tried just both images;-)
With the new CDs everything is fine now!
Thanks for your help
Best regards,
Mike

---

