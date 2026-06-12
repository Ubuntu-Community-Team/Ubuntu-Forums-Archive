---
title: "dpkg: error, postinst seg-faults"
date: 2006-07-11
forum: Installation &amp; Upgrades
---

### Post by yotam on 2006-07-11
Trying to install Dapper/xubuntu starting from RedHat-based box.
I did the partiton/debootstrap/chroot kernel-install grub-configuring.
Now it booted nicely to Ubuntu,

Later trying to:
    apt-get install xubuntu-desktop
I consistently get into series of failures.
For examplem now when trying to 
    apt-get -f remove
I get 380 lines of mostly erro messages starting with:

Reading package lists...
Building dependency tree...
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
63 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up gconf2 (2.14.0-1ubuntu2) ...
gconf-merge-tree: error while loading shared libraries: /usr/lib/libgobject-2.0.so.0: invalid ELF header
dpkg: error processing gconf2 (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of capplets-data:
 capplets-data depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing capplets-data (--configure):
 dependency problems - leaving unconfigured
Setting up desktop-file-utils (0.10-1ubuntu12) ...
/var/lib/dpkg/info/desktop-file-utils.postinst: line 9: 18380 Segmentation fault      /usr/bin/update-desktop-database
dpkg: error processing desktop-file-utils (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of gksu:
 gksu depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing gksu (--configure):
 dependency problems - leaving unconfigured
Setting up libgtk2.0-bin (2.8.17-1ubuntu5) ...
Updating the IM modules list for GTK+-2.4.0.../usr/bin/gtk-query-immodules-2.0: error while loading shared libraries: /usr/lib/libgmodule-2.0.so.0: invalid ELF header

---

### Post by linear on 2006-07-11
[LEFT]Welcome to the wonderful world of broken dependencies.
 
The is a very good howto [here]("http://www.ubuntuforums.org/showthread.php?t=186672") that may be of some help.[/LEFT]

---

