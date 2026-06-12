---
title: "Can not delete /usr/share/icons/hicolor/scalable"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by GexNZ on 2006-06-02
I have used update-manager to move from breezy to dapper.
However I noticed I had a few KDE packages installed from when I was using breezy that are no longer required.  When removing them through synaptic i get:
```
E: khelpcenter: failed to delete `/usr/share/icons/hicolor/scalable/apps/khelpcenter.svgz.dpkg-tmp'
E: klipper: failed to delete `/usr/share/icons/hicolor/scalable/apps/klipper.svgz.dpkg-tmp'
E: konsole: failed to delete `/usr/share/icons/hicolor/scalable/apps/konsole.svgz.dpkg-tmp'
```

ls -l on /usr/share/icons/hicolor/ gives
```
tv@jitterbug:/usr/share/icons/hicolor$ ls -l
total 1818
drwxr-xr-x 9 root root     232 2005-11-24 22:15 128x128
drwxr-xr-x 9 root root     232 2005-11-24 22:15 16x16
drwxr-xr-x 9 root root     232 2005-11-24 22:15 192x192
drwxr-xr-x 9 root root     232 2005-11-24 22:15 22x22
drwxr-xr-x 9 root root     232 2005-11-24 22:15 24x24
drwxr-xr-x 9 root root     232 2005-11-24 22:15 32x32
drwxr-xr-x 9 root root     232 2005-11-24 22:15 36x36
drwxr-xr-x 9 root root     232 2005-11-24 22:15 48x48
drwxr-xr-x 9 root root     232 2005-11-24 22:15 64x64
drwxr-xr-x 9 root root     232 2005-11-24 22:15 72x72
drwxr-xr-x 9 root root     232 2005-11-24 22:15 96x96
-rw-r--r-- 1 root root 1839080 2006-06-02 22:55 icon-theme.cache
-rw-r--r-- 1 root root   16878 2006-05-23 18:26 index.theme
?--------- ? ?    ?          ?                ? scalable

```
Note the strange figures for scalable. I tried to remove scalable myself as root but it says I don't have permissions.

Is there something wrong with the file system?  Any help would be greatly appreciated.

---

### Post by zorglab on 2006-06-06
Strange, I have the same problem with some folders in /var/lib : doc-base, gcj-4.1, gstreamer, sgml-base, xkb and xml-core.

I can't do anything with them, and thus, scrollkeeper, which needs access to /var/lib/xml-core can't be configured.

---

### Post by GexNZ on 2006-06-08
I'm still having the same problem.

Futher information:

lsattr scalable/
lsattr: Inappropriate ioctl for device While reading flags on scalable/apps
lsattr: Inappropriate ioctl for device While reading flags on scalable/devices
lsattr: Inappropriate ioctl for device While reading flags on scalable/stock
lsattr: Inappropriate ioctl for device While reading flags on scalable/mimetypes
lsattr: Inappropriate ioctl for device While reading flags on scalable/emblems
lsattr: Inappropriate ioctl for device While reading flags on scalable/filesystems
lsattr: Inappropriate ioctl for device While reading flags on scalable/actions

---

### Post by GexNZ on 2006-06-08
I ran a fsck on my root partition and it reported 'No corruptions found' so I don't think it is a file corruption problem...

---

### Post by GexNZ on 2006-06-08
ls -l /usr/share/icons/hicolor/
now results in
total 1542
drwxr-xr-x 9 root root     232 2005-11-24 22:15 128x128
drwxr-xr-x 9 root root     232 2005-11-24 22:15 16x16
drwxr-xr-x 9 root root     232 2005-11-24 22:15 192x192
drwxr-xr-x 9 root root     232 2005-11-24 22:15 22x22
drwxr-xr-x 9 root root     232 2005-11-24 22:15 24x24
drwxr-xr-x 9 root root     232 2005-11-24 22:15 32x32
drwxr-xr-x 9 root root     232 2005-11-24 22:15 36x36
drwxr-xr-x 9 root root     232 2005-11-24 22:15 48x48
drwxr-xr-x 9 root root     232 2005-11-24 22:15 64x64
drwxr-xr-x 9 root root     232 2005-11-24 22:15 72x72
drwxr-xr-x 9 root root     232 2005-11-24 22:15 96x96
-rw-r--r-- 1 root root 1552900 2006-06-08 22:04 icon-theme.cache
-rw-r--r-- 1 root root   16878 2006-05-23 18:26 index.theme
drwxr-xr-x 9 root root     232 2005-11-24 22:15 scalable

I am told it is unlikely that the fsck would have fixed this problem.  But in my case it seems to have as I didn't do anything else.

Basically I logged out of gnome.
Hit <ctrl>+<alt>+F1
logged in as a user
```
sudo telinit 1
mount -o remount,ro /
fsck /dev/hda1
```
It then told me "No corruptions found".
Once I rebooted 'reboot' all was back to normal, hope this helps someone.

---

