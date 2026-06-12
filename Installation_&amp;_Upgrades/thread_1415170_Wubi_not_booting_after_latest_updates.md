---
title: "Wubi not booting after latest updates"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by paal_a on 2010-02-24
Been running Wubu Ubuntu 9.10 for a while under Windows 7 NTFS. Has been working just fine until today when Ubunto downloaded a lot of updates. After the downloads were completed I was prompted to reboot now or later. I clicked now and the PC shutdown and the rebooted. But instead of getting the usual boot menu where I could choose between Ubuntu or Windows 7 I not get some grub command line. 

I typed exit as luckily Windows 7 booted. I still have root.disk, swap.disk under /ubuntu/disks.

Any ideas on how to get my Ubuntu booting again?

---

### Post by darkod on 2010-02-24
Not sure if it's related but there was a bug in the original wubildr file. Get the new one from here:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

and replace it in C: or D:, etc, depending where you installed wubi.

---

### Post by paal_a on 2010-02-24
Thanks, that solved my problem. Back in Ubuntu now :)

---

