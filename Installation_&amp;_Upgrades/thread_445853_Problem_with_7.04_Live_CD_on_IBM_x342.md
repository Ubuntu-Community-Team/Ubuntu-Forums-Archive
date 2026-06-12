---
title: "Problem with 7.04 Live CD on IBM x342"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by Mad Dawg on 2007-05-16
Greetings all!  A bit of newb (last time I was this serious about Linux was 1997), so bear with me.

Have the following:

IBM eServer xSeries 342 (Type 8669-1RX)

-(2) Intel Pentium III 1266Mhz

-2048MB RAM

-onboard SCSI (disabled in BIOS)

-onboard IDE (enabled in BIOS)
--Pioneer DVR-111D (DVD+/-RW DL)

-IBM ServeRAID 4Lx
--(3) 36GB U320 drives (RAID 5)

Edgy Live CD boots fine (though not without its quirks, I have to move the mouse around during startup or I lose video), but Feisty Live CD freezes almost immediately after the progress indicator starts.  I ran "Check CD for Defects," and it says there are errors in 34 files.  I have run the checksum against the downloaded ISO and burned many copies at very low speeds that all work splendidly on other platforms.  Thinking it's my DVD writer, I temporarily put the CD-ROM drive that originally came with the box back in.  Still a no go.  I also Google "Feisty" and "Pioneer" and find many people are successful with this particular piece of hardware.  Maybe it's the motherboard?  Seems unlikely since Edgy runs so fabulously well, as does IBM ServerGuide Setup and Installation, as does IBM ServeRAID Application, as does Gparted, as does Ghost 4 Linux...  All of them booting with some variation of Linux.

I can install Edgy and then run the Update Manager to upgrade to Feisty, but then my DVD writer doesn't work anymore.  CD's and DVD's no longer auto-mount.  After a forced mount the system can't do anything with the data on them other than browse the contents.  Put in a DVD movie, it starts to play then craps out.  Double-click an audio file, it starts to play then craps out.  Try to copy over any file from a disc in the drive, same results.  I suspect this has something to do with my fstab file changing from /dev/hda in Edgy to /dev/cdrom (symbolic link to /dev/scd0) in Feisty, which is to be expected with the new libata drivers.  Running "hdparm -i /dev/scd0" shows all the information I expect it would.  I read somewhere that somebody was able to fix this by doing a fresh install instead of an upgrade, which is the reason for my first paragraph.

I have upgraded the machine's BIOS, the SCSI adapter's BIOS, the SCSI drives' firmware and the DVD writer's firmware all to the latest and greatest.  For the DVD writer that meant a 3-hour ordeal loading Windoze just to run a 5-second application.  THANKS PIONEER!!!  I'm highly motivated, but at the end of my rope.  Maybe I should just stick with Edgy for the time being.  Any ideas would be greatly appreciated.

---

### Post by Mad Dawg on 2007-05-21
*crickets chirping*

Bump!

Anyone?

---

