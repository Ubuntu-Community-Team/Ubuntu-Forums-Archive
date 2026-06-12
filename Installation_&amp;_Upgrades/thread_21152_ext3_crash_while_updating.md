---
title: "ext3 crash while updating"
date: 2005-03-20
forum: Installation &amp; Upgrades
---

### Post by alexisg on 2005-03-20
Hello,

I've got a big problem with my ubuntu... I've upgraded if from warty to hoary. Recently, when I wanted tu update with synaptic, the process managing the EXT3 filesystem might have crashed and I couldn't write on it anymore. So the update did not finish. Now, when I reboot my computer, I get a kernel panic and that error:

"EXT3-fs error (devide hda1):ext3_find_entry: reading directory #587521 offset 0 exec: 429 chroot: not found
Kernel panic: Attempted to kill init!"

I tried to format my hda1 partition, reinstall warty and upgrading to hoary, but I still get the same problem!

I can boot the system in recovery mode, but / is mounted in read-only so I can't do anything with it...

Does anyone has the same problem? Did you find how to solve it?

Is it possible to finish the upgrade from an other system? I mean I could use the ubuntu live CD and run dpkg to finish the update, but I don't know how to connect dpkg to an other package database...

---

