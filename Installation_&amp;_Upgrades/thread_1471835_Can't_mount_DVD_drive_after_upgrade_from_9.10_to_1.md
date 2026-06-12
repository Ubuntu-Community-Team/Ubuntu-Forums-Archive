---
title: "Can't mount DVD drive after upgrade from 9.10 to 10.04"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by stegouin on 2010-05-03
I have an LG DVD+RW and an older DVD drive...FSTAB contains the following:
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

I see a cdrom0 in "Places", but get the following error when access:

"Unable to mount cdrom0. mount: no medium found on /dev/sr0"

I do see the following mount points in the filesystem under media:

/media/cdrom0
/media/cdrom1

Any ideas? I assum my fstab entry is incorrect... not sure how to resolve though. I'd like to get my DVD+RW working, so I can burn a Live CD and re-install from scratch instead of upgrade.

Thanks for the help

---

### Post by stegouin on 2010-05-04
This is frustrating... if anyone can offer some assistance, I'd appreciate it... I've search the forums, and found some older posts suggesting a few things, but so far, no luck in Ubuntu mounting my DVD burner.

I have some aditional info if it cn help:

```

 *-disk                  
       description: ATA Disk
       product: ST3500630AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       version: 3.AA
       serial: 5QG1A74D
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=c29835b7
  *-disk
       description: ATA Disk
       product: SAMSUNG SP8004H
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: QW10
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0fe90fe9
  *-cdrom:0
       description: DVD-RAM writer
       product: DVDRAM GSA-H10N
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: JL12
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
  *-cdrom:1
       description: DVD reader
       product: DVD-ROM SD-816B
       vendor: SAMSUNG
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: H000
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: SCSI Disk
       product: My Book
       vendor: WD
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdc
       version: 1028
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=4 signature=41ffc810
stephane@home-pc:~$ grep "UDMA" /var/log/dmesg
[    0.264473] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.264478] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.463143] ata1.00: ATA-6: SAMSUNG SP8004H, QW100-61, max UDMA/100
[    0.463185] ata1.00: limited to UDMA/33 due to 40-wire cable
[    0.470582] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-H10N, JL12, max UDMA/33
[    0.470633] ata2.01: ATAPI: SAMSUNG DVD-ROM SD-816B, H000, max UDMA/33
[    0.478561] ata1.00: configured for UDMA/33
[    0.486790] ata2.00: configured for UDMA/33
[    0.494534] ata2.01: configured for UDMA/33
[    1.324324] ata3: SATA max UDMA/100 mmio m512@0xff9ffc00 tf 0xff9ffc80 irq 21
[    1.324330] ata4: SATA max UDMA/100 mmio m512@0xff9ffc00 tf 0xff9ffcc0 irq 21
[    1.689797] ata3.00: ATA-7: ST3500630AS, 3.AAK, max UDMA/133
[    1.756450] ata3.00: configured for UDMA/100

```

currently, my /etc/fstab looks like this:

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=cfbd22cc-b008-432f-93b1-df614d49ca41 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=bf4c544d-c7a0-40c5-859f-489787958763 none            swap    sw              0       0
#Internal ext4 hdd
UUID=0fbdf443-e185-40d9-af0e-916b57f72232 /media/internalhdd               ext4    errors=remount-ro 0       2
# external ntfs hdd
UUID=3AC42467C4242799 /media/externalhdd               ntfs    defaults 0       0
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/cdrom1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

If I can at least get my burner to work, I'll burn myself a liveCD and do a full install... hopefully a cleaner install of Lucid than what I have now.

Thanks for the help

---

### Post by sanctimonious on 2010-05-05
Same problem here. When there are media in both my DVD-RW drives, there are errors thrown in the dmesg. When there are no media, there are no errors, but the devices still fail to auto-mount. I have forced them to mount by adding entries to fstab:

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
```

but still no joy.

Any help will be appreciated.

I have attached my dmesg and my lshw.

---

### Post by stegouin on 2010-05-05
I managed to get my DVD burner mounted and workng... enough to burn an install cd... so I re-installed Ubuntu Lucid, hoping to have all resolved. Nada.

My fstab skills are getting better though, and I quickly got my external hdd and internal hdd back online... now onto the DVD drives...:-(

---

### Post by sanctimonious on 2010-05-07
I see you also have a number of PATA connections/drives. Is this a laptop or a desktop? If the latter, which motherboard are you using?

---

### Post by dino99 on 2010-05-07
you may install mountmanager and tweak it

---

### Post by stegouin on 2010-05-07
Thanks for the replies... this is a desktop. Intel® Desktop Board D845PEBT2

I have an internal SATA2 500GB hdd with ext4, and an external HDD western Digital MyBook, NTFS.

---

### Post by stegouin on 2010-05-08
I have tried mountmanager... nice utility, but still hasn't fixed my problem.

In Karmic, I used to be able to pop in any DVD, and it would either launch Movie Player, or if a blank CDR or DVDRW, would open up Brasero etc.

It doesn't even mount or recognize a simple first generation iPod shuffle... 

Surprisingly, it recognized and mounted my Casio Digital camera and I got a prompt to open F-Spot... so I'm not totally in the dog house ... yet.

My /etc/fstab now looks like this, courtesy of mountmanager:

```

/dev/sr0 /media/cdrom0 udf,iso9660 group,noauto 0 0
/dev/sr1 /media/cdrom1 udf,iso9660 group,noauto 0 0
UUID=0fbdf443-e185-40d9-af0e-916b57f72232 /mnt/internalhdd ext4 defaults 0 2
UUID=250a143e-6cd8-4b3f-9119-fcc6e1e914e6 / ext4 defaults 0 1
UUID=84920ceb-9276-413d-8402-edb72488171e swap swap sw 0 0
UUID=3AC42467C4242799 /mnt/externalhdd ntfs-3g noauto 0 0

```

Still no working optical drives or iPOD mounting... I haven't tried my Sony Handycam yet, but I'll assume it works since my digital camera seems to work and mount ok.

Any help or guidance on the optical drives and iPOD mounting issues would be greatly appreciated.

---

### Post by stegouin on 2010-05-10
Well... seemed to have found a solution to my problem...

Erratic mounting behaviour for my LG DVDRW and usb sticks, iPOD shuffle... read in an ubuntu forum thread a suggestion to disable the floppy disk in BIOS.

did that.. basically disabled everyting relating to floppy drive... controller, boot priority etc...

Restart once more... pop in a CD-R in drive tray... almost immediate prompt from Brasero for action...

Popin my iPod suffle in docking station... bam, iPOD icon mount appears on desktop...

I haven't tested the iPOD syncing yet... but this is looking pretty good so far!

My USB Casio digital camera worked before this, so I'm hoping it still does now that disabling floppy drive seems to have resolved other problems... ditto for my Sony Handycam.

This was a close call, I was contemplating going back to Karmic... glad I persisted.

Hope this info helps others.

I will post an update once I've had a chance to fully test iPOD and camera connectivity.

---

