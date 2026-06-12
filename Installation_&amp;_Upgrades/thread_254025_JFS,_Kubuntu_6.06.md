---
title: "JFS, Kubuntu 6.06"
date: 2006-09-09
forum: Installation &amp; Upgrades
---

### Post by alexeys on 2006-09-09
Hello!

Is it possible to install Ubuntu/Kubuntu on JFS as root filesystem?

Last time I have problems with this - installer just can't install GRUB properly and installation seems to be incomplete after. I tried both graphical and text installers.

I've met similar problems with XFS when was trying it before...

It seems to me installer wants /usr to be on ext2/3. Finally, I install system with / as ext3 and /home as JFS, then create new partion with JFS, moved all stuff from /usr there and changed fstab to mount it as /usr. But is there simpler way?

---

