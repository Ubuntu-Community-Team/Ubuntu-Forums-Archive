---
title: "IDE drive recognized as SCSI drive by Ubuntu"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by geek2330 on 2007-05-16
I have an IDE drive connected to the normal IDE channel on the mainboard.
Why Ubuntu treats/reads this drive as SCSI drive? It shows as sda, which is SCSI....:confused::confused:

Note that during install if I go to "Advance" to select the grub boot order it defaults as (hd0) but otherwise it shows sda in all other places...

---

### Post by logos34 on 2007-05-16
Grub designates all hard disks as 'hd0', 'hd1', and so on regardless of whether they're sata, pata, scsi, usb...

What's the output for 
sudo lshw -C disk

?

---

### Post by geek2330 on 2007-05-16
The output is:

[COLOR="Blue"]*-disk                  
       description: SCSI Disk
       product: WDC WD400BB-75DE
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 05.0
       serial: WD-WMAD1F219691
       size: 37GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume:0
          description: Linux filesystem partition
          physical id: 1
          bus info: scsi@0:0.0.0,1
          logical name: /dev/sda1
          capacity: 13GB
          capabilities: primary
     *-volume:1
          description: Linux filesystem partition
          physical id: 2
          bus info: scsi@0:0.0.0,2
          logical name: /dev/sda2
          capacity: 9538MB
          capabilities: primary
     *-volume:2
          description: W95 FAT32 partition
          physical id: 3
          bus info: scsi@0:0.0.0,3
          logical name: /dev/sda3
          capacity: 13GB
          capabilities: primary
     *-volume:3
          description: Linux swap / Solaris partition
          physical id: 4
          bus info: scsi@0:0.0.0,4
          logical name: /dev/sda4
          capacity: 956MB
          capabilities: primary nofs
  *-cdrom
       description: DVD reader
       product: XJ-HD166S
       vendor: JLMS
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: DS14
       capabilities: removable audio dvd
       configuration: ansiversion=5
     *-disc
          physical id: 0
          logical name: /dev/cdrom[/COLOR]

---

### Post by logos34 on 2007-05-16
That's odd.  Does your BIOS recognize it correctly?

Is it operating ok? You could try these commands:

sudo hdparm -i /dev/sda
sudo hdparm -tT /dev/sda

The latter will test the read/write speed.  You should be getting a sustainted rate of roughly 50 MB/s.  

Not sure why it's not showing up as hda.  Only if you had it connected via a usb enclosure should it appear as sda.

---

### Post by geek2330 on 2007-05-16
ok logos, here's the output from the first command:

[COLOR="Blue"]/dev/sda:

 Model=WDC WD400BB-75DEA0                      , FwRev=05.03E05, SerialNo=WD-WMAD1F219691
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=57600, SectSize=600, ECCbytes=40
 BuffType=DualPortCache, BuffSize=2048kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=78165360
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 udma5 udma3 udma4 udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5

 * signifies the current active mode[/COLOR]


and here's for the 2nd:
[COLOR="Blue"]
/dev/sda:
 Timing cached reads:   1298 MB in  2.00 seconds = 648.71 MB/sec
 Timing buffered disk reads:   82 MB in  3.03 seconds =  27.05 MB/sec[/COLOR]


This is odd, isn't it.....!!!!! It IS an IDE drive.
BTW - does the HD speed look ok, I guess it doesn't.....

.

---

### Post by logos34 on 2007-05-16
>  UDMA modes: udma0 udma1** *udma2** udma3 udma4 udma5 udma3 udma4 udma5
AdvancedPM=no WriteCache=enabled
Drive conforms to: Unspecified: ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5

* signifies the current active mode


and here's for the 2nd:

/dev/sda:
Timing cached reads: 1298 MB in 2.00 seconds = 648.71 MB/sec
Timing buffered disk reads: 82 MB in 3.03 seconds = 27.05 MB/sec

This is odd, isn't it.....!!!!! It IS an IDE drive.
BTW - does the HD speed look ok, I guess it doesn't.....

No, becuase it's apparently in udma2 mode...should be udma5 (my ata133 comes in around 54 MB/s).  Yeah, it's definitely and IDE/PATA drive, i have the specs right here.

---

### Post by logos34 on 2007-05-16
maybe you're using an older (slower) 40-pin ide cable or it's an older mobo that doesn't support udma 33/66/100/133?

---

### Post by logos34 on 2007-05-16
are you using 7.04 Feisty?  If so there seems to be a problem with some ide drives showing up as 'sdx' rather than 'hdx'. I haven't installed it yet so this is the first I've heard of it. (been on the road last few months with only windows machine so I've got some catching up to do).

check out these threads
[B]
[http://ubuntuforums.org/showthread.php?t=422336](http://ubuntuforums.org/showthread.php?t=422336)
[http://ubuntuforums.org/showthread.php?t=415057](http://ubuntuforums.org/showthread.php?t=415057)
[http://ubuntuforums.org/showthread.php?t=400356](http://ubuntuforums.org/showthread.php?t=400356)[/B]

---

### Post by geek2330 on 2007-05-16
Thanks for all the help logos.
I'm using Ubuntu with the KDE interface, so Kubuntu 7.04.

Anyways, will get a better/faster drive down the road....

Anyway to force it into udma5 mode ?? I will keep reading the other threads....

.

---

### Post by logos34 on 2007-05-16
> Anyway to force it into udm5 mode ??

not sure...you can check

/etc/hdparm.conf

but I think that's just for enablng/disabling dma, write-caching.  

good luck.

---

### Post by geek2330 on 2007-05-16
you know, something I must say that I forgot to mention.
Whenever I try to open any document from Terminal It throws an error even though the document opens just fine.

For example, I just opened the hdparm.conf using the above command, Terminal throws this:
[COLOR="Red"]
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device[/COLOR]

However the document opens fine......is that a clue for something wrong ??
The jumper on the HD is set to CS (cable select). A few hours ago I changed it to "Master" and tried to reload the OS, however it could NOT detect any settings for the HD when getting to the HD partition options (only "Guided" showed up but the next screen was just blank....no HD info at all so I had to cancel the install and revert back to cable select for the jumper, then I could install the OS).

The HD is using PRIMARY as Master. No other HD connected right now.
CD/DVD are on SECONDARY channel as master/slave.

.

Thanks for all the help..!!

---

### Post by logos34 on 2007-05-16
dunno about the error message.  you'll have to google it.

Not sure about the problem installing with jumper set as master unless the disk was plugged into the slave connector (gray, the middle one)

---

### Post by geek2330 on 2007-05-17
logos, I just happened to remove the jumper from the HDD, according to the specs no jumper is needed for a single HDD on the cable, now the read/write output is as follows:
[COLOR="Blue"]
/dev/sda:
 Timing cached reads:   1308 MB in  2.00 seconds = 653.41 MB/sec
 Timing buffered disk reads:  136 MB in  3.04 seconds =  44.71 MB/sec[/COLOR]

So there's an improvement. However Kubuntu still takes about 2 minutes or more to boot, it usually stays at the Kubuntu screen (right after "Starting up...." ) and the blue bar takes about 1min 45sec.

---

### Post by geek2330 on 2007-05-17
.....and now it looks like it is in udma5:

[COLOR="Blue"] UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 udma3 udma4 *udma5 [/COLOR]

---

### Post by logos34 on 2007-05-18
> **geek2330 said:**
> logos, I just happened to remove the jumper from the HDD, according to the specs no jumper is needed for a single HDD on the cable, now the read/write output is as follows:
[COLOR="Blue"]
/dev/sda:
 Timing cached reads:   1308 MB in  2.00 seconds = 653.41 MB/sec
 Timing buffered disk reads:  136 MB in  3.04 seconds =  44.71 MB/sec[/COLOR]

So there's an improvement. However Kubuntu still takes about 2 minutes or more to boot, it usually stays at the Kubuntu screen (right after "Starting up...." ) and the blue bar takes about 1min 45sec.

That's more like it.  (although it seems you should be up nearer to 50 MB/s in udma5 mode).  

Come to think of it one of my drives doesn't need the jumper either when it's the only one on the cable.

---

### Post by poe503 on 2007-05-27
You are not alone in having hda being recognized as sda. 

 I've installed Ubuntu  7.04 on an older computer, 1ghz p3, Asus cusl2-c motherboard.  The BIOS sets the IDE drive as udma5.  There is no SCSI system on this unit.

  The Ubuntu partition utility recognizes the IDE drive as SCSI. 

  I installed the same Ubuntu cd on my internet computer which is newer, 1.7ghz P4, and it correctly identifies hda as hda.  

Ubuntu works great on my newer computer but complains immediately about "crc error" and halts boot up on the older computer.

  These are both dual boot installations and Windows boots up just fine on the older computer.

---

### Post by vishnumrao on 2007-06-05
I too have the same problem. Just purchased a Hitachi 500 Gb Sata drive. , while my older Samsung IDE drive (my OS drive) is detected correctly.

Here is the output of   sudo lshw -C disk

*-disk
       description: SCSI Disk
       product: Hitachi HDS72505
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: K2AB
       serial: KRVN23ZAGETW7D
       size: 465GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume
          description: Linux filesystem partition
          physical id: 1
          bus info: scsi@0:0.0.0,1
          logical name: /dev/sda1
          capacity: 465GB
          capabilities: primary

Also Every time I boot into my machine, I have to put in my root password to access it. How do I fix the above two problems?

Thanks in advance.
vishnumrao.

---

### Post by pclark36 on 2007-12-08
I have IDE drives for my hard drive and my DVD/RW in my laptop. They both displayed as SCSI drives.  To fix it, on startup, when Grub pops up, I press Escape,  and on the newest Kernel, I edit the options, add a new line at the end that says
> hwprobe=-modules.pata

and all my drives started showing up and working correctly.

---

