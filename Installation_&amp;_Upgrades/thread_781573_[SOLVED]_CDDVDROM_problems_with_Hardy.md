---
title: "[SOLVED] CD/DVDROM problems with Hardy"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by sdhays on 2008-05-04
I just upgraded to Hardy Heron from Gutsy Gibbon on my x86_64 box, and I like it.  My only problem is that the CDROM drive doesn't work anymore.  I can't mount the drive manually, and trying to run VLC with it, I get the following errors in dmesg:

```
[  685.383948] sr 0:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[  685.383951] end_request: I/O error, dev sr0, sector 136
[  685.406398] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  685.406403] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current]
[  685.406406] sr 0:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[  685.406410] end_request: I/O error, dev sr0, sector 64
[  685.425906] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  685.425910] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current]
[  685.425912] sr 0:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[  685.425916] end_request: I/O error, dev sr0, sector 64
```

Something else that's weird is that it has the drive set as /dev/cdrom1 and nothing set as /dev/cdrom0, like it was in Gutsy.  Any advice?

---

### Post by Pumalite on 2008-05-04
Try this:
(from another thread)

Code:

gksudo gedit /etc/fstab

Replace:

/dev/cdrom0 /media/cdrom0 auto ro,noauto,user,exec 0 0
/dev/cdrom1 /media/cdrom1 auto ro,noauto,user,exec 0 0

By:

/dev/scd0 /media/cdrom0 auto ro,noauto,user,exec 0 0
/dev/scd1 /media/cdrom1 auto ro,noauto,user,exec 0 0

mount -a

---

### Post by sdhays on 2008-05-04
Thanks, but I already tried that.  I didn't post until I did some looking on the forum first to see if anyone had the problems I'm having.  While plenty of people seem to be having trouble, their problems don't seem to directly match mine, hence the new thread.

The fact there is a /dev/cdrom1, but no /dev/cdrom0 seems to indicate something is not being set up right.  That's controlled by udev, right?

---

### Post by monchichi on 2008-05-12
I have the same problem.

Check out this thread:
[http://www.uluga.ubuntuforums.org/showthread.php?t=767449](http://www.uluga.ubuntuforums.org/showthread.php?t=767449)

People seem unwilling to accept that this is a bug with the hardy kernel. Something with the switch from IDE modules to SCI-emulation module seems to have broken cd and dvd drives for a lot of people.

---

### Post by monchichi on 2008-05-12
Oh and I forgot to mention, the workaround is to add all_generic_ide to your kernel line in /boot/menu.list

---

### Post by sdhays on 2008-05-18
> **monchichi said:**
> Oh and I forgot to mention, the workaround is to add all_generic_ide to your kernel line in /boot/menu.list

THANKS!  That did it!
Scott

---

### Post by guzzigeezer on 2008-10-23
Hi
 I'm a totally GUI user having just migrated from windows due to work insisting we use ubuntu. I have been using a DVDrw to backup our data files for the last 6 months and it has just stopped recording. I have used Ubuntu desktop, an ISO burner and a couple of back up programs. None of them write to the disc. The DVD shows up as a blank disc on the desk top when inserted.
and quite happily reads discs Ok. I have tried the burner in a windows system with no problems.
Can somebody please come up with something slightly more informative than "just add ** to ***". Sorry about the long winded post but just wanted to get all relevant(i hope) information across.:( IMHO linux will never be popular until it stops assuming that every body who uses it is a command line programming whizzkid. most people just want it to work.

---

