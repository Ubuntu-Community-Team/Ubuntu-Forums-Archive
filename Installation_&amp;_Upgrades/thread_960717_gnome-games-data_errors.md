---
title: "gnome-games-data errors"
date: 2008-10-27
forum: Installation &amp; Upgrades
---

### Post by hardyderik on 2008-10-27
hello!
for starters i am a complete nOOb who recently ditched windows for linux, so please take it easy on me hahaha. I seem to be having an issue with gnome-games-data. Every time I install a new game or a new upgrade it fails to do so. This is a message that I recently got when I typed in sudo apt-get install -f. It is really similar to all the other messages I have gotten. 

Setting up gnome-games-data (1:2.22.3-0ubuntu2) ...
/usr/share/gconf/schemas/gnibbles.schemas:2702: parser error : Input is not proper UTF-8, indicate encoding !
Bytes: 0x84 0xE3 0x82 0x82
        <short>Á&#65533;&#12418;&#34411;&#12398;&#33394;</short>
                 ^
dpkg: error processing gnome-games-data (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 gnome-games-data
E: Sub-process /usr/bin/dpkg returned an error code (1)

I tried searching around the forums for a problem that is similar to mind, but i have yet to. Any help would be greatly appreciated!

---

