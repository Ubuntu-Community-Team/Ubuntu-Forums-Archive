---
title: "Plymouth stuck blinking, unless I manually run fsck at every boot..."
date: 2012-05-02
forum: Installation &amp; Upgrades
---

### Post by daas88 on 2012-05-02
I did a fresh install of kubuntu 12.04 over the partition where I had ubuntu 11.10. Every time I turn on the computer, it gets stuck at plymouth, the system gets frozen and the screen flickers. One workaround I found out was to reboot to recovery mode and run fsck, fsck used to show errors about the partitions being writen in the future (by less than a day) and fsck always set the clock wrong, just to get rid of the error. I "fixed" that (another workaround...) by changing my locale from VET to UTC. 

Now the clock is fine and fsck doesn't show any errors but I still need to run it in order to get kubuntu to boot. I use the default open source drivers for my graphics card, an ati radeon hd 6670.

---

