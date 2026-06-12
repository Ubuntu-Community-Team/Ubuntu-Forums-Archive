---
title: "Error while updating libfreetype6"
date: 2013-01-23
forum: Installation &amp; Upgrades
---

### Post by 81duz1d0 on 2013-01-23
Hi!

After an apt-get upgrade, my system returned


```
dpkg: error processing libfreetype6 (--configure):
 libfreetype6:amd64 2.4.8-1ubuntu2 cannot be configured because libfreetype6:i386 is in a different version (2.4.8-1ubuntu2.1)
dpkg: error processing libfreetype6:i386 (--configure):
 libfreetype6:i386 2.4.8-1ubuntu2.1 cannot be configured because libfreetype6:amd64 is in a different version (2.4.8-1ubuntu2)
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

And I'm not really sure about how to proceed. 

Can anyone help? Thanks!

---

### Post by zvacet on 2013-01-24
```
sudo dpkg --configure -a
```

---

### Post by 81duz1d0 on 2013-02-17
got this

```

root@biduzido-note:/home/biduzido# dpkg --configure -a
dpkg: error processing libfreetype6 (--configure):
 libfreetype6:amd64 2.4.8-1ubuntu2 cannot be configured because libfreetype6:i386 is in a different version (2.4.8-1ubuntu2.1)
dpkg: error processing libfreetype6:i386 (--configure):
 libfreetype6:i386 2.4.8-1ubuntu2.1 cannot be configured because libfreetype6:amd64 is in a different version (2.4.8-1ubuntu2)
dpkg: dependency problems prevent configuration of vlc-nox:
 vlc-nox depends on libfreetype6 (>= 2.2.1); however:
  Package libfreetype6 is not configured yet.
dpkg: error processing vlc-nox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc:
 vlc depends on vlc-nox (= 2.0.5-0ubuntu0.12.04.1); however:
  Package vlc-nox is not configured yet.
 vlc depends on libfreetype6 (>= 2.2.1); however:
  Package libfreetype6 is not configured yet.
dpkg: error processing vlc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc-plugin-notify:
 vlc-plugin-notify depends on vlc-nox (= 2.0.5-0ubuntu0.12.04.1); however:
  Package vlc-nox is not configured yet.
dpkg: error processing vlc-plugin-notify (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc-plugin-pulse:
 vlc-plugin-pulse depends on vlc-nox (= 2.0.5-0ubuntu0.12.04.1); however:
  Package vlc-nox is not configured yet.
dpkg: error processing vlc-plugin-pulse (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libfreetype6
 libfreetype6:i386
 vlc-nox
 vlc
 vlc-plugin-notify
 vlc-plugin-pulse

```

---

