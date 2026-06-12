---
title: "GPG Error"
date: 2013-04-25
forum: Installation &amp; Upgrades
---

### Post by archp2009 on 2013-04-25
I  get this when attempting updates.  Is there a fix?                              
RELEASE: GPG error: [http://viewizard.com](http://viewizard.com) debian/ Release: The following signatures were invalid: NODATA 1 NODATA 2

---

### Post by plucky on 2013-04-26
> **archp2009 said:**
> I  get this when attempting updates.  Is there a fix?                              
RELEASE: GPG error: [http://viewizard.com](http://viewizard.com) debian/ Release: The following signatures were invalid: NODATA 1 NODATA 2

Disable **[http://viewizard.com](http://viewizard.com)** as a source in your Software Sources.

Then run ```
sudo apt-get update
``` from a terminal. If still getting errors,post the output from the update command to the forum.

Good Luck

---

### Post by archp2009 on 2013-04-26
Thanks.  Now have this.  Fetched 26.1 MB in 54s (477 kB/s)                                              
Reading package lists... Done
arch@arch-Ubuntu:~$

---

### Post by archp2009 on 2013-04-26
My automatic updates popped up and completed right after.  Thanks again.

---

