---
title: "Virtual PC install.  xorg.conf cant find"
date: 2005-10-20
forum: Installation &amp; Upgrades
---

### Post by Garvie on 2005-10-20
I went to install 5.10 on Virtual PC and I cant find the file to change the setting from 24 to 16.  Apparently in the other versions of this Linux you could use root dir and go to /etc/X11  and pico the xorg.conf file and change this setting.  This dir does not exist apparently, or maybe i'm just a little slow.  Somebody please help me along my way

 Garvie

---

### Post by TeckniX on 2005-10-20
so what's in your X11 directory? or does the directory itself not exist?
You could probably try to run the xf86config on a command line and edit it - but if you do have a display then there has to be some kind of file that XF86 is reading.

---

### Post by Garvie on 2005-10-20
I was stressed out and just didnt take the time to find the file.  I just ended up finding the file and made the necessary changes.  Its working just fine now!  Thanks for the help though!

---

