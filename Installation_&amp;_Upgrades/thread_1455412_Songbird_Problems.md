---
title: "Songbird Problems"
date: 2010-04-15
forum: Installation &amp; Upgrades
---

### Post by hawaiian1der on 2010-04-15
I was trying to install Songbird following this guide:
[HTML]http://www.ubuntugeek.com/install-songbird-music-player-in-ubuntu.html[/HTML]

I got all the way up to running the code:
```
./Songbird
```

I thought it was capitalization error so I changed it to ./songbird. That didn't work. I checked it with the ls command in the Songbird directory and the name of it is songbird not Songbird. I can't figure out what is wrong because when i run ./songbird this happens:
```
/opt/Songbird$ ./songbird

(songbird-bin:10552): GLib-WARNING **: g_set_prgname() called multiple times
././songbird-bin: symbol lookup error: /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_task_pool_get_type
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal

```

---

### Post by hawaiian1der on 2010-04-16
Does anyone know? It's in the _gst.so file.

---

