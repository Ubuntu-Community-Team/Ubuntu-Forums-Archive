---
title: "Source not found?  Cannot install!"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by yerdon on 2007-04-21
Hi everyone.  I'm trying to upgrade from Edgy to the latest and I start the update manager with:

$ gksu "update-manager -c"

It appears to go fine, except that after download files for a few minutes, it stops presenting me this error message and won't go on.  I'm kind of new to Linux and don't know where I need to go to fix this:

Failed to fetch [http://theli.free.fr/packages/dists/edgy/listen/binary-i386/Packages.gz](http://theli.free.fr/packages/dists/edgy/listen/binary-i386/Packages.gz) 301 Moved Permanently

Do I have to update a sources file or something?

---

### Post by taurus on 2007-04-21
You need to edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and comment out all those 3rd party repos by placing a # in front of them.  Then, update it and see if you can upgrade it now.

```
sudo aptitude update
```

---

### Post by yerdon on 2007-04-21
Thanks, I did comment out that line and now it is going much further.  Hope it will work!

Thanks again!

Joseph

---

