---
title: "Dual Boot!!!!"
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by castro_manolo on 2007-11-17
I have windows xp intalled on disk 0. Then installed ubuntu on disk 1 with dual boot (i think lilo), had no problems booting as I had the chance to choose wich OS to load. Then I had to reinstall windows and now I can't load linux anymore. Anybody can help me please?

---

### Post by Herman on 2007-11-17
Hello castro_manolo,
You should able to use Super Grub Disk to boot Ubuntu with, (I don't know of any  Super LiLo Disk), and then run [Run Liloconfig]("http://users.bigpond.net.au/hermanzone/p4.html#Run_Liloconfig") to install LiLo to MBR again.
That would be the easiest. :)

If you want to do it by a fancier method you could use your Ubuntu Live CD and mount the hard disk installed Ubuntu file system, chroot and re-install LiLo, here's how, [Install Lilo from a Linux Live CD]("http://users.bigpond.net.au/hermanzone/p4.html#Install_Lilo_from_a_Linux_LiveCD")...An emergency method for installing Lilo. (Even works for an non-bootable Ubuntu installation) :)

Regards, Herman :)

---

### Post by castro_manolo on 2007-11-17
Thank you very much Herman... :):):)

---

