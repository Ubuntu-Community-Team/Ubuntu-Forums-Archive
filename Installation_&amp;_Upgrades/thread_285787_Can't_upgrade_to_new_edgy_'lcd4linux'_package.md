---
title: "Can't upgrade to new edgy 'lcd4linux' package"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by Psimon on 2006-10-27
I get the following error when trying to update packages, so the update notifier is permanently displayed.

Does anyone have any suggestions?

Preparing to replace lcd4linux 0.10.0+cvs20051015-2ubuntu2 (using .../lcd4linux_0.10.0+cvs20060825-1_i386.deb) ...
Stopping lcd4linux: invoke-rc.d: initscript lcd4linux, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Stopping lcd4linux: invoke-rc.d: initscript lcd4linux, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/lcd4linux_0.10.0+cvs20060825-1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Starting lcd4linux: lcd4linux.
Errors were encountered while processing:
 /var/cache/apt/archives/lcd4linux_0.10.0+cvs20060825-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by elleP on 2006-11-01
Same here, I can't seem to get rid of the old package.

---

### Post by elleP on 2006-11-01
I did a quick and ugly fix:

Download the .deb package
```
#aptitude download lcd4linux
#gnome-open lcd4linux_0.10.0+cvs20060825-1_i386.deb

```
Extract the files to some dir and:
```
#gnome-open data.tar.gz
```
Extract the files to "/"
rerun aptitude
```
#aptitude update
#aptitude upgrade
```

---

