---
title: "Flashplugin-nonfree upgrade error"
date: 2006-09-20
forum: Installation &amp; Upgrades
---

### Post by Garyu on 2006-09-20
```
Ställer in flashplugin-nonfree (7.0.68~ubuntu1~dapper1) ...
Downloading...  done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: fel vid hantering av flashplugin-nonfree (--configure):
 underprocess post-installation script gav felkod 1
Fel uppstod vid hantering:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

The automatic update thing said that there is a new version of flashplugin-nonfree, but when I said OK to install I get an error. If I "sudo apt-get upgrade" now I get the above output... Is there anyone else having this problem or is it just me?

---

### Post by mgpower0 on 2006-09-20
just a few

[http://www.ubuntuforums.org/showthread.php?t=261179](http://www.ubuntuforums.org/showthread.php?t=261179)

---

### Post by Tech^CF on 2006-09-20
I rolled back to the old version with remove and then: sudo apt-get install flashplugin-nonfree/dapper as suggested in the other thread. Waiting for new update..

---

