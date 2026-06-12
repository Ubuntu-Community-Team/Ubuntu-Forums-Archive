---
title: "pls help: update broke all PNG"
date: 2007-04-11
forum: Installation &amp; Upgrades
---

### Post by not_a_commie on 2007-04-11
Yesterday I ran apt-get update on Dapper. It seemed to go fine. When I ran startx, though, I got a bunch of messages stating that the image format was unsupported. When it finally showed me the desktop, there were no icons where there should have been and there was no background image. When I ran update-manager, I got a similar message. I decided to run the full Edgy upgrade and see if that helped. The upgrade (using apt-get) finished fine. However, after a reboot, I still have the same problem. This message is from update-manager:

gobject.GError: Couldn't recognize the image file format for file /usr/share/icons/Tnago/32x32/apps/update-manager.png'

I'd appreciate any help...

---

### Post by not_a_commie on 2007-04-11
So I think my gdk-pixbuf.loaders file is corrupt. It contains no "png" anywhere and ends with this line: 

"  <!DOCT"YPE svg"  "*                   " 100

Can somebody tell me how to repair the file? Thanks.

---

### Post by not_a_commie on 2007-04-11
Another update: running gdk-pixbuf-query-loaders gives this message:

g_module_open() failed for libpixbufloader-png.so: /opt/local/lib/libpng12.so.0: undefined symbol: deflate

Any idea how to fix this one? Thanks again.

---

### Post by not_a_commie on 2007-04-11
So it's using libpng from /opt/local/lib when it should be using the one from /usr/lib, true? How do I change it to use the right one for GTK2?

---

### Post by not_a_commie on 2007-04-11
Okay. Fixed it. I had to change the ordering in ld.so.conf and rerun ldconfig.

---

