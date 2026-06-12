---
title: "Why can I play WMA/WMV without w32codecs"
date: 2007-07-25
forum: Installation &amp; Upgrades
---

### Post by Kwag on 2007-07-25
Hi All!

I do NOT have the w32codecs package installed.  (as a side note nor do I have libdvdcss2 installed).

Yet I can play .wma, .wmv, .mpg, .mpeg, .mov files.  I can view video on cnn.com and msnbc.com using swiftfox web browser.  All of these media types load up in MPlayer.  Sometimes I get an error prompt saying that w32codecs are missing, sometimes not.  However, in all cases the media plays flawlessly.

WHY?  I don't get it.  

Thanks to whoever will alleviate my confusion and satisfies my curiosity.

---

### Post by yabbadabbadont on 2007-07-26
The latest ffmpeg libraries provide native support for most versions of those formats.  You still won't be able to play WMA or WMV files that use DRM, but you wouldn't be able to with the win32codecs installed either.  libdvdcss2 is only needed when decoding the VOB files that are on DVDs, so as long as you don't try to play a CSS protected DVD, you don't need it.  If you ever do need it, just install libdvdread3 and then, in a terminal window, run ```
sudo /usr/share/doc/libdvdread3/install-css.sh
```
Edit: Actually, that is the command to use on Feisty.  On Edgy, it might be different.  I think the install-css.sh script is in /usr/share/doc/libdvdread3/examples on Edgy and Dapper.

---

### Post by Kwag on 2007-07-26
Thanks for the info.  

I wonder how many people aren't aware of this and are therefore using Automatix, EasyUbuntu, or manually installing w32codecs when they don't really need to.

As for me, I have no desire to play these protected DVDs on my computer ( that is what my TV is for :) )

---

