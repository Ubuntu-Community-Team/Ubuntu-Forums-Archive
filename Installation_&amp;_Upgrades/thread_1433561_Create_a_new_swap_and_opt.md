---
title: "Create a new swap and /opt"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by Data-Base on 2010-03-19
Hello,

I have a server that is installed on a single disk in a VM
now I add 2 disks to the VM

I want to move the **swap** to one and the **/opt** to the other one

how I can do that? I need that for learning and to have more knowledge in Linux

any suggestions?


cheers

---

### Post by madverb on 2010-03-19
You can do it with fstab.

Just need to make the partition a swap partition and mount the other as /opt

Just copy everything from the currect /opt to the new partition.

---

### Post by tom4everitt on 2010-03-19
fstab guide:

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

If you mount a partition at /opt you will see the contents of that partition under /opt, rather then the content you had there before. So first copy what you have in /opt to the new partition, then you can add a mount for it.

---

