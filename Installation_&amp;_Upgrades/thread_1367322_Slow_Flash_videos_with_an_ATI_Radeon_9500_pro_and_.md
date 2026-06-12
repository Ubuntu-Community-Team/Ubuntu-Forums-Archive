---
title: "Slow Flash videos with an ATI Radeon 9500 pro and Ubuntu Karmic 9.10"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by stefano.bolli on 2009-12-29
Hello!
I have a pc with an ATI Radeon 9500 pro and Ubuntu 9.10 Karmic. I have experienced very slow flash videos, very very slow loading of wine programs (the lightest utorrent, office 2003...) and changing gtk2.0 themes. I have found a solution browsing the internet and unfortunately I cannot give the author the right credits at this moment ( I hope to do it soon editing this post). this solution works like a charm for me:

1)run a terminal and type:
sudo /etc/init.d/gdm stop
to shut down gnome.
2) log in with your username and password
3)sudo Xorg -configure
to create xorg.conf.new in your home
4)sudo gdm stop
to restart gnome.
5) sudo gedit xorg.conf.new
6)add these lines in Section "Device":
Option      "AGPmode"             "1"
Option      "AccelMethod"         "EXA"
Option      "MigrationHeuristic"  "greedy"
Option      "AccelDFS"            "true"
Option      "EnablePageFlip"      "true"
Option      "EnableDepthMoves"    "true"
7)save as /etc/X11/xorg.conf
8) repeat steps 1 and 4 to restart your gnome.

Happy new year!

---

### Post by crc294 on 2010-01-12
That worked for me, thanks!

I have a mobility radeon 9600.

---

