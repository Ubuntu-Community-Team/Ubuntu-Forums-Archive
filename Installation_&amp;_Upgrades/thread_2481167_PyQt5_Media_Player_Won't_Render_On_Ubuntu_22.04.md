---
title: "PyQt5 Media Player Won't Render On Ubuntu 22.04"
date: 2022-11-20
forum: Installation &amp; Upgrades
---

### Post by mike375 on 2022-11-20
Recently installed Ubuntu 22.04 on a new laptop.  I've got a simple  Python video app that uses QMediaPlayer.  I'm getting the following  error in the console: Error: "Internal error: could not render surface"  when I open a mp4 file. 

Believe I'm running X11;  In /etc/gdm3/custom.conf has a line "WaylandEnabled=false".  
The Python application runs fine on my old laptop running Ubuntu 20.04.

 
There are no changes to the program between Ubuntu 20.04 and 22.04.

Googled all around and can't find anything.

---

### Post by #&amp;thj^% on 2022-11-20
I'm not sure if I can help with this, but is this installed?
```
gstreamer1.0-plugins-base-apps
```
Info:
```
 nala show gstreamer1.0-plugins-base-apps
Package: gstreamer1.0-plugins-base-apps
Version: 1.20.3-2
Architecture: amd64
Installed: yes
Priority: optional
Essential: no
Section: utils
Source: gst-plugins-base1.0
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Maintainers of GStreamer packages <gst-plugins-base1.0@packages.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 190 KB
Depends: 
  libc6 (>= 2.34)
  libglib2.0-0 (>= 2.56)
  libgstreamer-plugins-base1.0-0 (>= 1.20.0)
  libgstreamer1.0-0 (>= 1.20.0)
  gstreamer1.0-tools
Conflicts: gstreamer1.0-plugins-base-apps
Homepage: https://gstreamer.freedesktop.org
Download-Size: 38 KB
APT-Sources: http://us.archive.ubuntu.com/ubuntu/ lunar/main amd64 Packages
Description: GStreamer helper programs from the "base" set
 GStreamer is a streaming media framework, based on graphs of filters
 which operate on media data.  Applications using this library can do
 anything from real-time sound processing to playing videos, and just
 about anything else media-related.  Its plugin-based architecture means
 that new data types or processing capabilities can be added simply by
 installing new plug-ins.
 .
 This package contains helper programs from the "base" set, an essential
 exemplary set of elements.

```
I find mutter a challenge this go round.

---

### Post by &amp;KyT$0P# on 2022-11-21
> **mike375 said:**
> Believe I'm running X11;

To be sure, what session type is selected at login?

> Error: "Internal error: could not render surface"

I would wonder if running your program with [FONT=Courier New]LIBGL_ALWAYS_SOFTWARE=1[/FONT] environment variable set might make any difference?

---

### Post by mike375 on 2022-11-21
Thanks.  I'm seeing  gstreamer1.0-plugins-base-apps is installed.  Might need to go back to 20.04.  V

---

### Post by #&amp;thj^% on 2022-11-21
> **mike375 said:**
> Thanks.  I'm seeing  gstreamer1.0-plugins-base-apps is installed.  Might need to go back to 20.04.  V
+1 Nothing beats a reliable working system
And halogen2 had a worth a shot suggestion as well.
Good Luck

---

