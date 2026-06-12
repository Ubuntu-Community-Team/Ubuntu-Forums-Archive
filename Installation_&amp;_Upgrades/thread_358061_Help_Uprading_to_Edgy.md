---
title: "Help Uprading to Edgy"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by GaryLikesGames on 2007-02-10
For whatever reason, I cannot upgrade to Edgy using **gksu "update-manager -c"** however it always stops at retrieving updates or whatever it's called before the modifying software channels list. It continually freezes at retrieving file 17 of 18. It then returns an error message saying connection timed out at [http://security.ubuntu.com...etc](http://security.ubuntu.com...etc). For whatever reason it will not download xorg. Has anyone else had this problem? Is it possible to just download the Edgy ISO and install this file from there?

---

### Post by revoltism on 2007-02-13
hmm..

```
gksudo "update-manager -c -d"
```


it should work... maybe only something that day...

try trunk with # befor the security string in sources.list.

---

### Post by haricharan on 2007-02-13
Check your internet connectivity. If its not proper, upgrading would not succeed. I had the same problem with my upgrade. The connection was unstable and i could not upgrade. Try upgrading through faster and stable connection.

---

### Post by GaryLikesGames on 2007-02-13
It was the connection. Thanks.
However, since I want to upgrade another computer I would still like to know if it's possible to upgrade to edgy without a connection, using just the installation cd (without installing and erasing all the already existing data)?

---

