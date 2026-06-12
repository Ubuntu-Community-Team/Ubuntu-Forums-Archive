---
title: "Combining HDDs?"
date: 2006-04-03
forum: Installation &amp; Upgrades
---

### Post by pseudo1 on 2006-04-03
I originally setup my Ubuntu mail server with / on one 40GB drive and /var on another 40GB.

I would now like to combine these into one drive.

Is this possible? If so, what is the best way?

---

### Post by Ptero-4 on 2006-04-03
I don't know if this works without formatting your root or var partitions. But you may create a RAID array that puts together those two HD's. You may need to remove one of the partitions and extend the other to cover the entire array, or you may need to remove both partitions and format with a special filesystem, but since I haven't made RAID's yet I don't know exactly how it works.

---

### Post by pseudo1 on 2006-04-03
I would ideally like to do this without any type of RAID setup.  I have plenty of blank hard drives laying around and I was hoping there would be some way to copy the contents of both HDDs to a new one and edit the fstab to make it all work.

---

### Post by tribaal on 2006-04-03
Well I don't know if this is what you were thinking about, but I believe you could just format the disk to ext3, and then use the mount command to mount the new partition somewhere in your directories?

Kind of a kiddish explanation, but I'm at school so I can't check out on ubuntu... :(

Hope this helps anyway

---

