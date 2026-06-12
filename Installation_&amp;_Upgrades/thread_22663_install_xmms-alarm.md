---
title: "install xmms-alarm"
date: 2005-03-28
forum: Installation &amp; Upgrades
---

### Post by LucianX on 2005-03-28
Hey guys,

i've been working on ubuntu for some time now, and ive just done a fresh reinstall. Ive gotten xmms to install with no problems once again, but now im tryin to install a plugin for it (xmms-alarm-0.3.6) and for some reason it will not install. ive done 
./configure and make install and heres the errors i get with make install.

alarm.c:43:25: xmms/plugin.h: No such file or directory
alarm.c:44:27: xmms/xmmsctrl.h: No such file or directory
alarm.c:45:29: xmms/configfile.h: No such file or directory

also a few of these errors:
implicit declaration of function
request for member `xmms_session' in something not a structure or union
warning: excess elements in scalar initializer

I've also read that im might want to install glib-devel, gtk-devel and xmms-devel packages. Can anyone tell me how to install these? Any help will be greatly appreciated!

Thnx - Lucian

---

