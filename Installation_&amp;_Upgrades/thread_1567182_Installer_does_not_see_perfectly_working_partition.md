---
title: "Installer does not see perfectly working partitions"
date: 2010-09-03
forum: Installation &amp; Upgrades
---

### Post by Menti on 2010-09-03
Hello all, I am totally puzzled by a weird issue.

I have two hard disks, the one that I work with and another one for backups. The main HD had an OS (Ubuntu) partition, a partition for /home and a lot of free space.

I installed latest Mandriva creating a new partition. Everything OK. But it overwrote GRUB and I couldn't boot into Ubuntu, so I reinstalled GRUB from the Ubuntu live CD. I got my Ubuntu back, but then it wouldn't boot into Mandriva. Well, I didn't care. But now the problem comes.

Right now, if I try to install Ubuntu from live CD, the installer won't see the partitions in my main drive. It sees the partitions in the backup drive, but the main drive appears as empty, no Ubuntu, no Mandriva, and no /home. Debian testing installer did just the same. Those partitions are there and I can boot into them and see them; it's only the installer that does not see them.

Anyone has any idea on this? I become a terrified newbie when it comes to partitioning.

---

### Post by quixote on 2010-09-05
Strange.  Once you boot into ubuntu -- which if I understand right, you can do now? -- did you ever run```
sudo update-grub
```If so, it should have found your Mandriva partition.  If not, that's why it's not there.

As for the installer behavior, I can only assume that somehow when the bootloader was overwritten, it changed something the installer looks at, but not other things, like grub, which also needs to know what the partition table looks like.  I suppose you could reinstall the Master Boot Record, but it seems a shame to mess with that if everything else is working.  ??

---

### Post by srs5694 on 2010-09-06
See [this page](http://www.rodsbooks.com/missing-parts/index.html) I wrote about this problem. I can't guarantee that the cause is the same for you, but chances are it's at least similar.

---

