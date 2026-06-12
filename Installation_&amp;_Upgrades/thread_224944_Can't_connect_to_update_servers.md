---
title: "Can't connect to update servers"
date: 2006-07-28
forum: Installation &amp; Upgrades
---

### Post by kaytrem on 2006-07-28
Whenever I try to update/install I get errors like:

> [SIZE="2"]Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz)  Connection failed [IP: 146.137.96.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz)  Connection failed [IP: 146.137.96.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz)  Connection failed [IP: 146.137.96.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz)  Connection failed [IP: 146.137.96.15 80]

[/SIZE]

Any thoughts on why?  Everything else on my network works fine but this error is happening to both Ubuntu boxes.  I can update my laptop when I take it to another site.  Also, this happened spontaneously up until a few days ago I was able to do this all the time.

---

### Post by scxtt on 2006-07-28
try either removing the **us** or replacing it w/ **uk** ... then **sudo aptitude update** ...

---

### Post by kaytrem on 2006-07-28
> **scxtt said:**
> try either removing the **us** or replacing it w/ **uk** ... then **sudo aptitude update** ...

remove from where? Those messages come up automatically when I run the command...

---

### Post by scxtt on 2006-07-28
edit your /etc/apt/sources.list (as root):
[indent]sudo vi /etc/apt/sources.list[/indent]

---

### Post by londonbabs on 2006-09-21
I had the same problem, following scxtt instructions now all's fine, the only thing is I had to write :
sudo gedit /etc/apt/sources.list
in order to properly edit, don't know if it'll help anyone...
thanks anyway, one more problem sorted on my ubuntu problem-ridden discovery path...

Drats !! Actually after a reboot of the system (which got frozen and I had to restart manually) the problem is back... any help anyone ?

---

