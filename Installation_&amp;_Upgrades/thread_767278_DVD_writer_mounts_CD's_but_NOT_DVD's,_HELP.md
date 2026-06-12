---
title: "DVD writer mounts CD's but NOT DVD's, HELP"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by Rubadubdub on 2008-04-25
Hi everyone,

(Before the upgrade everything worked)

I just upgraded to Hardy and everything is working, but for this problem.

I have 2 DVD drives a DVD reader and a writer. The reader functions normally, but the writer has issues since the upgrade.

If I insert a CD everything works normally, the CD mounts automatically. But when I insert a DVD nothing happens. I have to mount the DVD via a terminal to see the contents, and still then the DVD drive is not functioning like before the upgrade.

And burning a CD or DVD results in to errors from both K3B and Brasero. Here error logs from both programs are attached to the post.


The DVD drive part of my fstab is:
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec 0 0

and with "sudo lshw" I get the following information about my drives:
 *-cdrom:0
             description: DVD-RAM writer
             product: DVD-RAM GSA-H54L
             vendor: HL-DT-ST
             physical id: 2
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom2
             logical name: /dev/dvd2
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: 1.00
             serial: [HL-DT-STDVD-RAM GSA-H54L1.0007/02/22
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom2
        *-cdrom:1
             description: DVD reader
             product: DVD-ROM SD-M1612
             vendor: TOSHIBA
             physical id: 3
             bus info: scsi@1:0.1.0
             logical name: /dev/scd1
             logical name: /dev/sr1
             logical name: /media/cdrom1
             version: J806
             capabilities: removable audio dvd
             configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted status=ready

Does anybody have any Idea's how I can fix this.

HELP IS VERY MUCH APPRECIATED!!!!

Thanks in advanced for the solution.

---

### Post by Rubadubdub on 2008-04-26
bump

---

### Post by Rubadubdub on 2008-04-26
An additional problem is that once a video-DVD is mounted with my reader the eject-button does nothing. The only way to eject is via the right mouse button.

---

### Post by Rubadubdub on 2008-04-26
lshw gives me the following info about my DVD-drives:

id:	
cdrom:0
description: 	DVD-RAM writer
product: 	DVD-RAM GSA-H54L
vendor: 	HL-DT-ST
physical id: 	
2
bus info: 	
scsi@1:0.0.0
logical name: 	
/dev/cdrom2
logical name: 	
/dev/dvd2
logical name: 	
/dev/scd0
logical name: 	
/dev/sr0
version: 	1.00
serial: 	[HL-DT-STDVD-RAM GSA-H54L1.0007/02/22
capabilities: 	removable audio cd-r cd-rw dvd dvd-r dvd-ram
configuration:	
ansiversion	=	5
status	=	open
id:	
cdrom:1
description: 	DVD reader
product: 	DVD-ROM SD-M1612
vendor: 	TOSHIBA
physical id: 	
3
bus info: 	
scsi@1:0.1.0
logical name: 	
/dev/scd1
logical name: 	
/dev/sr1
version: 	J806
capabilities: 	removable audio dvd
configuration:	
ansiversion	=	5
status	=	open

---

### Post by Rubadubdub on 2008-04-26
And burning a CD or DVD results in to errors from both K3B and Brasero. Here error logs from both programs are attached to the post. 

Nobody has got an idea how to fix this?

anybody...?

---

### Post by odin79 on 2008-04-26
I also have problems with my DVD similar to the ones you are describing. Can't anybody help please?

---

### Post by Rubadubdub on 2008-04-27
I found out where the problem lies. And a way to fix it. I do not think this is definite sollution, but it is easy and it will do for now.

The problem with my DVD writer was, that it was using the wrong UDMA (UDMA4). According to my bios it should have been UDMA2.

What I read in this forum and several bugs submitted to launchpad this problem has existed since Feisty. It has to do with sata drivers (at least that is what I could find) taking over the ide devices.

The solution:

Adding the following to my boot grub solved my problems:
**all_generic_ide**

just pres alt+F2 and type the following:
gksudo gedit /boot/grub/menu.lst

find your "kernel" line and ad all_generic_ide like shown below:
**kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4fd2a7c6-a5b9-49c0-9488-88fbf7fa0983 ro quiet splash all_generic_ide**

Then just restart.

THis worked for me. I can now mount dvd's an burn cd's and dvd's again.

If there is a different solution or you know what the problem is with the sata drivers, please let me know.

I hope this info helps some of you.

---

### Post by LostInBrittany on 2008-05-01
I have the same problem, I'm going to try your fix.

EDIT

It hasn't worked for me... :(

Anybody has any idea ?

---

### Post by andydread on 2008-05-01
same here on 2 machines i tried.  This is show stopping.  
I tried the all_generic_ide on both the laptop and the pc 
both with DVD-ROM/CDRW Drives.  CDs mount fine. Data or Video 
DVDs that were burned with the same drives under Gutsy do not work
in Hardy.  When I click on the DVD drive after inserting i get 
 ```
Unable to mount location. No media in drive. 
```
Basically as it stands the DVDrom/CDRW drives are useless
with DVD media

---

### Post by LostInBrittany on 2008-05-02
I've tried in two computers, a laptop, upgraded from Gutsy, and a desktop freshly installed.

When I try to mount it I get :

```
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

In both computers, the line of /etc/fstab for the dvd drive is :

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

---

### Post by Rubadubdub on 2008-05-02
What do you get when you type "sudo hdparm -I /dev/scd0" in a terminal?

---

### Post by Longun on 2008-06-12
> **Rubadubdub said:**
> I found out where the problem lies. And a way to fix it. I do not think this is definite sollution, but it is easy and it will do for now.

The problem with my DVD writer was, that it was using the wrong UDMA (UDMA4). According to my bios it should have been UDMA2.

What I read in this forum and several bugs submitted to launchpad this problem has existed since Feisty. It has to do with sata drivers (at least that is what I could find) taking over the ide devices.

The solution:

Adding the following to my boot grub solved my problems:
**all_generic_ide**

just pres alt+F2 and type the following:
gksudo gedit /boot/grub/menu.lst

find your "kernel" line and ad all_generic_ide like shown below:
**kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4fd2a7c6-a5b9-49c0-9488-88fbf7fa0983 ro quiet splash all_generic_ide**

Then just restart.

THis worked for me. I can now mount dvd's an burn cd's and dvd's again.

If there is a different solution or you know what the problem is with the sata drivers, please let me know.

I hope this info helps some of you.

This work around worked great for me running Hardy.  Can now burn CD's again plus DVD's don't lock the CD Drive.  Thanks.

---

### Post by Momof9Blessings on 2008-06-14
> **Rubadubdub said:**
> What do you get when you type "sudo hdparm -I /dev/scd0" in a terminal?

This is what I get

/dev/scd0:

ATAPI CD-ROM, with removable media
	Model Number:       HL-DT-ST DVDRAM GMA-4082N               
	Serial Number:      K0165OC3811         
	Firmware Revision:  HQ04    
Standards:
	Likely used CD-ROM ATAPI-1
Configuration:
	DRQ response: 50us.
	Packet size: 12 bytes
Capabilities:
	LBA, IORDY(can be disabled)
	DMA: mdma0 mdma1 *mdma2 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
HW reset results:
	CBLID- below Vih
	Device num = 0


My mount error is - Unable to mount location, Can't mount file

it is not recognizing a cd

thank you,
Mom

---

### Post by Pumalite on 2008-06-14
What kernel are you running and have you updated with all your repos opened, especially backports?
Post:
uname -a

---

### Post by sebutler2 on 2008-07-08
I attempted the work around, but still no lock... I can burn cds just fine, but whenever I attempt to burn a dvd with any program it fails..

---

### Post by dfmalh on 2008-08-25
Hi, 

I have no problems reading CDs or DVDs, after they were burned. I have tried K3B, Brasero and GnomeBaker. All burn the CD/DVD and gives me a successful burn "optput" and I can see that something was burned on the disk, but is shows up as blank when I put it back into my laptop.

Any Ideas? I am new to this type of problem, everything was smooth sailing in Gutsy.

I also tried to Google this "/usr/bin/wodim: Warning: controller returns wrong page 3 for Ricoh Vendor Page page (30)"...but I was not very successful.

Here is my K3B log file:

```
System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-21-generic
Devices
-----------------------
Slimtype DVDRW SOSW-852S PRS9 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]

K3bIsoImager
-----------------------
mkisofs print size result: 97168 (199000064 bytes)
Pipe throughput: 199000064 bytes read, 199000064 bytes written.

Used versions
-----------------------
mkisofs: 1.1.6
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
/usr/bin/wodim: Warning: controller returns wrong page 3 for Ricoh Vendor Page page (30).
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'Slimtype'
Identification : 'DVDRW SOSW-852S '
Revision       : 'PRS9'
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
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1422080 = 1388 KB
FIFO size      : 12582912 = 12288 KB
/usr/bin/wodim: Warning: controller returns wrong page 3 for Ricoh Vendor Page page (30).
Speed set to 1764 KB/s
Track 01: data   189 MB        
Total size:      217 MB (21:35.60) = 97170 sectors
Lout start:      218 MB (21:37/45) = 97170 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 3
  Reference speed: 6
  Is not unrestricted
  Is erasable
  Disk sub type: High speed Rewritable (CAV) media (1)
  ATIP start of lead in:  -11745 (97:25/30)
  ATIP start of lead out: 359848 (79:59/73)
  1T speed low:  4 1T speed high: 10
  2T speed low:  4 2T speed high:  0 (reserved val  6)
  power mult factor: 1 5
  recommended erase/write power: 5
  A1 values: 24 1A D8
  A2 values: 26 B2 4A
Disk type:    Phase change
Manuf. index: 40
Manufacturer: INFODISC Technology Co., Ltd.
Blocks total: 359848 Blocks current: 359848 Blocks remaining: 262678
Starting to write CD/DVD at speed  10.0 in real TAO mode for multi session.
Last chance to quit, starting real write in  2 seconds.
   1 seconds.
   0 seconds. Operation starts.
/usr/bin/wodim: Warning: controller returns wrong page 3 for Ricoh Vendor Page page (30).
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Track 01:    0 of  189 MB written.
Track 01:    1 of  189 MB written (fifo 100%) [buf 100%]   2.7x.
Track 01:    2 of  189 MB written (fifo 100%) [buf 100%]  10.3x.
Track 01:    3 of  189 MB written (fifo 100%) [buf 100%]  10.6x.
Track 01:    4 of  189 MB written (fifo 100%) [buf 100%]  10.3x.

Track 01:    5 of  189 MB written (fifo 100%) [buf 100%]  10.6x.
Track 01:    6 of  189 MB written (fifo 100%) [buf 100%]  10.3x.
Track 01:    7 of  189 MB written (fifo 100%) [buf 100%]  10.6x.
Track 01:    8 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:    9 of  189 MB written (fifo 100%) [buf 100%]  10.6x.
Track 01:   10 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:   11 of  189 MB written (fifo 100%) [buf 100%]  10.5x.
Track 01:   12 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:   13 of  189 MB written (fifo 100%) [buf 100%]  10.5x.
Track 01:   14 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:   15 of  189 MB written (fifo 100%) [buf 100%]  10.5x.
Track 01:   16 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:   17 of  189 MB written (fifo 100%) [buf 100%]  10.5x.
Track 01:   18 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:   19 of  189 MB written (fifo 100%) [buf 100%]  10.5x.
Track 01:   20 of  189 MB written (fifo 100%) [buf 100%]  10.1x.
Track 01:   21 of  189 MB written (fifo 100%) [buf 100%]  10.4x.
Track 01:   22 of  189 MB written (fifo 100%) [buf 100%]  10.1x.
Track 01:   23 of  189 MB written (fifo 100%) [buf 100%]  10.4x.
Track 01:   24 of  189 MB written (fifo 100%) [buf 100%]  10.1x.
Track 01:   25 of  189 MB written (fifo 100%) [buf 100%]  10.4x.
Track 01:   26 of  189 MB written (fifo 100%) [buf 100%]  10.1x.
Track 01:   27 of  189 MB written (fifo 100%) [buf 100%]  10.4x.
Track 01:   28 of  189 MB written (fifo 100%) [buf 100%]  10.1x.
Track 01:   29 of  189 MB written (fifo 100%) [buf 100%]  10.4x.
Track 01:   30 of  189 MB written (fifo 100%) [buf 100%]  10.0x.
Track 01:   31 of  189 MB written (fifo 100%) [buf 100%]  10.3x.
Track 01:   32 of  189 MB written (fifo 100%) [buf 100%]  10.0x.
Track 01:   33 of  189 MB written (fifo 100%) [buf 100%]  10.3x.
Track 01:   34 of  189 MB written (fifo 100%) [buf 100%]  10.6x.
Track 01:   35 of  189 MB written (fifo 100%) [buf 100%]  10.3x.
Track 01:   36 of  189 MB written (fifo 100%) [buf 100%]  10.6x.
Track 01:   37 of  189 MB written (fifo 100%) [buf 100%]  10.3x.
Track 01:   38 of  189 MB written (fifo 100%) [buf 100%]  10.6x.
Track 01:   39 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:   40 of  189 MB written (fifo 100%) [buf 100%]  10.6x.
Track 01:   41 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:   42 of  189 MB written (fifo 100%) [buf 100%]  10.5x.
Track 01:   43 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:   44 of  189 MB written (fifo 100%) [buf 100%]  10.5x.
Track 01:   45 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:   46 of  189 MB written (fifo 100%) [buf 100%]  10.5x.
Track 01:   47 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:   48 of  189 MB written (fifo 100%) [buf 100%]  10.5x.
Track 01:   49 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:   50 of  189 MB written (fifo 100%) [buf 100%]  10.5x.
Track 01:   51 of  189 MB written (fifo 100%) [buf 100%]  10.1x.
Track 01:   52 of  189 MB written (fifo 100%) [buf 100%]  10.4x.
Track 01:   53 of  189 MB written (fifo 100%) [buf 100%]  10.1x.
Track 01:   54 of  189 MB written (fifo 100%) [buf 100%]  10.4x.
Track 01:   55 of  189 MB written (fifo 100%) [buf 100%]  10.1x.
Track 01:   56 of  189 MB written (fifo 100%) [buf 100%]  10.4x.
Track 01:   57 of  189 MB written (fifo 100%) [buf 100%]  10.1x.
Track 01:   58 of  189 MB written (fifo 100%) [buf 100%]  10.4x.
Track 01:   59 of  189 MB written (fifo 100%) [buf 100%]  10.1x.
Track 01:   60 of  189 MB written (fifo 100%) [buf 100%]  10.4x.
Track 01:   61 of  189 MB written (fifo 100%) [buf 100%]  10.0x.
Track 01:   62 of  189 MB written (fifo 100%) [buf 100%]  10.3x.
Track 01:   63 of  189 MB written (fifo 100%) [buf  99%]  10.0x.
Track 01:   64 of  189 MB written (fifo 100%) [buf 100%]  10.3x.
Track 01:   65 of  189 MB written (fifo 100%) [buf 100%]  10.6x.
Track 01:   66 of  189 MB written (fifo 100%) [buf  99%]  10.3x.
Track 01:   67 of  189 MB written (fifo 100%) [buf 100%]  10.6x.

Track 01:   68 of  189 MB written (fifo 100%) [buf 100%]  10.3x.
Track 01:   69 of  189 MB written (fifo 100%) [buf 100%]  10.6x.
Track 01:   70 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:   71 of  189 MB written (fifo 100%) [buf 100%]  10.6x.
Track 01:   72 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:   73 of  189 MB written (fifo 100%) [buf 100%]  10.5x.
Track 01:   74 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:   75 of  189 MB written (fifo 100%) [buf 100%]  10.5x.
Track 01:   76 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:   77 of  189 MB written (fifo 100%) [buf 100%]  10.5x.
Track 01:   78 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:   79 of  189 MB written (fifo 100%) [buf 100%]  10.5x.
Track 01:   80 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:   81 of  189 MB written (fifo 100%) [buf 100%]  10.5x.
Track 01:   82 of  189 MB written (fifo 100%) [buf 100%]  10.1x.
Track 01:   83 of  189 MB written (fifo 100%) [buf  99%]  10.4x.
Track 01:   84 of  189 MB written (fifo 100%) [buf 100%]  10.1x.
Track 01:   85 of  189 MB written (fifo 100%) [buf 100%]  10.4x.
Track 01:   86 of  189 MB written (fifo 100%) [buf 100%]  10.1x.
Track 01:   87 of  189 MB written (fifo 100%) [buf 100%]  10.4x.
Track 01:   88 of  189 MB written (fifo 100%) [buf 100%]  10.1x.
Track 01:   89 of  189 MB written (fifo 100%) [buf 100%]  10.4x.
Track 01:   90 of  189 MB written (fifo 100%) [buf 100%]  10.1x.
Track 01:   91 of  189 MB written (fifo 100%) [buf 100%]  10.4x.
Track 01:   92 of  189 MB written (fifo 100%) [buf 100%]  10.0x.
Track 01:   93 of  189 MB written (fifo 100%) [buf 100%]  10.3x.
Track 01:   94 of  189 MB written (fifo 100%) [buf 100%]  10.0x.
Track 01:   95 of  189 MB written (fifo 100%) [buf 100%]  10.3x.
Track 01:   96 of  189 MB written (fifo 100%) [buf 100%]  10.6x.
Track 01:   97 of  189 MB written (fifo 100%) [buf 100%]  10.3x.
Track 01:   98 of  189 MB written (fifo 100%) [buf 100%]  10.6x.
Track 01:   99 of  189 MB written (fifo 100%) [buf 100%]  10.3x.
Track 01:  100 of  189 MB written (fifo 100%) [buf 100%]  10.6x.
Track 01:  101 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:  102 of  189 MB written (fifo 100%) [buf 100%]  10.6x.
Track 01:  103 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:  104 of  189 MB written (fifo 100%) [buf 100%]  10.5x.
Track 01:  105 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:  106 of  189 MB written (fifo 100%) [buf 100%]  10.5x.
Track 01:  107 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:  108 of  189 MB written (fifo 100%) [buf 100%]  10.5x.
Track 01:  109 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:  110 of  189 MB written (fifo 100%) [buf 100%]  10.5x.
Track 01:  111 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:  112 of  189 MB written (fifo 100%) [buf 100%]  10.5x.
Track 01:  113 of  189 MB written (fifo 100%) [buf 100%]  10.1x.
Track 01:  114 of  189 MB written (fifo 100%) [buf 100%]  10.4x.
Track 01:  115 of  189 MB written (fifo 100%) [buf 100%]  10.1x.
Track 01:  116 of  189 MB written (fifo 100%) [buf 100%]  10.4x.
Track 01:  117 of  189 MB written (fifo 100%) [buf 100%]  10.1x.
Track 01:  118 of  189 MB written (fifo 100%) [buf 100%]  10.4x.
Track 01:  119 of  189 MB written (fifo 100%) [buf 100%]  10.1x.
Track 01:  120 of  189 MB written (fifo 100%) [buf 100%]  10.4x.
Track 01:  121 of  189 MB written (fifo 100%) [buf 100%]  10.1x.
Track 01:  122 of  189 MB written (fifo 100%) [buf 100%]  10.4x.
Track 01:  123 of  189 MB written (fifo 100%) [buf 100%]  10.0x.
Track 01:  124 of  189 MB written (fifo 100%) [buf 100%]  10.3x.
Track 01:  125 of  189 MB written (fifo 100%) [buf 100%]  10.0x.
Track 01:  126 of  189 MB written (fifo 100%) [buf 100%]  10.3x.
Track 01:  127 of  189 MB written (fifo 100%) [buf 100%]  10.6x.
Track 01:  128 of  189 MB written (fifo 100%) [buf 100%]  10.3x.
Track 01:  129 of  189 MB written (fifo 100%) [buf 100%]  10.6x.
Track 01:  130 of  189 MB written (fifo 100%) [buf 100%]  10.3x.

Track 01:  131 of  189 MB written (fifo 100%) [buf 100%]  10.6x.
Track 01:  132 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:  133 of  189 MB written (fifo 100%) [buf 100%]  10.6x.
Track 01:  134 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:  135 of  189 MB written (fifo 100%) [buf 100%]  10.5x.
Track 01:  136 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:  137 of  189 MB written (fifo 100%) [buf 100%]  10.5x.
Track 01:  138 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:  139 of  189 MB written (fifo 100%) [buf 100%]  10.5x.
Track 01:  140 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:  141 of  189 MB written (fifo 100%) [buf 100%]  10.5x.
Track 01:  142 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:  143 of  189 MB written (fifo 100%) [buf 100%]  10.5x.
Track 01:  144 of  189 MB written (fifo 100%) [buf 100%]  10.1x.
Track 01:  145 of  189 MB written (fifo 100%) [buf 100%]  10.4x.
Track 01:  146 of  189 MB written (fifo 100%) [buf  99%]  10.1x.
Track 01:  147 of  189 MB written (fifo 100%) [buf 100%]  10.4x.
Track 01:  148 of  189 MB written (fifo 100%) [buf 100%]  10.1x.
Track 01:  149 of  189 MB written (fifo 100%) [buf 100%]  10.4x.
Track 01:  150 of  189 MB written (fifo 100%) [buf 100%]  10.1x.
Track 01:  151 of  189 MB written (fifo 100%) [buf 100%]  10.4x.
Track 01:  152 of  189 MB written (fifo 100%) [buf 100%]  10.1x.
Track 01:  153 of  189 MB written (fifo 100%) [buf 100%]  10.4x.
Track 01:  154 of  189 MB written (fifo 100%) [buf 100%]  10.0x.
Track 01:  155 of  189 MB written (fifo 100%) [buf 100%]  10.3x.
Track 01:  156 of  189 MB written (fifo 100%) [buf 100%]  10.0x.
Track 01:  157 of  189 MB written (fifo 100%) [buf 100%]  10.3x.
Track 01:  158 of  189 MB written (fifo 100%) [buf 100%]  10.6x.
Track 01:  159 of  189 MB written (fifo 100%) [buf 100%]  10.3x.
Track 01:  160 of  189 MB written (fifo 100%) [buf 100%]  10.6x.
Track 01:  161 of  189 MB written (fifo 100%) [buf 100%]  10.3x.
Track 01:  162 of  189 MB written (fifo 100%) [buf 100%]  10.6x.
Track 01:  163 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:  164 of  189 MB written (fifo 100%) [buf 100%]  10.6x.
Track 01:  165 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:  166 of  189 MB written (fifo 100%) [buf 100%]  10.5x.
Track 01:  167 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:  168 of  189 MB written (fifo 100%) [buf 100%]  10.5x.
Track 01:  169 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:  170 of  189 MB written (fifo 100%) [buf 100%]  10.5x.
Track 01:  171 of  189 MB written (fifo 100%) [buf  99%]  10.2x.
Track 01:  172 of  189 MB written (fifo 100%) [buf 100%]  10.5x.
Track 01:  173 of  189 MB written (fifo 100%) [buf 100%]  10.2x.
Track 01:  174 of  189 MB written (fifo 100%) [buf 100%]  10.5x.
Track 01:  175 of  189 MB written (fifo 100%) [buf 100%]  10.1x.
Track 01:  176 of  189 MB written (fifo 100%) [buf 100%]  10.4x.
Track 01:  177 of  189 MB written (fifo 100%) [buf 100%]  10.1x.
Track 01:  178 of  189 MB written (fifo 100%) [buf 100%]  10.4x.
Track 01:  179 of  189 MB written (fifo 100%) [buf 100%]  10.1x.
Track 01:  180 of  189 MB written (fifo 100%) [buf 100%]  10.4x.
Track 01:  181 of  189 MB written (fifo 100%) [buf 100%]  10.1x.
Track 01:  182 of  189 MB written (fifo 100%) [buf 100%]  10.4x.
Track 01:  183 of  189 MB written (fifo 100%) [buf 100%]  10.1x.
Track 01:  184 of  189 MB written (fifo 100%) [buf 100%]  10.4x.
Track 01:  185 of  189 MB written (fifo 100%) [buf 100%]  10.0x.
Track 01:  186 of  189 MB written (fifo 100%) [buf 100%]  10.3x.
Track 01:  187 of  189 MB written (fifo 100%) [buf 100%]  10.0x.
Track 01:  188 of  189 MB written (fifo 100%) [buf 100%]  10.3x.
Track 01:  189 of  189 MB written (fifo 100%) [buf 100%]  10.6x.
Track 01: Total bytes read/written: 199000064/199000064 (97168 sectors).
Writing  time:  150.400s
Average write speed   9.5x.
Min drive buffer fill was 99%
Fixating...
Fixating time:   33.739s
/usr/bin/wodim: Warning: controller returns wrong page 3 for Ricoh Vendor Page page (30).
/usr/bin/wodim: fifo had 3135 puts and 3135 gets.
/usr/bin/wodim: fifo was 0 times empty and 2929 times full, min fill was 96%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=10 -tao driveropts=burnfree -overburn -multi -xa -tsize=97168s - 

mkisofs
-----------------------
97168
I: -input-charset not specified, using utf-8 (detected in locale settings)
Using KENDO_FUNDAMENTALS_VOLUM000.PDF;1 for  /Kendo Fundamentals Volume I.pdf (Kendo Fundamentals Volume II.pdf)
  0.53% done, estimate finish Thu Aug 21 16:32:11 2008
  1.04% done, estimate finish Thu Aug 21 16:27:30 2008
  1.55% done, estimate finish Thu Aug 21 16:26:59 2008
  2.07% done, estimate finish Thu Aug 21 16:25:53 2008
  2.58% done, estimate finish Thu Aug 21 16:25:15 2008
  3.09% done, estimate finish Thu Aug 21 16:24:50 2008
  3.61% done, estimate finish Thu Aug 21 16:24:31 2008
  4.13% done, estimate finish Thu Aug 21 16:24:17 2008
  4.64% done, estimate finish Thu Aug 21 16:24:07 2008
  5.15% done, estimate finish Thu Aug 21 16:23:58 2008
  5.66% done, estimate finish Thu Aug 21 16:23:51 2008
  6.19% done, estimate finish Thu Aug 21 16:23:45 2008
  6.70% done, estimate finish Thu Aug 21 16:28:24 2008
  7.21% done, estimate finish Thu Aug 21 16:27:59 2008
  7.72% done, estimate finish Thu Aug 21 16:27:51 2008
  8.25% done, estimate finish Thu Aug 21 16:27:44 2008
  8.76% done, estimate finish Thu Aug 21 16:27:26 2008
  9.27% done, estimate finish Thu Aug 21 16:27:21 2008
  9.78% done, estimate finish Thu Aug 21 16:27:17 2008
 10.31% done, estimate finish Thu Aug 21 16:27:02 2008
 10.82% done, estimate finish Thu Aug 21 16:26:59 2008
 11.33% done, estimate finish Thu Aug 21 16:26:57 2008
 11.84% done, estimate finish Thu Aug 21 16:26:45 2008
 12.37% done, estimate finish Thu Aug 21 16:26:43 2008
 12.88% done, estimate finish Thu Aug 21 16:26:41 2008
 13.39% done, estimate finish Thu Aug 21 16:26:32 2008
 13.90% done, estimate finish Thu Aug 21 16:26:31 2008
 14.42% done, estimate finish Thu Aug 21 16:26:29 2008
 14.93% done, estimate finish Thu Aug 21 16:26:21 2008
 15.44% done, estimate finish Thu Aug 21 16:26:21 2008
 15.95% done, estimate finish Thu Aug 21 16:26:20 2008
 16.48% done, estimate finish Thu Aug 21 16:26:13 2008
 16.99% done, estimate finish Thu Aug 21 16:26:12 2008
 17.50% done, estimate finish Thu Aug 21 16:26:12 2008
 18.01% done, estimate finish Thu Aug 21 16:26:06 2008
 18.54% done, estimate finish Thu Aug 21 16:26:05 2008
 19.05% done, estimate finish Thu Aug 21 16:26:05 2008
 19.56% done, estimate finish Thu Aug 21 16:26:00 2008
 20.07% done, estimate finish Thu Aug 21 16:26:00 2008
 20.60% done, estimate finish Thu Aug 21 16:26:00 2008
 21.11% done, estimate finish Thu Aug 21 16:25:55 2008
 21.62% done, estimate finish Thu Aug 21 16:25:55 2008
 22.13% done, estimate finish Thu Aug 21 16:25:55 2008
 22.66% done, estimate finish Thu Aug 21 16:25:50 2008
 23.17% done, estimate finish Thu Aug 21 16:25:50 2008
 23.68% done, estimate finish Thu Aug 21 16:25:51 2008
 24.19% done, estimate finish Thu Aug 21 16:25:47 2008
 24.71% done, estimate finish Thu Aug 21 16:25:47 2008
 25.23% done, estimate finish Thu Aug 21 16:25:47 2008
 25.74% done, estimate finish Thu Aug 21 16:25:43 2008
 26.25% done, estimate finish Thu Aug 21 16:25:43 2008
 26.77% done, estimate finish Thu Aug 21 16:25:44 2008
 27.28% done, estimate finish Thu Aug 21 16:25:40 2008
 27.79% done, estimate finish Thu Aug 21 16:25:40 2008
 28.30% done, estimate finish Thu Aug 21 16:25:41 2008
 28.83% done, estimate finish Thu Aug 21 16:25:37 2008
 29.34% done, estimate finish Thu Aug 21 16:25:38 2008
 29.85% done, estimate finish Thu Aug 21 16:25:35 2008
 30.36% done, estimate finish Thu Aug 21 16:25:35 2008
 30.89% done, estimate finish Thu Aug 21 16:25:35 2008
 31.40% done, estimate finish Thu Aug 21 16:25:36 2008
 31.91% done, estimate finish Thu Aug 21 16:25:33 2008
 32.42% done, estimate finish Thu Aug 21 16:25:33 2008
 32.95% done, estimate finish Thu Aug 21 16:25:33 2008
 33.46% done, estimate finish Thu Aug 21 16:25:31 2008
 33.97% done, estimate finish Thu Aug 21 16:25:31 2008
 34.48% done, estimate finish Thu Aug 21 16:25:32 2008
 34.99% done, estimate finish Thu Aug 21 16:25:29 2008
 35.52% done, estimate finish Thu Aug 21 16:25:29 2008
 36.03% done, estimate finish Thu Aug 21 16:25:30 2008
 36.54% done, estimate finish Thu Aug 21 16:25:27 2008
 37.05% done, estimate finish Thu Aug 21 16:25:28 2008
 37.58% done, estimate finish Thu Aug 21 16:25:28 2008
 38.09% done, estimate finish Thu Aug 21 16:25:26 2008
 38.60% done, estimate finish Thu Aug 21 16:25:26 2008
 39.11% done, estimate finish Thu Aug 21 16:25:27 2008
 39.64% done, estimate finish Thu Aug 21 16:25:24 2008
 40.15% done, estimate finish Thu Aug 21 16:25:25 2008
 40.66% done, estimate finish Thu Aug 21 16:25:25 2008
 41.17% done, estimate finish Thu Aug 21 16:25:23 2008
 41.70% done, estimate finish Thu Aug 21 16:25:24 2008
 42.21% done, estimate finish Thu Aug 21 16:25:22 2008
 42.72% done, estimate finish Thu Aug 21 16:25:22 2008
 43.23% done, estimate finish Thu Aug 21 16:25:22 2008
 43.75% done, estimate finish Thu Aug 21 16:25:23 2008
 44.26% done, estimate finish Thu Aug 21 16:25:21 2008
 44.78% done, estimate finish Thu Aug 21 16:25:21 2008
 45.29% done, estimate finish Thu Aug 21 16:25:22 2008
 45.81% done, estimate finish Thu Aug 21 16:25:20 2008
 46.32% done, estimate finish Thu Aug 21 16:25:20 2008
 46.83% done, estimate finish Thu Aug 21 16:25:19 2008
 47.34% done, estimate finish Thu Aug 21 16:25:19 2008
 47.87% done, estimate finish Thu Aug 21 16:25:19 2008
 48.38% done, estimate finish Thu Aug 21 16:25:18 2008
 48.89% done, estimate finish Thu Aug 21 16:25:18 2008
 49.40% done, estimate finish Thu Aug 21 16:25:18 2008
 49.93% done, estimate finish Thu Aug 21 16:25:19 2008
 50.44% done, estimate finish Thu Aug 21 16:25:17 2008
 50.95% done, estimate finish Thu Aug 21 16:25:18 2008
 51.46% done, estimate finish Thu Aug 21 16:25:16 2008
 51.99% done, estimate finish Thu Aug 21 16:25:16 2008
 52.50% done, estimate finish Thu Aug 21 16:25:17 2008
 53.01% done, estimate finish Thu Aug 21 16:25:15 2008
 53.52% done, estimate finish Thu Aug 21 16:25:16 2008
 54.05% done, estimate finish Thu Aug 21 16:25:16 2008
 54.56% done, estimate finish Thu Aug 21 16:25:16 2008
 55.07% done, estimate finish Thu Aug 21 16:25:15 2008
 55.58% done, estimate finish Thu Aug 21 16:25:15 2008
 56.10% done, estimate finish Thu Aug 21 16:25:14 2008
 56.61% done, estimate finish Thu Aug 21 16:25:14 2008
 57.12% done, estimate finish Thu Aug 21 16:25:15 2008
 57.64% done, estimate finish Thu Aug 21 16:25:13 2008
 58.16% done, estimate finish Thu Aug 21 16:25:14 2008
 58.67% done, estimate finish Thu Aug 21 16:25:14 2008
 59.18% done, estimate finish Thu Aug 21 16:25:13 2008
 59.69% done, estimate finish Thu Aug 21 16:25:13 2008
 60.22% done, estimate finish Thu Aug 21 16:25:13 2008
 60.73% done, estimate finish Thu Aug 21 16:25:12 2008
 61.24% done, estimate finish Thu Aug 21 16:25:12 2008
 61.75% done, estimate finish Thu Aug 21 16:25:13 2008
 62.28% done, estimate finish Thu Aug 21 16:25:13 2008
 62.79% done, estimate finish Thu Aug 21 16:25:12 2008
 63.30% done, estimate finish Thu Aug 21 16:25:12 2008
 63.81% done, estimate finish Thu Aug 21 16:25:11 2008
 64.34% done, estimate finish Thu Aug 21 16:25:11 2008
 64.85% done, estimate finish Thu Aug 21 16:25:12 2008
 65.36% done, estimate finish Thu Aug 21 16:25:10 2008
 65.87% done, estimate finish Thu Aug 21 16:25:11 2008
 66.40% done, estimate finish Thu Aug 21 16:25:11 2008
 66.91% done, estimate finish Thu Aug 21 16:25:10 2008
 67.42% done, estimate finish Thu Aug 21 16:25:10 2008
 67.93% done, estimate finish Thu Aug 21 16:25:11 2008
 68.45% done, estimate finish Thu Aug 21 16:25:11 2008
 68.96% done, estimate finish Thu Aug 21 16:25:10 2008
 69.47% done, estimate finish Thu Aug 21 16:25:10 2008
 69.98% done, estimate finish Thu Aug 21 16:25:09 2008
 70.51% done, estimate finish Thu Aug 21 16:25:09 2008
 71.02% done, estimate finish Thu Aug 21 16:25:10 2008
 71.53% done, estimate finish Thu Aug 21 16:25:09 2008
 72.04% done, estimate finish Thu Aug 21 16:25:09 2008
 72.57% done, estimate finish Thu Aug 21 16:25:09 2008
 73.08% done, estimate finish Thu Aug 21 16:25:10 2008
 73.59% done, estimate finish Thu Aug 21 16:25:09 2008
 74.10% done, estimate finish Thu Aug 21 16:25:09 2008
 74.63% done, estimate finish Thu Aug 21 16:25:09 2008
 75.14% done, estimate finish Thu Aug 21 16:25:08 2008
 75.65% done, estimate finish Thu Aug 21 16:25:09 2008
 76.16% done, estimate finish Thu Aug 21 16:25:08 2008
 76.69% done, estimate finish Thu Aug 21 16:25:08 2008
 77.20% done, estimate finish Thu Aug 21 16:25:08 2008
 77.71% done, estimate finish Thu Aug 21 16:25:08 2008
 78.22% done, estimate finish Thu Aug 21 16:25:08 2008
 78.75% done, estimate finish Thu Aug 21 16:25:08 2008
 79.26% done, estimate finish Thu Aug 21 16:25:07 2008
 79.77% done, estimate finish Thu Aug 21 16:25:07 2008
 80.28% done, estimate finish Thu Aug 21 16:25:07 2008
 80.80% done, estimate finish Thu Aug 21 16:25:07 2008
 81.31% done, estimate finish Thu Aug 21 16:25:07 2008
 81.82% done, estimate finish Thu Aug 21 16:25:07 2008
 82.33% done, estimate finish Thu Aug 21 16:25:06 2008
 82.86% done, estimate finish Thu Aug 21 16:25:07 2008
 83.37% done, estimate finish Thu Aug 21 16:25:07 2008
 83.88% done, estimate finish Thu Aug 21 16:25:06 2008
 84.39% done, estimate finish Thu Aug 21 16:25:06 2008
 84.92% done, estimate finish Thu Aug 21 16:25:07 2008
 85.43% done, estimate finish Thu Aug 21 16:25:06 2008
 85.94% done, estimate finish Thu Aug 21 16:25:06 2008
 86.45% done, estimate finish Thu Aug 21 16:25:06 2008
 86.98% done, estimate finish Thu Aug 21 16:25:05 2008
 87.49% done, estimate finish Thu Aug 21 16:25:06 2008
 88.00% done, estimate finish Thu Aug 21 16:25:06 2008
 88.51% done, estimate finish Thu Aug 21 16:25:05 2008
 89.04% done, estimate finish Thu Aug 21 16:25:05 2008
 89.55% done, estimate finish Thu Aug 21 16:25:06 2008
 90.06% done, estimate finish Thu Aug 21 16:25:05 2008
 90.57% done, estimate finish Thu Aug 21 16:25:05 2008
 91.09% done, estimate finish Thu Aug 21 16:25:05 2008
 91.61% done, estimate finish Thu Aug 21 16:25:05 2008
 92.12% done, estimate finish Thu Aug 21 16:25:05 2008
 92.63% done, estimate finish Thu Aug 21 16:25:05 2008
 93.15% done, estimate finish Thu Aug 21 16:25:04 2008
 93.66% done, estimate finish Thu Aug 21 16:25:05 2008
 94.17% done, estimate finish Thu Aug 21 16:25:05 2008
 94.68% done, estimate finish Thu Aug 21 16:25:04 2008
 95.21% done, estimate finish Thu Aug 21 16:25:04 2008
 95.72% done, estimate finish Thu Aug 21 16:25:05 2008
 96.23% done, estimate finish Thu Aug 21 16:25:04 2008
 96.74% done, estimate finish Thu Aug 21 16:25:04 2008
 97.27% done, estimate finish Thu Aug 21 16:25:04 2008
 97.78% done, estimate finish Thu Aug 21 16:25:04 2008
 98.29% done, estimate finish Thu Aug 21 16:25:04 2008
 98.80% done, estimate finish Thu Aug 21 16:25:04 2008
 99.33% done, estimate finish Thu Aug 21 16:25:03 2008
 99.84% done, estimate finish Thu Aug 21 16:25:04 2008
Total translation table size: 0
Total rockridge attributes bytes: 376
Total directory bytes: 578
Path table size(bytes): 10
Max brk space used 0
97168 extents written (189 MB)

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid Kendo -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-danie/k3bsfL08b.tmp -rational-rock -hide-list /tmp/kde-danie/k3bJT2E7a.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-danie/k3baqzsDa.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-danie/k3bK8aNba.tmp 

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid Kendo -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-danie/k3bz1gi3b.tmp -rational-rock -hide-list /tmp/kde-danie/k3bCbTbga.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-danie/k3bzX7Ida.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-danie/k3bzmPQvb.tmp
```



Thanks, any help will be greatly appreciated!

---

### Post by dfmalh on 2008-08-26
Update...

Now I can't read a DVD... the drive "locks" and just keeps spinning. The only way out of this is to "hard reset/shutdown" and remove the CD/DVD from  the drive :confused:

Any help, anybody"

---

### Post by Thievrey Corporation on 2008-09-06
Hi,

I am having the same kinf of problems.
I have a CD reader/writer and a DVD reader/writer.
Whenever I insert a CD into DVD writer, it is recognized by Brasero.
But when I insert a DVD, Brasero gives me only the option to burn with the CD writer ....
And also, when the CD is inserted into DVD burner, it spins with high speed and the only way to stop it is to turn off the DVD writer.

I'll try solution proposed above and let you know.

---

### Post by Pumalite on 2008-09-06
Try different setting in the BIOS.

---

### Post by Thievrey Corporation on 2008-09-06
It worked for me, thanks to the solution proposed by Rudadubdub.
By the way, I am using Ubuntu 8.04.
I got an error at the end of the burning process on DVD, but I guess it is not related to the problem we are dealing with in this thread.

---

### Post by dfmalh on 2008-09-06
Hi, I also "fixed" my problem by down-grading to Gutsy. Now everyting is burning again... 

It must be someting todo with the update of the kernel.

Hope this problem is solved.

---

