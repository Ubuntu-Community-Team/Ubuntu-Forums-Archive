---
title: "Fstab Confusion"
date: 2013-08-30
forum: Installation &amp; Upgrades
---

### Post by BarryD9545 on 2013-08-30
Hey All-
I have a 13.04(gnome fallback) server running, and I am very confused as to why within /etc/fstab
[I]
  /dev/sdb1    /media/barry    ntfs-3g    defaults  0     0
[/I]
functions perfectly, but
[I]
  /dev/sdb1    /MediaServer    ntfs-3g    defaults  0     0
[/I]
puts the directory in place without mounting a drive.

Frustrating because my media server sees the files within the */MediaServer* directory tree, but cannot load them.
I _do_ have the directory in place...I assume that if i didn't, it wouldn't show the files in that folder under the root.
I've turned on the folders share settings, but that didn't have any effect.

Why?
Just trying to trim the branches of the Media Server's tree.

Thanks in advance...

---

