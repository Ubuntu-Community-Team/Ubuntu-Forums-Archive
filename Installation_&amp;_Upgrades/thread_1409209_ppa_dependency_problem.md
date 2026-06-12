---
title: "ppa dependency problem"
date: 2010-02-17
forum: Installation &amp; Upgrades
---

### Post by james82 on 2010-02-17
I'm trying to use the kubuntu ppa to install kde 4.4.0.  My /etc/apt/sources.list says:
```
deb http://ppa.launchpad.net/kubuntu-ppa/staging/ubuntu karmic main
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu karmic main
```

But there is a problem installing kde-window manager. aptitude says:
```
dpkg: error processing /var/cache/apt/archives/kde-window-manager_4%3a4.4.0-0ubuntu1~karmic1~ppa8_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/kde4/kwin_aurorae_config.so', which is also in package build 0:20090707-1
```

This also stops the install of kdebase-workspace, which depends on it. 

I've tried ```
 aptitude install -f 
```

The package list is up-to-date. I've also tried removing `kwin-style-aurorae' - no luck.

Any help much appreciated :)

---

### Post by james82 on 2010-02-18
Okay, I fixed it. I found the deb file in /var/cache/apt, and forced the install with dpkg.

```
 dpkg --force-overwrite -i /var/cache/apt/.../kde-window-manager...4.4.0.deb 
```

marking as solved (perhaps there should be a tag for nvm-i-fixed-it-myself

---

