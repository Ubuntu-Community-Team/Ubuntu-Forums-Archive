---
title: "Google Chrome"
date: 2009-09-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by wfp on 2009-09-09
Have Chrome installed on koala64-bit need help with getting adobe flash 10 alpha to work. Thanks

---

### Post by waspbr on 2009-09-09
[try here]("http://www.ubuntugeek.com/howto-enable-flash-support-for-google-chromium-browser.html")

---

### Post by wfp on 2009-09-09
I really do not want to install nsplugin-wrapper is there not a way to install adobe alpha 10 instead. Thanks

---

### Post by steffmeister on 2009-09-09
you can install a 32bit version of chrome...

i wouldn't use chrome at all at the moment, because of important features missing and it is quite unstable what concerns plugins.

i don't know if it is able to use plugins like gnash or swfdec (search for them).

---

### Post by wfp on 2009-09-09
Np thanks.

---

### Post by wfp on 2009-09-09
Plugins (e.g. Flash) are partway implemented and will cause frequent crashes. Use --enable-plugins to turn them on if you're ok with that; the browser is otherwise quite stable  From Google

---

### Post by waspbr on 2009-09-09
Try copying the flash plugin (libflashplayer.so) into the folder

```
/usr/lib/chromium-browser/plugins
```

what I did was just to copy the one from my ~/.mozilla/plugin folder


then use the 

```
chromium-browser --enable-plugins
```

command to start chromium

---

### Post by Joe_Bishop on 2009-09-09
Put 64 bit for 64 bit system or 32 bit for 32 one plugin into ~/.mozilla/plugins, then run chromium with --enable-plugins option

---

### Post by KegHead on 2009-09-09
Hi!

I'm using chrome on 9.10 with no problems.

kegHead

---

