---
title: "evince annotiations"
date: 2010-10-09
forum: Installation &amp; Upgrades
---

### Post by desmane on 2010-10-09
Hi folks, 

after all annotiations of pdfs arrived on the gnome desktop. After waiting a for a while now, I have installed evince 2.32.0 on my ubuntu 10.04 (which is actually a maverick deb). I've been told that I need poppler 0.15 to actually ADD annotiations. So I went to their website and installed the package from source, the usual way with ./configure - make - make install. Even tried checkinstall to make sure it gets properly installed on my system. 

I can see annotiations in pdf files and have the item in the drop down menu of the sidebar in evince, but I am missing the ADD button (I guess related to poppler being and old package still) in evince, seen in the video here: [http://carlosgc.linups.org/img/ev-annots.ogg](http://carlosgc.linups.org/img/ev-annots.ogg)

Opening the "about" of evince, it says Document Viewer
Using poppler/cairo (0.14.3). Why the f*** :) is evince not using the new poppler 0.15 ??? 

Uprading to maverick doesnt seem to fix this since poppler 0.14 is still in the repos. 

Help is appreciated, thanks a lot!!

---

### Post by desmane on 2010-10-09
please help

---

### Post by desmane on 2010-10-09
-.-

---

### Post by desmane on 2010-10-24
Yes, YOU have an idea! :)

---

### Post by desmane on 2010-10-24
after installing poppler 0.15 (./configure, make, sudo make install) it says: 

```
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

```

what does that mean??

---

### Post by jpfle on 2010-10-24
Maybe you would have some info in the poppler mailing list:

[http://lists.freedesktop.org/mailman/listinfo/poppler](http://lists.freedesktop.org/mailman/listinfo/poppler)

---

