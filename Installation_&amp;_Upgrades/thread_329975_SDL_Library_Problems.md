---
title: "SDL Library Problems"
date: 2007-01-02
forum: Installation &amp; Upgrades
---

### Post by Pobega on 2007-01-02
Well I'm trying to install the SDL_image library ([http://www.libsdl.org/projects/SDL_image/](http://www.libsdl.org/projects/SDL_image/)) and *./configure* went fine. Then I jumped into *make* and it spat out an error at me:

> pobega@ackbar:~/downloads/SDL_image-1.2.5$ make
/bin/bash ./libtool --tag=CC --mode=link gcc  -g -O2 -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT   -o libSDL_image.la -rpath /usr/local/lib -no-undefined -release 1.2 -version-info 1:4:1 IMG.lo IMG_bmp.lo IMG_gif.lo IMG_jpg.lo IMG_lbm.lo IMG_pcx.lo IMG_png.lo IMG_pnm.lo IMG_tga.lo IMG_tif.lo IMG_xcf.lo IMG_xpm.lo IMG_xv.lo -lpng -lz -ljpeg -ltiff -lz -L/usr/local/lib -Wl,-rpath,/usr/local/lib -lSDL -lpthread
gcc -shared  .libs/IMG.o .libs/IMG_bmp.o .libs/IMG_gif.o .libs/IMG_jpg.o .libs/IMG_lbm.o .libs/IMG_pcx.o .libs/IMG_png.o .libs/IMG_pnm.o .libs/IMG_tga.o .libs/IMG_tif.o .libs/IMG_xcf.o .libs/IMG_xpm.o .libs/IMG_xv.o  -Wl,--rpath -Wl,/usr/local/lib -Wl,--rpath -Wl,/usr/local/lib -lpng -ljpeg -ltiff -lz -L/usr/local/lib /usr/local/lib/libSDL.so -lpthread  -Wl,-rpath -Wl,/usr/local/lib -Wl,-soname -Wl,libSDL_image-1.2.so.0 -o .libs/libSDL_image-1.2.so.0.1.4
/usr/bin/ld: cannot find -ljpeg
collect2: ld returned 1 exit status
make: *** [libSDL_image.la] Error 1

I know it has *something* to do with the libjpeg library, but I have no clue exactly what.

**Edit:** For archival purposes, I forgot to install libjpeg-dev. I also needed to install libtiff-dev before it would run fully. Both available on aptitude.

---

### Post by Pobega on 2007-01-03
Well, I've moved on from this and got everything installed, and now I'm trying to install SDL_mixer. And for some reason it keeps telling me Ogg Vorbis libraries aren't installed.

> checking for Ogg Vorbis headers and libraries... no

I've tried:

*./configure --includedir=/usr/include/ogg*
*./configure --includedir=/usr/include/OggFLAC*

But neither work. I've also tried installing Ogg from [this site](http://www.linuxfromscratch.org/blfs/view/svn/multimedia/libogg.html) and running *./configure* and *./configure --includedir=/usr/include/ogg*, but all of them still give me the same "No" on Ogg Vorbis.

---

### Post by Pobega on 2007-01-04
Bump, I still need help here.

---

### Post by Pobega on 2007-01-05
Double bump?

If I can't install this from source, is there any way to get it (with Ogg support) through Aptitude or Synaptic? (From what I've tried those packages don't work too well)

---

### Post by Pobega on 2007-01-06
Okay, I got it working. I needed to install [Libogg](http://www.linuxfromscratch.org/blfs/view/svn/multimedia/libogg.html) and [Libvorbis](http://www.linuxfromscratch.org/blfs/view/cvs/multimedia/libvorbis.html) from source.

---

### Post by po0f on 2007-01-06
Pobega,

You probably could have installed [libvorbis-dev](http://packages.ubuntu.com/edgy/libdevel/libvorbis-dev) and [libogg-dev](http://packages.ubuntu.com/edgy/libdevel/libogg-dev) from the repos.  You probably already had the libraries installed, you were just missing the header files.

How and where did you install your custom compiled libvorbis and libogg?  You might run into problems upgrading/updating your system if you put them in the wrong spot.

---

### Post by Pobega on 2007-01-07
> **po0f said:**
> Pobega,

You probably could have installed [libvorbis-dev](http://packages.ubuntu.com/edgy/libdevel/libvorbis-dev) and [libogg-dev](http://packages.ubuntu.com/edgy/libdevel/libogg-dev) from the repos.  You probably already had the libraries installed, you were just missing the header files.

How and where did you install your custom compiled libvorbis and libogg?  You might run into problems upgrading/updating your system if you put them in the wrong spot.

libogg-dev nd libvorbis-dev didn't solve any of my problems, I installed everything libogg* and libvorbis* and that didn't work either. 

I linked to where I got the libvorbis and libogg from, and I installed them using ./configure/make/make install.

---

