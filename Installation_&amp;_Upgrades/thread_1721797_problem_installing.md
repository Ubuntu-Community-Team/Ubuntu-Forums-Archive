---
title: "problem installing"
date: 2011-04-05
forum: Installation &amp; Upgrades
---

### Post by Eddie_E on 2011-04-05
Hello, I attempted to install Linux for the first time using Wubi. I tried installing it both online and using a burned iso disk . The installation seems to run OK but but when I boot and choose Ubutu I get the following message "The selected entry could not be loaded because the application is missing or corrupt" It appears the file it's looking for is wubildr.mbr. That file was on both my C drive and the CD that I burned. I was able to boot in Windows 7, 64bit without any problems. Can anyone please tell what I may be doing wrong? Thanks

---

### Post by bcbc on 2011-04-05
This is possible if you have an older bios and the file C:\wubildr.mbr is physically > 137GB from the start of the disk. If that's the case you can try defragmenting but there's no guarantee it won't happen again (because the wubildr file has the same constraint.)
You can rule out this if your drive is < 137GB (or the entire C: partition falls < 137GB) or your BIOS can see > 137GB.
But it's always a good idea to run chkdsk and defrag before trying wubi.

---

### Post by Eddie_E on 2011-04-05
> **bcbc said:**
> This is possible if you have an older bios and the file C:\wubildr.mbr is physically > 137GB from the start of the disk. If that's the case you can try defragmenting but there's no guarantee it won't happen again (because the wubildr file has the same constraint.)
You can rule out this if your drive is < 137GB (or the entire C: partition falls < 137GB) or your BIOS can see > 137GB.
But it's always a good idea to run chkdsk and defrag before trying wubi.
 
Thanks I'll try defraging and see if that helps. I have a newly built system with a new model motherboard and the latest bios so that should not be an issue.

---

### Post by Eddie_E on 2011-04-05
OK I tried chkdsk and defragging. I still have the exact same problem. I even tried installing it on a USB 3.0 external hard drive and I get the exact same error. Her is a screen shot of the error.  [https://picasaweb.google.com/ehicks54/WubiError?feat=directlink](https://picasaweb.google.com/ehicks54/WubiError?feat=directlink)  Any other suggestions please?
 
System configuration:
 
CPU - Intel i5 2500K
Motherboard - ASUS P8P67 Pro
Graphic card - XFX, ATI Radeon HD 5750
Memory - ADATA XPG DDR3 1600  2x4GB
Hard drive - Western Digital WD5000AAKS 500GB  
Optical drive - LG Blu-ray disc rewriter WH10LS30

---

### Post by bcbc on 2011-04-05
I should have picked up that you mentioned windows 7. So it doesn't refer to C:\wubildr.mbr. What's happening is that it's trying to call the one on your USB in the \ubuntu\winboot folder (or that you had previously in C:\ubuntu\winboot\wubildr.mbr

And you're right a new motherboard shouldn't have those issue with the 137GB limit.

So... not really sure where to go from here. I'll dig around... but I'd refer to Microsoft's instructions for bcdedit to check that the entry is setup correctly. Also check google for grub4dos issues similar to this - e.g. referring to grldr.mbr - since wubildr.mbr == grldr.mbr with a different name.

I'll look around as well.

---

### Post by Eddie_E on 2011-04-05
> **bcbc said:**
> I should have picked up that you mentioned windows 7. So it doesn't refer to C:\wubildr.mbr. What's happening is that it's trying to call the one on your USB in the \ubuntu\winboot folder (or that you had previously in C:\ubuntu\winboot\wubildr.mbr
 
And you're right a new motherboard shouldn't have those issue with the 137GB limit.
 
So... not really sure where to go from here. I'll dig around... but I'd refer to Microsoft's instructions for bcdedit to check that the entry is setup correctly. Also check google for grub4dos issues similar to this - e.g. referring to grldr.mbr - since wubildr.mbr == grldr.mbr with a different name.
 
I'll look around as well.
 
 
Thank you very much. At least I have sommething else to search for. I may just try to install it on my Windows XP laptop just to get a feel of it.

---

