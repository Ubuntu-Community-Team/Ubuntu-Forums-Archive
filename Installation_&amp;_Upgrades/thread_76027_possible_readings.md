---
title: "possible readings"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by gpredrag on 2005-10-14
I am still waiting for shipit CD's, so I haven't upgraded to Breezy yet to tell you my experience with Ubuntu, but I have recently updated few very important Debian machines (servers)  to Sarge (with no problem at all). There were some important steps in process, and  I am planning to do it same way with Ubuntu.
First: simply apt-get dist-upgrade was not recomended. Instead I used:
 "aptitude -f --with-recommends dist-upgrade"
aptitude is supposed to do a better job.
Even more important is to check status of your packages beforehand with: "dpkg --audit"
Anyway here's the link:

[http://www.debian.org/releases/stable/i386/release-notes/ch-upgrading.en.html](http://www.debian.org/releases/stable/i386/release-notes/ch-upgrading.en.html)

most of the stuff is very debian specific (like upgrading aptitude, doc-base, ...) and you should ignore it, but I beleive there are some very importnat advices that might spare trouble people who have installed/ununstaled/half-instaled a lots of nonstandard packages and backports.

---

