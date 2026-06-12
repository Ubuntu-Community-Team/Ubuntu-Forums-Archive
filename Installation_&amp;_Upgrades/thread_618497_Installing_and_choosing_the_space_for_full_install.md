---
title: "Installing and choosing the space for full install"
date: 2007-11-20
forum: Installation &amp; Upgrades
---

### Post by delilahjed44 on 2007-11-20
Hey, I am installing Ubuntu...on the resize the disk, where it tells you the size, I see 64 and that the lever is in the middle, Now, I am doing a full install, so,,,do I need to move that lever all the way over to the right? as I will use Ubuntu only...I dont remember fulling with this when I originally installed Edgy, but I am re-installing 710 and I want the space partitioned correctly?

  I am installing now, its the choice directly after choosing  your region.
  Thank you
   Sherri

---

### Post by kidders on 2007-11-21
Hi there,

My advice would be not to feel like you *have* to allocate _all_ your disk space, just because it's there. You can always create more partitions in the future if your Ubuntu needs them, whereas freeing & reassigning space that's already been allocated can be risky & awkward.

You never know what you might want a little extra space for in the future (maybe more swap, a second OS, an encrypted filesystem, or some such thing), or what filesystem type you'll want to use (Ext2, FAT32, ...), so I would suggest taking a stab at how much you think "enough" is, and leave the rest free.

---

### Post by Pumalite on 2007-11-21
If you want Ubuntu alone in your computer, you can have it. I congratulate you. Get Gparted live CD and partition your whole drive. A good scheme:
10 GB for '/'
2x RAM up to 1 GB
The rest for /home
Having home in a separate partition means you can keep your settings and all kind of goodies for future reinstallation. You can make a separate partition for 'data', but it's not necessary since you'll be in Linux all the way.

---

