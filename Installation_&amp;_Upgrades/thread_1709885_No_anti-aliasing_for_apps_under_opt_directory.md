---
title: "No anti-aliasing for apps under /opt directory"
date: 2011-03-19
forum: Installation &amp; Upgrades
---

### Post by herophuong on 2011-03-19
I have installed the newest version of LibreOffice and Firefox 4 RC under the /opt directory (manual install, not via synaptic). But the awful thing is that none of these apps get anti-aliasing from system. 
Anyone here knows the solution?

---

### Post by kidders on 2011-03-20
Hi there,

In general, applications in /opt are self-contained binary packages that aren't necessarily linked against the rest of your system. Consequently, they'll be pretty generic builds, and you have to expect some features to be missing. The most obvious solutions are to install versions specifically built for your version of Ubuntu, or compile both applications from source, so that they *do* link against the libraries on your system responsible for anti-aliasing.

I hope that helps.

---

### Post by herophuong on 2011-03-20
I have built Firefox from source with my system configurations but nothing is different.

---

### Post by kidders on 2011-03-20
> **herophuong said:**
> I have built Firefox from source with my system configurations but nothing is different.

It's been a while since I built firefox from scratch, but if you post your ./configure output, I'll do my best to find the problem.

---

### Post by herophuong on 2011-03-20
I can only run "firefox" after it is built, not "firefox-bin" because when i run firefox-bin, the error that libxul.so not found appears. Is it the problem?
```
loading cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for gawk... (cached) mawk
checking for perl5... (cached) /usr/bin/perl
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for c++... (cached) c++
checking whether the C++ compiler (c++  ) works... yes
checking whether the C++ compiler (c++  ) is a cross-compiler... no
checking whether we are using GNU C++... (cached) yes
checking whether c++ accepts -g... (cached) yes
checking for ranlib... (cached) ranlib
checking for as... (cached) /usr/bin/as
checking for ar... (cached) ar
checking for ld... (cached) ld
checking for strip... (cached) strip
checking for windres... no
checking whether gcc and cc understand -c and -o together... (cached) yes
checking how to run the C preprocessor... (cached) gcc -E
checking how to run the C++ preprocessor... (cached) c++ -E
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether ln -s works... (cached) yes
checking for minimum required perl version >= 5.006... 5.010001
checking for full perl installation... yes
checking for python2.7... (cached) /usr/bin/python2.6
checking for doxygen... (cached) :
checking for autoconf... (cached) /usr/bin/autoconf
checking for unzip... (cached) /usr/bin/unzip
checking for zip... (cached) /usr/bin/zip
checking for makedepend... no
checking for xargs... (cached) /usr/bin/xargs
checking for gmake... (cached) /usr/bin/make
checking for X... (cached) libraries , headers 
checking for dnet_ntoa in -ldnet... (cached) no
checking for dnet_ntoa in -ldnet_stub... (cached) no
checking for gethostbyname... (cached) yes
checking for connect... (cached) yes
checking for remove... (cached) yes
checking for shmat... (cached) yes
checking for IceConnectionNumber in -lICE... (cached) yes
checking whether the compiler supports -Wno-invalid-offsetof... yes
checking whether the compiler supports -Wno-variadic-macros... yes
checking whether the compiler supports -Werror=return-type... yes
checking whether ld has archive extraction flags... (cached) yes
checking that static assertion macros used in autoconf tests work... (cached) yes
checking for 64-bit OS... no
checking for Python version >= 2.5 but not 3.x... yes
checking for ANSI C header files... (cached) yes
checking for working const... (cached) yes
checking for mode_t... (cached) yes
checking for off_t... (cached) yes
checking for pid_t... (cached) yes
checking for size_t... (cached) yes
checking for __stdcall... (cached) no
checking for ssize_t... (cached) yes
checking for st_blksize in struct stat... (cached) yes
checking for siginfo_t... (cached) yes
checking for int16_t... (cached) yes
checking for int32_t... (cached) yes
checking for int64_t... (cached) yes
checking for int64... (cached) no
checking for uint... (cached) yes
checking for uint_t... (cached) no
checking for uint16_t... (cached) no
checking for uname.domainname... (cached) yes
checking for uname.__domainname... (cached) no
checking for usable char16_t (2 bytes, unsigned)... (cached) no
checking for usable wchar_t (2 bytes, unsigned)... (cached) no
checking for compiler -fshort-wchar option... (cached) yes
checking for visibility(hidden) attribute... (cached) yes
checking for visibility(default) attribute... (cached) yes
checking for visibility pragma support... (cached) yes
checking For gcc visibility bug with class-level attributes (GCC bug 26905)... (cached) no
checking For x86_64 gcc visibility bug with builtins (GCC bug 20297)... (cached) no
checking for __force_align_arg_pointer__ attribute... (cached) yes
checking for dirent.h that defines DIR... (cached) yes
checking for opendir in -ldir... (cached) no
checking for sys/byteorder.h... (cached) no
checking for compat.h... (cached) no
checking for getopt.h... (cached) yes
checking for sys/bitypes.h... (cached) yes
checking for memory.h... (cached) yes
checking for unistd.h... (cached) yes
checking for gnu/libc-version.h... (cached) yes
checking for nl_types.h... (cached) yes
checking for malloc.h... (cached) yes
checking for X11/XKBlib.h... (cached) yes
checking for io.h... (cached) no
checking for sys/statvfs.h... (cached) yes
checking for sys/statfs.h... (cached) yes
checking for sys/vfs.h... (cached) yes
checking for sys/mount.h... (cached) yes
checking for sys/quota.h... (cached) yes
checking for linux/quota.h... (cached) yes
checking for mmintrin.h... (cached) no
checking for new... (cached) yes
checking for sys/cdefs.h... (cached) yes
checking for gethostbyname_r in -lc_r... (cached) no
checking for library containing dlopen... (cached) -ldl
checking for dlfcn.h... (cached) yes
checking for dladdr... (cached) yes
checking for socket in -lsocket... (cached) no
checking for XDrawLines in -lX11... (cached) yes
checking for XextAddDisplay in -lXext... (cached) yes
checking for XtFree in -lXt... (cached) yes
checking for XShmCreateImage in -lXext... (cached) yes
checking for X11/extensions/XShm.h... (cached) yes
checking for X11/extensions/scrnsaver.h... (cached) no
checking for XieFloGeometry in -lXIE... (cached) no
checking for X11/extensions/XIElib.h... (cached) no
checking for freetype-config... (cached) /usr/bin/freetype-config
checking for FreeType - version >= 6.1.0... yes
checking for FT_Bitmap_Size.y_ppem... (cached) yes
checking for FT_GlyphSlot_Embolden... (cached) yes
checking for FT_Load_Sfnt_Table... (cached) yes
checking for FT_Select_Size... (cached) yes
checking for ARM SIMD support in compiler... no
checking for ARM NEON support in compiler... no
checking for pthread_create in -lpthreads... no
checking for pthread_create in -lpthread... yes
checking whether gcc accepts -pthread... yes
checking whether mmap() sees write()s... yes
checking whether gcc needs -traditional... (cached) no
checking for 8-bit clean memcmp... (cached) yes
checking for random... (cached) yes
checking for strerror... (cached) yes
checking for lchown... (cached) yes
checking for fchmod... (cached) yes
checking for snprintf... (cached) yes
checking for statvfs... (cached) yes
checking for memmove... (cached) yes
checking for rint... (cached) no
checking for stat64... (cached) yes
checking for lstat64... (cached) yes
checking for truncate64... (cached) yes
checking for statvfs64... (cached) yes
checking for setbuf... (cached) yes
checking for isatty... (cached) yes
checking for flockfile... (cached) yes
checking for getpagesize... (cached) yes
checking for localtime_r... (cached) yes
checking for strtok_r... (cached) yes
checking for clock_gettime(CLOCK_MONOTONIC) and -lrt... (cached) yes
checking for wcrtomb... (cached) yes
checking for mbrtowc... (cached) yes
checking for res_ninit()... (cached) yes
checking for gnu_get_libc_version()... (cached) yes
checking for iconv in -lc... (cached) yes
checking for iconv()... (cached) yes
checking for iconv() with const input... (cached) no
checking for nl_langinfo and CODESET... (cached) yes
checking for an implementation of va_copy()... (cached) yes
checking for an implementation of __va_copy()... (cached) yes
checking whether va_lists can be copied by value... (cached) yes
checking for gcc 3.0 ABI... (cached) yes
checking for C++ "explicit" keyword... (cached) yes
checking for C++ "typename" keyword... (cached) yes
checking for modern C++ template specialization syntax support... (cached) yes
checking whether partial template specialization works... (cached) yes
checking whether operators must be re-defined for templates derived from templates... (cached) no
checking whether we need to cast a derived template to pass as its base class... (cached) no
checking whether the compiler can resolve const ambiguities for templates... (cached) yes
checking whether the C++ "using" keyword can change access... (cached) yes
checking whether the C++ "using" keyword resolves ambiguity... (cached) yes
checking for "std::" namespace... (cached) yes
checking whether standard template operator!=() is ambiguous... (cached) unambiguous
checking for C++ reinterpret_cast... (cached) yes
checking for C++ dynamic_cast to void*... (cached) yes
checking whether C++ requires implementation of unused virtual methods... (cached) yes
checking for trouble comparing to zero near std::operator!=()... (cached) no
checking for __thread keyword for TLS variables... (cached) yes
checking for malloc.h... (cached) yes
checking for strndup... (cached) yes
checking for posix_memalign... (cached) yes
checking for memalign... (cached) yes
checking for valloc... (cached) yes
checking for __attribute__((always_inline))... (cached) yes
checking for __attribute__((malloc))... (cached) yes
checking for __attribute__((warn_unused_result))... (cached) yes
checking for __attribute__((noreturn))... (cached) yes
checking for LC_MESSAGES... (cached) yes
checking for localeconv... (cached) yes
checking for YASM assembler... checking for yasm... (cached) yasm
checking if app-specific confvars.sh exists... ./browser/confvars.sh
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.10.0 gtk+-unix-print-2.0 glib-2.0 gobject-2.0 gdk-x11-2.0... yes
checking MOZ_GTK2_CFLAGS... -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gtk-unix-print-2.0  
checking MOZ_GTK2_LIBS... -pthread -lgtk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lfreetype -lfontconfig -lgdk-x11-2.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lm -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -lpng12 -lgthread-2.0 -lrt -lglib-2.0  
checking for pango >= 1.14.0... yes
checking _PANGOCHK_CFLAGS... -pthread -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking _PANGOCHK_LIBS... -pthread -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking for pango >= 1.14.0 pangoft2 >= 1.14.0 pangocairo >= 1.14.0... yes
checking MOZ_PANGO_CFLAGS... -pthread -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/libpng12  
checking MOZ_PANGO_LIBS... -pthread -lpangoft2-1.0 -lfreetype -lfontconfig -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking for gnome-vfs-2.0 >= 2.0 gnome-vfs-module-2.0 >= 2.0... yes
checking MOZ_GNOMEVFS_CFLAGS... -pthread -DORBIT2=1 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gnome-vfs-module-2.0  
checking MOZ_GNOMEVFS_LIBS... -pthread -lgnomevfs-2 -lgconf-2 -lgmodule-2.0 -lgobject-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking for gconf-2.0 >= 1.2.1 gobject-2.0 ... yes
checking MOZ_GCONF_CFLAGS... -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking MOZ_GCONF_LIBS... -pthread -lgconf-2 -lgobject-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking for libnotify >= 0.4... yes
checking MOZ_LIBNOTIFY_CFLAGS... -pthread -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12  
checking MOZ_LIBNOTIFY_LIBS... -pthread -L/lib -lnotify -lgtk-x11-2.0 -ldbus-glib-1 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lm -lcairo -lpng12 -lpango-1.0 -lfreetype -lfontconfig -lgmodule-2.0 -ldbus-1 -lpthread -lgobject-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking for libgnomeui-2.0 >= 2.2.0... yes
checking MOZ_GNOMEUI_CFLAGS... -DORBIT2=1 -pthread -D_REENTRANT -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/gio-unix-2.0/ -I/usr/include/pixman-1 -I/usr/include/libpng12  
checking MOZ_GNOMEUI_LIBS... -pthread -lgnomeui-2 -lSM -lICE -lbonoboui-2 -lgnomevfs-2 -lgnomecanvas-2 -lgnome-2 -lpopt -lbonobo-2 -lbonobo-activation -lORBit-2 -lart_lgpl_2 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lm -lcairo -lpango-1.0 -lfreetype -lfontconfig -lpng12 -lgconf-2 -lgmodule-2.0 -lgobject-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking for dbus-1 >= 0.60... yes
checking MOZ_DBUS_CFLAGS... -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include  
checking MOZ_DBUS_LIBS... -L/lib -ldbus-1 -lpthread -lrt  
checking for dbus-glib-1 >= 0.60... yes
checking MOZ_DBUS_GLIB_CFLAGS... -pthread -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking MOZ_DBUS_GLIB_LIBS... -pthread -L/lib -ldbus-glib-1 -ldbus-1 -lpthread -lgobject-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking __attribute__ ((aligned ())) support... (cached) 64
checking for alsa... yes
checking MOZ_ALSA_CFLAGS... -I/usr/include/alsa  
checking MOZ_ALSA_LIBS... -lasound  
checking for java... (cached) /usr/bin/java
checking for javac... (cached) :
checking for jar... (cached) :
checking for gthread-2.0... yes
checking MOZ_GTHREAD_CFLAGS... -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking MOZ_GTHREAD_LIBS... -pthread -lgthread-2.0 -lrt -lglib-2.0  
checking for curl/curl.h... (cached) yes
checking for tar archiver... checking for gnutar... (cached) tar
tar
checking for wget... checking for wget... (cached) wget
wget
checking for conic... checking for valid optimization flags... yes
checking size of int *... (cached) 4
checking for __cxa_demangle... (cached) yes
checking for unwind.h... (cached) yes
checking for _Unwind_Backtrace... (cached) yes
checking for gcc -pipe support... yes
checking whether C compiler supports -fprofile-generate... yes
checking whether C++ compiler has -pedantic long long bug... no
checking for correct temporary object destruction order... yes
checking for correct overload resolution with const and templates... no
checking for libIDL-2.0 >= 0.8.0 glib-2.0 gobject-2.0... yes
checking HOST_LIBIDL_CFLAGS... -pthread -I/usr/include/libIDL-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking HOST_LIBIDL_LIBS... -pthread -lIDL-2 -lgobject-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking for glib-2.0 >= 1.3.7 gobject-2.0... yes
checking GLIB_CFLAGS... -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking GLIB_LIBS... -pthread -lgobject-2.0 -lgthread-2.0 -lrt -lglib-2.0  
checking for stdint.h... (cached) yes
checking for inttypes.h... (cached) yes
checking for sys/int_types.h... (cached) no
checking for iwlib.h... (cached) yes
checking for posix_fallocate... yes
checking for GL/glx.h... (cached) yes
checking for fontconfig/fcfreetype.h... (cached) yes
creating ./config.status
creating config/autoconf.mk
creating config/doxygen.cfg
creating gfx/cairo/cairo/src/cairo-features.h
creating netwerk/necko-config.h
netwerk/necko-config.h is unchanged
creating xpcom/xpcom-config.h
xpcom/xpcom-config.h is unchanged
creating xpcom/xpcom-private.h
xpcom/xpcom-private.h is unchanged
gfx/cairo/cairo/src/cairo-features.h is unchanged
configuring in nsprpub
running /bin/sh ./configure  --enable-application=browser --with-dist-prefix=/home/herop/mozilla-2.0/dist --with-mozilla --disable-debug --enable-optimize --cache-file=.././config.cache --srcdir=.
loading cache .././config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for whoami... (cached) /usr/bin/whoami
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking how to run the C preprocessor... (cached) gcc -E
checking for ranlib... (cached) ranlib
checking for as... (cached) /usr/bin/as
checking for ar... (cached) /usr/bin/ar
checking for ld... (cached) /usr/bin/ld
checking for strip... (cached) /usr/bin/strip
checking for windres... no
checking for gcc -pipe support... no
checking whether C compiler supports -fprofile-generate... yes
checking for visibility(hidden) attribute... (cached) yes
checking for visibility pragma support... (cached) yes
checking for perl5... (cached) /usr/bin/perl
checking for dlopen in -ldl... (cached) yes
checking for dlfcn.h... (cached) yes
checking whether gcc needs -traditional... (cached) no
checking for lchown... (cached) yes
checking for strerror... (cached) yes
checking for pthread_create in -lpthreads... no
checking for pthread_create in -lpthread... yes
checking whether gcc accepts -pthread... yes
creating ./config.status
creating Makefile
creating config/Makefile
creating config/autoconf.mk
creating config/nsprincl.mk
creating config/nsprincl.sh
creating config/nspr-config
creating lib/Makefile
creating lib/ds/Makefile
creating lib/libc/Makefile
creating lib/libc/include/Makefile
creating lib/libc/src/Makefile
creating lib/tests/Makefile
creating pkg/Makefile
creating pkg/linux/Makefile
creating pkg/solaris/Makefile
creating pkg/solaris/SUNWpr/Makefile
creating pkg/solaris/SUNWprd/Makefile
creating pr/Makefile
creating pr/include/Makefile
creating pr/include/md/Makefile
creating pr/include/obsolete/Makefile
creating pr/include/private/Makefile
creating pr/src/Makefile
creating pr/src/io/Makefile
creating pr/src/linking/Makefile
creating pr/src/malloc/Makefile
creating pr/src/md/Makefile
creating pr/src/md/unix/Makefile
creating pr/src/memory/Makefile
creating pr/src/misc/Makefile
creating pr/src/threads/Makefile
creating pr/tests/Makefile
creating pr/tests/dll/Makefile
creating pr/src/pthreads/Makefile
configuring in js/src
running /bin/sh ./configure  --enable-application=browser --enable-threadsafe --enable-ctypes --disable-shared-js --with-nspr-cflags='-I/home/herop/mozilla-2.0/dist/include/nspr' --with-nspr-libs='-L/home/herop/mozilla-2.0/dist/lib -lplds4 -lplc4 -lnspr4 -lpthread -ldl' --with-dist-dir=../../dist --prefix=/home/herop/mozilla-2.0/dist --with-sync-build-files=/home/herop/mozilla-2.0 --enable-jemalloc --cache-file=../.././config.cache --srcdir=.
loading cache ../.././config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for gawk... (cached) mawk
checking for perl5... (cached) /usr/bin/perl
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for c++... (cached) c++
checking whether the C++ compiler (c++  ) works... yes
checking whether the C++ compiler (c++  ) is a cross-compiler... no
checking whether we are using GNU C++... (cached) yes
checking whether c++ accepts -g... (cached) yes
checking for ranlib... (cached) ranlib
checking for as... (cached) /usr/bin/as
checking for ar... (cached) ar
checking for ld... (cached) ld
checking for strip... (cached) strip
checking for windres... no
checking whether gcc and cc understand -c and -o together... (cached) yes
checking how to run the C preprocessor... (cached) gcc -E
checking how to run the C++ preprocessor... (cached) c++ -E
checking for sb-conf... no
checking for ve... no
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether ln -s works... (cached) yes
checking for minimum required perl version >= 5.006... 5.010001
checking for full perl installation... yes
checking for python2.7... (cached) /usr/bin/python2.6
checking for doxygen... (cached) :
checking for autoconf... (cached) /usr/bin/autoconf
checking for unzip... (cached) /usr/bin/unzip
checking for zip... (cached) /usr/bin/zip
checking for makedepend... no
checking for xargs... (cached) /usr/bin/xargs
checking for gmake... (cached) /usr/bin/make
checking for X... (cached) libraries , headers 
checking for dnet_ntoa in -ldnet... (cached) no
checking for dnet_ntoa in -ldnet_stub... (cached) no
checking for gethostbyname... (cached) yes
checking for connect... (cached) yes
checking for remove... (cached) yes
checking for shmat... (cached) yes
checking for IceConnectionNumber in -lICE... (cached) yes
checking whether the compiler supports -Wno-invalid-offsetof... yes
checking whether the compiler supports -Wno-variadic-macros... yes
checking whether the compiler supports -Werror=return-type... yes
checking whether ld has archive extraction flags... (cached) yes
checking that static assertion macros used in autoconf tests work... (cached) yes
checking for 64-bit OS... no
checking for Python version >= 2.5 but not 3.x... yes
checking for ANSI C header files... (cached) yes
checking for working const... (cached) yes
checking for mode_t... (cached) yes
checking for off_t... (cached) yes
checking for pid_t... (cached) yes
checking for size_t... (cached) yes
checking for __stdcall... (cached) no
checking for ssize_t... (cached) yes
checking for st_blksize in struct stat... (cached) yes
checking for siginfo_t... (cached) yes
checking for stdint.h... (cached) yes
checking for the size of void*... (cached) 4
checking for the alignment of void*... (cached) 4
checking for the size of double... (cached) 8
checking for int16_t... (cached) yes
checking for int32_t... (cached) yes
checking for int64_t... (cached) yes
checking for int64... (cached) no
checking for uint... (cached) yes
checking for uint_t... (cached) no
checking for uint16_t... (cached) no
checking for uname.domainname... (cached) yes
checking for uname.__domainname... (cached) no
checking for visibility(hidden) attribute... (cached) yes
checking for visibility(default) attribute... (cached) yes
checking for visibility pragma support... (cached) yes
checking For gcc visibility bug with class-level attributes (GCC bug 26905)... (cached) no
checking For x86_64 gcc visibility bug with builtins (GCC bug 20297)... (cached) no
checking for __force_align_arg_pointer__ attribute... (cached) yes
checking for dirent.h that defines DIR... (cached) yes
checking for opendir in -ldir... (cached) no
checking for sys/byteorder.h... (cached) no
checking for compat.h... (cached) no
checking for getopt.h... (cached) yes
checking for sys/bitypes.h... (cached) yes
checking for memory.h... (cached) yes
checking for unistd.h... (cached) yes
checking for gnu/libc-version.h... (cached) yes
checking for nl_types.h... (cached) yes
checking for malloc.h... (cached) yes
checking for X11/XKBlib.h... (cached) yes
checking for io.h... (cached) no
checking for sys/statvfs.h... (cached) yes
checking for sys/statfs.h... (cached) yes
checking for sys/vfs.h... (cached) yes
checking for sys/mount.h... (cached) yes
checking for sys/quota.h... (cached) yes
checking for linux/quota.h... (cached) yes
checking for mmintrin.h... (cached) no
checking for new... (cached) yes
checking for sys/cdefs.h... (cached) yes
checking for linux/perf_event.h... (cached) yes
checking for gethostbyname_r in -lc_r... (cached) no
checking for library containing dlopen... (cached) -ldl
checking for dlfcn.h... (cached) yes
checking for dladdr... (cached) yes
checking for socket in -lsocket... (cached) no
checking for ARM SIMD support in compiler... no
checking for ARM NEON support in compiler... no
checking for pthread_create in -lpthreads... no
checking for pthread_create in -lpthread... yes
checking whether gcc accepts -pthread... yes
checking whether mmap() sees write()s... yes
checking whether gcc needs -traditional... (cached) no
checking for 8-bit clean memcmp... (cached) yes
checking for fchmod... (cached) yes
checking for flockfile... (cached) yes
checking for getc_unlocked... (cached) yes
checking for _getc_nolock... (cached) no
checking for getpagesize... (cached) yes
checking for lchown... (cached) yes
checking for localtime_r... (cached) yes
checking for lstat64... (cached) yes
checking for memmove... (cached) yes
checking for random... (cached) yes
checking for rint... (cached) no
checking for sbrk... (cached) yes
checking for snprintf... (cached) yes
checking for stat64... (cached) yes
checking for statvfs... (cached) yes
checking for statvfs64... (cached) yes
checking for strerror... (cached) yes
checking for strtok_r... (cached) yes
checking for truncate64... (cached) yes
checking for clock_gettime(CLOCK_MONOTONIC) and -lrt... (cached) yes
checking for wcrtomb... (cached) yes
checking for mbrtowc... (cached) yes
checking for res_ninit()... (cached) yes
checking for gnu_get_libc_version()... (cached) yes
checking for iconv in -lc... (cached) yes
checking for iconv()... (cached) yes
checking for iconv() with const input... (cached) no
checking for an implementation of va_copy()... (cached) yes
checking for an implementation of __va_copy()... (cached) yes
checking whether va_lists can be copied by value... (cached) yes
checking for gcc 3.0 ABI... (cached) yes
checking for C++ "explicit" keyword... (cached) yes
checking for C++ "typename" keyword... (cached) yes
checking for modern C++ template specialization syntax support... (cached) yes
checking whether partial template specialization works... (cached) yes
checking whether operators must be re-defined for templates derived from templates... (cached) no
checking whether we need to cast a derived template to pass as its base class... (cached) no
checking whether the compiler can resolve const ambiguities for templates... (cached) yes
checking whether the C++ "using" keyword can change access... (cached) yes
checking whether the C++ "using" keyword resolves ambiguity... (cached) yes
checking for "std::" namespace... (cached) yes
checking whether standard template operator!=() is ambiguous... (cached) unambiguous
checking for C++ reinterpret_cast... (cached) yes
checking for C++ dynamic_cast to void*... (cached) yes
checking whether C++ requires implementation of unused virtual methods... (cached) yes
checking for trouble comparing to zero near std::operator!=()... (cached) no
checking for __thread keyword for TLS variables... (cached) yes
checking for malloc.h... (cached) yes
checking for strndup... (cached) yes
checking for posix_memalign... (cached) yes
checking for memalign... (cached) yes
checking for valloc... (cached) yes
checking for __attribute__((always_inline))... (cached) yes
checking for __attribute__((malloc))... (cached) yes
checking for __attribute__((warn_unused_result))... (cached) yes
checking for __attribute__((noreturn))... (cached) yes
checking for LC_MESSAGES... (cached) yes
checking for localeconv... (cached) yes
checking for valid optimization flags... yes
checking size of int *... (cached) 4
checking for __cxa_demangle... (cached) yes
checking for unwind.h... (cached) yes
checking for _Unwind_Backtrace... (cached) yes
checking for gcc -pipe support... yes
checking whether C compiler supports -fprofile-generate... yes
checking whether C++ compiler has -pedantic long long bug... no
checking for correct temporary object destruction order... yes
checking for correct overload resolution with const and templates... no
checking for tm_zone tm_gmtoff in struct tm... (cached) yes
checking for posix_fallocate... yes
checking for setlocale... (cached) yes
checking for localeconv... (cached) yes
creating ./config.status
creating config/autoconf.mk
creating js-config.h
js-config.h is unchanged
config/autoconf.mk is unchanged
invoking make to create js-config script
make: `js-config' is up to date.
configuring in ctypes/libffi
running /bin/sh ./configure  --disable-shared --enable-static --disable-raw-api --with-pic --cache-file=/home/herop/mozilla-2.0/js/src/ctypes/libffi/config.cache --srcdir=.
configure: loading cache /home/herop/mozilla-2.0/js/src/ctypes/libffi/config.cache
checking build system type... (cached) i686-pc-linux-gnu
checking host system type... (cached) i686-pc-linux-gnu
checking target system type... (cached) i686-pc-linux-gnu
checking for a BSD-compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... (cached) /bin/mkdir -p
checking for gawk... (cached) mawk
checking whether make sets $(MAKE)... (cached) yes
checking for gcc... (cached) gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... (cached) o
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking for style of include used by make... GNU
checking dependency style of gcc... (cached) gcc3
checking dependency style of gcc... (cached) gcc3
checking whether gcc and cc understand -c and -o together... (cached) yes
checking for a sed that does not truncate output... (cached) /bin/sed
checking for grep that handles long lines and -e... (cached) /bin/grep
checking for egrep... (cached) /bin/grep -E
checking for fgrep... (cached) /bin/grep -F
checking for ld used by gcc... (cached) /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... (cached) yes
checking for BSD- or MS-compatible name lister (nm)... (cached) /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... (cached) BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... (cached) 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... (cached) -r
checking for objdump... (cached) objdump
checking how to recognize dependent libraries... (cached) pass_all
checking for ar... (cached) ar
checking for strip... (cached) strip
checking for ranlib... (cached) ranlib
checking command to parse /usr/bin/nm -B output from gcc object... (cached) ok
checking how to run the C preprocessor... (cached) gcc -E
checking for ANSI C header files... (cached) yes
checking for sys/types.h... (cached) yes
checking for sys/stat.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for memory.h... (cached) yes
checking for strings.h... (cached) yes
checking for inttypes.h... (cached) yes
checking for stdint.h... (cached) yes
checking for unistd.h... (cached) yes
checking for dlfcn.h... (cached) yes
checking for objdir... (cached) .libs
checking if gcc supports -fno-rtti -fno-exceptions... (cached) no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... (cached) yes
checking if gcc static flag -static works... (cached) yes
checking if gcc supports -c -o file.o... (cached) yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... no
checking whether to build static libraries... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for sys/mman.h... (cached) yes
checking for mmap... (cached) yes
checking for sys/mman.h... (cached) yes
checking for mmap... (cached) yes
checking whether read-only mmap of a plain file works... (cached) yes
checking whether mmap from /dev/zero works... (cached) yes
checking for MAP_ANON(YMOUS)... (cached) yes
checking whether mmap with MAP_ANON(YMOUS) works... (cached) yes
checking for ANSI C header files... (cached) yes
checking for memcpy... (cached) yes
checking for working alloca.h... (cached) yes
checking for alloca... (cached) yes
checking size of double... (cached) 8
checking size of long double... (cached) 12
checking whether byte ordering is bigendian... (cached) no
checking assembler .cfi pseudo-op support... (cached) yes
checking assembler supports pc related relocs... (cached) yes
checking assembler .ascii pseudo-op support... (cached) yes
checking assembler .string pseudo-op support... (cached) yes
checking whether .eh_frame section should be read-only... (cached) no
checking for __attribute__((visibility("hidden")))... (cached) yes
configure: creating ./config.status
config.status: creating include/Makefile
config.status: creating include/ffi.h
config.status: creating Makefile
config.status: creating testsuite/Makefile
config.status: creating man/Makefile
config.status: creating libffi.pc
config.status: creating fficonfig.h
config.status: fficonfig.h is unchanged
config.status: linking src/x86/ffitarget.h to include/ffitarget.h
config.status: executing depfiles commands
config.status: executing libtool commands
config.status: executing include commands
config.status: executing src commands
config/autoconf.mk is unchanged
```
I also have attached the output here.

---

### Post by kidders on 2011-03-21
Damn... I can't see anything missing. I wonder could be problem be something more basic, like something turned off in about:config.

I'm not sure what's causing that xulrunner-related error, but I doubt it's related. You've had a few versions of Firefox on your box... firefox-bin might belong to an old version that's no longer installed.

Sorry I can't be more helpful. I don't have Firefox 4 on my own box, so I can really only guess at what might be wrong :-(

---

### Post by herophuong on 2011-03-21
I have fount the problem: I don't use .fonts.conf to config my system. I only use gnome-appearance-properties. I will marked this thread as solved. Anyway, thanks for your effort to help me. God bless you.

---

### Post by Razlo on 2011-03-23
I have the same problem with firefox4 installed in /opt. Could you please help me in solving it? I don't know how to fix it :S

---

### Post by herophuong on 2011-03-23
Just edit the file /etc/fonts/fonts.conf (if it doesn't exist, just create one), add these lines at the end and before  </fontconfig> tag:
```
<match target="font"> 
  <edit mode="assign" name="rgba"> 
   <const>rgb</const> 
  </edit> 
 </match> 
 <match target="font"> 
  <edit mode="assign" name="hinting"> 
   <bool>true</bool> 
  </edit> 
 </match> 
 <match target="font"> 
  <edit mode="assign" name="hintstyle"> 
   <const>hintslight</const> 
  </edit> 
 </match> 
<match target="font"> 
    <edit mode="assign" name="lcdfilter"> 
      <const>lcddefault</const> 
    </edit> 
  </match>
```

---

### Post by Razlo on 2011-03-24
I've tried this solution without almost thinking about what I was doing. It didn't work. Thanks anyway, I'll try again when I am less busy.

---

### Post by herophuong on 2011-03-24
This anti-alasing method is not similar to gnome-appearance-properties. And I must admit that this method is a little bit uglier. But you can check that is is anti-alised or not by zoom in the text inside the browser. If it doesn't have any alias, so that the smoothing font engine is doing its job.

About  the above method, you have to restart to get your system to take effect after editing the file.

---

### Post by Razlo on 2011-03-25
I restarted the browser, but not the system, and didn't observe any change. The letters appear with colour pixels in the corners, instead of grey tones.

Although I did it fast, I looked for the font config file in .local, referenced in /etc/fonts/fonts.conf Should I have looked in /local instead of ~/.local ?? I'll give it a try soon.
thanks!

---

