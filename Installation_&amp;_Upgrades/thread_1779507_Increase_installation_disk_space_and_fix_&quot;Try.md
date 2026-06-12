---
title: "Increase installation disk space and fix &quot;Try hd(0,0): NTFS5: No wubildr&quot;"
date: 2011-06-10
forum: Installation &amp; Upgrades
---

### Post by DeliriumGHS on 2011-06-10
Hello.

I have installed Ubuntu through Wubi and now I want to increase the space of the installation from 30gb to 50~. Is there any way to do this through Ubuntu?

Also before GRUB is loaded I'm getting this message: ***Try hd(0,0): NTFS5: No wubildr***

Is there any way to fix that?

Thanks in advance.

Delirium.

---

### Post by bcbc on 2011-06-10
You probably could... but why do it? The virtual disk wubi uses is less reliable than storing files directly on the physical partition. And you have access to the windows /host partition already. So just store all those big media files there.
1. it's reliable
2. you don't have to do anything special

Wubi is great to try out Ubuntu without partitioning, but it's not intended to be used for ever. Although I've never personally lost a the virtual disk (root.disk), it's happened to others due to perhaps a hard shutdown.

That said, there are some options available [here]("https://wiki.ubuntu.com/WubiGuide#How do I resize the virtual disks?")


Regarding that "Try..." message. It's not an error. There's nothing to fix. Wubi uses grub4dos to boot and it looks on all partitions for the wubildr file. For every partition it looks on that doesn't have it (in the root), it issues that message.
You could mount /dev/sda1 and copy wubildr to it, but unless it's hanging for a long period of time, I wouldn't bother.

---

