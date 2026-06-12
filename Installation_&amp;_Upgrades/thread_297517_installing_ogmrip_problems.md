---
title: "installing ogmrip problems"
date: 2006-11-11
forum: Installation &amp; Upgrades
---

### Post by chris.olsen on 2006-11-11
when I try to install ogmrip I get errors when I try to make.  The errors all point to line like the following:

--------
#if MPLAYER_MAJOR > 0
  g_ptr_array_add (argv, g_strdup_printf ("dvd://%d", vid + 1));
#else /* MPLAYER_MAJOR */
  g_ptr_array_add (argv, g_strdup ("-dvd"));
  g_ptr_array_add (argv, g_strdup_printf ("%d", vid + 1));
#endif /* MPLAYER_MAJOR */
--------
with the the compiler error of:
ogmrip-backend.c:532:5: error: missing binary operator before token "2"

I am not a C programmer, but from refernce it looks ok, unless of course the MPLAYER_MAJOR is not initialized, which I can't find where it is set, but since it is global I don't even know where to start looking.

Thanks for any help

---

### Post by billl on 2006-11-13
Can you please try this patch [http://ogmrip.sourceforge.net/patches/ogmrip-0.10.0-mplayer-rc.patch](http://ogmrip.sourceforge.net/patches/ogmrip-0.10.0-mplayer-rc.patch)

Thanks,

Olivier

---

### Post by chris.olsen on 2006-11-14
Thanks for the reply, but..(dumass moment coming up)..what do I do with the patch code?

Thanks

---

### Post by billl on 2006-11-15
$ tar -xvzf /path/to/ogmrip-0.10.0.tar.gz
$ cd ogmrip-0.10.0
$ patch -p1 < /path/to/ogmrip-0.10.0-mplayer-rc.patch

Of course, this can only work when compiling OGMRip from sources. If you're trying to install OGMRip the debian/ubuntu source package, I don't know how this be done.

---

### Post by chris.olsen on 2006-11-18
I ran the patch, but am back to getting errors when running make
-----------
clude -I/usr/include/libxml2 -I../libogmjob -I../libogmdvd -DOGMRIP_DATA_DIR=\"/usr/local/share\" -I/usr/local/include -g -O2 -I/usr/local/include -I.. -Wall -Werror -MT ogmrip-backend.lo -MD -MP -MF .deps/ogmrip-backend.Tpo -c ogmrip-backend.c  -fPIC -DPIC -o .libs/ogmrip-backend.o
ogmrip-backend.c:59:34: error: missing binary operator before token "2"
ogmrip-backend.c:431:34: error: missing binary operator before token "2"
ogmrip-backend.c:461:34: error: missing binary operator before token "2"
...
...
...

---

### Post by billl on 2006-11-20
Can you please paste the result of mplayer without any option:

$ mplayer

Thanks,

Olivier

---

### Post by haui on 2006-11-25
The problem is that the mplayer mayor version number is not detected correctly be the configure scripts. 

You can fix this by opening the file 

   ./config.h

with an editor and replace the line that looks like

   #define MPLAYER_MAJOR MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8...

with 

   #define MPLAYER_MAJOR MPlayer 2

Best regards
Haui

---

### Post by haui on 2006-11-25
Sorry, use the replacement

#define MPLAYER_MAJOR 2

Haui

---

### Post by billl on 2006-11-27
This thread on OGMRip's forums already adresses this issue which is very ubuntu specific: [http://sourceforge.net/forum/forum.php?thread_id=1530591&forum_id=258033](http://sourceforge.net/forum/forum.php?thread_id=1530591&forum_id=258033)

However, if you're using the patch above, you should apply thoses changes in config.h:

- with mplayer-2:0.99+1.0pre7try2+cvs20060117-0ubuntu8
```
#define MPLAYER_MAJOR_VERSION 1
#define MPLAYER_MINOR_VERSION 0
#define MPLAYER_PRE_VERSION 8
#define MPLAYER_RC_VERSION 0
```
- with mplayer 1.0rc1:
```
#define MPLAYER_MAJOR_VERSION 1
#define MPLAYER_MINOR_VERSION 0
#define MPLAYER_PRE_VERSION 0
#define MPLAYER_RC_VERSION 1
```
- with svn versions of mplayer:
```
#define MPLAYER_MAJOR_VERSION 99
#define MPLAYER_MINOR_VERSION 99
#define MPLAYER_PRE_VERSION 99
#define MPLAYER_RC_VERSION 99
```

Anyway, there is a source package for Dapper Drake, just follow the guidelines on the homepage (thanks to Rob Neild): [http://ogmrip.sourceforge.net/index.html#download](http://ogmrip.sourceforge.net/index.html#download)

Cheers,

Olivier

---

### Post by aresius on 2007-03-01
When i visit the ogmrip website, there is no download for or notice about ubuntu. I found a deb package at [Chenjinfen]("http://chenjinfen.supersized.org/archives/9-OGMRIP-Ubuntu-Dapper-Package.html"), but the installation make an error alert. I asked him about this...

Do you know about available debian/ubuntu packages, binaries for ogmrip? :)

---

### Post by billl on 2007-03-01
Unfortunately, there are none yet.

---

### Post by ap9er on 2007-04-16
hey guys, just thought I'd let you know that I have ogmrip working in Fiesty Fawn, mplayer was installed via apt-get and ogmrip from the rpm listed on the ogmrip website (using alien to convert to .deb). Encoded a couple of movies thus far with no problems.

---

### Post by jamesford on 2007-05-06
getdeb.net has ogmrip debs now :D

---

