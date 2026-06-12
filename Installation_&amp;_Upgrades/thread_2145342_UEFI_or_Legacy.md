---
title: "UEFI or Legacy"
date: 2013-05-15
forum: Installation &amp; Upgrades
---

### Post by JonPaul on 2013-05-15
Hello

I have just installed Ubuntu RR on an Acer Aspire E1 after having removed Windows 8.:D
I changed the Bios to Legacy and it installed fine and is working fine.
Are there any advantages to trying to get Ubuntu to boot in EFI?
I have read how to do it but I can't find out why I would want to.
Is there any performance improvement to be gained with EFI?

Thanks

JonPaul

---

### Post by bluenova on 2013-05-15
I'm not completely up to speed with EFI but I think you'd only need it if your boot drive is bigger than 2 TB.

---

### Post by fantab on 2013-05-15
BIOS/ Legacy Boot had been around for more than 30 years and is unable to address the latest hardware efficiently, to put it simply. UEFI addresses all the newer hardware without limitations, so far. It is the FUTURE. Gradually, but sure we will move to UEFI's only. Similarly, "msdos" partition table or lets again use the word 'legacy' partition table has its limitations, the most glaring of which is only Four Primary partitions Limitation, another is that it cannot handle HDD/Disks more than 2.2TB. So if you have a, say 2.5TBHDD you cannnot use "msdos" partition table. To address these limitations and more we now have GPT/GUID partition table. You can have more than 100 primary partitions easily. 

The deal between UEFI and GPT is that GPT is a subsystem of UEFI. Together they are the future. So is 64bit OS.
We still have large number of 'old'/'legacy' computers that is why we still have OS supporting both. It will change. Perhaps, IMO, not in another 5 years but it will. 

You can seach www for more info on UEFI (**Unified Extensible Firmware Interface**) and GPT (**GUID Partition Table**).

EDIT: Ubuntu can boot from GPT in both BIOS and UEFI mode. Windows can't. And I don't think even 32bit OS can boot from GPT, though I am not sure.

My two cents....

---

