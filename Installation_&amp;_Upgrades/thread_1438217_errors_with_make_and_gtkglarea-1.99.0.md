---
title: "errors with make and gtkglarea-1.99.0"
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by Goblin82 on 2010-03-24
Hi I'm having trouble getting gtkglarea setup on my system, I was wondering if you could take a look at the output and tell me if I'm missing something.

```
Making all in gtkgl
make[1]: Entering directory `/home/goblin/gtkglarea-1.99.0/gtkgl'
source='gdkgl.c' object='gdkgl.lo' libtool=yes \
    depfile='.deps/gdkgl.Plo' tmpdepfile='.deps/gdkgl.TPlo' \
    depmode=gcc3 /bin/bash ../depcomp \
    /bin/bash ../libtool --mode=compile gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DSTDC_HEADERS=1  -I. -I. -I..      -c -o gdkgl.lo `test -f gdkgl.c || echo './'`gdkgl.c
rm -f .libs/gdkgl.lo
gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DSTDC_HEADERS=1 -I. -I. -I.. -c gdkgl.c -MT gdkgl.lo -MD -MP -MF .deps/gdkgl.TPlo  -fPIC -DPIC -o .libs/gdkgl.lo
In file included from gdkgl.c:20:
gdkgl.h:22:18: error: glib.h: No such file or directory
gdkgl.h:31:21: error: gdk/gdk.h: No such file or directory
In file included from gdkgl.c:20:
gdkgl.h:77: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'gdk_gl_query'
gdkgl.h:78: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
gdkgl.h:80: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
gdkgl.h:81: error: expected ')' before '*' token
gdkgl.h:83: error: expected ')' before '*' token
gdkgl.h:84: error: expected ')' before '*' token
gdkgl.h:85: error: expected declaration specifiers or '...' before 'gint'
gdkgl.h:90: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'gdk_gl_make_current'
gdkgl.h:91: error: expected ')' before '*' token
gdkgl.h:102: error: expected ')' before '*' token
gdkgl.h:106: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'gdk_gl_pixmap_make_current'
gdkgl.h:110: error: expected ')' before '*' token
gdkgl.c:22:22: error: gdk/gdkx.h: No such file or directory
gdkgl.c:30: error: expected ')' before '*' token
gdkgl.c:59: error: expected specifier-qualifier-list before 'guint'
gdkgl.c:65: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'gdk_gl_query'
gdkgl.c:71: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
gdkgl.c:82: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
gdkgl.c:100: error: expected ')' before '*' token
gdkgl.c:122: error: expected ')' before '*' token
gdkgl.c:128: error: expected ')' before '*' token
gdkgl.c:158: error: expected declaration specifiers or '...' before 'gint'
gdkgl.c: In function 'gdk_gl_context_attrlist_share_new':
gdkgl.c:160: error: 'GdkVisual' undeclared (first use in this function)
gdkgl.c:160: error: (Each undeclared identifier is reported only once
gdkgl.c:160: error: for each function it appears in.)
gdkgl.c:160: error: 'visual' undeclared (first use in this function)
gdkgl.c:162: error: 'direct' undeclared (first use in this function)
gdkgl.c:162: warning: return makes pointer from integer without a cast
gdkgl.c: In function 'gdk_gl_context_ref':
gdkgl.c:172: error: 'GdkGLContextPrivate' has no member named 'ref_count'
gdkgl.c: In function 'gdk_gl_context_unref':
gdkgl.c:183: error: 'GdkGLContextPrivate' has no member named 'ref_count'
gdkgl.c:185: error: 'GdkGLContextPrivate' has no member named 'ref_count'
gdkgl.c: At top level:
gdkgl.c:198: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'gdk_gl_make_current'
gdkgl.c:217: error: expected ')' before '*' token
gdkgl.c:240: error: expected specifier-qualifier-list before 'GdkPixmap'
gdkgl.c:247: error: expected ')' before '*' token
gdkgl.c: In function 'gdk_gl_pixmap_ref':
gdkgl.c:291: error: 'GdkGLPixmapPrivate' has no member named 'ref_count'
gdkgl.c: In function 'gdk_gl_pixmap_unref':
gdkgl.c:302: error: 'GdkGLPixmapPrivate' has no member named 'ref_count'
gdkgl.c:304: error: 'GdkGLPixmapPrivate' has no member named 'ref_count'
gdkgl.c:310: error: 'GdkGLPixmapPrivate' has no member named 'front_left'
gdkgl.c: At top level:
gdkgl.c:317: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'gdk_gl_pixmap_make_current'
gdkgl.c:334: error: expected ')' before '*' token
make[1]: *** [gdkgl.lo] Error 1
make[1]: Leaving directory `/home/goblin/gtkglarea-1.99.0/gtkgl'
make: *** [all-recursive] Error 1

```from what I could understand I would need glib and GDK+ but I have both, any ideas?

---

