---
title: "Edgy Eft to Hardy Heron from CD's?"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by jonathanhayward on 2008-06-04
I want to be able to upgrade a friend's computer from Edgy Eft to Hardy Heron from CD's (they have a bandwidth-limited connection, and CD's are probably the easiest way to get the data over.

How do I upgrade from CD? I tried, as a test, trying to upgrade a test VMware VM from 6.06 to 7.10 with the network disconnected. I could get the CD to show up and access the filesystem, but it wasn't clear what (if anything) was the next step to get Ubuntu to upgrade **from the CD**.

Any help would be appreciated, or a warning that what I'm trying is not an easy task.

---

### Post by logos34 on 2008-06-04
You need to use the **alternate installation cd**s.
[http://www.ubuntu.com/getubuntu/upgrading#head-7311a7de9fdf1ca310c6937460c0a9d33f54279d](http://www.ubuntu.com/getubuntu/upgrading#head-7311a7de9fdf1ca310c6937460c0a9d33f54279d)

---

### Post by jonathanhayward on 2008-06-04
Thank you. Where are the alternate installation CD's? (I couldn't find links in the page you linked to.)

---

### Post by logos34 on 2008-06-04
[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

(check box just below big green 'Start Download')

---

### Post by jonathanhayward on 2008-06-09
> **logos34 said:**
> You need to use the **alternate installation cd**s.
[http://www.ubuntu.com/getubuntu/upgrading#head-7311a7de9fdf1ca310c6937460c0a9d33f54279d](http://www.ubuntu.com/getubuntu/upgrading#head-7311a7de9fdf1ca310c6937460c0a9d33f54279d)I downloaded an alternate install CD, and inserted it and ran /cdrom/cdromupgrade from sudo on the command line - but got a popup window, saying, "An upgrade from edgy to hardy is not supported with this tool."

I guess I might make progress if I make an intermediate upgrade... but I'm wondering how many extra steps will be included. :(

---

### Post by avtolle on 2008-06-09
I'm not sure why you want to proceed this way, there are likely reasons not yet articulated, but I would recommend a clean, fresh install of 8.04 from CD if possible, as that is likely to be the least time consuming way to go. Just my 2 cents.

Otherwise, as I see it, you will need to go from Edgy to Feisty to Gutsy to Hardy, taking the time to d/l each iso, burn it to CD, then spend the time getting each intermediate installation "current", then taking the next step to go to the next release, etc.

---

### Post by logos34 on 2008-06-09
> **avtolle said:**
> I'm not sure why you want to proceed this way...but I would recommend a clean, fresh install of 8.04 from CD if possible, as that is likely to be the least time consuming way to go. Just my 2 cents

you're right--a clean install would be the best way. Otherwise you have to upgrade one release at a time (only Dapper LTS -> Heron is supported), and so you'd need to download Feisty as well as Gutsy and Hardy alt cds. 

I sometimes assume posters know exactly what they want and do not think to suggest alternative methods.

jonathan,

if you friend would like to keep as much of his/her files and settings intact, have him/her make a separate /home, and maybe backup /usr/local. Then install hardy, telling it to use (but NOT format!) the separate /home.

---

