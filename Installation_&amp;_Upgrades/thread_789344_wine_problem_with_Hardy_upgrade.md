---
title: "wine problem with Hardy upgrade"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by groovomata on 2008-05-10
I just upgraded to Hardy from Gutsy and I must say that everything has worked fine so far (including wireless and restricted nvidia drivers) except that when I try to run a game with Wine I get this error:
"Wine(X)/Cedega not in your PATH"
Does anyone know how to resolve this?
Thanks,
Erik.

---

### Post by Rocket2DMn on 2008-05-11
Newer versions of wine are working a little bit differently (and a 1.0 release candidate is out now).  You need to disable the old wine repos from System->Administration->Software Sources under the Third Party Software tab, then add them from here: [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)
Then you can
```
sudo apt-get upgrade
```

---

### Post by groovomata on 2008-06-17
Solved. Sorry, I forgot to get back on this one earlier, but everything's working fine now.

---

### Post by Rocket2DMn on 2008-06-18
Just in time for wine 1.0 - first stable version was released today.

---

