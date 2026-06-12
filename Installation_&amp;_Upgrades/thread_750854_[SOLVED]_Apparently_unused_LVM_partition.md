---
title: "[SOLVED] Apparently unused LVM partition"
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by brilyant on 2008-04-09
This system is dual-boot, originally Windows/Fedora, now Windows/Ubuntu (Gutsy).

I have unexpectedly run out of disk space.  Digging around I have discovered an LVM partition which I never new existed, and which comprises most of the disk space.  Perhaps it was created during the original Fedora install.  I think that this is entirely unused, so I want to pop /home and /var in there.

I have no experience of administering LVM. Can I assume that if there is no mention of the partition in /etc/fstab and /etc/mtab it really is unused by the Ubuntu installation, or doesn't LVM show itself in these files?

Thanks for reading this far.

---

### Post by Rocket2DMn on 2008-04-10
The chances are it's not used by Ubuntu or Windows, so you should be safe to do whatever you want with it.  Fedora uses LVMs by default, so that is probably where it came from.  I would do your work using the GParted LiveCD - [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)
You have a few options:
1) delete the LVM and grow your root partition to use the extra space (if the 2 partitions are side by side)
2) delete the partition and use it for /home - see here: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
3) delete the partition and create 2 new ones out of it for /var and /home like you originally wanted.  Having separate partitions for locations like /var, /usr, and /boot are not very common in Ubuntu, but you should be able to do it just fine as long as you can get the data moved correctly.

As always, you should backup your important data before fiddling with partitions.

---

### Post by brilyant on 2008-04-10
I had worked out some of that piecemeal from various web sources, but you've no idea how reassuring it was to read it all at once.

---

