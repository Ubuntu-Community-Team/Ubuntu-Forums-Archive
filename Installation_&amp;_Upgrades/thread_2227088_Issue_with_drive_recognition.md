---
title: "Issue with drive recognition"
date: 2014-05-30
forum: Installation &amp; Upgrades
---

### Post by jordan21 on 2014-05-30
So, some background: I installed Ubuntu on my laptop (on a SSD) ~2 months ago. I remembered a couple of days ago that there was some data (some old writings, Word docs and the like) on my old Windows hdd I wanted to recover, so I removed the ssd and swapped to the old hdd again. I got my data, took the old drive out and put my ssd with Ubuntu back in the laptop.

My issue lies in the drive now being unrecognized by even my BIOS, preventing me from selecting it in boot order (it's not available for selection). So, in my limited knowledge of things not Windows, I come here in a plea for assistance. Any insight into the problem, and obviously solutions, I greatly appreciate in advance.

---

### Post by ubfan1 on 2014-05-30
Are you sure the SSD is plugged in properly?  If the BIOS can't even see it, this is not really an Ubuntu problem.

---

### Post by jordan21 on 2014-05-30
Yes, it's seated firmly and mounted properly in the bracket. I suppose it's not out of the question that the drive died, but I want to make sure there's not some chance that dismounting a drive with Ubuntu on it and interrupting some sort of hardware congruency would be, for some reason, detrimental.

I'll connect the drive to my desktop to see if it's recognized, that should at least lend to knowing if it's hardware fault or not.

---

### Post by ubfan1 on 2014-05-31
Is this a UEFI machine?    If so, maybe the nvram entry was removed at some point -- I've heard of other devices disappearing.  Never saw such behavior myself, but maybe  with the device plugged in you can get to the UEFI settings/BIOS and "add a boot entry" some way.  I suppose efibootmgr could do it but I'm not sure what to call the device.

---

