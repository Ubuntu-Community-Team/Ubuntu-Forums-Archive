---
title: "Trying to install Cairo-Dock"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by chango77745 on 2008-05-12
Trying to install cairo-dock
I downloaded the tarball
Extracted to my desktop and now I am trying to copy it to my /opt and this is what I get

"evan@evan-laptop:~$ sudo cp /home/evan/Desktop/cairo-dock /opt
cp: omitting directory `/home/evan/Desktop/cairo-dock'"

But I am not gettig the folder in the /opt folder......

I need to install the cairo-dock
This is what is in it

"evan@evan-laptop:~$ ls /home/evan/Desktop/cairo-dock
amarok.svg folder.svg mozilla-firefox.svg
azureus.svg gaim.svg music.svg
beagled.svg gconf-editor.svg ooo-calc.svg
cairo-dock gnome-audio.svg ooo-impress.svg
cairo-dock.c gnome-calculator.svg ooo-writer.svg
cairo-dock.c~ gnome-fs-home.svg search.svg
cairo-dock.copy1 gnome-gimp.svg start-cairo-dock.sh
chat.svg gnome-terminal.svg sticky-notes.svg
clock.svg gxine.svg stop.svg
computer.svg im.svg tango-colors.h
configure.scan lockscreen.svg terminal.svg
dc++.svg logout.svg user-home.svg
development.svg lowfat.svg user-trash-full.svg
editor.svg Makefile web-browser.svg
email.svg movies.svg xmms.svg"

---

### Post by Partyboi2 on 2008-05-13
use the -r option (copy directories recursively)
so
```
 sudo cp -r /home/evan/Desktop/cairo-dock /opt
```

Incase you were not aware you can install the cairo-dock deb package.
[http://prdownload.berlios.de/cairo-dock/cairo-dock-plug-ins_v1.5.5.4_i686-32bits.deb](http://prdownload.berlios.de/cairo-dock/cairo-dock-plug-ins_v1.5.5.4_i686-32bits.deb)
[http://prdownload.berlios.de/cairo-dock/cairo-dock_v1.5.5.4_i686-32bits.deb](http://prdownload.berlios.de/cairo-dock/cairo-dock_v1.5.5.4_i686-32bits.deb)

---

### Post by neymac on 2008-05-14
Or you ca try the SVN version using the how-to of the site [http://www.cairo-dock.org/ww_page.php?p=From SVN&lang=en]("http://www.cairo-dock.org/ww_page.php?p=From SVN&lang=en")

---

