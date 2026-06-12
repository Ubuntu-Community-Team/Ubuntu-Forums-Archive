---
title: "DVD drive:  &quot;No medium found&quot;"
date: 2007-07-28
forum: Installation &amp; Upgrades
---

### Post by stephanecharette on 2007-07-28
I've replaced my old CD drive with a DVD drive, but now I cannot access the drive from Ubuntu 7.04.

# mount /dev/hdc /media/cdrom
mount: No medium found

Drive is a BenQ installed as master on secondary IDE.  No slave drives:

# dmesg | grep "hd.:"
[    5.477298]     ide0: BM-DMA at 0xd800-0xd807, BIOS settings: hda : DMA, hdb : pio
[    5.477322]     ide1: BM-DMA at 0xd808-0xd80f, BIOS settings: hdc : DMA, hdd : pio
[    5.799722] hda: WDC WD1200JB-00CRA1, ATA DISK drive
[    7.211620] hdc: BENQ DVD DD DW1625, ATAPI CD/DVD-ROM drive
[    8.113713] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)

Only other IDE drive installed is my boot drive, the master on the primary IDE.  If relevant, this system also has a SCSI drive:

# dmesg | grep scsi
[   23.102416] scsi0 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
[   23.105534] scsi 0:0:0:0: Direct-Access     SEAGATE  ST318436LW       0010 PQ: 0 ANSI: 3

When I click on Places->Computer, I do have an icon that says:  "CD-RW/DVD+-RW Drive".  Trying to open that icon gives me:

"Unable to mount media.  There is probably no media in the drive."

(I've tried this with many different CDs, same result.)

Here are the relevant portions of my /etc/fstab:

# grep hdc /etc/fstab
#/dev/hdc        /media/cdrom0   udf,iso9660 user,auto     0       0
/dev/hdc        /media/cdrom0   auto user,noauto     0       0

This is a clean-install (not upgrade) of 7.04.  System is up-to-date.

Running "tail -f /var/log/messages" doesn't seem to show anything as I try to access the CD/DVD drive.  (Should it?)

Any help greatly appreciated.  Thanks!

---

### Post by stephanecharette on 2007-07-28
I guess I should add that since this is a brand new drive, it doesn't have a region set.  I've tried using "regionset", but I get the following:

$ sudo regionset 
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.

---

### Post by logos34 on 2007-07-28
> # grep hdc /etc/fstab
#/dev/hdc /media/cdrom0 udf,iso9660 user,auto 0 0
/dev/hdc /media/cdrom0 auto user,noauto 0 0

What happens when you use the old entry that's been commented out:
[B]
/dev/hdc /media/cdrom0 udf,iso9660 user,auto 0 0[/B]

just take out the '#' and the second entry and reboot

---

### Post by gyeti on 2007-07-29
Hi,

I just fight with a similar problem with an external DVD multi reader/burner. Sounds like yours is built in and thus doesn't need to connect through USB. In my case I can read and write CDs, I can read and write data DVDs, but I cannot access video DVD. From searching the net itis clear that many people have this problem. However, there seems to be no general solution.

Anyway, I guess the region code is not a problem. My drive worked fine (except for video) without the code set. I set it today with "regionset". This only works if there is a recognized disk in the drive. I just used an audio CD which worked fine. Did you try audio CDs yet? These are not mounted and you can learn something if audio works.

---

### Post by stephanecharette on 2007-07-31
> **logos34 said:**
> What happens when you use the old entry that's been commented out:
[B]
/dev/hdc /media/cdrom0 udf,iso9660 user,auto 0 0[/B]

just take out the '#' and the second entry and reboot

Nothing different.  Same error message.  I tried both ways, which is why it is still in the file.

---

### Post by medland77 on 2007-08-11
I get exactly the same symptoms with my SAMSUNG DVD-ROM SD-616E, as well as the fact that it won't boot from that drive (using cds or DVDs) either. Here's the info:

dmesg | grep "hd.:"
[    4.224000]     ide0: BM-DMA at 0xb400-0xb407, BIOS settings: hda:DMA, hdb:DMA
[    4.224000]     ide1: BM-DMA at 0xb408-0xb40f, BIOS settings: hdc:DMA, hdd:DMA
[    4.664000] hda: Maxtor 2B020H1, ATA DISK drive
[    4.960000] hdb: WDC WD1600SB-01RFA0, ATA DISK drive
[    7.372000] hdc: HL-DT-ST GCE-8160B, ATAPI CD/DVD-ROM drive
[    8.212000] hdd: SAMSUNG DVD-ROM SD-616E, ATAPI CD/DVD-ROM drive
[    8.304000] hda: max request size: 128KiB
[    8.324000] hda: 40020624 sectors (20490 MB) w/2048KiB Cache, CHS=39703/16/63
[    8.324000] hda: cache flushes not supported
[    8.324000]  hda: hda1 hda2 < hda5 >
[    8.364000] hdb: max request size: 512KiB
[    8.376000] hdb: 321672960 sectors (164696 MB) w/8192KiB Cache, CHS=20023/255/63, UDMA(100)
[    8.376000] hdb: cache flushes supported
[    8.376000]  hdb: hdb1 hdb2 hdb3
[    8.424000] hdc: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache, DMA
[    8.424000] hdd: ATAPI 48X DVD-ROM drive, 512kB Cache, UDMA(33)

grep hdd /etc/fstab
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

---

