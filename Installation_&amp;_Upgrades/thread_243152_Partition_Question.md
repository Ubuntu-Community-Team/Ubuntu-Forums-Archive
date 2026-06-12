---
title: "Partition Question"
date: 2006-08-24
forum: Installation &amp; Upgrades
---

### Post by Kinny on 2006-08-24
I have a computer with 2 hard drives. I have Win XP Pro installed on the 1st drive (master) and I want to install Kubuntu on the second (slave) drive.  I've check some of the sites that help with dual boot installation but I haven't seen that scenario.

Is this possible and will the graphical installer handle this environment?

TIA

---

### Post by zxee on 2006-08-24
Are these IDE, Sata or one of each? SATA drives can sometimes cause problems.
If these are IDE/ATA drives everything should work provided there are no hardware incompatibilities. Grub (the linux bootloader) will normally "see" your windows install and set up a menu listing for it.

---

### Post by Kinny on 2006-08-24
Both drives are EIDE. The one I was going to install ubuntu on is NTFS but I can delete the partition before installing if the installation would go better/faster.

---

### Post by reg-br on 2006-08-24
That's my current system, 1 hd for ubuntu, 1 for xp. I disconnected the xp hd and connected the old hd, installed ubuntu without problems, then i put the xp back. Both hds are using the same data cable, in the bios setup i choose which i want to boot from. There were no problems, i can also access the xp file (ntfs) booting in ubuntu from the terminal. You can do access linux data from xp also, using fs-drive (fs-drive.org).

---

