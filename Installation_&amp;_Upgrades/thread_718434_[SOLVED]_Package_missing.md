---
title: "[SOLVED] Package missing?"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by msknight on 2008-03-08
Not sure where to ask this, so given the nature of the message, I'm posting here.

apt-get rosegarden ends up with ...

Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/khelpcenter_3.5.8-0ubuntu2.1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/khelpcenter_3.5.8-0ubuntu2.1_i386.deb) 404 Not Found

I'm in the U.K. using Gutsy on a laptop.

---

### Post by forestpixie on 2008-03-08
what do you get with 

```
sudo apt-get update && sudo apt-get install rosegarden
```

---

### Post by msknight on 2008-03-08
Bingo - thanks!

---

