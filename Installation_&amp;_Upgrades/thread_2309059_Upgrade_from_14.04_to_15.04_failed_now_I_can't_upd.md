---
title: "Upgrade from 14.04 to 15.04 failed now I can't update"
date: 2016-01-07
forum: Installation &amp; Upgrades
---

### Post by hobgoblinn on 2016-01-07
Hello,

During the update at some point the system crashed, the login worked then quickly displayed a message (too quick to read) then returned to the login page. At the moment I cannot access ubuntu as I normally would as I am greeted to a black/grey screen. Using grub I can access the system via the upstart option.

It appears to be an issue with the dependencies that is preventing me from upgrading the system and installing packages.

I've tried the usual suspects (dpkg --configure -a, apt-get install -f, apt-get install --fix-broken...) however it keeps failing. Below is some of the output:

dpkg --confgure -a sample output:

```

## Redacted some of the above output


dpkg: error processing package totem (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of totem-plugins:
 totem-plugins depends on libtotem0 (>= 3.14.3-0ubuntu0.1); however:
  Version of libtotem0 on system is 3.10.1-1ubuntu4.
 totem-plugins depends on totem (= 3.14.3-0ubuntu0.1); however:
  Package totem is not configured yet.
 totem-plugins depends on gir1.2-totem-1.0 (= 3.14.3-0ubuntu0.1); however:
  Package gir1.2-totem-1.0 is not configured yet.

dpkg: error processing package totem-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on libclutter-gtk-1.0-0 (>= 0.91.8); however:
  Package libclutter-gtk-1.0-0:amd64 is not configured yet.

dpkg: error processing package gnome-control-center (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gstreamer1.0-clutter
 libcogl-path20:amd64
 libclutter-gtk-1.0-0:amd64
 libcogl-pango20:amd64
 gir1.2-totem-1.0
 totem
 totem-plugins
 gnome-control-center
```

apt-get install -f:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies.
 acl : Depends: libacl1 (= 2.2.52-1) but 2.2.52-2 is installed
 gir1.2-totem-1.0 : Depends: libtotem0 (>= 3.14.3-0ubuntu0.1) but 3.10.1-1ubuntu4 is installed
 gstreamer1.0-clutter : Depends: libcogl20 (>= 1.17.4) but it is not installed
 libclutter-gtk-1.0-0 : Depends: libclutter-1.0-0 (>= 1.18) but 1.16.4-0ubuntu2 is installed
                        Depends: libcogl20 (>= 1.17.4) but it is not installed
 libcogl-pango20 : Depends: libcogl20 (>= 1.17.4) but it is not installed
 libcogl-path20 : Depends: libcogl20 (>= 1.18.0) but it is not installed
 totem : Depends: libtotem0 (>= 3.14.3-0ubuntu0.1) but 3.10.1-1ubuntu4 is installed
 totem-plugins : Depends: libtotem0 (>= 3.14.3-0ubuntu0.1) but 3.10.1-1ubuntu4 is installed
 tzdata-java : Depends: tzdata (= 2015g-0ubuntu0.14.04) but 2015g-0ubuntu0.15.04 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```

Any help with this would be appreacited

---

### Post by v3.xx on 2016-01-07
What's your sources look like?

```
cat /etc/apt/sources.list && ls /etc/apt/sources.list.d/*.list
```

---

