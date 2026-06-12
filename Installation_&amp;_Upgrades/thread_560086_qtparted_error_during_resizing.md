---
title: "qtparted error during resizing"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by agb1970 on 2007-09-25
Hi.

I'm trying to install gutsy on a lenovo thinkpad r61. While trying to shrink my windows xp partition using the live cd the error from qtparted is:

Failed to check /dev/sda1 mount state. No such file or directory.

As suggested in a thread I found I tried disabling hibernate and setting the swap size to zero, but to no avail. I have not been able to find any other advice, hence this post.

---

### Post by Pumalite on 2007-09-25
Use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) (the stand alone, burn to CD, boot from, program)

---

### Post by agb1970 on 2007-09-25
Thanks for the prompt reply. I'm downloading gparted now.

One other basic question. Once the free space has been created (assuming gparted works), should I use gparted to create two new formatted partitions in the free space (i.e., root and swap)? Or should I just leave the space free/unallocated--that is, will the installer create the root and swap partitions?

---

### Post by Pumalite on 2007-09-26
In the new partition; give 10 GB to'/', 500 MB to /swap and the rest to /home.

---

