---
title: "Ubuntu server on external HDD"
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by agentorannnge on 2007-12-24
Ok, I got 7.10 server edition (not the live CD) and I need to put it on an exterenal seagate usb 2.0 250GB hdd...

Im not sure if I would need to create the partitions first, or manually mount it or what...

I have no internal hard drive but I do have access to other computers. its a IBM xSeries 345 server. Im setting up the LAMP install btw.

Im not a linux pro so dumb it down for me haha.. What I was thinking was to plug it into my windows pc and create the partitions before hand. But I need to know which to set and how to get the 7.10 alternative installer to find the external HDD.

Its like "mount" something.

---

### Post by logos34 on 2007-12-24
no internal drive makes it easier.  You don't need to pre-partition the drive--it's all done during installation from the cd (choose guided or manual).  Hook it up to the server (need a monitor though) and go.  Let grub install to it's default location (hd0, the mbr of the external since only drive in system).  You will now be able to boot to grub on the external if your bios supports USB boot (better check if unsure)

---

### Post by agentorannnge on 2007-12-24
Oh haha. I tried it before and it wouldn't find anything. Then we realised the orange bar LED wasn't lit up.

So we plugged it into my laptop to see if windows found it and the light fired on. So we tried it again and found it like a charm..


But when its creating the ext3 file system it seems to get stuck at 33%.. We aren't sure if its loading or froze. Would the usb 2.0 be slower causing the partitioner to be sluggish?

---

### Post by logos34 on 2007-12-24
it shouldn't be that much slower...something is wrong if it's freezing...If nothing changes try burning the iso to disk again (slow--2x - 4x),,,check the md5sum if you haven't already

since you're doing this from laptop instead (which has an internal hard disk), be sure to change the grub location to (hd1) or /dev/sda (or sdb depending on how it detects the internal drive)

---

### Post by agentorannnge on 2007-12-24
We checked the integrity and it said something about a md5check sum error.

I'll try burning again slower but while I do that can you explain this md5check?

---

### Post by logos34 on 2007-12-24
> **agentorannnge said:**
> We checked the integrity and it said something about a md5check sum error.

 can you explain this md5check?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by agentorannnge on 2007-12-24
Okay I compaired the check sums and they are different... 

Here is the one for the ISO:
7d88cd87df509a740d9f47b9bbf1375e

Here is the one given from ubuntu:
9a4ae3cfd68911a861d094ec834c9b48

I checked it with winMd5Sum and mismatched. But now what do I do? I tried re-downloading it like 3 times. If someone is willing to walk me through this leave your AIM..

---

### Post by logos34 on 2007-12-24
Try a different mirror or disable any download accelerators you may be using (for instance, like fasterfox).

---

### Post by agentorannnge on 2007-12-24
We tried redownloading it from another mirror and without any accelerators but the partitioner still freezes at 33%..


Is there anyway to pre-partition the harddrive and skip that step?

---

### Post by logos34 on 2007-12-24
> **agentorannnge said:**
> We tried redownloading it from another mirror and without any accelerators but the partitioner still freezes at 33%..

Is there anyway to pre-partition the harddrive and skip that step?

Use Gparted (on the ubuntu live/desktop CD or the Gparted live CD)

---

