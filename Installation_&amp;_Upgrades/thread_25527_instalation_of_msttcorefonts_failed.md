---
title: "instalation of msttcorefonts failed"
date: 2005-04-10
forum: Installation &amp; Upgrades
---

### Post by dworzec.net on 2005-04-10
hello everybody,
in my Kubuntu 5.4 sudo apt-get install msttcorefonts results in  sth. like
> there is no version of msttcorefonts available or it is not in the repositories (it's translation from my console which is in Polish, but it's more or less the meaning)
and universe is enabled:
> deb [http://pl.archive.ubuntu.com/ubuntu](http://pl.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://pl.archive.ubuntu.com/ubuntu](http://pl.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe 
maybe I should add some other reps? any suggestions?

---

### Post by soul_rebel on 2005-04-10
maybe you need multiverse. (see wiki for that)

---

### Post by edubarr on 2005-04-10
[QUOTE=soul_rebel]maybe you need multiverse. (see wiki for that)[/QUOTE]
 Yes, they are in the multiverse.

---

### Post by dworzec.net on 2005-04-10
thanks, I'll try. I was looking in universe because of [http://ubuntuforums.org/showpost.php?p=3533&postcount=2](http://ubuntuforums.org/showpost.php?p=3533&postcount=2)

---

