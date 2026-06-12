---
title: "Trying to dual boot..."
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by Clove7 on 2010-02-25
For some reason, I can't install windows; it says hard disk not found. I'm trying to install windows first, then ubuntu but I don't know where to go from here to get windows installed, as all the resolutions to get that windows error fixed are based on the user using windows. Can anyone help me please?

---

### Post by oldfred on 2010-02-25
From either of the Ubuntu liveCd or a Gparted liveCD can you see your drive. If it was previously formated maybe windows cannot see it. You can use gparted from a live CD to create a NTFS partition that windows should see. Make sure it is a primary partitions as windows will not install to a logical in an extended.

---

### Post by Clove7 on 2010-02-26
Totally didn't work at all. I even completely formatted the drive with the NTFS file system and tried to install, same thing. Ironically, windows came installed on this laptop...lol. But only linux will install on it, not windows now.

---

### Post by darkod on 2010-02-26
Which windows, XP? Don't forget XP can't see SATA disks. At least not unless you can use Native IDE mode for the SATA Type in BIOS which most modern BIOSes seem to have.
Otherwise you need your correct sata drivers slipstreamed into XP with something like nlite software (free), or floppy with the sata drivers. I don't think it can accept cd since you need to have XP install cd inside.
You press F6 when the installer is starting for the floppy drivers option.

PS. I just noticed you said laptop so you probably don't have floppy on it these days. Either slipstream with nlite, or check BIOS for different sata modes.

---

### Post by wilee-nilee on 2010-02-26
> **darkod said:**
> Which windows, XP? Don't forget XP can't see SATA disks. At least not unless you can use Native IDE mode for the SATA Type in BIOS which most modern BIOSes seem to have.
Otherwise you need your correct sata drivers slipstreamed into XP with something like nlite software (free), or floppy with the sata drivers. I don't think it can accept cd since you need to have XP install cd inside.
You press F6 when the installer is starting for the floppy drivers option.

PS. I just noticed you said laptop so you probably don't have floppy on it these days. Either slipstream with nlite, or check BIOS for different sata modes.

I had this problem on a acer aspire with XP; bios let me change to IDE. No slow down seen with this with this setup with XP/W7/Lucid on the same HD.

---

### Post by Clove7 on 2010-02-26
> **darkod said:**
> Which windows, XP? Don't forget XP can't see SATA disks. At least not unless you can use Native IDE mode for the SATA Type in BIOS which most modern BIOSes seem to have.
Otherwise you need your correct sata drivers slipstreamed into XP with something like nlite software (free), or floppy with the sata drivers. I don't think it can accept cd since you need to have XP install cd inside.
You press F6 when the installer is starting for the floppy drivers option.

PS. I just noticed you said laptop so you probably don't have floppy on it these days. Either slipstream with nlite, or check BIOS for different sata modes.
But I can't use nlite! That's my problem...you need to install some .net framework, and that CAN'T be installed, even under wine...I could run a VM, but I'd prefer not to lol. I've never had that great of luck getting a VM to work.

---

### Post by Clove7 on 2010-02-26
Alright, I remembered I have windows XP installed on a HD on another PC I have in the basement...anyways, how do I figure out my hard disk info so that I can get some drivers for it, to add to my XP install. Basically how do I get that kind of disk information in ubuntu?

---

### Post by wilee-nilee on 2010-02-26
> **Clove7 said:**
> Alright, I remembered I have windows XP installed on a HD on another PC I have in the basement...anyways, how do I figure out my hard disk info so that I can get some drivers for it, to add to my XP install. Basically how do I get that kind of disk information in ubuntu?

You might look at the computer manufacturer and see if they have a ISO available. I have a acer aspire and was able to get XP with SP3 slipstreamed although I didn't access the drivers for sata if they were included.

Have you gone into the bios to see how the disc is set?

---

