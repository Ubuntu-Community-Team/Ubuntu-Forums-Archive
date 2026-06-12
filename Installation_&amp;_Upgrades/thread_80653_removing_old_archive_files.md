---
title: "removing old archive files"
date: 2005-10-22
forum: Installation &amp; Upgrades
---

### Post by dninja on 2005-10-22
I'm sharing my /var/cache/apt/archives directory between a few machines but it is getting quite big now. I want to delete all the outdated files, e.g. out of this lot

xvfb_6.8.2-10_i386.deb
xvfb_6.8.2-56_i386.deb
xvfb_6.8.2-61_i386.deb
xvfb_6.8.2-69_i386.deb
xvfb_6.8.2-75_i386.deb
xvfb_6.8.2-77_i386.deb

I want to only be left with xvfb_6.8.2-77_i386.deb.

Also, if there are patches for a version of a package which is out of date, I want those deleted as well.

Does anyone have a script which would do all of this?

---

### Post by oik on 2005-10-22
Why not just delete everything?

---

### Post by dninja on 2005-10-22
[QUOTE=oik]Why not just delete everything?[/QUOTE]

I'm sharing the archive between mulitple machines so I only have to download stuff once.

I could delete everything then get all machines up-to-date but some machines only get fired up once in a while so that wouldn't work.

---

