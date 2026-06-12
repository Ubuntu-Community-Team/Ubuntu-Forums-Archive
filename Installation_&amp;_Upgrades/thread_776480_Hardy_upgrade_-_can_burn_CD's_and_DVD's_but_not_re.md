---
title: "Hardy upgrade - can burn CD's and DVD's but not read"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by odin79 on 2008-04-30
Ok I'm trying one last time to fix my DVD. I just upgraded to Hardy from a fresh Gutsy install. Problem that I have now is that I can burn CD's and DVD's but I can't read them. AVI movies that play fine won't play from DVD (even though I can see the files). So the cd/dvd mounts, but won't read.

It worked fine in Gutsy and works fine i WinXP. I was told that this might have to with my dvd player entries in /dev/ lists as "cdrom1, dvd1" and so on instead of "cdrom, dvd"....

When I try to play the disc in VLC I get these errors: 

libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title:  
libdvdnav: DVD Serial Number: 
libdvdnav: DVD Title (Alternative):   ,  
libdvdnav: Unable to find map file '/home/richard/.dvdnav/.map'
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
[00000294] dvdread demuxer error: DVDRead cannot open source: /dev/scd0
[00000297] vcd access error: no movie tracks found
ioctl(): No medium found
[00000297] vcdx access error: error reading Info sector (150)
[00000297] access_file access error: file /dev/scd0 is empty, aborting
[00000304] main private error: cannot pre fill buffer
[00000307] cdda access error: could not read block 0 from disc


Anynoe got any ideas? And please don't tell me to get a new DVDRW please. The one I have is less than a year old and works fine!

Tnx!

---

### Post by Craigupdegrove on 2008-04-30
How did you get your DVD's to be read mine won't read but i can play dvd's to play and read if they were made before

---

### Post by odin79 on 2008-05-01
"can burn CD's and DVD's but I can't read them."

The DVD/CD is displayed on my desktop, and when I open it I can see all the files in there: But I can't open them!

---

### Post by LostInBrittany on 2008-05-01
I had no problem reading DVDs and CDs with Gutsy. Yesterday I did upgarde both my work laptop and my home desktop, and now both computers are unable to read DVDs or CDs, it says "unable to mount" as if not disk was inserted.

---

### Post by mad.man on 2008-07-15
I have the same problem since upgrading (with a new install) from Gutsy to Hardy. Did anyone here manage to solve it? Is it a problem with the new PATA Modules?

---

### Post by mdionne81 on 2008-08-05
I am unable to read any DVD's (manufactured, burned, or blank) but I am able to read all CD's fine.  My DVD-RW drive is a Sony DRU-710 and it was working fine until recently, today was the first time I had noticed.  Unable to mount location No media in the drive is the message I get.  Any suggestions would be great.

---

### Post by nadrach on 2008-08-09
I have a similar problem with playing DVD's with VLC. It says that it cannot open device /dev/scd0, to which /dev/cdrom, /dev/dvd, et al are  linked. I can play a DVD with Kaffeine (installed by default), but not with VLC (which I added after the initial install). I did not have this problem on an earlier install of Kubuntu Hardy on a laptop, only on a recent install on a desktop machine, but after a recent upgrade of VLC was propagated, I now have the same situation on both machines. My guess is that there is a permissions problem, which may also be the cause of the DVD/CD access difficulties reported in several threads (including this one). The permissions on /dev/scd0 are "brw-rw----+ root cdrom ...", and I cannot remember the significance of the "+" symbol, but this would appear to be the block device for a drive to which all other devices point. The lack of "rw" on the general category may be a problem ...

Any suggestions greatly appreciated.

---

### Post by dfmalh on 2008-08-22
Hi, I am experiencing the opposite... 

I have no problems reading CDs or DVDs, but I am having problems burning CDs and DVDs. I have tried K3B, Brasero and GnomeBaker. All burn the CD/DVD and gives me a successful burn "optput" and I can see that something was burned on the disk, but is shows up as blank when I put it back into my laptop.

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

### Post by dfmalh on 2008-08-27
Update...


My *cdrecord -version* output:

```

Cdrecord-yelling-line-to-tell-frontends-to-use-it-like-version 2.01.01a03-dvd 
Wodim 1.1.6
Copyright (C) 2006 Cdrkit suite contributors
Based on works from Joerg Schilling, Copyright (C) 1995-2006, J. Schilling
```

My *cdrecord --scanbus* output:

```

scsibus1:
	1,0,0	100) 'Slimtype' 'DVDRW SOSW-852S ' 'PRS9' Removable CD-ROM
	1,1,0	101) *
	1,2,0	102) *
	1,3,0	103) *
	1,4,0	104) *
	1,5,0	105) *
	1,6,0	106) *
	1,7,0	107) *
```


I get exactly the same outputs when I run wodim -version and wodim --scanbus.

I have no idea how to fix this problem. I tried diffent burners and they all give the same result, burned the CD, but afterwards although it looks like something is on the CD, it says empty.

Now when I insert a DVD into my drive it locks up, keeps spinning, and the only way to remove it, is to "hard" power on/off. 

This all started happening after a fresh install of Hardy, everything was working perfectly in Feisy :lolflag:

---

### Post by wpshooter on 2008-08-27
All of this seems to be yet another confirmation of my thoughts that Hardy is NOT ready for prime time.  

I will still be sticking to Gutsy, thank you.

---

