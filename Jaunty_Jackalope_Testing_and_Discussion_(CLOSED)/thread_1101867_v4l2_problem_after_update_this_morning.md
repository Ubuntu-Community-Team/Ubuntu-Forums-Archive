---
title: "v4l2 problem after update this morning"
date: 2009-03-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by zaomaster on 2009-03-20
So I just got a Logitech QuickCam Pro for Notebooks this morning and when I plugged it in to my ThinkPad T30 everything worked great. Then I did an update, which installed these files:
```
Upgraded the following packages:
cups-driver-gutenprint (5.2.3-0ubuntu1) to 5.2.3-0ubuntu2
ffmpeg (3:0.svn20090303-1ubuntu1) to 3:0.svn20090303-1ubuntu2
foo2zjs (20090217-0ubuntu2) to 20090217-0ubuntu3
gnome-app-install (0.5.21-0ubuntu1) to 0.5.22-0ubuntu1
gnome-panel (1:2.26.0-0ubuntu2) to 1:2.26.0-0ubuntu3
gnome-panel-data (1:2.26.0-0ubuntu2) to 1:2.26.0-0ubuntu3
gnome-settings-daemon (2.26.0-0ubuntu1) to 2.26.0-0ubuntu2
gucharmap (1:2.26.0-0ubuntu1) to 1:2.26.0-0ubuntu2
libavdevice52 (3:0.svn20090303-1ubuntu1) to 3:0.svn20090303-1ubuntu2
libavfilter0 (3:0.svn20090303-1ubuntu1) to 3:0.svn20090303-1ubuntu2
libavformat52 (3:0.svn20090303-1ubuntu1) to 3:0.svn20090303-1ubuntu2
libc6 (2.9-4ubuntu2) to 2.9-4ubuntu3
libc6-dev (2.9-4ubuntu2) to 2.9-4ubuntu3
libc6-i686 (2.9-4ubuntu2) to 2.9-4ubuntu3
libgtkhtml-editor-common (1:3.26.0-0ubuntu1) to 1:3.26.0-0ubuntu2
libgtkhtml-editor0 (1:3.26.0-0ubuntu1) to 1:3.26.0-0ubuntu2
libgtkhtml3.14-19 (1:3.26.0-0ubuntu1) to 1:3.26.0-0ubuntu2
libgtksourceview2.0-0 (2.6.0-0ubuntu1) to 2.6.0-0ubuntu2
libgtksourceview2.0-common (2.6.0-0ubuntu1) to 2.6.0-0ubuntu2
libgucharmap7 (1:2.26.0-0ubuntu1) to 1:2.26.0-0ubuntu2
libgutenprint2 (5.2.3-0ubuntu1) to 5.2.3-0ubuntu2
libnautilus-extension1 (1:2.26.0-0ubuntu3) to 1:2.26.0-0ubuntu4
libpanel-applet2-0 (1:2.26.0-0ubuntu2) to 1:2.26.0-0ubuntu3
libpostproc51 (3:0.svn20090303-1ubuntu1) to 3:0.svn20090303-1ubuntu2
libpq5 (8.3.6-1build1) to 8.3.7-1
libswscale0 (3:0.svn20090303-1ubuntu1) to 3:0.svn20090303-1ubuntu2
nautilus (1:2.26.0-0ubuntu3) to 1:2.26.0-0ubuntu4
nautilus-data (1:2.26.0-0ubuntu3) to 1:2.26.0-0ubuntu4
python-gnome2-desktop (2.26.0-0ubuntu1) to 2.26.0-0ubuntu2
rhythmbox (0.11.99.1-0ubuntu1) to 0.12.0-0ubuntu1
splix (2.0.0-0.1ubuntu1) to 2.0.0-0.1ubuntu2
usplash-theme-ubuntu (0.22) to 0.23
```
and now it doesn't work... Through 'gstreamer-properties' I had the device show up in 'Default Input', but now, it doesn't see it.

Any thoughts as to which update might have borked this? And what I might do to fix it?

Thanks

---

