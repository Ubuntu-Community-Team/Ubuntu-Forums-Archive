---
title: "isolinux: Disk error 01, AX = 0201, drive 80 during first boot"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by rklauco on 2007-11-30
I am trying to install Ubuntu 7.10 onto USB harddrive.
The drive has a capacity of 500GB.
Installation goes fine. The disk is S-ATA connected using USB to S-ATA/P-ATA housing kit.
During the first boot I receive the error
```
isolinux: Disk error 01, AX = 0201, drive 80
```
And the boot process stops.
I unplugged the disk, put it directly to other machine's S-ATA drive and it booted just fine, including GRUB and the rest.
Can someone point me out to some solution?
Already tried googling with no results :-(
Could the drive capacity be a problem in this case?

---

### Post by meierfra on 2007-11-30
[http://ubuntuforums.org/showthread.php?t=622850]("http://ubuntuforums.org/showthread.php?t=622850")

A quote from that thread:


> MOST IMPORTANT!!!!! Make sure the IDE cables are connected correctly as if they were CS (Cable Select) - the HDD is closest to the motherboard & CD/DVD is at the end - it didn't matter to the system whether or not the components were jumpered master/slave

---

### Post by Pumalite on 2007-11-30
Check your BIOS in IDE Configuration and post your settings.

---

### Post by rklauco on 2007-12-03
Well, if you read my post, you can see, that I am trying to install to USB, so there is no such thing as CS closest to mainboard, or BIOS IDE settings.
The disk is S-ATA, so I believe I can't even set Master/Slave/CS option.

---

### Post by Pumalite on 2007-12-03
Does your BIOS recognize your USB? If so, disconnect all others and install to it.
[http://ubuntuforums.org/showthread.php?t=598961&highlight=boot+from+external+drive](http://ubuntuforums.org/showthread.php?t=598961&highlight=boot+from+external+drive)
[http://ubuntuforums.org/showthread.php?t=598787&highlight=boot+from+external+drive](http://ubuntuforums.org/showthread.php?t=598787&highlight=boot+from+external+drive)
[http://ubuntuforums.org/showthread.php?t=598961](http://ubuntuforums.org/showthread.php?t=598961)
[http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/](http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/)
[http://ubuntuforums.org/showthread.php?t=614913](http://ubuntuforums.org/showthread.php?t=614913)
[http://ubuntuforums.org/showthread.php?t=614863](http://ubuntuforums.org/showthread.php?t=614863)

---

### Post by Pumalite on 2007-12-03
If it turns out your drive is no good; use TestDist or Rescuecd to test and repair it if possible

---

### Post by rklauco on 2007-12-03
The drive is OK.
I already checked the drive.
And, as I wrote, it works just fine inside the machine pluged into S-ATA - boots, works, no problem.
Even plugged to USB, I can see the disk, copy the data in whatever direction and everything else.
The BIOS supports booting from USB, because I used Slax, put it onto my 1gig USB stick and booted just fine.

---

### Post by Herman on 2007-12-03
Maybe I'm being old fashioned, but I still make sure if I have any IDE drives in a machine, that they are jumpered correctly as master and slave it they are on a IDE cable with black plugs.
If the IDE cable has a blue plug, that one goes to the MBR socket and the black plug goes to the master IDE disk and the grey plug goes to the slave IDE disk. The jumper settings in that case should be set to 'Cable Select' for both hard disks.

Even professional computer technicians sometimes plug IDE cables in and set the jumpers in strange ways, because "they know what they are doing", and/or they don't happen to have the correct length IDE cable on hand at the time to reach both drives and plug them in correctly. An IDE cable of the correct length would only cost about a dollar or so in most countries.

Even if you are trying to boot a USB, it appears that your BIOS is mis-directed and is trying to boot your CD/DVD drive instead.

The same error message has already been found to have been caused by internal hard drives having been plugged in and jumpered incorrectly in other threads. 

Please shine a light around inside your computer case and try to establish whether your IDE hard drives (if any) are plugged in and jumpered correctly.

Even if you have no IDE hard drives, most CD/DVD drives I've seen are IDE, (I haven't seen a SATA CD/DVD drive yet, but possibly they exist)?

Regards, Herman :)

---

### Post by madfitz on 2008-02-28
just to be sure we're clear, this is regarding SATA, not IDE. I'm installing 7.10 AMD64 non-gui ubuntu on my file server on a new 500GB WD drive. I have had the previous version running on this exact hardware setup. Gigabyte ga-k8n ultra9. This motherboard has 8 sets of sata ports, SATA and SATA2. This is the first time I'm trying to install any drive (primary or data) on the SATA2. Install and everything works like a charm, howecer on bootup I get the error as thiis thread's title.

Please, don't suggest looking at IDE settings and jumpersw, this is pure SATA, no IDE. Any suggestions on this error?

Could it be this version of Ubuntu doesn't support SATA2
Could the drive (though advertised as SATA2) not be SATA2

Thanks for your reply.

---

### Post by Pumalite on 2008-02-28
[http://www.google.com/search?hl=en&q=+isolinux%3A+Disk+error+01%2C+AX+%3D+0201%2C+drive+80+&btnG=Google+Search](http://www.google.com/search?hl=en&q=+isolinux%3A+Disk+error+01%2C+AX+%3D+0201%2C+drive+80+&btnG=Google+Search)

---

### Post by rklauco on 2008-02-29
> **Pumalite said:**
> [http://www.google.com/search?hl=en&q=+isolinux%3A+Disk+error+01%2C+AX+%3D+0201%2C+drive+80+&btnG=Google+Search](http://www.google.com/search?hl=en&q=+isolinux%3A+Disk+error+01%2C+AX+%3D+0201%2C+drive+80+&btnG=Google+Search)
You must be some kind of joker.
Did you read my first post? I already searched lots of forums, G was my place to start, but did not help.

I appreciate any of your ATA cable help attempts, but the PC has no ATA drives, just SATA DVDRW and USB casing of SATA HDD. I am computer technician and believe me, I know how long should the cable be and how to connect it and set the jumpers.
As I said, the drive works just fine using the same cable simply plugged onto the mainboard.
The USB casing works just fine, too - the installation to that drive was made using the USB casing.
But, the actual boot ends up with the $SUBJ error message.

---

