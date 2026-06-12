---
title: "RealPlayer"
date: 2005-06-19
forum: Installation &amp; Upgrades
---

### Post by lukus001 on 2005-06-19
I installed realplayer 10 from real player linux and followed some istallation steps i found in these forums... but real player wont start... and in the terminal i just get this error

```
(realplay.bin:9212): Gdk-WARNING **: locale not supported by Xlib

(realplay.bin:9212): Gdk-WARNING **: can not set locale modifiers

(realplay.bin:9212): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(realplay.bin:9212): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(realplay.bin:9212): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libsmooth.so: cannot open shared object file: No such file or directory

(realplay.bin:9212): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libsmooth.so: cannot open shared object file: No such file or directory

(realplay.bin:9212): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libsmooth.so: cannot open shared object file: No such file or directory

(realplay.bin:9212): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libsmooth.so: cannot open shared object file: No such file or directory

(realplay.bin:9212): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libsmooth.so: cannot open shared object file: No such file or directory

(realplay.bin:9212): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libsmooth.so: cannot open shared object file: No such file or directory
Failed to load pixbuf file: /usr/local/RealPlayer/share/realplay/icon.png: Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory

(realplay.bin:9212): GdkPixbuf-CRITICAL **: file gdk-pixbuf-io.c: line 770 (gdk_pixbuf_new_from_file): assertion `error == NULL || *error == NULL' failed

(realplay.bin:9212): GdkPixbuf-CRITICAL **: file gdk-pixbuf-io.c: line 770 (gdk_pixbuf_new_from_file): assertion `error == NULL || *error == NULL' failed

(realplay.bin:9212): GdkPixbuf-CRITICAL **: file gdk-pixbuf-io.c: line 770 (gdk_pixbuf_new_from_file): assertion `error == NULL || *error == NULL' failed

(realplay.bin:9212): GdkPixbuf-CRITICAL **: file gdk-pixbuf-io.c: line 770 (gdk_pixbuf_new_from_file): assertion `error == NULL || *error == NULL' failed

(realplay.bin:9212): GdkPixbuf-CRITICAL **: file gdk-pixbuf-io.c: line 770 (gdk_pixbuf_new_from_file): assertion `error == NULL || *error == NULL' failed

(realplay.bin:9212): GdkPixbuf-CRITICAL **: file gdk-pixbuf-io.c: line 770 (gdk_pixbuf_new_from_file): assertion `error == NULL || *error == NULL' failed
Failed to load pixbuf file: /usr/local/RealPlayer/share/realplay/icon.png: Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory

** (realplay.bin:9212): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:9212): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:9212): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:9212): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:9212): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:9212): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:9212): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:9212): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:9212): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:9212): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:9212): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(realplay.bin:9212): GLib-GObject-CRITICAL **: file gobject.c: line 1561 (g_object_ref): assertion `G_IS_OBJECT (object)' failed

** (realplay.bin:9212): CRITICAL **: file pango-engine.c: line 68 (_pango_engine_shape_shape): assertion `PANGO_IS_FONT (font)' failed

** ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
aborting...
/usr/bin/realplay: line 75:  9212 Aborted                 $REALPLAYBIN "$@"
```

---

### Post by afonic on 2005-06-19
How did you install it? Did you use apt-get or....

Make sure you follow these instructions:
[http://www.ubuntuguide.org/#realplayer](http://www.ubuntuguide.org/#realplayer)

---

### Post by lukus001 on 2005-06-19
it's because im on amd64 it doesn't work... apparantly... it's not on the repositories /synaptic so i manuall isntalled it from the .bin file provided from real's website.

unfortunatly that wasnt enough.  i've done this chroot thing i've read about and although synaptic32 /apt-get didn't work properly for realplayer... synaptic just hanged on installing and apt-get told me to download the rpm for an older version that i couldnt get my hands on and installed realplayer 10GOLD in the wrong areas.

I was able to edit/re-install the realplayer i downloaded to work as a chroot 32 application or what ever you would call it...  it's just missing a lot of codecs by the looks because downloading them in the terminal, some are missing/ missing installing candidate and others keep bringing up a realplayer installer (the same from using apt-get realplayer) so i don't think it's installing properly...

also doesnt look like it intergrated with my firefox32 version...

---

### Post by afonic on 2005-06-19
Well obviously there are some libraries missing, however I am not sure which ones you need to install. Maybe if you install the apt-get version you can get them installed and then remove just the realplayer and try the bin file?

BTW is w32codecs installed? If you install this you can play realvideo in totem and mplayer...

---

### Post by lukus001 on 2005-06-20
The w32codec isn't installed, it wouldn't allow me via apt-get see:
```
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
```

i might have to add the new repositories for the 32bit synaptic...

---

### Post by afonic on 2005-06-20
w32codecs is not in the default repositories, nor the universe ones you might have enabled. Also I think it should work with the 64bit version as well.
([http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories))

However in my opinion the A64 version of Ubuntu isn't mature yet. I have an Athlon64 for myself and I still use the i386 version for stability and compatibility reasons.

---

### Post by lukus001 on 2005-06-20
[QUOTE=afonic]w32codecs is not in the default repositories, nor the universe ones you might have enabled. Also I think it should work with the 64bit version as well.
([http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories))

However in my opinion the A64 version of Ubuntu isn't mature yet. I have an Athlon64 for myself and I still use the i386 version for stability and compatibility reasons.[/QUOTE]

Yeah, I saw the AMD64 download and assumed it was a build of ubuntu speicaly made for AMD64 chip /optimised version taking advantage of AMD's chip features or basically had the correct drivers for the CPU. Although I did asume it was going to be a 64bit operating sytem, I would have thought it would be back-compatible with 32bit aps seeing as the CPU runs both 32bit & 64bit, similar to window XP's compatbility mode for Win89 aps etc..

Would it be wise to format back to a 32bit version? i'm not really bothered about setting chroot up, i got this system for graphic design and so far all the aps such as GIMP, Blender, BlueFish have installed well and working perfectly as far as i can see, i just love real player and that is a little bit flaky atm.   My only problem is being new i don't really have a clue what i'm doing esp with chroot, I know i've installed it but i dont know how it works or what i've gone and done to my system =)

I added some more downlaod sources to that source.list /repositories (under dchroot -d) and it allowed me to install the w32codecs fine however real player isn't using them, I dont know if thats because part of the chroot process i renamed it to realplay32 OR because i set real play up at /usr/local/RealPlayer/ which is where i read to do it, but that was before i found out about the 64bit issue/chroot.   i think i might have to re-install it into /usr/bin like the other aps?

But yeah, w32codec are in 64bit aswell but of course realplayer isnt :'(

---

