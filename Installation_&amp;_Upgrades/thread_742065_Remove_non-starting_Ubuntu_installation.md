---
title: "Remove non-starting Ubuntu installation"
date: 2008-04-01
forum: Installation &amp; Upgrades
---

### Post by LeCzar on 2008-04-01
I screwed up, *hrmpf*,  the startup of one Gutsy installation and installed it newly, so that I am now having two installations of the same version. Wanted to copy out some important files from the old one into the new installation. Win XP is BTW also still installed.
Is there a safe way of removing the non-starting installation and incorporating the free disk space into the new Gutsy partition?

---

### Post by forestpixie on 2008-04-01
I would move the files first and then boot with either the livecd for it's partition editor or the editor of your choice and add the old partition to the new one.

I use parted magic - [http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php). Obviously make sure you know which partition you are booting to beforehand. Make sure you have backups of anything you can't afford to lose.

If that makes no sense to you and you've not done anything like it before post back.

---

### Post by LeCzar on 2008-04-01
Okay, no, I think I can handle that :) Will try that later and report the degree of success.
Thanks so far!

---

### Post by forestpixie on 2008-04-01
Be aware that when you change the partitions the UUID for them will probably change - so you will need to get access to your real installion files through the livecd to edit your fstab.

Edit - alternatively you can use nano in recovery mode to edit it if necessary, use ```
blkid
``` to get uuid for partitions then use ```
nano /etc/fstab
``` to edit the necessary partitions. To save file in nano Ctrl+O, then enter, then Ctrl+X to leave nano.

---

