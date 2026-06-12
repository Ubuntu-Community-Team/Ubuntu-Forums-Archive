---
title: "My new lubuntu 12.10 won't apply updates"
date: 2012-11-07
forum: Installation &amp; Upgrades
---

### Post by ecowan on 2012-11-07
I just installed lubuntu on an older Dell Inspiron. Somehow I have mangaed to corrupt the apt mechanism, probably while trying to accomodate my approx server. Whenever I try Software Updater or Synaptic or apt-get it fails while running install-info.

I attach the results of an attempt to run apt-get dist-upgrade.

Can anyone help me fix it, or do I have to re-install?

Thanks. - Erny

---

### Post by ecowan on 2012-11-09
I have done "rm /var/lib/apt/lists/* -vf".

I get pretty much the same message whatever I try with apt - apt-get dist-upgrade, apt-get install, apt-get autoremove - except "apt-get clean" and "apt-get update".

- Erny

---

### Post by ecowan on 2012-11-10
I gave up and did a re-install.

---

