---
title: "php w/o Apache"
date: 2007-03-29
forum: Installation &amp; Upgrades
---

### Post by jtalerico on 2007-03-29
I would like to install php5 without Apache. Could I do this using apt-get or should I just install it from source?

---

### Post by EmmEff on 2007-03-29
Did you try installing php5-cli?

If I knew how to check dependencies using dpkg/apt-get/aptitude, I'd do that for you.

Even if you have to install Apache, just set it not to automatically run.  It doesn't waste that much disk space.

---

### Post by jtalerico on 2007-03-29
Ahhh! Thank you! That did the trick. 

I need to check to see about installing with speical build options with apt...

---

### Post by EmmEff on 2007-03-29
I'd like to know that as well...  so much to learn with apt.

---

