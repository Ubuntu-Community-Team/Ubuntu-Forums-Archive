---
title: "Plex broken - Wont remove or re-install"
date: 2013-02-15
forum: Installation &amp; Upgrades
---

### Post by GoldenHippo on 2013-02-15
Hi all - I'm having problems running Plex.  It was installed and working fine, then the web interface seemed to break (not loading fulling).  Now Plex is still active in my processes list (DNLA and Media Servers), refuing to be stopped, restarted or killed.
Any attempt to update results in an error stating that Plex requires "installation of untrusted packages", with "plexmediaserver" in the Details pane.
Any help in totally removing Plex to enable a fresh install would be appreciated.

Running Ubuntu 12.10
Intel Pentium D 3.4Ghzx2
3Gb RAM

---

### Post by MBro on 2013-02-22
Plex is starting too early.  I don't know a perminate fix but a bandaid would be+```
sudo service plexmediaserver restart
```

---

