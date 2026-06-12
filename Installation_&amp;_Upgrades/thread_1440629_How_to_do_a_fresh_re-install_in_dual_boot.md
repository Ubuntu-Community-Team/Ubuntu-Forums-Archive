---
title: "How to do a fresh re-install in dual boot?"
date: 2010-03-27
forum: Installation &amp; Upgrades
---

### Post by Satchmo2 on 2010-03-27
Hi, so I need to re-install ubuntu but I also have windows on the same computer(GRUB). Can I just boot from cd? Is there and option in the live cd for reinstalls or do I have to destroy the partition?

Thanks in advanced.

---

### Post by l.billon on 2010-03-27
Hi!
Just remove all the Ubuntu partitions during installation, Grub will regenerate a new MBR at the end of the installation and you will be able to access bothe the new Ubuntu and windows.

---

### Post by Satchmo2 on 2010-03-27
Thanks, this forum must have a lot of people, it's pretty fast!

---

### Post by ajgreeny on 2010-03-27
Just make sure you have backed up any files in home first as all will be lost.

Actually now could be the right time to start with as separate /home partition.  Just choose manual partitioning at that point of the install and make three partitions, a 10GB /root, a swap of about 2GB, depending on your ram amount, (2x ram was once the rule, but probably not needed that large any more) and the rest /home.  It will all appear sea,less once installed but makes life so much easier in future installs and distro version upgrades, eg to 10.04 in a few weeks.

---

