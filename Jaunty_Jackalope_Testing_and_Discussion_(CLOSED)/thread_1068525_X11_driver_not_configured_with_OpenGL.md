---
title: "X11 driver not configured with OpenGL"
date: 2009-02-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nullack on 2009-02-13
Anyone else having problems with running SDL? In relation to this bug:

[https://bugs.launchpad.net/ubuntu/+bug/328932](https://bugs.launchpad.net/ubuntu/+bug/328932)

I'm not quite sure whats going on with this and how to debug it further.

---

### Post by Alejandro Nova on 2009-02-13
I got the same problem.

Fixed it with a quick:

```
1. Download the tarball from http://www.libsdl.org.
2. # tar xvfz [tarball]
3. # ./configure --prefix=/usr && make && make install
```

This is definitely a packaging issue, and that fact makes it a quickly fixable bug.

---

### Post by Nullack on 2009-02-13
Excellent, thanks

---

### Post by n3had on 2009-02-14
I got this error while compiling.. 

```
Generating dependencies for ./src/SDL_fatal.c
Generating dependencies for ./src/audio/SDL_audio.c
Generating dependencies for ./src/audio/SDL_audiocvt.c
Generating dependencies for ./src/audio/SDL_audiodev.c
Generating dependencies for ./src/audio/SDL_mixer.c
Generating dependencies for ./src/audio/SDL_mixer_MMX.c
Generating dependencies for ./src/audio/SDL_mixer_MMX_VC.c
Generating dependencies for ./src/audio/SDL_mixer_m68k.c
Generating dependencies for ./src/audio/SDL_wave.c
Generating dependencies for ./src/cdrom/SDL_cdrom.c
Generating dependencies for ./src/cpuinfo/SDL_cpuinfo.c
Generating dependencies for ./src/events/SDL_active.c
Generating dependencies for ./src/events/SDL_events.c
Generating dependencies for ./src/events/SDL_expose.c
Generating dependencies for ./src/events/SDL_keyboard.c
Generating dependencies for ./src/events/SDL_mouse.c
Generating dependencies for ./src/events/SDL_quit.c
Generating dependencies for ./src/events/SDL_resize.c
Generating dependencies for ./src/file/SDL_rwops.c
Generating dependencies for ./src/stdlib/SDL_getenv.c
Generating dependencies for ./src/stdlib/SDL_iconv.c
Generating dependencies for ./src/stdlib/SDL_malloc.c
Generating dependencies for ./src/stdlib/SDL_qsort.c
Generating dependencies for ./src/stdlib/SDL_stdlib.c
Generating dependencies for ./src/stdlib/SDL_string.c
Generating dependencies for ./src/thread/SDL_thread.c
Generating dependencies for ./src/timer/SDL_timer.c
Generating dependencies for ./src/video/SDL_RLEaccel.c
Generating dependencies for ./src/video/SDL_blit.c
Generating dependencies for ./src/video/SDL_blit_0.c
Generating dependencies for ./src/video/SDL_blit_1.c
Generating dependencies for ./src/video/SDL_blit_A.c
Generating dependencies for ./src/video/SDL_blit_N.c
Generating dependencies for ./src/video/SDL_bmp.c
Generating dependencies for ./src/video/SDL_cursor.c
Generating dependencies for ./src/video/SDL_gamma.c
Generating dependencies for ./src/video/SDL_pixels.c
Generating dependencies for ./src/video/SDL_stretch.c
Generating dependencies for ./src/video/SDL_surface.c
Generating dependencies for ./src/video/SDL_video.c
Generating dependencies for ./src/video/SDL_yuv.c
Generating dependencies for ./src/video/SDL_yuv_mmx.c
Generating dependencies for ./src/video/SDL_yuv_sw.c
Generating dependencies for ./src/joystick/SDL_joystick.c
Generating dependencies for ./src/video/dummy/SDL_nullevents.c
Generating dependencies for ./src/video/dummy/SDL_nullmouse.c
Generating dependencies for ./src/video/dummy/SDL_nullvideo.c
Generating dependencies for ./src/audio/disk/SDL_diskaudio.c
Generating dependencies for ./src/audio/dummy/SDL_dummyaudio.c
Generating dependencies for ./src/loadso/dlopen/SDL_sysloadso.c
Generating dependencies for ./src/audio/dsp/SDL_dspaudio.c
Generating dependencies for ./src/audio/dma/SDL_dmaaudio.c
Generating dependencies for ./src/audio/alsa/SDL_alsa_audio.c
Generating dependencies for ./src/audio/esd/SDL_esdaudio.c
Generating dependencies for ./src/audio/pulse/SDL_pulseaudio.c
Generating dependencies for ./src/audio/nas/SDL_nasaudio.c
Generating dependencies for ./src/video/x11/SDL_x11dga.c
Generating dependencies for ./src/video/x11/SDL_x11dyn.c
Generating dependencies for ./src/video/x11/SDL_x11events.c
Generating dependencies for ./src/video/x11/SDL_x11gamma.c
Generating dependencies for ./src/video/x11/SDL_x11gl.c
Generating dependencies for ./src/video/x11/SDL_x11image.c
Generating dependencies for ./src/video/x11/SDL_x11modes.c
Generating dependencies for ./src/video/x11/SDL_x11mouse.c
Generating dependencies for ./src/video/x11/SDL_x11video.c
Generating dependencies for ./src/video/x11/SDL_x11wm.c
Generating dependencies for ./src/video/x11/SDL_x11yuv.c
Generating dependencies for ./src/video/Xext/Xxf86dga/XF86DGA.c
Generating dependencies for ./src/video/Xext/Xxf86dga/XF86DGA2.c
Generating dependencies for ./src/video/dga/SDL_dgaevents.c
Generating dependencies for ./src/video/dga/SDL_dgamouse.c
Generating dependencies for ./src/video/dga/SDL_dgavideo.c
Generating dependencies for ./src/video/Xext/Xxf86vm/XF86VMode.c
Generating dependencies for ./src/video/Xext/Xv/Xv.c
Generating dependencies for ./src/video/Xext/Xinerama/Xinerama.c
Generating dependencies for ./src/video/Xext/XME/xme.c
Generating dependencies for ./src/video/fbcon/SDL_fb3dfx.c
Generating dependencies for ./src/video/fbcon/SDL_fbelo.c
Generating dependencies for ./src/video/fbcon/SDL_fbevents.c
Generating dependencies for ./src/video/fbcon/SDL_fbmatrox.c
Generating dependencies for ./src/video/fbcon/SDL_fbmouse.c
Generating dependencies for ./src/video/fbcon/SDL_fbriva.c
Generating dependencies for ./src/video/fbcon/SDL_fbvideo.c
Generating dependencies for ./src/video/directfb/SDL_DirectFB_events.c
Generating dependencies for ./src/video/directfb/SDL_DirectFB_video.c
Generating dependencies for ./src/video/directfb/SDL_DirectFB_yuv.c
Generating dependencies for ./src/thread/pthread/SDL_systhread.c
Generating dependencies for ./src/thread/pthread/SDL_syssem.c
Generating dependencies for ./src/thread/pthread/SDL_sysmutex.c
Generating dependencies for ./src/thread/pthread/SDL_syscond.c
Generating dependencies for ./src/joystick/linux/SDL_sysjoystick.c
Generating dependencies for ./src/cdrom/linux/SDL_syscdrom.c
Generating dependencies for ./src/timer/unix/SDL_systimer.c
make: Nothing to be done for `all'.
/bin/bash ./build-scripts/mkinstalldirs /usr/bin
/usr/bin/install -c -m 755 sdl-config /usr/bin/sdl-config
/usr/bin/install: cannot create regular file `/usr/bin/sdl-config': Permission denied
make: *** [install-bin] Error 1

```

---

### Post by jocko on 2009-02-14
> **n3had said:**
> I got this error while compiling.. 

```
/bin/bash ./build-scripts/mkinstalldirs /usr/bin
/usr/bin/install -c -m 755 sdl-config /usr/bin/sdl-config
[COLOR=Red]/usr/bin/install: cannot create regular file `/usr/bin/sdl-config': Permission denied[/COLOR]
make: *** [install-bin] Error 1

```

You need to run the "make install" command with root permissions:
```
[COLOR=Red]sudo[/COLOR] make install
```Or if you want to configure, compile with one command (you'll be asked for a password after the compile):
```
./configure --prefix=/usr && make &&[COLOR=Red] sudo[/COLOR] make install
```

---

### Post by n3had on 2009-02-14
I thought i'll compile first and then install... 
```
./configure --prefix=/usr && make
```


I got a different error now...
```
checking for atof... yes
checking for strcmp... yes
checking for strncmp... yes
checking for _stricmp... no
checking for strcasecmp... yes
checking for _strnicmp... no
checking for strncasecmp... yes
checking for sscanf... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for iconv... yes
checking for sigaction... yes
checking for setjmp... yes
checking for nanosleep... yes
checking for libiconv_open in -liconv... no
checking for pow in -lm... yes
checking for GCC -fvisibility=hidden option... yes
checking for dlopen... yes
checking for dlopen in -lc... no
checking for dlopen in -ldl... yes
checking for dlvsym in -ldl... yes
checking altivec.h usability... no
checking altivec.h presence... no
checking for altivec.h... no
checking for Altivec with GCC -maltivec option... no
checking for Altivec with GCC -faltivec option... no
checking for OSS audio support... yes
checking for dmedia audio support... no
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 0.9.0... found.
checking for snd_ctl_open in -lasound... yes
-- /usr/lib/libasound.so.* -> libasound.so.2
checking for artsc-config... no
checking for esd-config... /usr/bin/esd-config
checking for ESD - version >= 0.2.8... yes
ls: cannot access -lesd: No such file or directory
ls: cannot access -laudiofile: No such file or directory
-- -lesd -laudiofile -> 
checking for pkg-config... /usr/bin/pkg-config
checking for PulseAudio 0.9 support... yes
-- /usr/lib/libpulse-simple.so.* -> libpulse-simple.so.0
checking audio/audiolib.h usability... yes
checking audio/audiolib.h presence... yes
checking for audio/audiolib.h... yes
checking for AuOpenServer in -laudio... yes
checking nas/audiolib.h usability... no
checking nas/audiolib.h presence... no
checking for nas/audiolib.h... no
checking for AuOpenServer in -lnas... no
checking for NAS audio support... yes
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
-- dynamic libX11 -> libX11.so.6
-- dynamic libX11ext -> libXext.so.6
checking for X11/extensions/Xrandr.h... yes
-- dynamic libXrender -> libXrender.so.1
-- dynamic libXrandr -> libXrandr.so.2
checking for X11/extensions/dpms.h... yes
checking for framebuffer console support... yes
checking for getpagesize... yes
checking for directfb-config... /usr/bin/directfb-config
checking for DirectFB 0.9.15 support... yes
checking for PlayStation 2 GS support... no
checking for SVGAlib (1.4.0+) support... no
checking for libVGL support... no
checking for wscons support... no
checking for OpenGL (GLX) support... yes
checking for Linux 2.4 unified input interface... yes
checking for Touchscreen library support... no
checking for hid_init in -lusbhid... no
checking usb.h usability... no
checking usb.h presence... no
checking for usb.h... no
checking libusb.h usability... no
checking libusb.h presence... no
checking for libusb.h... no
checking for hid_init in -lusb... no
checking for usbhid... no
checking for pthreads... yes
checking for recursive mutexes... yes
checking for pthread semaphores... yes
checking linux/version.h usability... yes
checking linux/version.h presence... yes
checking for linux/version.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating sdl-config
config.status: creating SDL.spec
config.status: creating SDL.qpg
config.status: creating sdl.pc
config.status: creating include/SDL_config.h
config.status: include/SDL_config.h is unchanged
config.status: executing default commands
./config.status: line 1035: build-deps: Permission denied

```

---

### Post by n3had on 2009-02-14
and is this the tarball i am asupposed to download?

[http://www.libsdl.org/release/SDL-1.2.13.tar.gz](http://www.libsdl.org/release/SDL-1.2.13.tar.gz) 

the stable one?


UPDATE:
```
sudo ./configure --prefix=/usr
```
```
make
```
```
sudo make isntall
```

supertuxkart running now!!! cheers

n3had

---

### Post by jocko on 2009-02-14
> **n3had said:**
> and is this the tarball i am asupposed to download?

[http://www.libsdl.org/release/SDL-1.2.13.tar.gz](http://www.libsdl.org/release/SDL-1.2.13.tar.gz) 

the stable one?


UPDATE:
```
sudo ./configure --prefix=/usr
``````
make
``````
sudo make isntall
```supertuxkart running now!!! cheers

n3had

Don't use sudo for running the configure script. That's what's messing up your permissions, causing you to fail.
Only the "make install" command require sudo.

---

