---
title: "Fixing the new Wubi installer"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by Smalls1652 on 2007-04-21
Ok, it was hard trying to install Ubuntu through this. I found the culprit.

[LIST=1]
[*]Frst of all, start installing
[*]When it gets to "Retrying in 5 Seconds" click cancel then click ok
[*]go into C:\wubi\config.ini
[*]Go down and replace the torrent and iso links with these:
[/LIST]
[http://ftp.acc.umu.se/mirror/ubuntu-releases/7.04/ubuntu-7.04-alternate-i386.iso](http://ftp.acc.umu.se/mirror/ubuntu-releases/7.04/ubuntu-7.04-alternate-i386.iso)

That is for both

You could just use Firefox's Dta! and you'll get it quicker. You'll still have to fix the config.ini file, i believe
:)

---

### Post by pjalegria on 2007-04-21
Dont work

---

