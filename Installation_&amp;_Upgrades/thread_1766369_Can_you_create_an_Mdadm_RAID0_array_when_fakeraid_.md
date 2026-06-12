---
title: "Can you create an Mdadm RAID0 array when fakeraid is enabled?"
date: 2011-05-24
forum: Installation &amp; Upgrades
---

### Post by kevpatts on 2011-05-24
I'm looking to shrink my windows partition on a raid0 array and create a mdadm ubuntu partition using raid0. Is this possible? can I just ignore the /dev/mapper device and use the standard /dev/sdx devices?

---

### Post by psusi on 2011-05-24
Absolutely not.  You can not mix software raid and fakeraid on the same disks, and you can not mess with the underlying disks while they are being used for raid ( unless you want to corrupt your filesystem ).

---

### Post by kevpatts on 2011-05-25
Thanks. That's what I expected. Just went with Linux RAID1 instead.

---

### Post by psusi on 2011-05-25
Don't forget to actually delete the fakeraid array in the bios utility.  Simply disabling the bios utility leaves the raid metadata on the disk intact and so Ubuntu will still recognize it.

---

### Post by kevpatts on 2011-05-25
Thanks psusi, yeah, I noticed this in my first install run. Removed the array and it worked fine. Had to use the alternate install CD though.

---

