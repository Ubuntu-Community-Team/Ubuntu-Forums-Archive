---
title: "trying to overwrite firefox error"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by dannemil on 2007-06-04
Synaptic keeps reporting a broken package. Every time I try to fix the broken package I get the following annoying error:

...trying to overwrite /usr/bin/firefox which is the diverted version of /usr/bin/firefox.ubuntu

and the fix fails. I know that I can force the newer firefox to install using

sudo dpkg --force-all -i /var/cache/apt/archives/firefox_2.0.0.4+1-0ubuntu1_i386.deb

but how do I get rid the the error in the first place so it won't keep coming back every time there is an update to firefox? I tried removing the /usr/bin/firefox link that I found, but the error persists. Any help would be appreciated.

---

### Post by zvacet on 2007-06-04
I don´t know if this will help but you can try

```
whereis firefox
```

and you will see every directory with firefox in it.Delete all firefox files in all directories and reinstall it.

---

