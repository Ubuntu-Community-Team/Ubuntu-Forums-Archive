---
title: "Problems with apache 2"
date: 2012-05-04
forum: Installation &amp; Upgrades
---

### Post by computerboy on 2012-05-04
Hi, I've been trying to get Apache 2 to work for a while now, and I forgot to make copies of some of the config files I was editing.  So I figured I would just uninstall and then install apache.  So after I typed

```
sudo apt-get remove apache2
```

into the terminal, I looked to see if the apache2 folder was still there and it was.  So I deleted the folder myself.  The problem is, after reinstalling apache 2, the apache2 folder in "etc" didn't pop back up.  Any ideas?

---

### Post by MG&amp;TL on 2012-05-04
Removing an application doesn't remove config files, particularly those the application or user spawned.

If you want to do that (providing they're registered with apt), use:

```
sudo apt-get remove --purge apache2
```

It won't make any more until you use it or make some more yourself.

---

### Post by computerboy on 2012-05-04
Thanks!

---

