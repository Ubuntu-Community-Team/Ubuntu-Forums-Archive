---
title: "Feisty fails to boot/install on AMD690 + X1250 based machine"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by mikelink on 2007-07-04
I have been using Ubuntu on a variety of machines for a fair while now. However, I simply cannot get Feisty to boot (and therefore cannot install) on my new AMD690+X1250 based machine. 

I can boot from the CDROM, select "Start Ubuntu" and the kernel is loaded (I remove the kernel parameter "quiet" from the standard options so I can watch what happens.) After about 30s, the boot process hangs, with the final log statement from the kernel being "attached scsi generic sg5." 

I have not managed to capture this log to a file for obvious reasons.

The machine works perfectly and came pre-installed with Vista. Any pointers as to how I can work around this would be appreciated. What is the next step the kernel takes after attaching scsi devices? Thanks.

---

