---
title: "lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/nate/.gvfs"
date: 2012-12-26
forum: Installation &amp; Upgrades
---

### Post by mackdiddy on 2012-12-26
help me plz 

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/nate/.gvfs
      Output information may be incomplete.
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF    NODE NAME
dpkg    3087 root    3uW  REG    8,2        0 2359963 /var/lib/dpkg/lock

---

### Post by Kirk Schnable on 2012-12-26
[http://forums.fedoraforum.org/showthread.php?t=258299](http://forums.fedoraforum.org/showthread.php?t=258299)

> Comes up every couple of days:

[http://forums.fedoraforum.org/showthread.php?t=258225](http://forums.fedoraforum.org/showthread.php?t=258225)

This is because gvfs is not a filesystem it is a memory resident tree
representing configuration controls for gnome.

Root doesn't have access because the process presenting the tree doesn't support it.

You will always get this error when you are logged via the GUI and using
gnome. A varient exists, I believe, for KDE.

You will also get this error if the user is terminated (kill -9) because
the process implementing the filesystem is aborted, leaving the mountpoint corrupted in the system cache (dentry I believe it is).

Ignore it.

Is this error causing you any issues?  If not, sounds like it's OK to ignore it.

---

