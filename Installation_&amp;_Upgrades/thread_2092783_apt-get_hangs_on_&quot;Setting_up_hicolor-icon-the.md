---
title: "apt-get hangs on &quot;Setting up hicolor-icon-theme&quot;"
date: 2012-12-08
forum: Installation &amp; Upgrades
---

### Post by NightsShadeQueen on 2012-12-08
Installing anything via apt-get gets to the point where it's

Setting up hicolor-icon-theme (0.12-1ubuntu2) ...

and then nothing happens. As far as I know, it just hangs there waiting for *something* to return, and it never continues.

username@server:~$ ps aux | grep hicolor-icon-theme
root      4033  0.0  0.0   4400   612 pts/3    Ss+  19:53   0:00 /bin/sh /usr/bin/dpkg --status-fd 67 --configure libglib2.0-0:amd64 hicolor-icon-theme:all
root      4034  0.0  0.3  25404 10172 pts/3    S+   19:53   0:00 /usr/bin/dpkg.debathena-orig --status-fd 67 --configure libglib2.0-0:amd64 hicolor-icon-theme:all
root      4043  0.0  0.0   4400   608 pts/3    S+   19:53   0:00 /bin/sh /var/lib/dpkg/info/hicolor-icon-theme.postinst configure 
username 4103  0.0  0.0  13588   876 pts/1    S+   20:08   0:00 grep hicolor-icon-theme

If I force-kill, apt-get will neither remove nor fully install that package, either. Currently running Ubuntu 12.04

---

### Post by ibjsb4 on 2012-12-08
Im thinking that theme is part of the default install and should of already been there.

Anyhow try this:

```
sudo apt-get install --reinstall hicolor-icon-theme
```

---

### Post by NightsShadeQueen on 2012-12-08
Just hangs in the same location.

Managed to install other packages by removing just hicolor-icon-themes and then tried to reinstall it later, but didn't work? 

Under further investigation: It's trying to run gtk-update-icon-cache-3.0 --force --quiet /usr/share/icons/hicolor

Running this process myself (minus the --quiet, which shouldn't matter) works.

That said, I have no clue if the icon theme is correctly installed now or not; the computer I'm currently working on is across campus from me, so I'm doing everything via ssh because I'm too lazy to walk.
[B]
EDIT: [/B]Figured out. gtk-update-icon-cache-3.0 --force --quiet /usr/share/icons/hicolor runs properly but doesn't tell dpkg it did, causing everything to hang. Or something like that. Either way, adding exit 0 at the end of /var/lib/dpkg/info/hicolor-icon-theme.postinst worked.

This is probably a stupid idea.

---

