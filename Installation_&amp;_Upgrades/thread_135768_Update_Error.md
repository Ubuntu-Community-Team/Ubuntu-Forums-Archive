---
title: "Update Error"
date: 2006-02-24
forum: Installation &amp; Upgrades
---

### Post by robenne on 2006-02-24
I just updated from Hoary to Breezy off the CD and now I continue to get this error when I am running the update manager: :-k 

**E: /var/cache/apt/archives/nautilus_2.12.1-0ubuntu1.1_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/share/gconf/schemas/apps_nautilus_preferences.schemas')**

A little help please.

Thanks
:cool:

---

### Post by Xian on 2006-02-24
There was most likely a corrupt file on the CD. 
Did you run md5sum on it to verify the integrity?

Remove that pkg from the cache path.
Then download & install it directly from [Ubuntu Packages](http://higgs.djpig.de/ubuntu/www/).

If the CD is corrupt I would repeat the burn process, verify, and reinstall.
There's no telling what else is lurking around.....

---

### Post by robenne on 2006-02-24
Cool! Thanks \\:D/  I'll give this a try Monday when I get back to work.

---

