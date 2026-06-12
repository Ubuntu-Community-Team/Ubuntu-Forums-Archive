---
title: "Live CD Freezes when loading"
date: 2007-03-04
forum: Installation &amp; Upgrades
---

### Post by Browneye on 2007-03-04
I've read some of the other posts about install program freezing when loading but I haven't found a post that quite matches my freeze scenario.

I boot from the CD(6.10), the menu comes up, select the first option to start or install, get a quick message about something expanding, then I get a black screen with a flashing white cursor in the corner and thats where it stops. Leave it for a while and nothing. Only way to recover is to a hard reboot.

Burnt multiple CD's at multiple speeds, no difference.

I read in some posts about a problem with SATA drives, but I couldn't see if there was a resolution yet. I have an all SATA drive setup, with only the CD being IDE. Could this be it?

All the other posts that mentioned they at least had got some way into the install then stopped. I don't seem to be able to get past step 1.

Thanks in advance for any advice
Steve Brown

---

### Post by taurus on 2007-03-04
What's the spec of your machine and I am sure the LiveCD is having a problem with your graphic card?  Therefore, you could use the alternate CD if you want to install Ubuntu on your machine.

[http://ubuntu-releases.cs.umn.edu/edgy/](http://ubuntu-releases.cs.umn.edu/edgy/)

---

### Post by Browneye on 2007-03-04
Sorry bout that, should have included the specs..

Pentium 4 3 Ghz
1Gb RAM
Radeon 9800XT Graphics (ATI Driver 8.205)
80Gb SATA Primary Drive
2 x 200Gb SATA RAID0
Intel 875 Chipset
ASUSP4G800-E Motherboard

---

### Post by Browneye on 2007-03-06
I tried the alternate CD, got the same result. Basically crashing just after it starts to load fomr the menu screen.

Anybody?

---

### Post by Kateikyoushi on 2007-03-06
You could try this with the live disc, this way can load the right driver for the video adapter. [LINK]("http://www.ubuntuforums.org/showpost.php?p=2193083&postcount=3")

---

### Post by Browneye on 2007-03-06
I tried the live disc load described in the above post, and it still crashes when it starts to boot.

It doesn't get to the prompt as described in that linked post, it seems to stop after this particular line....

ACPI: Looking for DSDT...not found!

and then it stops.

Whats DSDT?

---

### Post by Kateikyoushi on 2007-03-06
Let't try it without ACPI.

Boot from the cd at the menu press F6 then start with this option.

Boot: linux noapic

---

### Post by Browneye on 2007-03-07
tried the above, still no boot, it crashes at the same point...

Should that have said

Boot: linux noapic

or 

Boot: linux noacpi

???

Either way, it still crashed at the same point.

---

### Post by Justintoxicated on 2007-03-08
I have this problem as well, no SATA drives, just IDE.

Sometimes it boots up, sometimes it freezes.  I thought it was my CPU overheating (old hardware and crappyHS), but it is not....

I managed to install, but it will not boot up at all off the Hard drive (WD 80gb)

Just a typical AMD 1.1 with 500 megs of SD ram...

I bured a CD at 4x and at 8x and one was alternate install, they both have random hard locks, but lucky for me it is spuratic.

I have a feeling these guys are right on with it being a video problem.  Maybe my driver is close, but not spot on?

---

### Post by watson540 on 2007-03-08
i was under the impression that only the alternate install cd could handle a RAID setup. when you boot the livecd ..when it first starts and gives you opotions, hit f6 and delete the words quiet and splash. that will enable you to see any error messages that would otherwise be hidden

---

### Post by shokwave- on 2007-03-08
Same problem happens to me. I also tried everything you guys said to do. nothing works. when i delete the "quiet splash" after hitting F6 i get two errors:

SQUASHFS error: sb_bread failed reading block 0x4023
SQUASHFS error: Unable to read page, block 1003aa7, size 5559

i'm running
Intel dual core E6700
ABIT aw9d-max motherboard
dual geforce EVGA 7950 gtx KO
Crucial Ballistix 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 1000 (PC2 8000) Dual Channel Kit  
               Desktop Memory Model BL2KIT12864AA1005
750gb sata seagate HD
Creative Fatal1ty soundcard

---

### Post by Kateikyoushi on 2007-03-08
Maybe this helps.

The trick is to Press F6 "other options" when grup starts on the cd.

Press E to edit the startupline and add noapic nolapic.

---

### Post by eapache on 2007-03-08
As far as I know, squashfs is what ubuntu uses to write temporarily to disk in order to create swap etc. when running on the live cd. The errors suggest to me that it is a hard-drive problem, but I don't know enough to be able to suggest a fix. If you have any other os installed, try running a checkdisk...

---

