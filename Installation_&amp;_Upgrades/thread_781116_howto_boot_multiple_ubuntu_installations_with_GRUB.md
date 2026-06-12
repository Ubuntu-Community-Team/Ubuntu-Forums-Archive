---
title: "howto boot multiple ubuntu installations with GRUB"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by mixersoft on 2008-05-04
Should this work?

1) I have a clean install of Hardy Server on /dev/sda6, with the swap on /dev/sda5. 
2) I backed up the /dev/sda6 partition using TrueImage and then restored it to /dev/sda7 and /dev/sda8

I want to be able to use GRUB boot from one of these 3 (currently identical) partitions. Should this work? If so, what do I have to do to Grub or fstab or whatever to choose the active installation? The other 2 unused partitions can remain unmounted.

My intention is to play with 3 different server configs, including the addition of Mythbuntu on 1 of them and ubuntu-desktop on the other, until I figure out which one is best for me.

TIA.

---

### Post by mixersoft on 2008-05-04
FYI, it looks like the filesystem UUIDs are the same for sda6/7/8. I suspect it is because I restored the same image into each partition. Is that a problem? 

I tried to change the grub root param to "root (0, x)" but when I choose to boot sda7/8 (the restored partitions) I get this error:

"Error 1: Filename must be either an absolut pathname or blocklist"

---

### Post by logos34 on 2008-05-04
you're headed for a trainwreck with a setup like that, but in theory it should be possible.  Yes, cloning a partition copies the whole thing along with the uuid.  Just make sure you don't try to mount the other partitions and make sure /etc/fstab includes only the / and /swap.

---

