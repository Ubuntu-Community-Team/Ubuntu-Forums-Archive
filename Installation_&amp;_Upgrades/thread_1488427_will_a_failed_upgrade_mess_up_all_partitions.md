---
title: "will a failed upgrade mess up all partitions?"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by noworldorder on 2010-05-20
I have windows 7 (yuck!) and Ubuntu 9.10 on my laptop.  If I upgrade to 10.04 and things go sideways, am I risking the whole computer going south?  That is, will Windows & be screwed too or just the partition that Ubuntu is on.

I want to upgrade but I am a bit scared...

---

### Post by bumanie on 2010-05-20
In theory it should only do something to the ubuntu partitions if things go wrong as win 7 partition should not be involved. There have been a number of reports of grub and the mbr being mucked up, in which case you would have to fix the win 7 bootloader and mbr (there are many tutorials how to do this) if the upgrade didn't work **OR **sometimes the upgrade works, but windows won't boot. In this case it is best to follow [this page]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector"). This seems to occur when one is not sure where to direct grub and one chooses to install grub to all partitions - avoid that mistake and all should be well. As with anything involving major changes to ones computer a full-backup is always prudent beforehand, just in case. Do some reading, there is plenty on the internet about this type of stuff.

---

