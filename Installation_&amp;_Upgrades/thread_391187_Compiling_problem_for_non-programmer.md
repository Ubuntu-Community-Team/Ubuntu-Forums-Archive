---
title: "Compiling problem for non-programmer"
date: 2007-03-22
forum: Installation &amp; Upgrades
---

### Post by Timokl on 2007-03-22
Hi everybody,

I have problems compiling a programme on my linux box. I guess, the general setup (gcc, makeinstall, ...) should be ok, as I managed to compile other programs before. I am not a programmer, so if  "make" gives me an error message, I have no idea how to proceed. :confused: 

The program I want to use on my computer is [Pfstools]("http://www.mpi-inf.mpg.de/resources/pfstools/") - program to combine a set of images with different exposures into a hdr image, see [http://en.wikipedia.org/wiki/High_dynamic_range_imaging]("http://en.wikipedia.org/wiki/High_dynamic_range_imaging") on what this might be. 

After I compile the single programs from the pftstools set, I can start them, but they don't complete their task. Once, I had the error message that the program cannot find a shared object from another programm that is included in this set. 

During the compilation process, I was told that 

```
libtool: install: warning: `../pfs/libpfs-1.2.la' has not been installed in `/home/timo/local/lib'
```

Synaptic does not find this file in a repository, Google gives me a lot of (for me) confusing information so that I don't know where to start.

What's missing on my machine to install the pfstools?

Any help is appreciated!

Here is a list log of my installation process:

```
**timo@aristoteles:~/Desktop/pfstools-1.6$ ./configure**
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for ranlib... ranlib
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... (cached) ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking for ppm_init in -lnetppm... no
checking for pbm_init in -lnetpbm... no
checking for ppm_init in -lppm... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for IMAGEMAGICK_CFLAGS... 
checking for IMAGEMAGICK_LIBS... 
checking for TIFFOpen in -ltiff... no
checking for jpeghdr_CreateDecompress in -ljpeghdr... no
dirname: missing operand
Try `dirname --help' for more information.
checking for OPENEXR_CFLAGS... 
checking for OPENEXR_LIBS... 
configure: WARNING: Package OpenEXR was not found in the pkg-config search path.
Perhaps you should add the directory containing `OpenEXR.pc'
to the PKG_CONFIG_PATH environment variable
No package 'OpenEXR' found 
no
checking for QT_CFLAGS... 
checking for QT_LIBS... 
configure: WARNING: Package qt-mt was not found in the pkg-config search path.
Perhaps you should add the directory containing `qt-mt.pc'
to the PKG_CONFIG_PATH environment variable
No package 'qt-mt' found 
checking for moc... no
configure: WARNING: no QT meta object compiler (moc) found in the path
checking for glDisable in -lGL... no
configure: WARNING: OpenGL test failed. pfsglview will not be compiled 
checking for mex... no
configure: WARNING: no matlab mex found in the path
./configure: line 20581: octave-config: command not found
./configure: line 20583: octave-config: command not found
configure: WARNING: no path for .oct files specified
configure: WARNING: no path for .m files specified
checking for mkoctfile... no
configure: WARNING: no mkoctfile found in the path
configure: WARNING: Octave support disabled
checking for pdflatex... no
configure: WARNING: pdflatex not found in the path
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/pfs/Makefile
config.status: creating src/pfs/pfs.pc
config.status: creating src/fileformat/Makefile
config.status: creating src/filter/Makefile
config.status: creating src/octave/Makefile
config.status: creating src/pfsview/Makefile
config.status: creating src/pfsglview/Makefile
config.status: creating src/matlab/Makefile
config.status: creating doc/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

pfstools is now configured for i686-pc-linux-gnu

  Source directory:     .
  Installation prefix:  /usr/local
  C++ compiler:         g++   -O2  

  Octave                no
    octave-m-dir:       
    octave-oct-dir:     
    mkoctfile:          

  Matlab                no
    matlab-dir:         /usr/local/share/pfstools/matlab
    mex:                

  PPM                   no
    LIBS:               
  TIFF                  no
    LIBS:               
  OpenEXR               no
    CFLAGS:             -I
    LIBS:               -lImath -lIlmImf -lHalf -lIex -lz
  ImageMagick++         no
    CFLAGS:             
    LIBS:               
  JPEG-HDR              no
    LIBS:               

  QT                    no
    QTDIR:              
    CFLAGS:             
    LIBS:               
    MOC:                

  OpenGL                no
    CFLAGS:             
    LIBS:               

  Debug mode            no




* To enable QT support, try specifying either --with-qtdir, or a triple --with-qtinclude, --with-qtlibs, --with-moc.

**timo@aristoteles:~/Desktop/pfstools-1.6$ make**
make  all-recursive
make[1]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6'
Making all in src
make[2]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src'
Making all in pfs
make[3]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfs'
make[3]: Für das Ziel »all« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfs'
Making all in fileformat
make[3]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/fileformat'
make[3]: Für das Ziel »all« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/fileformat'
Making all in filter
make[3]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/filter'
make[3]: Für das Ziel »all« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/filter'
make[3]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src'
make[3]: Für das Ziel »all-am« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src'
make[2]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src'
make[2]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6'
make[2]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6'
make[1]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6'

**timo@aristoteles:~/Desktop/pfstools-1.6$ sudo make install**
Password:
Making install in src
make[1]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src'
Making install in pfs
make[2]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfs'
make[3]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfs'
/bin/bash ../../mkinstalldirs /usr/local/lib
 /bin/bash ../../libtool --mode=install /usr/bin/install -c  libpfs-1.2.la /usr/local/lib/libpfs-1.2.la
/usr/bin/install -c .libs/libpfs-1.2.so.0.0.0 /usr/local/lib/libpfs-1.2.so.0.0.0
(cd /usr/local/lib && rm -f libpfs-1.2.so.0 && ln -s libpfs-1.2.so.0.0.0 libpfs-1.2.so.0)
(cd /usr/local/lib && rm -f libpfs-1.2.so && ln -s libpfs-1.2.so.0.0.0 libpfs-1.2.so)
/usr/bin/install -c .libs/libpfs-1.2.lai /usr/local/lib/libpfs-1.2.la
/usr/bin/install -c .libs/libpfs-1.2.a /usr/local/lib/libpfs-1.2.a
ranlib /usr/local/lib/libpfs-1.2.a
chmod 644 /usr/local/lib/libpfs-1.2.a
libtool: install: warning: remember to run `libtool --finish /home/timo/local/lib'
/bin/bash ../../mkinstalldirs /usr/local/include/pfs-1.2
 /usr/bin/install -c -m 644 pfs.h /usr/local/include/pfs-1.2/pfs.h
 /usr/bin/install -c -m 644 array2d.h /usr/local/include/pfs-1.2/array2d.h
/bin/bash ../../mkinstalldirs /usr/local/lib/pkgconfig
 /usr/bin/install -c -m 644 pfs.pc /usr/local/lib/pkgconfig/pfs.pc
make[3]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfs'
make[2]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfs'
Making install in fileformat
make[2]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/fileformat'
make[3]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/fileformat'
/bin/bash ../../mkinstalldirs /usr/local/bin
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfsinrgbe /usr/local/bin/pfsinrgbe
libtool: install: warning: `../pfs/libpfs-1.2.la' has not been installed in `/home/timo/local/lib'
/usr/bin/install -c .libs/pfsinrgbe /usr/local/bin/pfsinrgbe
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfsoutrgbe /usr/local/bin/pfsoutrgbe
libtool: install: warning: `../pfs/libpfs-1.2.la' has not been installed in `/home/timo/local/lib'
/usr/bin/install -c .libs/pfsoutrgbe /usr/local/bin/pfsoutrgbe
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfsinpfm /usr/local/bin/pfsinpfm
libtool: install: warning: `../pfs/libpfs-1.2.la' has not been installed in `/home/timo/local/lib'
/usr/bin/install -c .libs/pfsinpfm /usr/local/bin/pfsinpfm
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfsoutpfm /usr/local/bin/pfsoutpfm
libtool: install: warning: `../pfs/libpfs-1.2.la' has not been installed in `/home/timo/local/lib'
/usr/bin/install -c .libs/pfsoutpfm /usr/local/bin/pfsoutpfm
/bin/bash ../../mkinstalldirs /usr/local/bin
 /usr/bin/install -c pfsin /usr/local/bin/pfsin
 /usr/bin/install -c pfsout /usr/local/bin/pfsout
 /usr/bin/install -c pfsoutffmpeg /usr/local/bin/pfsoutffmpeg
 /usr/bin/install -c pfsinmulti /usr/local/bin/pfsinmulti
 /usr/bin/install -c pfsindcraw /usr/local/bin/pfsindcraw
/bin/bash ../../mkinstalldirs /usr/local/man/man1
 /usr/bin/install -c -m 644 ./pfsin.1 /usr/local/man/man1/pfsin.1
 /usr/bin/install -c -m 644 ./pfsout.1 /usr/local/man/man1/pfsout.1
 /usr/bin/install -c -m 644 ./pfsinppm.1 /usr/local/man/man1/pfsinppm.1
 /usr/bin/install -c -m 644 ./pfsinexr.1 /usr/local/man/man1/pfsinexr.1
 /usr/bin/install -c -m 644 ./pfsinrgbe.1 /usr/local/man/man1/pfsinrgbe.1
 /usr/bin/install -c -m 644 ./pfsintiff.1 /usr/local/man/man1/pfsintiff.1
 /usr/bin/install -c -m 644 ./pfsoutppm.1 /usr/local/man/man1/pfsoutppm.1
 /usr/bin/install -c -m 644 ./pfsoutexr.1 /usr/local/man/man1/pfsoutexr.1
 /usr/bin/install -c -m 644 ./pfsoutffmpeg.1 /usr/local/man/man1/pfsoutffmpeg.1
 /usr/bin/install -c -m 644 ./pfsinpfm.1 /usr/local/man/man1/pfsinpfm.1
 /usr/bin/install -c -m 644 ./pfsoutpfm.1 /usr/local/man/man1/pfsoutpfm.1
 /usr/bin/install -c -m 644 ./pfsinmulti.1 /usr/local/man/man1/pfsinmulti.1
 /usr/bin/install -c -m 644 ./pfsinimgmagick.1 /usr/local/man/man1/pfsinimgmagick.1
 /usr/bin/install -c -m 644 ./pfsoutimgmagick.1 /usr/local/man/man1/pfsoutimgmagick.1
 /usr/bin/install -c -m 644 ./pfsinjpeghdr.1 /usr/local/man/man1/pfsinjpeghdr.1
 /usr/bin/install -c -m 644 ./pfsoutjpeghdr.1 /usr/local/man/man1/pfsoutjpeghdr.1
 /usr/bin/install -c -m 644 ./pfsindcraw.1 /usr/local/man/man1/pfsindcraw.1
make  install-data-hook
make[4]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/fileformat'
cd /usr/local/man/man1; \
        ln -f -s pfsoutppm.1 pfsouttiff.1; \
        ln -f -s pfsoutppm.1 pfsoutrgbe.1;
make[4]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/fileformat'
make[3]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/fileformat'
make[2]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/fileformat'
Making install in filter
make[2]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/filter'
make[3]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/filter'
/bin/bash ../../mkinstalldirs /usr/local/bin
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfsclamp /usr/local/bin/pfsclamp
**libtool: install: warning: `../pfs/libpfs-1.2.la' has not been installed in `/home/timo/local/lib'**
/usr/bin/install -c .libs/pfsclamp /usr/local/bin/pfsclamp
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfsgamma /usr/local/bin/pfsgamma
**libtool: install: warning: `../pfs/libpfs-1.2.la' has not been installed in `/home/timo/local/lib'**
/usr/bin/install -c .libs/pfsgamma /usr/local/bin/pfsgamma
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfstag /usr/local/bin/pfstag
**libtool: install: warning: `../pfs/libpfs-1.2.la' has not been installed in `/home/timo/local/lib'**
/usr/bin/install -c .libs/pfstag /usr/local/bin/pfstag
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfssize /usr/local/bin/pfssize
**libtool: install: warning: `../pfs/libpfs-1.2.la' has not been installed in `/home/timo/local/lib'**
/usr/bin/install -c .libs/pfssize /usr/local/bin/pfssize
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfsextractchannels /usr/local/bin/pfsextractchannels[B]
libtool: install: warning: `../pfs/libpfs-1.2.la' has not been installed in `/home/timo/local/lib'[/B]
/usr/bin/install -c .libs/pfsextractchannels /usr/local/bin/pfsextractchannels
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfspanoramic /usr/local/bin/pfspanoramic
**libtool: install: warning: `../pfs/libpfs-1.2.la' has not been installed in `/home/timo/local/lib'**
/usr/bin/install -c .libs/pfspanoramic /usr/local/bin/pfspanoramic
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfsrotate /usr/local/bin/pfsrotate
libtool: install: warning: `../pfs/libpfs-1.2.la' has not been installed in `/home/timo/local/lib'
/usr/bin/install -c .libs/pfsrotate /usr/local/bin/pfsrotate
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfsflip /usr/local/bin/pfsflip
libtool: install: warning: `../pfs/libpfs-1.2.la' has not been installed in `/home/timo/local/lib'
/usr/bin/install -c .libs/pfsflip /usr/local/bin/pfsflip
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfscut /usr/local/bin/pfscut
libtool: install: warning: `../pfs/libpfs-1.2.la' has not been installed in `/home/timo/local/lib'
/usr/bin/install -c .libs/pfscut /usr/local/bin/pfscut
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfspad /usr/local/bin/pfspad
libtool: install: warning: `../pfs/libpfs-1.2.la' has not been installed in `/home/timo/local/lib'
/usr/bin/install -c .libs/pfspad /usr/local/bin/pfspad
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfscat /usr/local/bin/pfscat
libtool: install: warning: `../pfs/libpfs-1.2.la' has not been installed in `/home/timo/local/lib'
/usr/bin/install -c .libs/pfscat /usr/local/bin/pfscat
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfsabsolute /usr/local/bin/pfsabsolute
libtool: install: warning: `../pfs/libpfs-1.2.la' has not been installed in `/home/timo/local/lib'
/usr/bin/install -c .libs/pfsabsolute /usr/local/bin/pfsabsolute
/bin/bash ../../mkinstalldirs /usr/local/man/man1
 /usr/bin/install -c -m 644 ./pfsgamma.1 /usr/local/man/man1/pfsgamma.1
 /usr/bin/install -c -m 644 ./pfsclamp.1 /usr/local/man/man1/pfsclamp.1
 /usr/bin/install -c -m 644 ./pfstag.1 /usr/local/man/man1/pfstag.1
 /usr/bin/install -c -m 644 ./pfssize.1 /usr/local/man/man1/pfssize.1
 /usr/bin/install -c -m 644 ./pfsextractchannels.1 /usr/local/man/man1/pfsextractchannels.1
 /usr/bin/install -c -m 644 ./pfspanoramic.1 /usr/local/man/man1/pfspanoramic.1
 /usr/bin/install -c -m 644 ./pfsrotate.1 /usr/local/man/man1/pfsrotate.1
 /usr/bin/install -c -m 644 ./pfsflip.1 /usr/local/man/man1/pfsflip.1
 /usr/bin/install -c -m 644 ./pfscut.1 /usr/local/man/man1/pfscut.1
 /usr/bin/install -c -m 644 ./pfspad.1 /usr/local/man/man1/pfspad.1
 /usr/bin/install -c -m 644 ./pfscat.1 /usr/local/man/man1/pfscat.1
 /usr/bin/install -c -m 644 ./pfsabsolute.1 /usr/local/man/man1/pfsabsolute.1
make[3]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/filter'
make[2]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/filter'
make[2]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src'
make[3]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src'
make[3]: Für das Ziel »install-exec-am« ist nichts zu tun.
make[3]: Für das Ziel »install-data-am« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src'
make[2]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src'
make[1]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src'
make[1]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6'
make[2]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6'
make[2]: Für das Ziel »install-exec-am« ist nichts zu tun.
make[2]: Für das Ziel »install-data-am« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6'
make[1]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6'
```

Thnx, Timo

---

### Post by Arby on 2007-03-23
Based on that output you are missing some library files. Here's how I found that out so you can figure it out yourself the next time. The key part is these few lines, especially the bits in bold ```
configure: **WARNING: Package OpenEXR was not found in the pkg-config search path.**
Perhaps you should add the directory containing `OpenEXR.pc'
to the PKG_CONFIG_PATH environment variable
No package 'OpenEXR' found 
no
checking for QT_CFLAGS... 
checking for QT_LIBS... 
configure: **WARNING: Package qt-mt was not found in the pkg-config search path.**
Perhaps you should add the directory containing `qt-mt.pc'
to the PKG_CONFIG_PATH environment variable
No package 'qt-mt' found 
checking for moc... no
configure: WARNING: no QT meta object compiler (moc) found in the path
checking for glDisable in -lGL... no
configure: WARNING: OpenGL test failed. pfsglview will not be compiled 
checking for mex... no
``` The bold lines tell you that you're missing the packages OpenEXR and qt-mt. So I ran the following two commands to find out which packages provide those functions. Box below shows the output ```
sudo apt-cache search OpenEXR
Password:
libopenexr-dev - development files for the OpenEXR image library
libopenexr2c2a - runtime files for the OpenEXR image library
cinepaint - motion picture image painting and retouching tool
exrtools - A collection of utilities for manipulating OpenEXR images
openexr - viewer and docs for the OpenEXR image format
richard@shiny:~$ sudo apt-cache search qt-mt
libqt3-headers - Qt3 header files
libqt3-mt - Qt GUI Library (Threaded runtime version), Version 3
libqt3-mt-dev - Qt development files (Threaded)

``` apt-cache search looks through the Ubuntu repositories for packages that match the name given. So you need to install some of those packages. Since you're compiling code you probably want the -dev versions as well as the runtime stuff. try this ```
sudo apt-get install libopenexr-dev openexr libqt3-mt libqt3-mt-dev
``` that may pull in some of the other packages as well as dependencies, I don't know. Then run ```
./configure
make
make install
``` again. Check the output of make carefully for anymore warnings. That should get you up and running.

The output you gave also complains about lacking some support for matlab and octave. You should be able to fix these by the same process outlined above. It just depends whether you actually want matlab/octave support or not. If you don't then you can ignore those. If you think you might ever need it then it's probably easier to do it now than forget later. 

This post is already too long. I hope that helps, if you have more trouble just ask.

Arby

---

### Post by Timokl on 2007-03-23
Hi Arby,

first of all thanks a lot for helping me out, and for showing me apt-cache.

Sadly, the compiling did not went through smoothly. I apt-get'ed the recommonded packages as well as the package octave2.9 (apt-cache did not find a candidate for matlab). Then I did ./configure and make - this resulted in an error 1 and an error 2. I have included the complete log. I bolded :) the error messages.

```
timo@aristoteles:~/Desktop/pfstools-1.6$ make
make  all-recursive
make[1]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6'
Making all in src
make[2]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src'
Making all in pfs
make[3]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfs'
if g++ -DHAVE_CONFIG_H -I. -I. -I../..     -fPIC -O2   -MT libpfs_a-pfs.o -MD -MP -MF ".deps/libpfs_a-pfs.Tpo" \
          -c -o libpfs_a-pfs.o `test -f 'pfs.cpp' || echo './'`pfs.cpp; \
        then mv -f ".deps/libpfs_a-pfs.Tpo" ".deps/libpfs_a-pfs.Po"; \
        else rm -f ".deps/libpfs_a-pfs.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../..     -fPIC -O2   -MT libpfs_a-pfsutils.o -MD -MP -MF ".deps/libpfs_a-pfsutils.Tpo" \
          -c -o libpfs_a-pfsutils.o `test -f 'pfsutils.cpp' || echo './'`pfsutils.cpp; \
        then mv -f ".deps/libpfs_a-pfsutils.Tpo" ".deps/libpfs_a-pfsutils.Po"; \
        else rm -f ".deps/libpfs_a-pfsutils.Tpo"; exit 1; \
        fi
rm -f libpfs.a
ar cru libpfs.a libpfs_a-pfs.o libpfs_a-pfsutils.o libpfs_a-colorspace.o 
ranlib libpfs.a
if /bin/bash ../../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../..     -O2   -MT pfs.lo -MD -MP -MF ".deps/pfs.Tpo" \
          -c -o pfs.lo `test -f 'pfs.cpp' || echo './'`pfs.cpp; \
        then mv -f ".deps/pfs.Tpo" ".deps/pfs.Plo"; \
        else rm -f ".deps/pfs.Tpo"; exit 1; \
        fi
 g++ -DHAVE_CONFIG_H -I. -I. -I../.. -O2 -MT pfs.lo -MD -MP -MF .deps/pfs.Tpo -c pfs.cpp  -fPIC -DPIC -o .libs/pfs.o
 g++ -DHAVE_CONFIG_H -I. -I. -I../.. -O2 -MT pfs.lo -MD -MP -MF .deps/pfs.Tpo -c pfs.cpp -o pfs.o >/dev/null 2>&1
if /bin/bash ../../libtool --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../..     -O2   -MT pfsutils.lo -MD -MP -MF ".deps/pfsutils.Tpo" \
          -c -o pfsutils.lo `test -f 'pfsutils.cpp' || echo './'`pfsutils.cpp; \
        then mv -f ".deps/pfsutils.Tpo" ".deps/pfsutils.Plo"; \
        else rm -f ".deps/pfsutils.Tpo"; exit 1; \
        fi
 g++ -DHAVE_CONFIG_H -I. -I. -I../.. -O2 -MT pfsutils.lo -MD -MP -MF .deps/pfsutils.Tpo -c pfsutils.cpp  -fPIC -DPIC -o .libs/pfsutils.o
 g++ -DHAVE_CONFIG_H -I. -I. -I../.. -O2 -MT pfsutils.lo -MD -MP -MF .deps/pfsutils.Tpo -c pfsutils.cpp -o pfsutils.o >/dev/null 2>&1
/bin/bash ../../libtool --mode=link g++  -O2     -o libpfs-1.2.la -rpath /usr/local/lib  pfs.lo pfsutils.lo colorspace.lo  
rm -fr  .libs/libpfs-1.2.a .libs/libpfs-1.2.la .libs/libpfs-1.2.lai .libs/libpfs-1.2.so .libs/libpfs-1.2.so.0 .libs/libpfs-1.2.so.0.0.0
g++ -shared -nostdlib /usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/crti.o /usr/lib/gcc/i486-linux-gnu/4.1.2/crtbeginS.o  .libs/pfs.o .libs/pfsutils.o .libs/colorspace.o  -L/usr/lib/gcc/i486-linux-gnu/4.1.2 -L/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib -L/lib/../lib -L/usr/lib/../lib -lstdc++ -lm -lc -lgcc_s /usr/lib/gcc/i486-linux-gnu/4.1.2/crtendS.o /usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/crtn.o  -Wl,-soname -Wl,libpfs-1.2.so.0 -o .libs/libpfs-1.2.so.0.0.0
(cd .libs && rm -f libpfs-1.2.so.0 && ln -s libpfs-1.2.so.0.0.0 libpfs-1.2.so.0)
(cd .libs && rm -f libpfs-1.2.so && ln -s libpfs-1.2.so.0.0.0 libpfs-1.2.so)
ar cru .libs/libpfs-1.2.a  pfs.o pfsutils.o colorspace.o
ranlib .libs/libpfs-1.2.a
creating libpfs-1.2.la
(cd .libs && rm -f libpfs-1.2.la && ln -s ../libpfs-1.2.la libpfs-1.2.la)
make[3]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfs'
Making all in fileformat
make[3]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/fileformat'
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I./../pfs -I/usr/include/OpenEXR       -O2   -MT pfsinrgbe.o -MD -MP -MF ".deps/pfsinrgbe.Tpo" \
          -c -o pfsinrgbe.o `test -f 'pfsinrgbe.cpp' || echo './'`pfsinrgbe.cpp; \
        then mv -f ".deps/pfsinrgbe.Tpo" ".deps/pfsinrgbe.Po"; \
        else rm -f ".deps/pfsinrgbe.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I./../pfs -I/usr/include/OpenEXR       -O2   -MT rgbeio.o -MD -MP -MF ".deps/rgbeio.Tpo" \
          -c -o rgbeio.o `test -f 'rgbeio.cpp' || echo './'`rgbeio.cpp; \
        then mv -f ".deps/rgbeio.Tpo" ".deps/rgbeio.Po"; \
        else rm -f ".deps/rgbeio.Tpo"; exit 1; \
        fi
/bin/bash ../../libtool --mode=link g++  -O2     -o pfsinrgbe  pfsinrgbe.o rgbeio.o  ../pfs/libpfs-1.2.la
g++ -O2 -o .libs/pfsinrgbe pfsinrgbe.o rgbeio.o  ../pfs/.libs/libpfs-1.2.so -Wl,--rpath -Wl,/usr/local/lib
creating pfsinrgbe
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I./../pfs -I/usr/include/OpenEXR       -O2   -MT pfsoutrgbe.o -MD -MP -MF ".deps/pfsoutrgbe.Tpo" \
          -c -o pfsoutrgbe.o `test -f 'pfsoutrgbe.cpp' || echo './'`pfsoutrgbe.cpp; \
        then mv -f ".deps/pfsoutrgbe.Tpo" ".deps/pfsoutrgbe.Po"; \
        else rm -f ".deps/pfsoutrgbe.Tpo"; exit 1; \
        fi
/bin/bash ../../libtool --mode=link g++  -O2     -o pfsoutrgbe  pfsoutrgbe.o rgbeio.o  ../pfs/libpfs-1.2.la
g++ -O2 -o .libs/pfsoutrgbe pfsoutrgbe.o rgbeio.o  ../pfs/.libs/libpfs-1.2.so -Wl,--rpath -Wl,/usr/local/lib
creating pfsoutrgbe
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I./../pfs -I/usr/include/OpenEXR       -O2   -MT pfsinpfm.o -MD -MP -MF ".deps/pfsinpfm.Tpo" \
          -c -o pfsinpfm.o `test -f 'pfsinpfm.cpp' || echo './'`pfsinpfm.cpp; \
        then mv -f ".deps/pfsinpfm.Tpo" ".deps/pfsinpfm.Po"; \
        else rm -f ".deps/pfsinpfm.Tpo"; exit 1; \
        fi
/bin/bash ../../libtool --mode=link g++  -O2     -o pfsinpfm  pfsinpfm.o  ../pfs/libpfs-1.2.la
g++ -O2 -o .libs/pfsinpfm pfsinpfm.o  ../pfs/.libs/libpfs-1.2.so -Wl,--rpath -Wl,/usr/local/lib
creating pfsinpfm
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I./../pfs -I/usr/include/OpenEXR       -O2   -MT pfsoutpfm.o -MD -MP -MF ".deps/pfsoutpfm.Tpo" \
          -c -o pfsoutpfm.o `test -f 'pfsoutpfm.cpp' || echo './'`pfsoutpfm.cpp; \
        then mv -f ".deps/pfsoutpfm.Tpo" ".deps/pfsoutpfm.Po"; \
        else rm -f ".deps/pfsoutpfm.Tpo"; exit 1; \
        fi
/bin/bash ../../libtool --mode=link g++  -O2     -o pfsoutpfm  pfsoutpfm.o  ../pfs/libpfs-1.2.la
g++ -O2 -o .libs/pfsoutpfm pfsoutpfm.o  ../pfs/.libs/libpfs-1.2.so -Wl,--rpath -Wl,/usr/local/lib
creating pfsoutpfm
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I./../pfs -I/usr/include/OpenEXR       -O2   -MT pfsinexr.o -MD -MP -MF ".deps/pfsinexr.Tpo" \
          -c -o pfsinexr.o `test -f 'pfsinexr.cpp' || echo './'`pfsinexr.cpp; \
        then mv -f ".deps/pfsinexr.Tpo" ".deps/pfsinexr.Po"; \
        else rm -f ".deps/pfsinexr.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I./../pfs -I/usr/include/OpenEXR       -O2   -MT exrio.o -MD -MP -MF ".deps/exrio.Tpo" \
          -c -o exrio.o `test -f 'exrio.cpp' || echo './'`exrio.cpp; \
        then mv -f ".deps/exrio.Tpo" ".deps/exrio.Po"; \
        else rm -f ".deps/exrio.Tpo"; exit 1; \
        fi
/bin/bash ../../libtool --mode=link g++  -O2     -o pfsinexr  pfsinexr.o exrio.o -lIlmImf -lImath -lHalf -lIex -lz   ../pfs/libpfs-1.2.la
g++ -O2 -o .libs/pfsinexr pfsinexr.o exrio.o  /usr/lib/libIlmImf.so /usr/lib/libImath.so /usr/lib/libHalf.so /usr/lib/libIex.so ../pfs/.libs/libpfs-1.2.so -lz -Wl,--rpath -Wl,/usr/local/lib
creating pfsinexr
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I./../pfs -I/usr/include/OpenEXR       -O2   -MT pfsoutexr.o -MD -MP -MF ".deps/pfsoutexr.Tpo" \
          -c -o pfsoutexr.o `test -f 'pfsoutexr.cpp' || echo './'`pfsoutexr.cpp; \
        then mv -f ".deps/pfsoutexr.Tpo" ".deps/pfsoutexr.Po"; \
        else rm -f ".deps/pfsoutexr.Tpo"; exit 1; \
        fi
/bin/bash ../../libtool --mode=link g++  -O2     -o pfsoutexr  pfsoutexr.o exrio.o -lIlmImf -lImath -lHalf -lIex -lz   ../pfs/libpfs-1.2.la
g++ -O2 -o .libs/pfsoutexr pfsoutexr.o exrio.o  /usr/lib/libIlmImf.so /usr/lib/libImath.so /usr/lib/libHalf.so /usr/lib/libIex.so ../pfs/.libs/libpfs-1.2.so -lz -Wl,--rpath -Wl,/usr/local/lib
creating pfsoutexr
make[3]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/fileformat'
Making all in filter
make[3]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/filter'
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I./../pfs    -O2   -MT pfsgamma.o -MD -MP -MF ".deps/pfsgamma.Tpo" \
          -c -o pfsgamma.o `test -f 'pfsgamma.cpp' || echo './'`pfsgamma.cpp; \
        then mv -f ".deps/pfsgamma.Tpo" ".deps/pfsgamma.Po"; \
        else rm -f ".deps/pfsgamma.Tpo"; exit 1; \
        fi
/bin/bash ../../libtool --mode=link g++  -O2     -o pfsgamma  pfsgamma.o  ../pfs/libpfs-1.2.la
g++ -O2 -o .libs/pfsgamma pfsgamma.o  ../pfs/.libs/libpfs-1.2.so -Wl,--rpath -Wl,/usr/local/lib
creating pfsgamma
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I./../pfs    -O2   -MT pfssize.o -MD -MP -MF ".deps/pfssize.Tpo" \
          -c -o pfssize.o `test -f 'pfssize.cpp' || echo './'`pfssize.cpp; \
        then mv -f ".deps/pfssize.Tpo" ".deps/pfssize.Po"; \
        else rm -f ".deps/pfssize.Tpo"; exit 1; \
        fi
/bin/bash ../../libtool --mode=link g++  -O2     -o pfssize  pfssize.o  ../pfs/libpfs-1.2.la
g++ -O2 -o .libs/pfssize pfssize.o  ../pfs/.libs/libpfs-1.2.so -Wl,--rpath -Wl,/usr/local/lib
creating pfssize
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I./../pfs    -O2   -MT pfsabsolute.o -MD -MP -MF ".deps/pfsabsolute.Tpo" \
          -c -o pfsabsolute.o `test -f 'pfsabsolute.cpp' || echo './'`pfsabsolute.cpp; \
        then mv -f ".deps/pfsabsolute.Tpo" ".deps/pfsabsolute.Po"; \
        else rm -f ".deps/pfsabsolute.Tpo"; exit 1; \
        fi
/bin/bash ../../libtool --mode=link g++  -O2     -o pfsabsolute  pfsabsolute.o  ../pfs/libpfs-1.2.la
g++ -O2 -o .libs/pfsabsolute pfsabsolute.o  ../pfs/.libs/libpfs-1.2.so -Wl,--rpath -Wl,/usr/local/lib
creating pfsabsolute
make[3]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/filter'
Making all in pfsview
make[3]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfsview'
/usr/bin/moc -o main.moc.cpp main.h
/usr/bin/moc -o pfsview_widget.moc.cpp pfsview_widget.h
/usr/bin/moc -o luminancerange_widget.moc.cpp luminancerange_widget.h
make  all-am
make[4]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfsview'
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -DQT_SHARED -DQT_TABLET_SUPPORT -DQT_THREAD_SUPPORT -D_REENTRANT -I/usr/include/qt3   -I../../src/pfs/    -O2   -MT main.o -MD -MP -MF ".deps/main.Tpo" \
          -c -o main.o `test -f 'main.cpp' || echo './'`main.cpp; \
        then mv -f ".deps/main.Tpo" ".deps/main.Po"; \
        else rm -f ".deps/main.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -DQT_SHARED -DQT_TABLET_SUPPORT -DQT_THREAD_SUPPORT -D_REENTRANT -I/usr/include/qt3   -I../../src/pfs/    -O2   -MT pfsview_widget.o -MD -MP -MF ".deps/pfsview_widget.Tpo" \
          -c -o pfsview_widget.o `test -f 'pfsview_widget.cpp' || echo './'`pfsview_widget.cpp; \
        then mv -f ".deps/pfsview_widget.Tpo" ".deps/pfsview_widget.Po"; \
        else rm -f ".deps/pfsview_widget.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -DQT_SHARED -DQT_TABLET_SUPPORT -DQT_THREAD_SUPPORT -D_REENTRANT -I/usr/include/qt3   -I../../src/pfs/    -O2   -MT luminancerange_widget.o -MD -MP -MF ".deps/luminancerange_widget.Tpo" \
          -c -o luminancerange_widget.o `test -f 'luminancerange_widget.cpp' || echo './'`luminancerange_widget.cpp; \
        then mv -f ".deps/luminancerange_widget.Tpo" ".deps/luminancerange_widget.Po"; \
        else rm -f ".deps/luminancerange_widget.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -DQT_SHARED -DQT_TABLET_SUPPORT -DQT_THREAD_SUPPORT -D_REENTRANT -I/usr/include/qt3   -I../../src/pfs/    -O2   -MT histogram.o -MD -MP -MF ".deps/histogram.Tpo" \
          -c -o histogram.o `test -f 'histogram.cpp' || echo './'`histogram.cpp; \
        then mv -f ".deps/histogram.Tpo" ".deps/histogram.Po"; \
        else rm -f ".deps/histogram.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -DQT_SHARED -DQT_TABLET_SUPPORT -DQT_THREAD_SUPPORT -D_REENTRANT -I/usr/include/qt3   -I../../src/pfs/    -O2   -MT main.moc.o -MD -MP -MF ".deps/main.moc.Tpo" \
          -c -o main.moc.o `test -f 'main.moc.cpp' || echo './'`main.moc.cpp; \
        then mv -f ".deps/main.moc.Tpo" ".deps/main.moc.Po"; \
        else rm -f ".deps/main.moc.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -DQT_SHARED -DQT_TABLET_SUPPORT -DQT_THREAD_SUPPORT -D_REENTRANT -I/usr/include/qt3   -I../../src/pfs/    -O2   -MT pfsview_widget.moc.o -MD -MP -MF ".deps/pfsview_widget.moc.Tpo" \
          -c -o pfsview_widget.moc.o `test -f 'pfsview_widget.moc.cpp' || echo './'`pfsview_widget.moc.cpp; \
        then mv -f ".deps/pfsview_widget.moc.Tpo" ".deps/pfsview_widget.moc.Po"; \
        else rm -f ".deps/pfsview_widget.moc.Tpo"; exit 1; \
        fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -DQT_SHARED -DQT_TABLET_SUPPORT -DQT_THREAD_SUPPORT -D_REENTRANT -I/usr/include/qt3   -I../../src/pfs/    -O2   -MT luminancerange_widget.moc.o -MD -MP -MF ".deps/luminancerange_widget.moc.Tpo" \
          -c -o luminancerange_widget.moc.o `test -f 'luminancerange_widget.moc.cpp' || echo './'`luminancerange_widget.moc.cpp; \
        then mv -f ".deps/luminancerange_widget.moc.Tpo" ".deps/luminancerange_widget.moc.Po"; \
        else rm -f ".deps/luminancerange_widget.moc.Tpo"; exit 1; \
        fi
/bin/bash ../../libtool --mode=link g++  -O2     -o pfsview  main.o pfsview_widget.o luminancerange_widget.o histogram.o main.moc.o pfsview_widget.moc.o luminancerange_widget.moc.o -L/usr/X11R6/lib -lqt-mt -laudio -lXt -ljpeg -lpng -lz -lXi -lXrender -lXrandr -lXcursor -lXinerama -lXft -lfreetype -lfontconfig -lXext -lX11 -lm -lSM -lICE -ldl -lpthread   ../pfs/libpfs-1.2.la
mkdir .libs
g++ -O2 -o .libs/pfsview main.o pfsview_widget.o luminancerange_widget.o histogram.o main.moc.o pfsview_widget.moc.o luminancerange_widget.moc.o  -L/usr/X11R6/lib /usr/lib/libqt-mt.so /usr/lib/libjpeg.so /usr/lib/libfreetype.so -lm ../pfs/.libs/libpfs-1.2.so -laudio -lXt -lpng -lXi -lXrender -lXrandr -lXcursor -lXinerama -lXft -lfontconfig -lXext -lX11 -lSM -lICE -ldl -lpthread -lz -Wl,--rpath -Wl,/usr/local/lib
creating pfsview
make[4]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfsview'
make[3]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfsview'
Making all in pfsglview
make[3]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfsglview'
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I./../pfs     -O2   -MT pfsglview.o -MD -MP -MF ".deps/pfsglview.Tpo" \
          -c -o pfsglview.o `test -f 'pfsglview.cpp' || echo './'`pfsglview.cpp; \
        then mv -f ".deps/pfsglview.Tpo" ".deps/pfsglview.Po"; \
        else rm -f ".deps/pfsglview.Tpo"; exit 1; \
        fi
In file included from pfsglview.cpp:32:
glenv.h:11:21: error: GL/glut.h: No such file or directory
pfsglview.cpp: In function ‘void display()’:
pfsglview.cpp:205: error: ‘GLUT_WINDOW_WIDTH’ was not declared in this scope
pfsglview.cpp:205: error: ‘glutGet’ was not declared in this scope
pfsglview.cpp:206: error: ‘GLUT_WINDOW_HEIGHT’ was not declared in this scope
pfsglview.cpp:245: error: ‘glutSwapBuffers’ was not declared in this scope
pfsglview.cpp: In function ‘void resizeWindow(int, int)’:
pfsglview.cpp:285: error: ‘GLUT_WINDOW_HEIGHT’ was not declared in this scope
pfsglview.cpp:285: error: ‘glutGet’ was not declared in this scope
pfsglview.cpp:287: error: ‘glutPostRedisplay’ was not declared in this scope
pfsglview.cpp: In function ‘void menuListener(int)’:
pfsglview.cpp:433: error: ‘glutPostRedisplay’ was not declared in this scope
pfsglview.cpp: In function ‘void mouseListener(int, int, int, int)’:
pfsglview.cpp:446: error: ‘GLUT_LEFT_BUTTON’ was not declared in this scope
pfsglview.cpp:447: error: ‘GLUT_DOWN’ was not declared in this scope
pfsglview.cpp:453: error: ‘GLUT_LEFT_BUTTON’ was not declared in this scope
pfsglview.cpp:453: error: ‘GLUT_UP’ was not declared in this scope
pfsglview.cpp:461: error: ‘GLUT_LEFT_BUTTON’ was not declared in this scope
pfsglview.cpp:461: error: ‘GLUT_UP’ was not declared in this scope
pfsglview.cpp:466: error: ‘GLUT_CURSOR_INHERIT’ was not declared in this scope
pfsglview.cpp:466: error: ‘glutSetCursor’ was not declared in this scope
pfsglview.cpp:469: error: ‘GLUT_LEFT_BUTTON’ was not declared in this scope
pfsglview.cpp:469: error: ‘GLUT_DOWN’ was not declared in this scope
pfsglview.cpp:475: error: ‘glutPostRedisplay’ was not declared in this scope
pfsglview.cpp: In function ‘void mouseMotionListener(int, int)’:
pfsglview.cpp:490: error: ‘GLUT_CURSOR_LEFT_SIDE’ was not declared in this scope
pfsglview.cpp:490: error: ‘glutSetCursor’ was not declared in this scope
pfsglview.cpp:498: error: ‘GLUT_CURSOR_RIGHT_SIDE’ was not declared in this scope
pfsglview.cpp:507: error: ‘GLUT_CURSOR_LEFT_RIGHT’ was not declared in this scope
pfsglview.cpp:536: error: ‘glutPostRedisplay’ was not declared in this scope
pfsglview.cpp: In function ‘void mousePassiveMotionListener(int, int)’:
pfsglview.cpp:547: error: ‘GLUT_WINDOW_HEIGHT’ was not declared in this scope
pfsglview.cpp:547: error: ‘glutGet’ was not declared in this scope
pfsglview.cpp:567: error: ‘glutPostRedisplay’ was not declared in this scope
pfsglview.cpp: In function ‘void specialKeyListener(int, int, int)’:
pfsglview.cpp:617: error: ‘GLUT_KEY_LEFT’ was not declared in this scope
pfsglview.cpp:619: error: ‘glutPostRedisplay’ was not declared in this scope
pfsglview.cpp:622: error: ‘GLUT_KEY_RIGHT’ was not declared in this scope
pfsglview.cpp:627: error: ‘GLUT_KEY_UP’ was not declared in this scope
pfsglview.cpp:632: error: ‘GLUT_KEY_DOWN’ was not declared in this scope
pfsglview.cpp: In function ‘void setWindowTitle()’:
pfsglview.cpp:730: error: ‘glutSetWindowTitle’ was not declared in this scope
pfsglview.cpp: In function ‘int main(int, char**)’:
pfsglview.cpp:775: error: ‘glutInit’ was not declared in this scope
pfsglview.cpp:776: error: ‘glutInitWindowPosition’ was not declared in this scope
pfsglview.cpp:782: error: ‘glutInitWindowSize’ was not declared in this scope
pfsglview.cpp:783: error: ‘GLUT_RGBA’ was not declared in this scope
pfsglview.cpp:783: error: ‘GLUT_DOUBLE’ was not declared in this scope
pfsglview.cpp:783: error: ‘glutInitDisplayMode’ was not declared in this scope
pfsglview.cpp:785: error: ‘glutCreateWindow’ was not declared in this scope
pfsglview.cpp:787: error: ‘GLUT_WINDOW_HEIGHT’ was not declared in this scope
pfsglview.cpp:787: error: ‘glutGet’ was not declared in this scope
pfsglview.cpp:799: error: ‘glutCreateMenu’ was not declared in this scope
pfsglview.cpp:800: error: ‘glutAddMenuEntry’ was not declared in this scope
pfsglview.cpp:832: error: ‘glutAddSubMenu’ was not declared in this scope
pfsglview.cpp:844: error: ‘GLUT_RIGHT_BUTTON’ was not declared in this scope
pfsglview.cpp:844: error: ‘glutAttachMenu’ was not declared in this scope
pfsglview.cpp:857: error: ‘glutMouseFunc’ was not declared in this scope
pfsglview.cpp:858: error: ‘glutMotionFunc’ was not declared in this scope
pfsglview.cpp:859: error: ‘glutPassiveMotionFunc’ was not declared in this scope
pfsglview.cpp:862: error: ‘glutKeyboardFunc’ was not declared in this scope
pfsglview.cpp:863: error: ‘glutSpecialFunc’ was not declared in this scope
pfsglview.cpp:865: error: ‘glutDisplayFunc’ was not declared in this scope
pfsglview.cpp:866: error: ‘glutReshapeFunc’ was not declared in this scope
pfsglview.cpp:867: error: ‘glutMainLoop’ was not declared in this scope[B]
make[3]: *** [pfsglview.o] Fehler 1
make[3]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfsglview'
make[2]: *** [all-recursive] Fehler 1
make[2]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src'
make[1]: *** [all-recursive] Fehler 1
make[1]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6'
make: *** [all] Fehler 2[/B]
timo@aristoteles:~/Desktop/pfstools-1.6$ sudo make
make  all-recursive
make[1]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6'
Making all in src
make[2]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src'
Making all in pfs
make[3]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfs'
make[3]: Für das Ziel »all« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfs'
Making all in fileformat
make[3]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/fileformat'
make[3]: Für das Ziel »all« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/fileformat'
Making all in filter
make[3]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/filter'
make[3]: Für das Ziel »all« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/filter'
Making all in pfsview
make[3]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfsview'
make  all-am
make[4]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfsview'
make[4]: Für das Ziel »all-am« ist nichts zu tun.
make[4]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfsview'
make[3]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfsview'
Making all in pfsglview
make[3]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfsglview'
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I./../pfs     -O2   -MT pfsglview.o -MD -MP -MF ".deps/pfsglview.Tpo" \
          -c -o pfsglview.o `test -f 'pfsglview.cpp' || echo './'`pfsglview.cpp; \
        then mv -f ".deps/pfsglview.Tpo" ".deps/pfsglview.Po"; \
        else rm -f ".deps/pfsglview.Tpo"; exit 1; \
        fi
In file included from pfsglview.cpp:32:
glenv.h:11:21: error: GL/glut.h: No such file or directory
pfsglview.cpp: In function ‘void display()’:
pfsglview.cpp:205: error: ‘GLUT_WINDOW_WIDTH’ was not declared in this scope
pfsglview.cpp:205: error: ‘glutGet’ was not declared in this scope
pfsglview.cpp:206: error: ‘GLUT_WINDOW_HEIGHT’ was not declared in this scope
pfsglview.cpp:245: error: ‘glutSwapBuffers’ was not declared in this scope
pfsglview.cpp: In function ‘void resizeWindow(int, int)’:
pfsglview.cpp:285: error: ‘GLUT_WINDOW_HEIGHT’ was not declared in this scope
pfsglview.cpp:285: error: ‘glutGet’ was not declared in this scope
pfsglview.cpp:287: error: ‘glutPostRedisplay’ was not declared in this scope
pfsglview.cpp: In function ‘void menuListener(int)’:
pfsglview.cpp:433: error: ‘glutPostRedisplay’ was not declared in this scope
pfsglview.cpp: In function ‘void mouseListener(int, int, int, int)’:
pfsglview.cpp:446: error: ‘GLUT_LEFT_BUTTON’ was not declared in this scope
pfsglview.cpp:447: error: ‘GLUT_DOWN’ was not declared in this scope
pfsglview.cpp:453: error: ‘GLUT_LEFT_BUTTON’ was not declared in this scope
pfsglview.cpp:453: error: ‘GLUT_UP’ was not declared in this scope
pfsglview.cpp:461: error: ‘GLUT_LEFT_BUTTON’ was not declared in this scope
pfsglview.cpp:461: error: ‘GLUT_UP’ was not declared in this scope
pfsglview.cpp:466: error: ‘GLUT_CURSOR_INHERIT’ was not declared in this scope
pfsglview.cpp:466: error: ‘glutSetCursor’ was not declared in this scope
pfsglview.cpp:469: error: ‘GLUT_LEFT_BUTTON’ was not declared in this scope
pfsglview.cpp:469: error: ‘GLUT_DOWN’ was not declared in this scope
pfsglview.cpp:475: error: ‘glutPostRedisplay’ was not declared in this scope
pfsglview.cpp: In function ‘void mouseMotionListener(int, int)’:
pfsglview.cpp:490: error: ‘GLUT_CURSOR_LEFT_SIDE’ was not declared in this scope
pfsglview.cpp:490: error: ‘glutSetCursor’ was not declared in this scope
pfsglview.cpp:498: error: ‘GLUT_CURSOR_RIGHT_SIDE’ was not declared in this scope
pfsglview.cpp:507: error: ‘GLUT_CURSOR_LEFT_RIGHT’ was not declared in this scope
pfsglview.cpp:536: error: ‘glutPostRedisplay’ was not declared in this scope
pfsglview.cpp: In function ‘void mousePassiveMotionListener(int, int)’:
pfsglview.cpp:547: error: ‘GLUT_WINDOW_HEIGHT’ was not declared in this scope
pfsglview.cpp:547: error: ‘glutGet’ was not declared in this scope
pfsglview.cpp:567: error: ‘glutPostRedisplay’ was not declared in this scope
pfsglview.cpp: In function ‘void specialKeyListener(int, int, int)’:
pfsglview.cpp:617: error: ‘GLUT_KEY_LEFT’ was not declared in this scope
pfsglview.cpp:619: error: ‘glutPostRedisplay’ was not declared in this scope
pfsglview.cpp:622: error: ‘GLUT_KEY_RIGHT’ was not declared in this scope
pfsglview.cpp:627: error: ‘GLUT_KEY_UP’ was not declared in this scope
pfsglview.cpp:632: error: ‘GLUT_KEY_DOWN’ was not declared in this scope
pfsglview.cpp: In function ‘void setWindowTitle()’:
pfsglview.cpp:730: error: ‘glutSetWindowTitle’ was not declared in this scope
pfsglview.cpp: In function ‘int main(int, char**)’:
pfsglview.cpp:775: error: ‘glutInit’ was not declared in this scope
pfsglview.cpp:776: error: ‘glutInitWindowPosition’ was not declared in this scope
pfsglview.cpp:782: error: ‘glutInitWindowSize’ was not declared in this scope
pfsglview.cpp:783: error: ‘GLUT_RGBA’ was not declared in this scope
pfsglview.cpp:783: error: ‘GLUT_DOUBLE’ was not declared in this scope
pfsglview.cpp:783: error: ‘glutInitDisplayMode’ was not declared in this scope
pfsglview.cpp:785: error: ‘glutCreateWindow’ was not declared in this scope
pfsglview.cpp:787: error: ‘GLUT_WINDOW_HEIGHT’ was not declared in this scope
pfsglview.cpp:787: error: ‘glutGet’ was not declared in this scope
pfsglview.cpp:799: error: ‘glutCreateMenu’ was not declared in this scope
pfsglview.cpp:800: error: ‘glutAddMenuEntry’ was not declared in this scope
pfsglview.cpp:832: error: ‘glutAddSubMenu’ was not declared in this scope
pfsglview.cpp:844: error: ‘GLUT_RIGHT_BUTTON’ was not declared in this scope
pfsglview.cpp:844: error: ‘glutAttachMenu’ was not declared in this scope
pfsglview.cpp:857: error: ‘glutMouseFunc’ was not declared in this scope
pfsglview.cpp:858: error: ‘glutMotionFunc’ was not declared in this scope
pfsglview.cpp:859: error: ‘glutPassiveMotionFunc’ was not declared in this scope
pfsglview.cpp:862: error: ‘glutKeyboardFunc’ was not declared in this scope
pfsglview.cpp:863: error: ‘glutSpecialFunc’ was not declared in this scope
pfsglview.cpp:865: error: ‘glutDisplayFunc’ was not declared in this scope
pfsglview.cpp:866: error: ‘glutReshapeFunc’ was not declared in this scope
pfsglview.cpp:867: error: ‘glutMainLoop’ was not declared in this scope[B]
make[3]: *** [pfsglview.o] Fehler 1
make[3]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfsglview'
make[2]: *** [all-recursive] Fehler 1
make[2]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src'
make[1]: *** [all-recursive] Fehler 1
make[1]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6'
make: *** [all] Fehler 2[/B]
```

Bye, Timo

---

### Post by Jason_25 on 2007-03-23
It looks like your still missing dev packages.

```

In file included from pfsglview.cpp:32:
glenv.h:11:21: error: GL/glut.h: No such file or directory

```

I think you need the opengl dev packages like libglut.

---

### Post by Arby on 2007-03-23
> **Timokl said:**
> Hi Arby,

first of all thanks a lot for helping me out, and for showing me apt-cache.

Sadly, the compiling did not went through smoothly. I apt-get'ed the recommonded packages as well as the package octave2.9 (apt-cache did not find a candidate for matlab). 

apt-cache won't find matlab. matlab is a windows program, Octave aims to be an open source equivalent to matlab. Anyway on to your problem. This had me confused for a while but I think I've got it. I reproduced your errors on my machine and it turns out it's just another missing library. The problem is all the lines that look like this ```
glenv.h:11:21: error: GL/glut.h: No such file or directory
pfsglview.cpp: In function ‘void display()’:
pfsglview.cpp:205: error: ‘GLUT_WINDOW_WIDTH’ was not declared in this scope
pfsglview.cpp:205: error: ‘glutGet’ was not declared in this scope
``` Another visit to apt-cache search tells me that these are all provided by the package libglut-dev. So I ran ```
sudo apt-get install libglut-dev
``` followed by ```
./configure
make
sudo make install
``` yet again. That completed and installed correctly on my system.

The problem actually occurred much earlier than the bits you had put in bold. The best way to troubleshoot problems like this is to look for the earliest point in the output where you can see words like 'error' or 'warning'. It's often the case that all the errors after that point are a consequence of the original error. So if you fix the first error others often go away.

Hope we've got it this time :) 

Arby

---

### Post by Timokl on 2007-03-24
Hi Arby,

we got it --- nearly. :-) The pfstools comprise of several commandline programs, and the one to write the result into a file (or a pipe) cannot be started. The programm in question should be **pfsoutppm**.

```
timo@aristoteles:~/Desktop/pfstools-1.6$ pfsoutppm
bash: pfsoutppm: command not found
```

According to the faq included in pfstools, the following command SHOULD work:

```
timo@aristoteles:~/Desktop$ pfsin bkk.exr | pfstmo_drago03 | pfsgamma 2.2 | pfsout bangkok.jpeg
/usr/local/bin/pfsout: line 104: pfsoutppm: command not found
pnmtojpeg: EOF / read error reading magic number
```

The man page of this program is available on my machine.

Here's the log of the make install

```

timo@aristoteles:~/Desktop/pfstools-1.6$ sudo make install
Making install in src
make[1]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src'
Making install in pfs
make[2]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfs'
make[3]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfs'
/bin/bash ../../mkinstalldirs /usr/local/lib
 /bin/bash ../../libtool --mode=install /usr/bin/install -c  libpfs-1.2.la /usr/local/lib/libpfs-1.2.la
/usr/bin/install -c .libs/libpfs-1.2.so.0.0.0 /usr/local/lib/libpfs-1.2.so.0.0.0
(cd /usr/local/lib && rm -f libpfs-1.2.so.0 && ln -s libpfs-1.2.so.0.0.0 libpfs-1.2.so.0)
(cd /usr/local/lib && rm -f libpfs-1.2.so && ln -s libpfs-1.2.so.0.0.0 libpfs-1.2.so)
/usr/bin/install -c .libs/libpfs-1.2.lai /usr/local/lib/libpfs-1.2.la
/usr/bin/install -c .libs/libpfs-1.2.a /usr/local/lib/libpfs-1.2.a
ranlib /usr/local/lib/libpfs-1.2.a
chmod 644 /usr/local/lib/libpfs-1.2.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
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
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
/bin/bash ../../mkinstalldirs /usr/local/include/pfs-1.2
 /usr/bin/install -c -m 644 pfs.h /usr/local/include/pfs-1.2/pfs.h
 /usr/bin/install -c -m 644 array2d.h /usr/local/include/pfs-1.2/array2d.h
/bin/bash ../../mkinstalldirs /usr/local/lib/pkgconfig
 /usr/bin/install -c -m 644 pfs.pc /usr/local/lib/pkgconfig/pfs.pc
make[3]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfs'
make[2]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfs'
Making install in fileformat
make[2]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/fileformat'
make[3]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/fileformat'
/bin/bash ../../mkinstalldirs /usr/local/bin
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfsinrgbe /usr/local/bin/pfsinrgbe
/usr/bin/install -c .libs/pfsinrgbe /usr/local/bin/pfsinrgbe
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfsoutrgbe /usr/local/bin/pfsoutrgbe
/usr/bin/install -c .libs/pfsoutrgbe /usr/local/bin/pfsoutrgbe
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfsinpfm /usr/local/bin/pfsinpfm
/usr/bin/install -c .libs/pfsinpfm /usr/local/bin/pfsinpfm
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfsoutpfm /usr/local/bin/pfsoutpfm
/usr/bin/install -c .libs/pfsoutpfm /usr/local/bin/pfsoutpfm
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfsinexr /usr/local/bin/pfsinexr
/usr/bin/install -c .libs/pfsinexr /usr/local/bin/pfsinexr
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfsoutexr /usr/local/bin/pfsoutexr
/usr/bin/install -c .libs/pfsoutexr /usr/local/bin/pfsoutexr
/bin/bash ../../mkinstalldirs /usr/local/bin
 /usr/bin/install -c pfsin /usr/local/bin/pfsin
 /usr/bin/install -c pfsout /usr/local/bin/pfsout
 /usr/bin/install -c pfsoutffmpeg /usr/local/bin/pfsoutffmpeg
 /usr/bin/install -c pfsinmulti /usr/local/bin/pfsinmulti
 /usr/bin/install -c pfsindcraw /usr/local/bin/pfsindcraw
/bin/bash ../../mkinstalldirs /usr/local/man/man1
 /usr/bin/install -c -m 644 ./pfsin.1 /usr/local/man/man1/pfsin.1
 /usr/bin/install -c -m 644 ./pfsout.1 /usr/local/man/man1/pfsout.1
 /usr/bin/install -c -m 644 ./pfsinppm.1 /usr/local/man/man1/pfsinppm.1
 /usr/bin/install -c -m 644 ./pfsinexr.1 /usr/local/man/man1/pfsinexr.1
 /usr/bin/install -c -m 644 ./pfsinrgbe.1 /usr/local/man/man1/pfsinrgbe.1
 /usr/bin/install -c -m 644 ./pfsintiff.1 /usr/local/man/man1/pfsintiff.1
 /usr/bin/install -c -m 644 ./pfsoutppm.1 /usr/local/man/man1/pfsoutppm.1
 /usr/bin/install -c -m 644 ./pfsoutexr.1 /usr/local/man/man1/pfsoutexr.1
 /usr/bin/install -c -m 644 ./pfsoutffmpeg.1 /usr/local/man/man1/pfsoutffmpeg.1
 /usr/bin/install -c -m 644 ./pfsinpfm.1 /usr/local/man/man1/pfsinpfm.1
 /usr/bin/install -c -m 644 ./pfsoutpfm.1 /usr/local/man/man1/pfsoutpfm.1
 /usr/bin/install -c -m 644 ./pfsinmulti.1 /usr/local/man/man1/pfsinmulti.1
 /usr/bin/install -c -m 644 ./pfsinimgmagick.1 /usr/local/man/man1/pfsinimgmagick.1
 /usr/bin/install -c -m 644 ./pfsoutimgmagick.1 /usr/local/man/man1/pfsoutimgmagick.1
 /usr/bin/install -c -m 644 ./pfsinjpeghdr.1 /usr/local/man/man1/pfsinjpeghdr.1
 /usr/bin/install -c -m 644 ./pfsoutjpeghdr.1 /usr/local/man/man1/pfsoutjpeghdr.1
 /usr/bin/install -c -m 644 ./pfsindcraw.1 /usr/local/man/man1/pfsindcraw.1
make  install-data-hook
make[4]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/fileformat'
cd /usr/local/man/man1; \
        ln -f -s pfsoutppm.1 pfsouttiff.1; \
        ln -f -s pfsoutppm.1 pfsoutrgbe.1;
make[4]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/fileformat'
make[3]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/fileformat'
make[2]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/fileformat'
Making install in filter
make[2]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/filter'
make[3]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/filter'
/bin/bash ../../mkinstalldirs /usr/local/bin
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfsclamp /usr/local/bin/pfsclamp
/usr/bin/install -c .libs/pfsclamp /usr/local/bin/pfsclamp
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfsgamma /usr/local/bin/pfsgamma
/usr/bin/install -c .libs/pfsgamma /usr/local/bin/pfsgamma
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfstag /usr/local/bin/pfstag
/usr/bin/install -c .libs/pfstag /usr/local/bin/pfstag
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfssize /usr/local/bin/pfssize
/usr/bin/install -c .libs/pfssize /usr/local/bin/pfssize
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfsextractchannels /usr/local/bin/pfsextractchannels
/usr/bin/install -c .libs/pfsextractchannels /usr/local/bin/pfsextractchannels
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfspanoramic /usr/local/bin/pfspanoramic
/usr/bin/install -c .libs/pfspanoramic /usr/local/bin/pfspanoramic
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfsrotate /usr/local/bin/pfsrotate
/usr/bin/install -c .libs/pfsrotate /usr/local/bin/pfsrotate
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfsflip /usr/local/bin/pfsflip
/usr/bin/install -c .libs/pfsflip /usr/local/bin/pfsflip
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfscut /usr/local/bin/pfscut
/usr/bin/install -c .libs/pfscut /usr/local/bin/pfscut
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfspad /usr/local/bin/pfspad
/usr/bin/install -c .libs/pfspad /usr/local/bin/pfspad
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfscat /usr/local/bin/pfscat
/usr/bin/install -c .libs/pfscat /usr/local/bin/pfscat
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfsabsolute /usr/local/bin/pfsabsolute
/usr/bin/install -c .libs/pfsabsolute /usr/local/bin/pfsabsolute
/bin/bash ../../mkinstalldirs /usr/local/man/man1
 /usr/bin/install -c -m 644 ./pfsgamma.1 /usr/local/man/man1/pfsgamma.1
 /usr/bin/install -c -m 644 ./pfsclamp.1 /usr/local/man/man1/pfsclamp.1
 /usr/bin/install -c -m 644 ./pfstag.1 /usr/local/man/man1/pfstag.1
 /usr/bin/install -c -m 644 ./pfssize.1 /usr/local/man/man1/pfssize.1
 /usr/bin/install -c -m 644 ./pfsextractchannels.1 /usr/local/man/man1/pfsextractchannels.1
 /usr/bin/install -c -m 644 ./pfspanoramic.1 /usr/local/man/man1/pfspanoramic.1
 /usr/bin/install -c -m 644 ./pfsrotate.1 /usr/local/man/man1/pfsrotate.1
 /usr/bin/install -c -m 644 ./pfsflip.1 /usr/local/man/man1/pfsflip.1
 /usr/bin/install -c -m 644 ./pfscut.1 /usr/local/man/man1/pfscut.1
 /usr/bin/install -c -m 644 ./pfspad.1 /usr/local/man/man1/pfspad.1
 /usr/bin/install -c -m 644 ./pfscat.1 /usr/local/man/man1/pfscat.1
 /usr/bin/install -c -m 644 ./pfsabsolute.1 /usr/local/man/man1/pfsabsolute.1
make[3]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/filter'
make[2]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/filter'
Making install in pfsview
make[2]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfsview'
make  install-am
make[3]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfsview'
make[4]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfsview'
/bin/bash ../../mkinstalldirs /usr/local/bin
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfsview /usr/local/bin/pfsview
/usr/bin/install -c .libs/pfsview /usr/local/bin/pfsview
/bin/bash ../../mkinstalldirs /usr/local/bin
 /usr/bin/install -c pfsv /usr/local/bin/pfsv
/bin/bash ../../mkinstalldirs /usr/local/man/man1
 /usr/bin/install -c -m 644 ./pfsview.1 /usr/local/man/man1/pfsview.1
 /usr/bin/install -c -m 644 ./pfsv.1 /usr/local/man/man1/pfsv.1
make[4]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfsview'
make[3]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfsview'
make[2]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfsview'
Making install in pfsglview
make[2]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfsglview'
make[3]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfsglview'
/bin/bash ../../mkinstalldirs /usr/local/bin
  /bin/bash ../../libtool --mode=install /usr/bin/install -c pfsglview /usr/local/bin/pfsglview
/usr/bin/install -c .libs/pfsglview /usr/local/bin/pfsglview
make[3]: Für das Ziel »install-data-am« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfsglview'
make[2]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src/pfsglview'
make[2]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src'
make[3]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6/src'
make[3]: Für das Ziel »install-exec-am« ist nichts zu tun.
make[3]: Für das Ziel »install-data-am« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src'
make[2]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src'
make[1]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6/src'
make[1]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6'
make[2]: Betrete Verzeichnis '/home/timo/Desktop/pfstools-1.6'
make[2]: Für das Ziel »install-exec-am« ist nichts zu tun.
make[2]: Für das Ziel »install-data-am« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6'
make[1]: Verlasse Verzeichnis '/home/timo/Desktop/pfstools-1.6'
```

Any ideas?

Bye,
Timo

---

### Post by Arby on 2007-03-24
OK I admit I'm struggling a bit now. A bit more googling led me to flickr of all places. The very last comment on this page [http://www.flickr.com/groups/hdr/discuss/72157594188924636/](http://www.flickr.com/groups/hdr/discuss/72157594188924636/) mentions the same problem and says it was fixed by installing libnetpbm10-dev and recompiling pfstools. Looking back at the make output in your original post I did find these lines ```
checking for ppm_init in -lnetppm... no
checking for pbm_init in -lnetpbm... no
checking for ppm_init in -lppm... no
``` These kind of indicate the same thing so lets try that. Run this command ```
sudo apt-get install libnetpbm10-dev
``` Then do the whole ./configure, make etc thing again. 

If that doesn't fix it this time then I don't know whats wrong. I suppose it could be things being in the wrong path but lets worry about that later.

Arby

---

### Post by Timokl on 2007-03-24
Yes, that was the missing link ... synchronicity! (wonderful "Police" song, btw). :lolflag: 

Arby, thnx a lot for your help! Now, I need to get a new Digital Camera, as my old seems to have died the last days. :( 

Anyway, I have attached a night shot at Bangkok from my balcony for you to enjoy. I guess it's the only way for me to give you something back for now, although it's not much.

Thnx again,
Timo

---

### Post by Arby on 2007-03-25
Glad we got it sorted in the end

---

