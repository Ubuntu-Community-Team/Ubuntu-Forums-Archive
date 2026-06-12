---
title: "Hoary (array 6) won't automount sata drive during boot"
date: 2005-03-09
forum: Installation &amp; Upgrades
---

### Post by merc on 2005-03-09
This is really weird. Here is my config:

/dev/hda2       mounted as /
/dev/hda3       mounted as /swap
/dev/sda2       mounted as /home

In the /etc/modules, I added "sata_via", which is the module for my motherboard.

Now, during boot, when it calls the "checkrootfs.sh" script, everything goes well. Next it does some other stuff, then the "checkallfs.sh" script, and gives an error saying "can't get to /dev/sda2", please fix yourself" (or something to that effect), and drops me to a temp shell. I have to hit Ctrl-D to continue booting. Then it says at the end "setting /home=/"

But immediately after logging in, if I do a "mount -a" (as root), then I can get to /home on /sda2. But without the mount -a command, I can't get to it. But "fdisk -l /dev/sda" does list the partitions correctly.

Any thoughts? I'm about ready to just put /home on hda along with /, and leave sda as a tertiary partition that I will load after I boot and login.

Edit: this is installing hoary with the "server" option, for a base install

---

