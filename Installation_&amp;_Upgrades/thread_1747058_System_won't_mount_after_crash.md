---
title: "System won't mount after crash"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by djpeebz on 2011-05-02
Hi,

After my computer crashed due to an electrical failure in the house, every time I try to boot up (I'm using Ubuntu 10.04) I get the following error:

mount: mounting /proc on /root/proc/ failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init= bootarg.

I'm then put into initramfs

Looking at the forums, I assume that this is because the system wasn't unmounted properly but I haven't been able to find the best way to solve this problem.

Any help would be much appreciated.

---

### Post by lechien73 on 2011-05-02
Hi and welcome to the forums :)

I would try booting in from a Live CD and then running e2fsck against the affected drive. Do you have your files backed up?

The command I would use is:

```
e2fsck -f -y -v /dev/AFFECTED PARTITION
```

Where AFFECTED PARTITION would be sda1 etc.

---

### Post by djpeebz on 2011-05-02
Many thanks indeed - the problem is solved!

I did have my stuff backed up (thank goodness :) )

For others reading this with the same problem, I booted from the live cd and then worked out which partitions I had and which needed checking (I've a dual-booting machine) using the Disk Utility program and then ran the 'check filesystem' command.  This came back with 'file system not clean' so then I ran the command you gave me on this partition.

The command corrected the errors and so when I rebooted all was fine!  Many thanks again for your swift and unbelievably helpful reply.

All the best.

---

