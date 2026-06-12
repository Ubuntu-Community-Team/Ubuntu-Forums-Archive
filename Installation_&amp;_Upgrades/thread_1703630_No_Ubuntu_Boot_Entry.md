---
title: "No Ubuntu Boot Entry"
date: 2011-03-09
forum: Installation &amp; Upgrades
---

### Post by dlpenguinlover on 2011-03-09
Hello. I have just installed ubuntu via ubuntu download but I can't get the ubuntu boot entry to appear in the windows xp boot menu. Any help?

I downloaded wubi from the download desktop page. I have installed ubuntu 10.10 via torrent download.

---

### Post by oldfred on 2011-03-09
If it is a standard install this should work for XP.

boot.ini entry:
c:\wubildr.mbr="Ubuntu-Linux"

There have been a few issues with wubi.
how to fix those Wubi installation breakages without going crazy Rubi1200 Dec 2010
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

---

### Post by bcbc on 2011-03-09
> **dlpenguinlover said:**
> Hello. I have just installed ubuntu via ubuntu download but I can't get the ubuntu boot entry to appear in the windows xp boot menu. Any help?

I downloaded wubi from the download desktop page. I have installed ubuntu 10.10 via torrent download.

It says it modified the boot.ini successfully. Maybe the timeout is set at zero. (right click My computer, Properties, Advanced, Startup & Recovery).

Note you've installed on a FAT32 partition which has a maximum single file size of 4GB so it split your virtual disks into 4GB for root.disk, 4GB for home.disk and 4GB for usr.disk.
You asked for 18GB but only got 12GB total - and that space is not fully available for e.g. personal files (which go in /home i.e. home.disk)
It is probably better to install on NTFS as you can get a single root.disk = 18GB.

In general... I advise being extra cautious with personal data stored on the virtual disks - they are less reliable than a real disk partition. So keep backups.

PS as oldfred suggested, check the wubi megathread as well. Some info there on locking grub. (This is not currently an issue with a fresh 10.10 install, but could be in the future).

---

