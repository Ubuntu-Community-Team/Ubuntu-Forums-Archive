---
title: "partitions not included in &quot;computer&quot;"
date: 2005-04-16
forum: Installation &amp; Upgrades
---

### Post by Turin Turambar on 2005-04-16
Why didn't I get fat32 and ntfs partitions mounted by default?
I did that manually with fstab, but those partitions still do not appear in "computer"! What shall I do?

Oh yeah, where can I get the boot log? I tried in /var/log, but didn't find it there. Thanks

---

### Post by hagman on 2005-04-16
Hi,

Maybe you can post your /etc/fstab so that we can have a closer look on that.
Did you try to mount the partitions manually? Did it work?

Cheers,

Helge

---

### Post by Turin Turambar on 2005-04-16
[QUOTE=hagman]Hi,

Maybe you can post your /etc/fstab so that we can have a closer look on that.
Did you try to mount the partitions manually? Did it work?

Cheers,

Helge[/QUOTE]

Unfortunately, I cannot post fstab (I still don't have internet in Ubuntu :( ). I mounted the partitions manually and I can access them via /media/xyz, but I don't have them visible in "Computer".

---

### Post by hagman on 2005-04-16
Try to modify your /etc/fstab to mount the partitions automatically, so you should see them in "Computer" after rebooting.

Cheers,

Helge

---

### Post by Turin Turambar on 2005-04-16
But I did. I added them in the fstab and they load on boot with RW status. However, they do not appear in "Computer".

In order to access them I have to go to /media/xyz.

---

### Post by Turin Turambar on 2005-04-16
Got it.
I needed to add option "user" for each partition.

---

