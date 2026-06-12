---
title: "CRC ERROR - SYSTEM HALTED on Boot"
date: 2006-07-10
forum: Installation &amp; Upgrades
---

### Post by m.h.shams on 2006-07-10
dear friends,

i have to install ubuntu 6.06 on my pc.
i have a sata hard disk on my pc.

when my installation finished, and i restart computer to boot from
installed ubuntu rather than live cd i got this error :

uncomperessing linux...

crc error

system halted.
m.h.shams is online now   	Edit/Delete Message

---

### Post by DarthMandeep on 2006-07-10
I've only ever had CRC errors when I've tried reading a CD that was burned improperly or was dirty. My guess is either the CD you burned was bad, or there's something weird happening with your disks.

I would try downloading a new copy of the iso and making sure that the downloaded file is the exact same size as what the web site says it should be. Then burn it on a new clean CD at a slow speed and run any kind of comparison tool your burner software may have to ensure it burned properly.

Then reinstall from that CD.

If that doesn't work, then I'd suggest making sure the hard drive isn't flaking out.

---

### Post by m.h.shams on 2006-07-10
> **DarthMandeep said:**
> I've only ever had CRC errors when I've tried reading a CD that was burned improperly or was dirty. My guess is either the CD you burned was bad, or there's something weird happening with your disks.

I would try downloading a new copy of the iso and making sure that the downloaded file is the exact same size as what the web site says it should be. Then burn it on a new clean CD at a slow speed and run any kind of comparison tool your burner software may have to ensure it burned properly.

Then reinstall from that CD.

If that doesn't work, then I'd suggest making sure the hard drive isn't flaking out.


but i used this cd to install ubuntu in 4 pc, i got this error just in a pc that have sata hard disk.

---

### Post by DarthMandeep on 2006-07-10
Then I'd check out the SATA disks for problems, maybe find out what kind of motherboard you have and see if there are issues with it.

Do you have another OS installed and working properly on that disk? Can you run a scandisk or fsck from that OS?

---

### Post by m.h.shams on 2006-07-11
> **DarthMandeep said:**
> Then I'd check out the SATA disks for problems, maybe find out what kind of motherboard you have and see if there are issues with it.

Do you have another OS installed and working properly on that disk? Can you run a scandisk or fsck from that OS?

my pcs mainboard is EPOX (i don't no exactly its model).

i had Win XP installed on it before, but XP has some problem too
i hangs during work sometimes, and during software installation it 
prompts me some errors sometimes.

---

### Post by DarthMandeep on 2006-07-13
Ah, sounds like a disk issue then. Can you run Scandisk from Windows? If your BIOS has SMART support, what does it say about your disk?

I'd suggest backing up any important files you have as when a hard drive starts acting up its life span is usually limited. You may need to replace the disk soon. If it's still under warranty, get a replacement or refund.

---

### Post by mrazster on 2006-07-13
I got the same error when I was fiddeling around with my memory settings in bios and set the latencies to low.

---

### Post by m.h.shams on 2006-07-15
dear friends,

my problem solved with replacing HDD, my old SATA HDD has some errors, i replaced it with new HDD, and i have no problem now.

thanks all
Regards
Dalahoo

---

