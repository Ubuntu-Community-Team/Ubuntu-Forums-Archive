---
title: "Ubuntu base + XFCE4 is good, but..."
date: 2005-09-07
forum: Installation &amp; Upgrades
---

### Post by fresco on 2005-09-07
Hello friends! 

I just installed an Ubuntu base and all the stuff for XFCE4. Everything works ok, but there are some problems to fix:

*First, where to add keyboard layouts? I need to set up Russian(winkeys) layout. I have edited the xorg.conf and changed from

Option          "XkbLayout"     "us"
to
Option          "XkbLayout"     "us,ru(winkeys)"

After restarting X didn't come up with an error, but I am still unable to locate my lang. settings. By the way, standart Ubuntu setup does not have ru(winkeys) option it its xorg.conf. I suppose, settings are kept somewhere within GNOME. Does any of you has had similar experience in XFCE? How to get layouts to appear and switch them?

*And second. Programs like Firefox and Thunderbird (not only these two) don't show russian text correcty, only these funny signs (see screenshot). Latvian text also has these problems. I have installed language-pack-ru and language-pack-lv, but nothing has changed.

So... What to do?  :grin: 

Thank you all!

---

### Post by mappleJoe on 2005-09-08
I'm not quite sure about language layout you mentioned but concerning messy characters (both Russian and Latvian) you should just regenerate locales by doing this:

```
sudo dpkg-reconfigure locales
```

then check appropriate locales (say, en_US, lv_LV, ru_RU).. 

You're done! I can't recall if logoff or restart was needed but at the end you'll get the results..

---

