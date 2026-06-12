---
title: "Gnome Screenshot utility removed in 24.04.1 LTS?"
date: 2024-11-06
forum: Installation &amp; Upgrades
---

### Post by geeky-1 on 2024-11-06
I upgraded to 24.04.1 LTS a week ago and the Gnome Screenshot tool seems to have been removed. I can't find it in Ubuntu Software either. Shouldn't this tool be in the software center or do I have to search for some other similar tool?

---

### Post by matt-rw on 2024-11-06
*I have it installed.   Try "sudo apt install gnome-screenshot" in a terminql.*

$ apt info gnome-screenshot
Package: gnome-screenshot
Version: 41.0-2build2
Priority: optional
Section: universe/gnome
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Installed-Size: 1,115 kB
Depends: libc6 (>= 2.34), libcairo2 (>= 1.10.0), libgdk-pixbuf-2.0-0 (>= 2.23.0), libglib2.0-0t64 (>= 2.79.0), libgtk-3-0t64 (>= 3.21.4), libhandy-1-0 (>= 1.5.0), libx11-6, libxext6, dconf-gsettings-backend | gsettings-backend
Homepage: [https://wiki.gnome.org/Apps/Attic/GnomeUtils](https://wiki.gnome.org/Apps/Attic/GnomeUtils)
Task: ubuntu-unity-desktop, ubuntucinnamon-desktop-minimal, ubuntucinnamon-desktop, ubuntucinnamon-desktop, ubuntucinnamon-desktop-raspi
Download-Size: 174 kB
APT-Manual-Installed: yes
APT-Sources: [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) noble/universe amd64 Packages
Description: screenshot application for GNOME
 This tool takes a picture of the desktop or of a window and saves it
 into a file.

---

### Post by davetheoldcoder on 2024-11-07
On Ubuntu 24.04.1, if I press the PrtSc key, the Screenshot Window Sizer (Gnome extension) pops up and lets me take a screenshot.

The package gnome-screenshot is not installed, so there's something else that's handling it on my system.

---

### Post by deadflowr on 2024-11-07
It's no longer there because gnome-shell has an integrated screenshot utility.
Which can either screenshot or do a screencast.

---

### Post by vanadium on 2024-11-08
You can always reassign the shortcut keys to make a screenshot to any other tool, including gnome-screenshot, if you wish (Settings - Keyboard).

---

