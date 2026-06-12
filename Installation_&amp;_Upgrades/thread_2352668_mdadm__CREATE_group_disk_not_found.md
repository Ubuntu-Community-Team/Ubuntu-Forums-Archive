---
title: "mdadm : CREATE group disk not found"
date: 2017-02-14
forum: Installation &amp; Upgrades
---

### Post by arbiel-perlacremaz on 2017-02-14
Hi everybody, and thank's to reading my post and trying to help me.

The context : Ubuntu 14.04 64bits, clear (uncryted) LVM and crypted logical volumes (/, /home and some other ones) on a one by one basis, no RAID.

After I accepted proposed modifications by the modification manager, which upgraded the kernel from 3.13.0-106-generic to 3.13.0-108-generic I'm unable to restart my system, which loops on a "mdadm : CREATE group disk not found". Kernel 3.13.0-106-generic is still working.

The loop goes that way (I remove the message timestamp)

scsi 7:0:0:0 Direct-Access Generic-Multi-Card
sd 7:0:0:0 Attached scsi generic sg3 type 0
mdadm : CREATE group disk not found
mdadm : CREATE group disk not found
mdadm : CREATE group disk not found
sd 7:0:0:0 [sdc] Test WP failed, assume Write Enabled
sd 7:0:0:0 [sdc] Asking for cache data failed
sd 7:0:0:0 [sdc] Assuming drive cache : write through
mdadm : CREATE group disk not found
mdadm : CREATE group disk not found
mdadm : CREATE group disk not found
sd 7:0:0:0 [sdc] Test WP failed, assume Write Enabled
sd 7:0:0:0 [sdc] Asking for cache data failed
sd 7:0:0:0 [sdc] Assuming drive cache : write through
&#8230;

Arbiel

---

