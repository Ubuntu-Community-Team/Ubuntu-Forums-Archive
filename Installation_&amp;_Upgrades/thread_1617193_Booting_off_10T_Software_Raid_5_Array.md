---
title: "Booting off 10T Software Raid 5 Array"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by roddersg on 2010-11-09
I am building a NAS with 10*1T hard disks using a software Raid 5 configuration on Ubuntu 10.04LTS.

If I follow the instructions for software raid and have 2 partitions per disk (512M-swap, 20G-raid volume) and install Ubuntu using Software Raid 5 (mdadm), there are no problems booting the system.  However, when I redo the partitions to include the entire disk (913GB raid volume), the system refuses to boot and I end up with the grub rescue> prompt which leads nowhere.

Further research has shown that I need to re-partition my hard disks using GPT to get over the 2T limits per volume, and on some recommendations, I need to create a small BIOS-BOOT partition.

Can someone advise:
a) should I repartition everything in GPT (including swap) and is there any recommendations for sizing.
b) can I create tbe BIOS-BOOT in the md0 partition, and again any recommendations
c) should I create one large raid and place swap in md0 there, alternatively.

Any help would be useful,

Thanks

---

