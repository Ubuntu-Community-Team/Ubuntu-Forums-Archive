---
title: "&quot;GRUB loading, please wait...&quot; I don't think this waiting is going to end..."
date: 2007-02-05
forum: Installation &amp; Upgrades
---

### Post by Ish on 2007-02-05
Installed Ubuntu 6.10 on my computer, while instaling I lost windows XP and all my data... No biggie, but I can't even start Ubuntu because it is hanging when it says:
"GRUB loading stage1.5.
GRUB loading, please wiat..."
I have waited for quite a while but I don't think it's ever going to load... Solutions?

I had FakeRAID running in 0 for my windows and I finally just elected to erase windows and reinstall it later once I got Ubuntu running. But Ubuntu isn't running, not yet. The Harddrives in the BIOS said RAID 0, and I think it might still be trying to run in RAID, but I'm not sure how to change it... A thought. Not sure if that's the culprit of this hang... :/

---

### Post by Delta_Farce on 2007-02-05
If you're using highpoint raid or nvidia raid then you're likely to have a seperate BIOS for the raid array. My machine has a setup like that.

To disable raid, you first have to disable the array in the raid controller and then in the BIOS. Your motherboard manual should tell you how to do this. If you've lost the manual, most motherboard makers have copies of their manuals on their web sites.

Basically, when it's done properly you should be able to define your boot devices as drive C, D, SCSI, or whatever they are.

Cheers,

Mark

---

