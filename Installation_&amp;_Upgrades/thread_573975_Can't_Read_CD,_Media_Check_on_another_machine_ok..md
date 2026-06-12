---
title: "Can't Read CD, Media Check on another machine ok."
date: 2007-10-12
forum: Installation &amp; Upgrades
---

### Post by havoc3d on 2007-10-12
I'm trying to get Server 7.04 loaded on an old IBM Netfinity 5600 (yes, thanks to Chyrlser)

Anyway, I've done several burns of the ISO at different speeds, the lowest my burner and nero will go is 12x, so that's what the last burn was at.  CD boots fine, goes through all the startup and prep stuff fine, but when it goes to start installing files, it just stops, no activity light on the drive going, nothing.

I tried a different drive, same problem.  Tried running the media check, again, boots ok, test starts ok, but can't read the files.  As a test, i pulled the drive and the most recent burn, and hooked them up to an intel 845 based desktop board, and the media test ran through and completed with no issues.

Anyone have any ideas what the problem might be?  Assuming it's loading the wrong driver for the onboard IDE on that old server, so i'm planning when i get home tonight to dig up my old Promise ATA100 PCI card, and trying it off that.

Looking for people to weigh in with their thoughts...

---

### Post by wpshooter on 2007-10-12
Could some BIOS setting possibly be an issue ?  Have you tried setting everything back to default/safe ?

---

### Post by havoc3d on 2007-10-12
Haven't yet.  I did an ubuntu server load on it probly about a year ago now, and that one went ok, but something could have been changed since then...good call.

---

### Post by havoc3d on 2007-10-13
Well, CMOS reset didn't help the situation.  I tried that old promise ata card, and i can't get this thing to boot from a device on it....

anyone else have any thoughts?

---

### Post by jimbean on 2007-10-13
pull the cmos battery for a day had a tandy {radio shack} screw up bios once and the only way to reset it was cmos battery pull
also try setting the harddrive settings manually to spec on harddrive 
disable sound
disable every on board setting for sound and vid card and modem irq
or fool around with them
got enough ram alot of people swear by 512

---

### Post by havoc3d on 2007-10-13
I've tried both a Reset to Defaults within the BIOS, and when that didn't work, i pulled the batt for about 10 minutes, which deffinatly was enough to reset everything.  I can try to disable everything that isn't required, but this is a server, so it doesn't have a whole lot it doesn't need.

Specs are Single 667 Slot1 P3, 1g ECC memory, and 5 scsi2 hotswap HDs....i thought maybe the controler card for those was causing a problem, but once i did just the CD test, and even that failed, i doubt that's it.

Oh yeah, i also tried a new ide cable for the cd drive....never know...heh

I grabbed CentOS as a test also, that installed OK, but doesn't want to boot right when it gets to network devices, but that atleast proves the drive, cable, etc, should be fine...was really hoping to get ubuntu working for the out-of-the-box LAMP, but maybe i'll have to just work with getting CentOS 5 fully booted...8o(

---

### Post by dinub1 on 2007-10-13
You may want to give a try to PCLinux 2007. Its a very nice distro,.

---

### Post by havoc3d on 2007-10-15
This thing's a gigantic server, and i thought pclinux was more desktop oriented.  I'm planning on turning it into a Jinzora server, so desktop niceties are moot.  all i really need is networking, apache, mysql, and php....amazing all the problems i'm having getting a distro going right...

---

### Post by jimbean on 2007-10-20
are u using a udma 66 or udma 33 or a udma other
flat ribbon cable i used a udma 66 on a cdrom once and that did 
not work
u can tell the difference on how many wires in the cable

---

### Post by jimbean on 2007-10-20
allso what i was asking was how many cylinders and sectors on hd
you can set them manually

---

### Post by voney on 2007-12-06
I've actually had this same issue myself. After much troubleshooting i think it's to do with the fact that the on board IDE only supports UDMA2 not UDMA3 like all the new CDROM drives. I've found that the install fails at the exact same point each time and if you check the media it does the same.

I don't think it's a driver issue because it does the same thing when installing windows, it basically fails to read the drive correctly after a certain point on the disk.

To get around it I've actually decided to install straight Debian as it has an install CD that is only 40MB and this seems to be before the "cutoff point" where the drive can no longer read correctly.

- Voney

---

