---
title: "how do I burn a distro to dvd"
date: 2011-07-30
forum: Installation &amp; Upgrades
---

### Post by bobk_nyc on 2011-07-30
I have a distro, in iso, that I want to make into a bootable DVD.  what can I use....open source, please

---

### Post by garvinrick4 on 2011-07-30
Package: brasero                         
State: installed
Automatically installed: no
Version: 3.0.0-1ubuntu2
Priority: optional
Section: gnome
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Uncompressed Size: 1,094 k
Depends: libbrasero-media3-1 (= 3.0.0-1ubuntu2), libc6 (>= 2.4), libcairo2 (>=
         1.2.4), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.28.0),
         libgstreamer-plugins-base0.10-0 (>= 0.10.0), libgstreamer0.10-0 (>=
         0.10.15), libgtk-3-0 (>= 3.0.0), libice6 (>= 1:1.0.0),
         liblaunchpad-integration-3.0-1 (>= 0.1.17), libnautilus-extension1 (>=
         1:2.91), libpango1.0-0 (>= 1.14.0), libsm6, libtotem-plparser17 (>=
         2.32), libxml2 (>= 2.7.4), gstreamer0.10-plugins-base (>= 0.10.0),
         gnome-icon-theme, gvfs, brasero-common (>= 3.0), brasero-common (< 3.1)
Recommends: brasero-cdrkit
Suggests: vcdimager, libdvdcss2
Conflicts: nautilus-cd-burner
Description: CD/DVD burning application for GNOME
 Brasero is a simple application to burn, copy and erase CD and DVD media:
 audio, video or data. It features among other things: 
 * On-the-fly burning 
 * Multisession support 
 * On-the-fly conversion of music playlists in all formats supported by
   GStreamer 
   
 This package contains the main binary, the burning plugins and the nautilus
 extension. 
 
 The following packages, if installed, will provide Brasero with added
 functionality: 
 * cdrdao to burn combined data/audio CDs and for byte-to-byte copy 
 * GStreamer backends to support more audio formats 
 * vcdimager to create VCDs or SVCDs 
 * libdvdcss2 to copy encrypted DVDs
Homepage: [http://www.gnome.org/projects/brasero/](http://www.gnome.org/projects/brasero/)

rick@rick-HP:~$

---

### Post by bobk_nyc on 2011-07-30
> **garvinrick4 said:**
> package: Brasero                         
state: Installed

 the following packages, if installed, will provide brasero with added
 functionality: 
 * cdrdao to burn combined data/audio cds and for byte-to-byte copy 
 * gstreamer backends to support more audio formats 
 * vcdimager to create vcds or svcds 
 * libdvdcss2 to copy encrypted dvds
homepage: [http://www.gnome.org/projects/brasero/](http://www.gnome.org/projects/brasero/)

rick@rick-hp:~$

thanks. That seems to be working

---

