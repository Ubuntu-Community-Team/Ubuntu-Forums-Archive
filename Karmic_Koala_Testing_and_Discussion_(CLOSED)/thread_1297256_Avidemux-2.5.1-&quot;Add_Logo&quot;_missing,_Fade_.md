---
title: "Avidemux-2.5.1-&quot;Add Logo&quot; missing, Fade out broken."
date: 2009-10-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by emarkay on 2009-10-21
It was here:[http://avidemux.org/admWiki/index.php?title=Video_filter_Logo](http://avidemux.org/admWiki/index.php?title=Video_filter_Logo)

And under "Video >  Filters" where  "Add Logo" feature was, now shows an entry "Partial" which crashes  program with:

Segfault
 at line 0, file ??/usr/lib/libADM_core.so(ADM_backTrack+0x6d) [0x1f292d]
/usr/lib/libADM_core.so(_Z20sig_segfault_handleri+0x46) [0x1f2db6]
[0x22a400]
/usr/lib/libADM_coreImage.so(_ZN10CONFcouple10lookupNameEPKc+0x1a) [0x213d9a]
/usr/lib/libADM_coreImage.so(_ZN10CONFcouple9getCoupleEPKcPj+0x2c) [0x2142bc]
avidemux2_gtk(_ZN15ADMVideoPartialC1EP22AVDMGenericVideoStreamP10CONFcouple+0x58) [0x80c8708]
avidemux2_gtk(_Z14partial_createP22AVDMGenericVideoStreamP10CONFcouple+0x2b) [0x80c881b]
avidemux2_gtk [0x81add5b]
/usr/lib/libgtk-x11-2.0.so.0 [0x11ec72f]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1b2) [0x646d072]
/usr/lib/libgobject-2.0.so.0 [0x64827a8]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7bd) [0x6483b2d]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0x6483fb6]
/usr/lib/libgtk-x11-2.0.so.0(gtk_tree_view_row_activated+0x98) [0x12e6fc8]
/usr/lib/libgtk-x11-2.0.so.0 [0x12f991a]
/usr/lib/libgtk-x11-2.0.so.0 [0x11ee474]
/usr/lib/libgobject-2.0.so.0 [0x646b6f9]
/usr/lib/libgobject-2.

This all worked fine in Jaunty!

---

### Post by emarkay on 2009-10-26
Bug filed:
[https://bugs.launchpad.net/ubuntu/+source/avidemux/+bug/461350](https://bugs.launchpad.net/ubuntu/+source/avidemux/+bug/461350)

Fix apparently in SVN, I am unsure as to my abilities in ensuring uncorrupted compilation, asked for assistance here:
[http://avidemux.org/admForum/viewtopic.php?id=6807]("http://avidemux.org/admForum/profile.php?id=3449")

---

