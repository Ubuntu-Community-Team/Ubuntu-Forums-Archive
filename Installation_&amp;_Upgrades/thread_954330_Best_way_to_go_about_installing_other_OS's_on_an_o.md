---
title: "Best way to go about installing other OS's on an only Ubuntu HDD"
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by superarmy on 2008-10-21
Currently my Hard Drive only has Ubuntu 8.04 on it. But I want to play Spore and I need to get Skype running, so I'm going to install Vista. What do you think is the best way to go about this is? I have several ideas, I just want to see what people recommend.

---

### Post by ronnielsen1 on 2008-10-21
Skype works in Ubuntu and I haven't tried it myself but
> Spore works quite well, starting with Wine 1.1.5 (2008-09-20) (which fixes some graphical glitches and network issues)
[http://colas.nahaboo.net/Hacks/Spore](http://colas.nahaboo.net/Hacks/Spore)
Anyway if you have the memory and hard drive space to run Vista - I personally would install on it's own hard drive. It makes things easier. If this isn't an option boot from a live cd and use gparted (wonderful package) to resize your hard drive to make room for vista (unless you already have unpartitioned space) and then install it.

---

### Post by oldos2er on 2008-10-21
Installing Vista will overwrite grub on the MBR, but you can use Super Grub Disk to restore it.

---

