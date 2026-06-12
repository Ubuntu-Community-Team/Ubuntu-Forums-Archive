---
title: "Update Error &quot;(gtk-update-icon-cache-3.0:4568): GdkPixbuf-WARNING **: Cannot open ..."
date: 2015-10-15
forum: Installation &amp; Upgrades
---

### Post by RogerDavis on 2015-10-15
14.04, 64 bit

Attempted todays update, got the following errors in the log:
-----------------------
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Processing triggers for libglib2.0-0:amd64 (2.40.2-0ubuntu1) ...
Processing triggers for libglib2.0-0:i386 (2.40.2-0ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for hicolor-icon-theme (0.13-1) ...

(gtk-update-icon-cache-3.0:4568): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.
Setting up libudev1:amd64 (204-5ubuntu20.15) ...
Setting up libudev1:i386 (204-5ubuntu20.15) ...
Setting up udev (204-5ubuntu20.15) ...
udev stop/waiting
udev start/running, process 4618
Removing 'diversion of /bin/udevadm to /bin/udevadm.upgrade by fake-udev'
update-initramfs: deferring update (trigger activated)
Setting up libsystemd-daemon0:amd64 (204-5ubuntu20.15) ...
-----------------------------------
Attempted running " gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache " as suggested :

roger@roger-desktop:~$ sudo gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
bash: /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache: Permission denied
roger@roger-desktop:~$ 
-------------------------------------------
Everything seems to be working, but the above is obviously not right.  Now what do I do ?

---

