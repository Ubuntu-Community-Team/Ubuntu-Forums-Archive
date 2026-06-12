---
title: "Shuttle Computer Install Help"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by pmgeahan on 2007-03-18
Folks - 

I recently picked up a Shuttle T3100h.  It's got an SiS SATA and IDE interface on board, as well as an SiS 190 Gigabit Ethernet adaptor.

Here's my problem: The Edgy installer doesn't recognize the SATA drives.  The latest build of Feisty does, but the install freezes at 35%.

I'd really like to get Ubuntu onto this box; does anyone have any ideas how to do so?  It seems that the kernel on the Edgy CD isn't up-to-bleeding enough to recognize my hardware - is there a way by which I can boot with the Feisty CD and install with the Edgy CD, perhaps?

Or is there an idea I'm missing entirely?

---

### Post by wpshooter on 2007-03-20
I THINK the problem may not be that it won't recognize the SATA drive BUT that it does not like the combination of SATA & IDE drives.  Try unplugging the IDE drive and see if it will work.

Good luck.

---

### Post by pmgeahan on 2007-03-20
Thanks for the response.  I ended up going with the Feisty Alternate Install CD, which recognized the IDE and the SATA drives, in total, and installed fine.  No idea why the Feisty Live CD failed, but them's the breaks I guess.

Still, I find myself unable to get the onboard network card to work.  Although it's listed as a Broadcom AC 131 in the manuals, it's detected as an SIS 190 in the install and by the modules.  Still trying to work that one out.

Onwards and upwards.

---

### Post by wpshooter on 2007-03-20
You might want to consider report these as possible bugs and perhaps they will be worked out in a few weeks when Feisty is supposed to be released.

---

