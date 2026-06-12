---
title: "Flash.."
date: 2010-02-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by HarshReality on 2010-02-17
Ive seen references (and I cant find them again for the life of me) of a Debian source that is flash x64 in the debian repos.. can somebody throw me a link to the deb so I can see about installing it rather than the wrapper in Lucid. Everything seems to be peachy thus far.

---

### Post by zika on 2010-02-18
Why not just download and extract:```
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz
tar xvf libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz
mkdir ~/.mozilla/plugins
mv libflashplayer.so ~/.mozilla/plugins
rm libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz
```...?

---

### Post by portis on 2010-02-18
> **HarshReality said:**
> Ive seen references (and I cant find them again for the life of me) of a Debian source that is flash x64 in the debian repos.. can somebody throw me a link to the deb so I can see about installing it rather than the wrapper in Lucid. Everything seems to be peachy thus far.

[http://packages.debian.org/sid/flashplugin-nonfree](http://packages.debian.org/sid/flashplugin-nonfree)

---

### Post by forcecore on 2010-02-18
> **zika said:**
> Why not just download and extract:```
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz
tar xvf libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz
mkdir ~/.mozilla/plugins
mv libflashplayer.so ~/.mozilla/plugins
rm libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz
```...?

i have done this way forever (GUI way with Nautilus) and always works.

---

### Post by zika on 2010-02-18
> **forcecore said:**
> i have done this way forever (GUI way with Nautilus) and always works.It's a bit more time consuming and tricky to explain the GUI way, isn't it...? But, once You've got a grip of how to do it, it's faster... But, only if You do not have script. With script, CLI way is much faster...

---

