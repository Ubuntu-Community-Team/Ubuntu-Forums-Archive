---
title: "Virtual Server 2005"
date: 2006-07-26
forum: Installation &amp; Upgrades
---

### Post by Geekster on 2006-07-26
:confused: I have installed into VS2K5 but can't get resolution or refresh settings correct. Login screen has inverted colors. I was able to change resolution to 640x480 from 800x600 and now it's black and white. The screen is wider than the monitor though so I can't see past middle. It also shows vertical lines on screen almost as if the screen is stretched out wider than it should be at those resolutions. I don't know if the monitor settings help much as VS2K5 presents no control over device types and I assume Ubuntu used drivers for the closest thing it could find. Any help would be greatly appreciated.

---

### Post by FredB on 2006-07-26
Kill this crap. It will never work great with linux, because it cannot use 24 or 32 bits display.

Try VMWare Server, which works great with linux or any other OSes other than Windows.

---

### Post by glennpratt on 2006-08-20
^ Lame.

Just install with graphics safe mode option from the CD boot menu.  Works great for me.  If you need to edit /etc/X11/xorg.conf and change the defaultdepth to 16.

Bear in mind Virtual Server is not really designed to use you virtual OS's directly like VPC or VMware, but rather just for minimal config (think of it like a virtual data center).  Use VNC or remote X (i forget the proper name) to manage it once it's installed.

---

