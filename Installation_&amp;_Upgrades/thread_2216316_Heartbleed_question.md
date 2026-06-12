---
title: "Heartbleed question"
date: 2014-04-11
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2014-04-11
I got two remote servres and a local machine.

On each I used:

sudo openssl version -a
local machine said before April 7, first remote said before April 7 and second said on April 7

The funny thing, I was not logged in at the second remote machine since March 12. How can it be upgraded to the new version?

I wonder especially that this machine had a ftpuser in /etc/passwd and /etc/schadow, which I removed. 

The upgrade results in a different file size for each  machine, which might be because all are different versions of Ubuntu.

How can I make sure that the version on the second remote (the one where the ftpuser was added on April 6 and had openssl already updated) are correct???

---

### Post by grahammechanical on 2014-04-11
I may be wrong. I have just a single user home machine. So, I am likely out of my depth. Although you have not logged in to that second remote machine since March 12 it was still switched on. Yes? Was the OS set to receive security updates automatically? Can that be set on a server?

If it helps, I am running trusty tahr (14.04) and it is up to date and this is part of what I get when I run sudo openssl version -a

> OpenSSL 1.0.1f 6 Jan 2014
built on: Mon Apr  7 21:22:23 UTC 2014

This blog may provide some assistance

[http://blog.utlemming.org/2014/04/updated-12044-lts-cloud-images-in.html](http://blog.utlemming.org/2014/04/updated-12044-lts-cloud-images-in.html)

> [COLOR=#333333][FONT=Helvetica Neue Light]If you elected to update, please note that services that have been started before updating the OpenSSL packages will need to be restarted; it is best to reboot any servers. [/FONT][/COLOR]

Regards.

---

### Post by SeijiSensei on 2014-04-11
Upgrades are only distributed for [supported versions]("https://wiki.ubuntu.com/Releases").  These are currently 10.04 Server, 12.04 LTS, 13.10, and the forthcoming 14.04 LTS.  If you have machines running 13.04 or earlier other than 10.04 Server or 12.04 LTS, you will not see an OpenSSL update.

Any machine used in production like a web server should be running an LTS release like 12.04.

---

### Post by ELMIT on 2014-04-12
yes, it was a supported version 12.04 and this machine had auto security updates enabled. I have not thought on that.

Thanks!

---

