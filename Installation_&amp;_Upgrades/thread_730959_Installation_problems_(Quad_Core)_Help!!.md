---
title: "Installation problems (Quad Core) Help!!"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by e4foxtrot1 on 2008-03-21
I'm having problems getting Ubuntu to install on my new system. I boot fine till I try normal install or safe mode. After about a minute everything just stops. Sometimes Ill get strange characters or a pixialated screen.

What I have attempted to do.

I've tried using a older pci-e card because I thought that may have been the problem.
Tried booting in different screen resolutions.
Reburnt my ISO at a slower speed and verification.
Tried to install the i386 version of Ubuntu.
Used F6 in safe mode and disabled PCI and ACPI, manually set my memory.

I have managed once to get it to start loading without the splash screen and noticed "kernel panic" errors.

My specs:

ASUS P5K3 DELUXE/WIFI-AP LGA 775 Intel P35 ATX Intel Motherboard
Intel Core 2 Quad Q6600 Kentsfield 2.4GHz LGA 775 Quad-Core Processor Model BX80562Q6600
OCZ Platinum 2GB (2 x 1GB) 240-Pin DDR3 SDRAM DDR3 1333 (PC3 10666)
NVIDIA GeForce 8800 GT OC Graphics Card
Western Digital - Raptor X 150GB Internal Hard Drive (O/S will be installed here)
Western Digital - 1TB Internal Hard Drive

I've spent 2 days searching for any help. Not much out there. My previous installations were flawless so I wasn't even expecting this many problems.

When I do get this up and running how much space should I plan on assigning to the /swap partition? I plan on using this as a HTPC and gaming.

I would really like not to having to install windows just to get this system up and running.

---

### Post by Dark Hornet on 2008-03-21
what version of Ubuntu are you trying to install?--I am not saying this is the issue, I am just curious....

Dark Hornet

---

### Post by e4foxtrot1 on 2008-03-21
Trying to install ubuntu-7.10-desktop

---

### Post by Dark Hornet on 2008-03-21
Did you just build this machine....I guess what I am wondering is are you sure that all of your components are working correctly?  I just built a similar machine with the exact processor the Intel Q6600, and 8 gigs of Corsair RAM, however 2 gigs of my RAM where bad, and needed to be replaced...you might want to do a memory test...just a thought.

Dark Hornet

---

### Post by sabasgg on 2008-03-21
I have roughly the same hardware config and have experienced the same problem trying to install Ubuntu 7.10 64bit.

My machine passes all sorts of hardware tests runing a different OS.

I tend to think that the problem is related to the nVidia GeForce 8800GT card instead of processor or RAM. jjgy posted today a similar issue in this thread [http://ubuntuforums.org/showthread.php?t=731322]("http://ubuntuforums.org/showthread.php?t=731322").

By the way, the installation of Ubuntu 7.04 32bit seemed to start up alright but I didn't complete it cause I'm going for the 64bit.

---

### Post by jacksaff on 2008-03-21
I just installed the 804 KDE4 64 bit beta  with a similar hardware set up.
I found the live cd would not boot due to the new graphics card.
I had to 
1. select safe mode
2. remove the 'quiet' and 'splash' options from the boot line. These cause the system to crash and restart for some reason.
The system would then hang as it booted due to problems with the dvd drive.
I ejected and reinserted the cd mid boot and all came up fine. The whole process of booting the livedisc took several minutes with lots of error messages most of which seemed to be complaining about the cd (which was a fine, checked burn).
Once up and running I was able to install with no hassles. 
On first boot from the hd I installed the nvidia drivers using adept and I've had no problems since (well, since last night when I did this...).
Hope this helps.

---

### Post by marvin1969 on 2008-03-22
I have a similar system 
  ASUS P5K-E (no WiFi)
  Q6600
  2GB Corsair RAM (certified with the board)
  WD 1x10kRPM 150GB SATA2 drive
  WD 1x7kRPM 750GB SATA2 drive
  Samsung SATA DVD-RW
  nVidia 8600GTS 256MB

When I try to install 7.10, I get odd errors related to the HDD 

```
Mar 21 12:04:29 ubuntu kernel: [  221.563113] sd 5:0:0:0: [sda] 1465149168 512-byte hardware sectors (750156 MB)
Mar 21 12:04:29 ubuntu kernel: [  221.563467] sd 5:0:0:0: [sda] Write Protect is off
Mar 21 12:04:29 ubuntu kernel: [  221.564160] sd 5:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 21 12:04:29 ubuntu kernel: [  221.564851] sd 5:0:0:0: [sda] 1465149168 512-byte hardware sectors (750156 MB)
Mar 21 12:04:29 ubuntu kernel: [  221.605007] sd 5:0:0:0: [sda] Write Protect is off
Mar 21 12:04:29 ubuntu kernel: [  221.606932]          res 51/04:08:e8:66:54/04:00:57:00:00/e0 Emask 0x1 (device error)
Mar 21 12:04:29 ubuntu kernel: [  221.628055] ata6.00: configured for UDMA/33
Mar 21 12:04:29 ubuntu kernel: [  221.803242] ata6.01: configured for UDMA/100
Mar 21 12:04:29 ubuntu kernel: [  221.803248] ata6: EH complete
Mar 21 12:04:29 ubuntu kernel: [  221.803567]          res 51/04:08:e8:66:54/04:00:57:00:00/e0 Emask 0x1 (device error)
Mar 21 12:04:29 ubuntu kernel: [  221.835913] ata6.00: configured for UDMA/33
Mar 21 12:04:29 ubuntu kernel: [  222.008207] ata6.01: configured for UDMA/100
Mar 21 12:04:29 ubuntu kernel: [  222.008213] ata6: EH complete
Mar 21 12:04:29 ubuntu kernel: [  222.008518]          res 51/04:08:e8:66:54/04:00:57:00:00/e0 Emask 0x1 (device error)
Mar 21 12:04:29 ubuntu kernel: [  222.032772] ata6.00: configured for UDMA/33
Mar 21 12:04:29 ubuntu kernel: [  222.204659] ata6.01: configured for UDMA/100
Mar 21 12:04:29 ubuntu kernel: [  222.204662] ata6: EH complete
Mar 21 12:04:29 ubuntu kernel: [  222.204974]          res 51/04:08:e8:66:54/04:00:57:00:00/e0 Emask 0x1 (device error)
Mar 21 12:04:29 ubuntu kernel: [  222.229675] ata6.00: configured for UDMA/33
Mar 21 12:04:29 ubuntu kernel: [  222.401109] ata6.01: configured for UDMA/100
Mar 21 12:04:29 ubuntu kernel: [  222.401111] ata6: EH complete
Mar 21 12:04:29 ubuntu kernel: [  222.401427]          res 51/04:08:e8:66:54/04:00:57:00:00/e0 Emask 0x1 (device error)
Mar 21 12:04:29 ubuntu kernel: [  222.425547] ata6.00: configured for UDMA/33
Mar 21 12:04:29 ubuntu kernel: [  222.597560] ata6.01: configured for UDMA/100
Mar 21 12:04:29 ubuntu kernel: [  222.597563] ata6: EH complete
Mar 21 12:04:29 ubuntu kernel: [  222.597877]          res 51/04:08:e8:66:54/04:00:57:00:00/e0 Emask 0x1 (device error)
Mar 21 12:04:29 ubuntu kernel: [  222.629399] ata6.00: configured for UDMA/33
Mar 21 12:04:29 ubuntu kernel: [  222.801252] ata6.01: configured for UDMA/100
Mar 21 12:04:29 ubuntu kernel: [  222.801256] sd 5:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Mar 21 12:04:29 ubuntu kernel: [  222.801259] sd 5:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
Mar 21 12:04:29 ubuntu kernel: [  222.801261] Descriptor sense data with sense descriptors (in hex):
Mar 21 12:04:29 ubuntu kernel: [  222.801263]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Mar 21 12:04:29 ubuntu kernel: [  222.801268]         57 54 66 e8 
Mar 21 12:04:29 ubuntu kernel: [  222.801270] sd 5:0:0:0: [sda] Add. Sense: No additional sense information
Mar 21 12:04:29 ubuntu kernel: [  222.801273] end_request: I/O error, dev sda, sector 1465149160
Mar 21 12:04:29 ubuntu kernel: [  222.801281] ata6: EH complete
```


Am I fighting a SATA cable issue here?  Anyone have an idea?

Thanks.

---

### Post by e4foxtrot1 on 2008-03-23
Ok, I'm throughly convinced it's gotta be my board at this point! I even found a site to manually set my ram into the board. If anyone is interested:

[http://www.ocztechnologyforum.com/forum/showthread.php?t=31299?t=32363](http://www.ocztechnologyforum.com/forum/showthread.php?t=31299?t=32363)

I cant even get XP to install. So, I'm boxing it up and sending it back to newegg. I swear I've never had problems with an ASUS board. Anyone had success installing an Intel Quad Core with DDR3? I need a suggestion for a new mobo! I think four days of persistent trial and error is enough.

---

