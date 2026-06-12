---
title: "Attempted to upgrade to 10.04 through The update manager. Computer crashed"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by Heyjoeh on 2010-05-08
So I attempted to Upgrade 2 days ago from 9.10 to 10.04. I started the upgrade and left my computer alone as it said it would take several hours. When I returned to check on it, It told me the the installation had failed and it was attempting to roll back to the previous installation. Afterward I couldn't access anything on my computer. I'd click a icon and it wouldn't do anything. I manually restarted it and was greeted with a message that it couldn't boot because there was no mount specified.

Since I had backed up all my files I tried to just reinstall ubuntu. However even after I reinstalled I'm greeted with the same message
Wut do?

---

### Post by dabl on 2010-05-08
If your data are all backed up, then boot a Live CD that has GParted on it, and format the target partition ext4.

For example, [[COLOR="Green"]**here's**[/COLOR]](http://partedmagic.com/download.html) a good one.

Then boot your Ubuntu Live CD or Alternate Install CD, and proceed using "manual" partition, and just choose your partition.  When it comes to the Grub installation at the end of the process, let it go to the MBR of the drive. Then you should be good to go.

---

