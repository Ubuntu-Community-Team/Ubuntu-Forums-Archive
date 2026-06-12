---
title: "AMI Megaraid not loading after upgrade"
date: 2005-10-22
forum: Installation &amp; Upgrades
---

### Post by bubba on 2005-10-22
My /etc/mkinitrd/modules file from hoary was:

megaraid
scsi_mod
sd_mod    

and the modules available for megaraid for kernel 2.6.10-5-686 were:

./kernel/drivers/scsi/megaraid.ko                                               

Now, megaraid is not detected/loaded at boot for the new breezy kernel (2.6.12-9-686).   Same options in mkinitrd modules, but now there are additional megaraid modules (I have a MegaRaid i4 - Dell Cerc ATA RAID card):

./kernel/drivers/scsi/megaraid.ko
./kernel/drivers/scsi/megaraid
./kernel/drivers/scsi/megaraid/megaraid_mbox.ko
./kernel/drivers/scsi/megaraid/megaraid_mm.ko               

Just wondering if I should try adding these, or if something else may be causing the problem.  Booting into the hoary kernel (2.6.10-5-686) loads everything fine, but I'd like to go ahead and this 2.6.12 kernel working.

Any tips for getting this going?

Thanks,
Bubba

---

### Post by bubba on 2005-10-22
FYI, this kernel is BOTCHED.  I went back to 2.6.10 and things are fine.

Please fix the kernel issues folks.

---

