---
title: "Is it possible to upgrade from the dapper desktop ISO?"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by Ndlovu on 2006-06-07
Yesterday I downloaded the Dapper Desktop ISO, hoping to upgrade from Breezy. Today I looked at the Dapper Upgrades page on the wiki ([https://wiki.ubuntu.com/DapperUpgrades)](https://wiki.ubuntu.com/DapperUpgrades)), and was very disappointed to see that I should have pulled the Alternate ISO for an upgrade.

I have a limited monthly download allocation, and I'm afraid that downloading another ISO would push me over the limit. Is there some way I can still use the Desktop cd, or will it likely break my system? The only other option will be to wait until next month to upgrade :-(.

Thanks,

Rudi

---

### Post by sdalley on 2006-06-07
I ran into the same problem. The update info is too scattered, and descriptions of what you do and don't get,and can and can't do with the cdrom images, hardware support etc, are inadequate. The ubuntu webpages could do with a good usability review ...

Anyway, the desktop cdrom iso CANNOT BE USED TO UPGRADE AN EXISTING INSTALLATION, IT WILL ONLY DO A FRESH INSTALLATION.(This should be stated in letters of fire on the download page.) One way round the problem would be to backup your /home hierarchy, or even everything depending on how much space you have, to spare disk partition(s), (by using say a knoppix cdrom, or the ubuntu desktop cdrom in rescue mode, or indeed your current installation), then do a full install from the desktop cd choosing your existing partitions (but **not** the backup partitions!) from the partitioning menu, then once the new system is running, recover any user files you find you need from the backup partition home directories. Of course, you will have to redo any printer setup, samba setup etc that you might have previously done on your breezy system.

Alternatively you could get a kind soul, or even shipit.ubuntu.com, to mail you an alternate version iso disk. This can then be used with "apt-cdrom add" as a local repository to apt-get from. I don't know what country you live in, but I have a spare LTS6.06 alternate-i386 disk that I could send.

---

### Post by Ndlovu on 2006-06-07
Thanks for the reply. Actually according to shipit, I already have some CDs coming my way. I'm guessing that these will all be the Desktop versions though. This could be quite an oversight on Canonical's side for all the people in developing parts of the world that don't have reliable Internet and want to upgrade their Ubuntu installations. I'm in South Africa, btw.

---

### Post by rpaller on 2006-06-07
You are not alone in downloading the incorrect ISO. I am faced with either backing up my home folder or downloading the correct ISO for the upgrade. The idea of a fresh install is tempting me.

Good luck.

---

### Post by rcarring on 2006-06-07
Maybe a route could be made for people in similar situations to order the alternate cd, perhaps tied in with the UbuntuPlus project?

---

