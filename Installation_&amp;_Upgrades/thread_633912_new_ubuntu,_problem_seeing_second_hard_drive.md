---
title: "new ubuntu, problem seeing second hard drive"
date: 2007-12-07
forum: Installation &amp; Upgrades
---

### Post by danmcb on 2007-12-07
Hi all,

I have had an old debian system for a while, based on an ASRock K7S41 motherboard. It has 2 hard drives and a CD, as follows:

 - IDE0 master : 40Gig Maxtor drive, this is system boot disc
 - IDE0 secondary - CDROM
 - IDE1 master - 200GB FAT32 drive for media and so on

this second 200GB drive always took a while to be recognised, but it has always worked fine, I used it as the root for a samba share on my home network.

Now I decided to reinstall this machine to latest ubuntu. There wasn't much on the main 40GB drive that I wanted, but I copied /etc, /var and so on to the 200GB drive anyhow so that I could always look at old config files and so on. Then did a clean Ubuntu install from CD, wiped the 40GB clean.

The install is like a dream, except for the fact that my 200GB drive is no place to be found. fdisk -l doesn't show it. It seems that there is a problem in detecting the drive. When I look in dmesg, I see this:


[   51.058939] pata_sis 0000:00:02.5: version 0.5.1
[   51.059267] scsi0 : pata_sis
[   51.100137] scsi1 : pata_sis
[   51.100347] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ff00 irq 14
[   51.100352] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ff08 irq 15
[   51.425304] ata1.00: ATA-7: Maxtor 6E040L0, NAR61HA0, max UDMA/133
[   51.425311] ata1.00: 80293248 sectors, multi 16: LBA 
[   51.425319] ata1.01: ATAPI: CD-RW IDE5232, VER A030, max UDMA/66
[   51.425325] ata1.00: limited to UDMA/33 due to 40-wire cable
[   51.425329] ata1.01: limited to UDMA/33 due to 40-wire cable
[   51.441307] ata1.00: configured for UDMA/33
[   51.613053] ata1.01: configured for UDMA/33
[   56.806361] ata2: port is slow to respond, please be patient (Status 0x80)
[   61.620079] ata2: SRST failed (errno=-16)
[   61.787195] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6E040L0   NAR6 PQ: 0 ANSI: 5
[   61.788123] scsi 0:0:1:0: CD-ROM            CDWRITER IDE5232          A030 PQ: 0 ANSI: 5

it seems that ata2 is slow to respond, as a result the system never recognises the drive. But there is no hardware problem that I know of - the old debian system always saw this drive, I did not even open the box before the new install.


Any ideas?


Daniel

---

### Post by logos34 on 2007-12-07
Does it show up in 

sudo lshw -C disk?

Replace your IDE cable with 80-pin, see if that helps.  (~$3 item)  at the very least you're crippling the throughput/speed on the drive it does detect.

---

### Post by danmcb on 2007-12-08
Thanks. It turned out that there was one 40 wire and one 80 wire cable in there, but the 80 wire was badly installed. Fxed all that, but still had the same issue (although the main hard drive is now coming up at UDMA 133)

The problem turned out to be a jumper on the 200GB drive called "CS Enabled" - cable select. When I removed this, the irritating delay at boot time is gone, and the drive now appears to the system.

cheers.

---

### Post by logos34 on 2007-12-08
aha...so it was the cs jumper setting.  

glad its working now at the proper speed

---

