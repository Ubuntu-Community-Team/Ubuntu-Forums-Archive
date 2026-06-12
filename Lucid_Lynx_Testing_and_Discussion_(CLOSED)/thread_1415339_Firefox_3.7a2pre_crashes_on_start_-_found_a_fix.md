---
title: "Firefox 3.7a2pre crashes on start - found a fix"
date: 2010-02-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by paul_in_london on 2010-02-24
Meant to post this a couple of days ago. Flash was causing Firefox **3.7a2pre** (Minefield) to become unresponsive at start up. Found a fix here:

[https://bugs.launchpad.net/firefox/+bug/513887](https://bugs.launchpad.net/firefox/+bug/513887)

The workaround that did the trick for me was to disable out of process plugins via about:config , setting the key **dom.ipc.plugins.enabled** to false

Upgraded to Flash 10.1 Beta 3 (10.1.51.95) earlier and it's still ok.

---

### Post by kahumba on 2010-02-24
I don't get it.
I heard there's not gonna be any 3.7 release. Going straight to 4.0 with a few serious additions served as updates to 3.6 in between.

---

### Post by paul_in_london on 2010-02-24
I use the mozilla nightly builds:

```
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/)

deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) lucid main 
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) lucid main

[http://www.webupd8.org/2010/02/firefox-37-alpha-nightly-build-finally.html](http://www.webupd8.org/2010/02/firefox-37-alpha-nightly-build-finally.html)
```

---

