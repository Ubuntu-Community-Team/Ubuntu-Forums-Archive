---
title: "GRUB installation error on both 7.04 and 7.10"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by bigsby on 2007-10-18
hello,

I've been trying to install Ubuntu for a few weeks now, and I'm finally coming here for help. I've already looked all around the forum and on the bugs page, but haven't found anything that is quite like this, other than one thread in the newbies section that didn't have an answer, this one here:

[http://ubuntuforums.org/showthread.php?t=448827](http://ubuntuforums.org/showthread.php?t=448827)

First, my system specs:
AMD Athlon 64 X2 3800+
Asus M2N-E AM2 MOBO
2GiB Corsair ram
EVGA 7600 GT KO
250 GB Western Digital Caviar HDD
160 GB Western Digital Passport external HDD
550 Watt Antec TruePower II PSU.

So the story goes, I have this computer with a single internal hard drive. I have the hard drive partitioned with all except 15 gigs for Windows XP, and the other part is for linux (I had no swap partition). I used to have Fedora 7 on the second partition (didn't use it much), but then there was an error with partition magic, which ended up eating my MBR so I had to rebuild it with just the windows one, meaning I couldn't use Fedora anymore.

Then a few weeks ago I decided that I'd try installing Ubuntu 7.04 on the unused partition. I downloaded it from the main server, did an md5sum check on it, burned it and booted to it. I then tried to install ubuntu, with the same configuration that I had before, just formatting the partition and installing. Everything goes well until it gets to ~95%, where it says "installation error, grub boot loader failed with code 1".

I've tried tons of different things, I've burned 3 or 4 other cds, bought a new dvd burner (that one I'm pretty sure was dying anyways), tried it with different settings, all with the same results. I've searched pages and pages from google, the forums and the error database, with nothing giving me an answer that worked, or an answer period.

I just downloaded Gutsy Gibbon today, checked its hash, burned it and tried to install it, but it gave me the exact same message as before. I tried it without the Swap partition, and then afterwards with a 2.2 gig swap partition, but it didn't do anything different.

I can post logs if needed, not sure which ones you will need.

---

### Post by bigsby on 2007-10-19
bump, I'd really like to figure this out. I have no clue how to fix it, and I really want to play around with Gutsy Gibbon.

---

### Post by logos34 on 2007-10-19
See if Super Grub Disk will boot ubuntu:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

[http://www.users.bigpond.net.au/hermanzone/p1.htm#Turn_off_MBR_antivirus_or_write_protect](http://www.users.bigpond.net.au/hermanzone/p1.htm#Turn_off_MBR_antivirus_or_write_protect)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/110292/comments/1](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/110292/comments/1)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/110292](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/110292)


try reinstalling grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Last resort (boot linux with winxp ntldr):
[http://users.bigpond.net.au/hermanzone/p9.html](http://users.bigpond.net.au/hermanzone/p9.html)

---

