---
title: "Freeze: Upgraded Breezy &gt; Dapper then Kernel to 2.6.15-27-686"
date: 2006-11-24
forum: Installation &amp; Upgrades
---

### Post by jazzwhistle on 2006-11-24
I upgraded Breezy to Dapper 6.06 LTS yesterday with no major problems (well I lost wireless until I blacklisted islsm_usb...), and today decided to upgrade to latest kernel :/

I have a Pentium 4 1.5Ghz, 684Mb RAM, and have used -686 kernel on Breezy with no problem for ages, but now I'm using 2.6.15-27 the system freezes completely after 2-3 minutes if I use the -686, but -386 seems to work fine so far.

I've tried booting to 2.6.12-10-686 but now have no wireless, ndiswrapper -l tells me all is ok, but modprobe ndiswrapper says "ndiswrapper not found".

Can anyone tell me why the 686 kernel is hanging, or advise me which Kernel I should be using? And why does my system now say "ubuntu 6.06.1 LTS"? I can find no reference to this anywhere on the forums.

Thank you in advance

****

Ubuntu 6.06.1 LTS \n \l
Linux ubuntu 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686

**UPDATE**

Upgraded to EDGY, using the "official" method of course ;). Have still to check if 686 kernel freezes as 386 seems to work fine.

---

