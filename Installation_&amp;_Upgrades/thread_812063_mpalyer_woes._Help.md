---
title: "mpalyer woes. Help"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by arasraj on 2008-05-29
I am relatively new to linux (running ubuntu 8.04) and trying to install mplayer. How ever the configure step always errors when trying the find the X11 extension XShape. I checked in /usr/include/X11/extension and shape.h is there. The error i get is:

> 
Detected operating system: Linux
Detected host architecture: i386
Checking for cc version ... 4.2.3, ok
Checking for host cc ... cc
Checking for cross compilation ... no
Checking for CPU vendor ... GenuineIntel (15:0:7)
Checking for CPU type ... Intel(R) Pentium(R) 4 CPU 1400MHz
Checking for kernel support of mmx ... yes
Checking for kernel support of mmxext ... yes
Checking for kernel support of sse ... yes
Checking for kernel support of sse2 ... yes
Checking for kernel support of cmov ... yes
Checking for mtrr support ... yes
Checking for GCC & CPU optimization abilities ... native
Checking for assembler support of -pipe option ... yes
Checking for compiler support of named assembler arguments ... yes
Checking for assembler (as ) ... ok
Checking for .align is a power of two ... no
Checking for Linux kernel version ... 2.6.24-17-generic, ok
Checking for -lposix ... no
Checking for -lm ... yes
Checking for langinfo ... yes
Checking for language ... using en (man pages: en )
Checking for enable sighandler ... yes
Checking for runtime cpudetection ... no
Checking for restrict keyword ... __restrict
Checking for __builtin_expect ... yes
Checking for kstat ... no
Checking for posix4 ... no
Checking for lrintf ... yes
Checking for mkstemp ... yes
Checking for nanosleep ... yes
Checking for socklib ... yes
Checking for inet_pton() ... yes (using )
Checking for network ... yes
Checking for inttypes.h (required) ... yes
Checking for int_fastXY_t in inttypes.h ... yes
Checking for word size ... 32
Checking for malloc.h ... yes
Checking for memalign() ... yes
Checking for alloca.h ... yes
Checking for mman.h ... yes
Checking for dynamic loader ... yes
Checking for dynamic a/v plugins support ... no
Checking for pthread ... yes (using -lpthread)
Checking for w32threads ... no (using pthread instead)
Checking for rpath ... no
Checking for iconv ... yes
Checking for soundcard.h ... yes (sys/soundcard.h)
Checking for sys/dvdio.h ... no
Checking for sys/cdio.h ... no
Checking for linux/cdrom.h ... yes
Checking for dvd.h ... no
Checking for termcap ... no
Checking for termios ... yes (sys/termios.h)
Checking for shm ... yes
Checking for strsep() ... yes
Checking for vsscanf() ... yes
Checking for swab() ... yes
Checking for POSIX select() ... yes
Checking for gettimeofday() ... yes
Checking for glob() ... yes
Checking for setenv() ... yes
Checking for sys/sysinfo.h ... yes
Checking for pkg-config ... yes
Checking for Samba support (libsmbclient) ... no
Checking for tdfxfb ... no
Checking for s3fb ... no
Checking for tdfxvid ... no
Checking for xvr100 ... no
Checking for tga ... yes
Checking for md5sum support ... yes
Checking for bl ... no
Checking for DirectFB ... no
Checking for X11 headers presence ... yes
Checking for X11 ... yes
Checking for DPMS ... yes (using Xdpms 4)
Checking for Xv ... no
Checking for XvMC ... no
Checking for Xinerama ... yes
Checking for Xxf86vm ... yes
Checking for XF86keysym ... yes
Checking for DGA ... yes (using DGA 2.0)
Checking for 3dfx ... no
Checking for OpenGL ... no
Checking for VIDIX ... yes (internal)
Checking for /dev/mga_vid ... no
Checking for xmga ... no
Checking for GGI ... no
Checking for GGI extension: libggiwmh ... no
Checking for AA ... no
Checking for CACA ... no
Checking for SVGAlib ... no
Checking for FBDev ... yes
Checking for DVB ... no
Checking for DVB HEAD ... yes
Checking for zr ... no
Checking for PNG support ... yes
Checking for JPEG support ... no
Checking for PNM support ... yes
Checking for GIF support ... no
Checking for VESA support ... no
Checking for SDL ... no
Checking for NAS ... no
Checking for DXR2 ... no
Checking for DXR3/H+ ... no
Checking for IVTV TV-Out ... no
Checking for V4L2 MPEG Decoder ... yes
Checking for OSS Audio ... yes
Checking for aRts ... no
Checking for EsounD ... no
Checking for Polyp ... no
Checking for JACK ... no
Checking for OpenAL ... no
Checking for ALSA audio ... no
Checking for Sun audio ... no
Checking for VCD support ... yes
Checking for dvdread ... yes (internal)
Checking for internal libdvdcss ... yes
Checking for cdparanoia ... no
Checking for libcdio ... no
Checking for bitmap font support ... yes
Checking for freetype >= 2.0.9 ... yes
Checking for fontconfig ... yes
Checking for SSA/*** support ... yes
Checking for fribidi with charsets ... no
Checking for ENCA ... no
Checking for zlib ... yes
Checking for RTC ... yes
Checking for liblzo2 support ... no
Checking for mad support ... no
Checking for Twolame ... no
Checking for Toolame ... no
Checking for OggVorbis support ... yes (internal Tremor)
Checking for libspeex (version >= 1.1 required) ... no
Checking for OggTheora support ... yes
Checking for internal mp3lib support ... yes
Checking for internal liba52 support ... yes
Checking for libdca support ... no
Checking for internal libmpeg2 support ... yes
Checking for libmpcdec (musepack, version >= 1.2.1 required) ... no
Checking for FAAC (AAC encoder) support ... no (in libavcodec: )
Checking for FAAD2 (AAC) support ... yes (internal floating-point)
Checking for LADSPA plugin support ... no
Checking for Win32 codecs ... yes (using /usr/lib/win32)
Checking for XAnim codecs ... yes (using /usr/lib/win32)
Checking for RealPlayer codecs ... yes (using /usr/lib/win32)
Checking for QuickTime codecs ... yes
Checking for Nemesi Streaming Media libraries ... no
Checking for LIVE555 Streaming Media libraries ... yes (using /usr/local/lib/live)
Checking for FFmpeg libavutil ... yes (static)
Checking for FFmpeg libavcodec ... yes (static)
Checking for FFmpeg libavformat ... yes (static)
Checking for FFmpeg libpostproc ... yes (static)
Checking for libamr narrowband ... no
Checking for libamr wideband ... no
Checking for libdv-0.9.5+ ... no
Checking for XviD ... no
Checking for x264 ... no (in libavcodec: no)
Checking for libnut ... no
Checking for libmp3lame (for mencoder) ... no
Checking for mencoder ... yes
Checking for fastmemcpy ... yes
Checking for UniquE RAR File Library ... yes
Checking for TV interface ... yes
Checking for Video 4 Linux TV interface ... no
Checking for Video 4 Linux 2 TV interface ... no
Checking for TV teletext interface ... no
Checking for Radio interface ... no
Checking for Capture for Radio interface ... no
Checking for Video 4 Linux 2 Radio interface ... no
Checking for Video 4 Linux Radio interface ... no
Checking for Video 4 Linux 2 MPEG PVR interface ... no
Checking for audio select() ... yes
Checking for ftp ... yes
Checking for vstream client ... no
Checking for byte order ... failed to autodetect byte order, defaulting to little-endian
Checking for OSD menu ... yes
Checking for Subtitles sorting ... yes
Checking for XMMS inputplugin support ... no
Checking for inet6 ... no
Checking for gethostbyname2 ... no
Checking for GUI ... yes
Checking for XShape extension ...
Error: The GUI requires the X11 extension XShape (which was not found).

Check "configure.log" if you do not understand why it failed.


I have searched for this problem everywhere and cannot find a solution. Any help is greatly appreciated.

---

### Post by Pumalite on 2008-05-29
Why didn't you install through Synaptic?

---

### Post by arasraj on 2008-05-29
I am trying to install a program called PHPMotion which needs Mplayer.  I was following instructions of the forum of the PHPMotion site.

---

### Post by Pumalite on 2008-05-29
Start a new thread with a more suitable title.

---

### Post by andrew.46 on 2008-05-31
A lot of the installation information is not very Ubuntu-specific and MPlayer can be a little dissicult to compile. Have a look at an Ubuntu specific walk-through that should have you set fairly quickly:

[http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

Bear in mind that this is the *subversion* mplayer.

     Andrew

---

### Post by W3ird_N3rd on 2008-06-05
Add --enable-xshape for compiling. Not a clue why but it works.

After you made a .deb (if you're going to) you will also find you cannot install it because it requires libconfhelper-perl. This package was dropped in Hardy because it was an orphan. Either someone at Ubuntu thought it would be funny to drop a package that people still need, or mplayer devs have been too slow to remove the dependency. Either way, get the Gutsy libconfhelper-perl here: [http://packages.ubuntu.com/gutsy/libconfhelper-perl](http://packages.ubuntu.com/gutsy/libconfhelper-perl). You can simply install it on Hardy.

By the way Pumalite: installing with Synaptic is not always an option, that version won't seek through h.264 transportstream files. I believe it didn't seek through AVI files either, but that doesn't bother me as much. On earlier Ubuntu versions (e.g. Feisty) I also always had to compile mplayer from source because that version didn't support widescreen displays properly. IMHO, it would be a good thing if the Ubuntu devs would drop the RC's altogether and just compile whatever SVN is available at distro release time. The RC's are simply too old, and SVN is usually quite stable.

---

### Post by Pumalite on 2008-06-05
Thanks for the info.

---

### Post by arasraj on 2008-06-11
thanks a lot. worked like a charm.

---

