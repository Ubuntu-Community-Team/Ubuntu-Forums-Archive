---
title: "Edgy - Apache, PHP, MySQL, Gallery2 - Apache won't parse PHTML, ever"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by zifferent on 2006-10-29
I'm at wits end. Holey moley. I've tried every fix I've ever seen on any of these lists (and a few other lists.)

I'm trying to get my Gallery2 working again, and no matter what I try the result is the same. Apache won't parse any PHP, and punts the scripts back to Firefox to try and download the PHTML files.

I've removed and reinstalled everything several times over (with and without --purge.) I've tried both Apache 1.3 and and Apache 2 with the works (libapache[2]-mod-php4, php-mysql, php4, etc.) I've checked, double and triple checked my php.ini, httpd.conf, apache[2].conf, modules.d folder, odd soft links to the php conf files (apache2), etc.)

The pertinent page is at [http://www.zifferent.net/gallery2/](http://www.zifferent.net/gallery2/) if you want to look. If you want copies of my config files, I can provide you with those. This worked all the way till I rebooted, and hasn't worked since.

I've been at this for several hours and it's getting a bit silly.

---

### Post by zifferent on 2006-10-30
Uhmm, never mind. It's strange. I tried one more time and purged and reinstalled everything (Apache2, PHP, all the modules, Gallery2 and it's working now)

---

### Post by bsherman on 2006-10-30
I ran into a very similar problem when I recently upgraded to 6.06 Dapper Drake. Surprisingly, in my case, Firefox kept telling me that Apache was serving up a PHTML file, obviously, not processing the PHP. I fought with this for over an hour. I finally discovered that when I flushed Firefox's cache and restarted Firefox, there was no problem. Apache had probably been working for a long while.

Anyway, my two cents.

---

