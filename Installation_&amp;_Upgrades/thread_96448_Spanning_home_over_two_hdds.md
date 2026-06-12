---
title: "Spanning /home over two hdds"
date: 2005-11-28
forum: Installation &amp; Upgrades
---

### Post by madtinkerer on 2005-11-28
Is it possible to span /home over 2 hdds?  I have 2 80gb hdds that I'm going to use for a file server.  I have 25 users or so and I want to assign each one some /home space so I need both hdds to accomplish.  Could someone tell me how and when to do this during the install process?

Thanks

---

### Post by g-a-c on 2005-11-29
As far as I know, the only way to concatenate two disks into one mount point would be to make the disks (or partitions thereof) into a RAID0 array. This obviously comes with the usual warnings (one disk dies, you lose 2 disks worth of content etc)...

---

### Post by kosmic on 2005-11-29
Yes you can use LVM to span the data in two disks like with was only 1

---

### Post by g-a-c on 2005-11-29
Oh, is that what LVM does? I'm only vaguely familiar with it because it's used by default in the newest Fedora Core/CentOS distros, but I've never really seen an explanation of what it does.

Oops :)

---

