---
title: "Possible solution for using a Promise FastTrak TX4310 RAID card?"
date: 2011-03-23
forum: Installation &amp; Upgrades
---

### Post by SiliconDragon on 2011-03-23
I've found that Ubuntu doesn't properly recognize disks attached to a Promise FastTrak TX4310 RAID5 card. I have a possible solution, but I could sure use  some feedback from people more experienced with 'nix and drivers. Please advise?

Promise has TX4310 drivers for SUSE and RHEL4 (note: I've never heard of that one before), but their support person said that their open source drivers should be ok to compile with any version of Linux based on the 2.6 core. Therefore, I'm wondering if these open source drivers could simply be recompiled for Ubuntu and used?

Please excuse my ignorance with this as I'm new to 'nix having 30 yrs experience only with big iron and Windows. I'm ramping-up quickly, but haven't been down the path of compiling drivers yet, not like it'd stop me.

Does this idea make sense? 
Has anyone tried it?
Please help if you can as I'd *really* hate to go back to Windows box simple because of a lack of Promise driver support.

Thanks in advance for anyone helping, it's greatly appreciated!
SD

PS My array currently resides on a Windows 2000 Server box which needs recycling, and I *strongly* prefer Ubuntu over SUSE for a file server.

---

### Post by Malcont3nt on 2011-08-21
I've got the same card and driver issue.  I've been trying to use make for two days and I cannot figure out where the new locations of certain files are.  The code from Promise's website is built against an older version of the kernel.

I have discovered that config.h is no more, but I can't find what the new file is for the current kernel.

---

