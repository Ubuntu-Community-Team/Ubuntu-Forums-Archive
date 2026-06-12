---
title: "Exporting Firefox Profile from 16.04 to 18.04"
date: 2018-10-17
forum: Installation &amp; Upgrades
---

### Post by wjbmd48 on 2018-10-17
Hi:

I've recently set up a new Lubuntu 18.04 system. Previously, to transfer my Firefox profile (bookmarks, addons, etc etc), all I had to do was copy the .mozilla folder from the old to the new machine. This doesn't seem to work when going from 16.04 to 18.04.

Any ideas?

Thanks!

Bill

---

### Post by pablosquared on 2018-10-17
I've used the following command successfully to do this:

```

firefox -profilemanager

```

Select "Create Profile", then browse to the location of your Firefox profile folder (the "<letters><numbers>.default" folder, and start firefox.

---

### Post by wjbmd48 on 2018-10-17
Bingo, and DUH!

Thanks!!

Bill

---

