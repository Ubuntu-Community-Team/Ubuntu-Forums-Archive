---
title: "How to move /tmp into tmpfs?"
date: 2011-04-01
forum: Installation &amp; Upgrades
---

### Post by mikeym on 2011-04-01
Hi,

I'm in the process of installing Ubuntu 10.04 (actually EasyPeasy) onto my Eeepc 900. I'm replacing the version of Arch I had before. 

In my previous setup I had moved my /tmp folder into RAM to reduce the number of writes to the disk. This was done with a line in my */etc/fstab* like so:

```

none                   /dev/shm      tmpfs     nodev,nosuid,size=256m        0      0
none                   /tmp          tmpfs     defaults,size=256m  0      0

```

Now I noticed that there are some *tmpfs* mounts out of the box on Ubuntu that don't appear in *fstab*, so what's the Ubuntu way to mount /tmp as *tmpfs*?

---

