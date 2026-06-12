---
title: "ext3 partition rw root only"
date: 2005-09-28
forum: Installation &amp; Upgrades
---

### Post by markr on 2005-09-28
Hi ,


During the installation I setup a spare ext3 partition to /data (i contains all my docs/music etc which I also access via WinXP using the funky IFS tool).  However, it only mounts as rw for root.

I've change the /data to chmod 777 to no avail.

My fstab lines reads:

/dev/hdc4      /data      ext3      defaults,rw,user    0     0

Any help appreciated.

Thanks

Mark.

---

### Post by markr on 2005-09-28
Fastest way of fixing this is to "chown" the entire disk structure so that my user owned it.  I can then read and write:

sudo chown -R markr /usbdisk

---

