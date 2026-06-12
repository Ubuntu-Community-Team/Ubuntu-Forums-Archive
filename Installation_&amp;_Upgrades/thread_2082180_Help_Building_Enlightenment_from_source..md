---
title: "Help Building Enlightenment from source."
date: 2012-11-08
forum: Installation &amp; Upgrades
---

### Post by eflix1 on 2012-11-08
Hello!. As you may know, recently there was a new release of the Enlightenment 17 desktop, and I wanted to install that latest version to my lubuntu desktop pc. I downloaded all packages suggested by the enlightenment page, built them, and installed them, including the enlightenment package itself. Problems came when I tried to start E17 using the enlightenment_start command from lxdm and nothing happened (It only brings me back to the login screen). Just to see what output do I get I started lxde and from there I executed E17 again, and this is the output:
```

E - PID=14733, valgrind=0
ESTART: 0.00000 [0.00000] - Begin Startup
ESTART: 0.00005 [0.00004] - Signal Trap
ESTART: 0.00006 [0.00001] - Signal Trap Done
ESTART: 0.00011 [0.00005] - Eina Init
ESTART: 0.00024 [0.00013] - Eina Init Done
ESTART: 0.00025 [0.00001] - Determine Prefix
INF<e>e_prefix.c:25 =================================
INF<e>e_prefix.c:26 Enlightenment relocation handling
INF<e>e_prefix.c:27 =================================
INF<e>e_prefix.c:28 PREFIX:  /usr/local
INF<e>e_prefix.c:29 BINDIR:  /usr/local/bin
INF<e>e_prefix.c:30 LIBDIR:  /usr/local/lib
INF<e>e_prefix.c:31 DATADIR: /usr/local/share/enlightenment
INF<e>e_prefix.c:32 LOCALE:  /usr/local/share/locale
INF<e>e_prefix.c:33 =================================
ESTART: 0.00036 [0.00012] - Determine Prefix Done
ESTART: 0.00038 [0.00001] - Environment Variables
ESTART: 0.00040 [0.00002] - Environment Variables Done
ESTART: 0.00040 [0.00001] - Parse Arguments
ESTART: 0.00041 [0.00001] - Parse Arguments Done
ESTART: 0.00042 [0.00001] - Eet Init
ESTART: 0.00169 [0.00127] - Eet Init Done
ESTART: 0.00170 [0.00001] - Ecore Init
ESTART: 0.00179 [0.00008] - Ecore Init Done
ESTART: 0.00180 [0.00001] - EIO Init
ESTART: 0.00184 [0.00004] - EIO Init Done
ESTART: 0.00185 [0.00001] - Ecore Event Handlers
ESTART: 0.00188 [0.00003] - Ecore Event Handlers Done
ESTART: 0.00188 [0.00001] - Ecore_File Init
ESTART: 0.00248 [0.00060] - Ecore_File Init Done
ESTART: 0.00250 [0.00002] - Ecore_Con Init
ESTART: 0.00381 [0.00132] - Ecore_Con Init Done
ESTART: 0.00383 [0.00001] - Ecore_Ipc Init
ESTART: 0.00384 [0.00001] - Ecore_Ipc Init Done
ESTART: 0.00389 [0.00004] - Ecore_X Init
ESTART: 0.00885 [0.00497] - Ecore_X Init Done
ESTART: 0.00890 [0.00005] - Ecore_IMF Init
ESTART: 0.00981 [0.00090] - Ecore_IMF Init Done
ESTART: 0.00985 [0.00004] - Ecore_Evas Init
ESTART: 0.01017 [0.00032] - Ecore_Evas Init Done
ESTART: 0.01023 [0.00006] - Elementary Init
ESTART: 0.01288 [0.00264] - Elementary Init Done
ESTART: 0.01292 [0.00004] - Ecore_Evas Engine Check
ESTART: 0.01293 [0.00001] - Ecore_Evas Engine Check Done
ESTART: 0.01294 [0.00001] - Edje Init
ESTART: 0.01295 [0.00001] - Edje Init Done
ESTART: 0.01296 [0.00001] - E Intl Init
ESTART: 0.01301 [0.00005] - E Intl Init Done
ESTART: 0.01302 [0.00001] - E_Alert Init
ESTART: 0.01303 [0.00001] - E_Alert Init Done
ESTART: 0.01304 [0.00001] - E_Xinerama Init
INF<e>e_xinerama.c:178 ======================= screens:
INF<e>e_xinerama.c:184 E17 INIT: XINERAMA CHOSEN: [0][0], 1280x1024+0+0
ESTART: 0.01322 [0.00019] - E_Xinerama Init Done
ESTART: 0.01324 [0.00001] - E_Hints Init
ESTART: 0.01405 [0.00082] - E_Hints Init Done
ESTART: 0.01407 [0.00002] - E_Configure Init
ESTART: 0.01416 [0.00009] - E_Configure Init Done
ESTART: 0.01418 [0.00001] - E Directories Init
ESTART: 0.01431 [0.00013] - E Directories Init Done
ESTART: 0.01432 [0.00001] - E_Filereg Init
ESTART: 0.01433 [0.00001] - E_Filereg Init Done
ESTART: 0.01434 [0.00001] - E_Config Init
ESTART: 0.01635 [0.00200] - E_Config Init Done
ESTART: 0.01639 [0.00005] - E_Randr Init
ERR<>e_randr.c:103 safety check failed: ecore_x_randr_query() is false
<<<< Enlightenment Error >>>>
Enlightenment cannot initialize E_Randr!

ESTART: 0.01645 [0.00005] - E_Randr Init Done
ESTART: 0.01646 [0.00001] - E_Env Init
ESTART: 0.01646 [0.00001] - E_Env Init Done
ESTART: 0.01649 [0.00003] - E_Scale Init
ESTART: 0.01652 [0.00003] - E_Scale Init Done
ESTART: 0.01653 [0.00001] - E_Pointer Init
ESTART: 0.01655 [0.00001] - E_Pointer Init Done
ESTART: 0.01655 [0.00001] - E Paths Init
ESTART: 0.01660 [0.00005] - E Paths Init Done
ESTART: 0.01661 [0.00001] - E_Ipc Init
ESTART: 0.01683 [0.00022] - E_Ipc Init Done
ESTART: 0.01684 [0.00002] - E_Font Init
ESTART: 0.01686 [0.00001] - E_Font Init Done
ESTART: 0.01687 [0.00001] - E_Font Apply
ESTART: 0.01688 [0.00001] - E_Font Apply Done
ESTART: 0.01689 [0.00001] - E_Canvas Recache
ESTART: 0.01691 [0.00002] - E_Canvas Recache Done
ESTART: 0.01692 [0.00001] - E_Theme Init
ESTART: 0.01696 [0.00005] - E_Theme Init Done
ESTART: 0.01697 [0.00001] - E_Moveresize Init
ESTART: 0.01699 [0.00002] - E_Moveresize Init Done
ESTART: 0.01700 [0.00001] - E_Intl Post Init
ESTART: 0.01707 [0.00008] - E_Intl Post Init Done
ESTART: 0.01708 [0.00001] - Efreet Init
ESTART: 0.02069 [0.00360] - Efreet Init Done
ESTART: 0.02076 [0.00007] - Test File Format Support
<<<< Enlightenment Error >>>>
Enlightenment found Evas can't load SVG files. Check Evas has SVG loader support.

<<<< Enlightenment Error >>>>
Enlightenment found Evas can't load the 'Sans' font. Check Evas has fontconfig
support and system fontconfig defines a 'Sans' font.

E17: Begin Shutdown Procedure!

```
I notided in the last errors that evas doesn't have all the features enlightment needs, svg and fontconfig support. Then I went to synaptic and I saw that the dev packages for svg and fontconfig are already installed (librsvg2-dev and libfontconfig1-dev). So I tried to compile evas again, but when I execute the ./configure command I saw that still there wasnt support for svg. These are the configuration options of my configure command con the evas folder:

```

------------------------------------------------------------------------
evas 1.7.1
------------------------------------------------------------------------

Configuration Options Summary:

Engines:
  Software Memory Buffer.....: yes
  Software X11...............: yes (Xlib: yes) (XCB: no)
  OpenGL X11.................: yes (Xlib: yes) (XCB: no) (GLES: no) (SGX: no) (s3c6410: no)
  Software GDI...............: no
  Software DirectDraw........: no
  Direct3d...................: no
  OpenGL SDL.................: no 

  OpenGL Cocoa...............: no
  Software Framebuffer.......: yes
  DirectFB...................: no
  PSL1GHT....................: no
  Software 8bit grayscale....: no
  Software 16bit ............: no
  Software 16bit X11.........: no
  Software 16bit WinCE.......: no
  Software 16bit SDL.........: no (primitive: no)
  Wayland Shm................: yes
  Wayland Egl................: no

Image Loaders:
  BMP.....................: yes
  EDB.....................: no
  EET.....................: yes
  GENERIC.................: yes
  GIF.....................: no
  ICO.....................: yes
  JPEG....................: yes (region: no)
  PMAPS...................: yes
  PNG.....................: yes
  PSD.....................: yes
  SVG.....................: no
  TGA.....................: yes
  TIFF....................: no
  WBMP....................: yes
  XPM.....................: yes

Font Sourcing Systems:
  EET.....................: yes

Font Searching Systems:
  Fontconfig..............: yes

Font Rendering Helpers:
  Fribidi.................: no
  Harfbuzz................: no
  liblinebreak............: yes

CPU Specific Extensions:
  Fallback C Code.........: yes
  MMX.....................: yes
  SSE.....................: yes
  SSE3....................: yes
  ALTIVEC.................: no
  NEON....................: no
  Thread Support..........: yes

Features:
  MAGIC_DEBUG.............: yes
  Cache Server............: no
  Cache Server 2..........: yes

  Threaded Pipe Rendering.: no
  Async Events............: yes
  Async Image Preload.....: yes

  Pixman..................: no
  Pixman Fonts............: no
  Pixman Rects............: no
  Pixman Lines............: no
  Pixman Polygons.........: no
  Pixman Images...........: no
  Pixman Image ScaleSample: no

  Tiled 32BPP rotate......: no

ARGB Software Engine Options:
  Sampling Scaler.........: yes
  Smooth Scaler...........: yes
  YUV Converter...........: yes

ARGB Conversion Options:
  Smaller Dither Mask.....: no
  Line Dither Mask........: no
  No Dither Mask for 16bpp: no
  8bpp RGB 332............: yes
  8bpp RGB 666............: yes
  8bpp RGB 232............: yes
  8bpp RGB 222............: yes
  8bpp RGB 221............: yes
  8bpp RGB 121............: yes
  8bpp RGB 111............: yes
  8bpp Grayscale (256)....: yes
  8bpp Grayscale (16).....: yes
  8bpp Grayscale 64-pal...: yes
  16bpp RGB 565...........: yes
  16bpp BGR 565...........: yes
  16bpp RGB 555...........: yes
  16bpp RGB 444...........: yes
  16bpp RGB 565 (444 ipaq): yes
  16bpp Rotation 0........: yes
  16bpp Rotation 90.......: yes
  16bpp Rotation 180......: yes
  16bpp Rotation 270......: yes
  24bpp RGB 888...........: yes
  24bpp BGR 888...........: yes
  24bpp RGB 666 (666 ezx).: yes
  32bpp RGB 8888..........: yes
  32bpp RGBX 8888.........: yes
  32bpp BGR 8888..........: yes
  32bpp BGRX 8888.........: yes
  32bpp RGB 666 (666 ezx).: yes
  32bpp Rotation 0........: yes
  32bpp Rotation 90.......: yes
  32bpp Rotation 180......: yes
  32bpp Rotation 270......: yes

Documentation.............: no
Examples..................: install:yes build:no
Tests.....................: no
Coverage..................: no

Compilation............: make (or gmake)
  CPPFLAGS.............: 
  CFLAGS...............: -g -O2
  CXXFLAGS.............: -g -O2
  LDFLAGS..............: 

Installation...........: make install (as root if needed, with 'su' or 'sudo')
  prefix...............: /usr/local


```

So, what other packages should I install to grant svg support to evas?  
Help! Thank you and sorry if this is the wrong forum for this post!.

---

### Post by Frogs Hair on 2012-11-08
I have used this PPA on 11.10 and 12.04 and once installed E17 shows up in the login selection. I have not tried to build it from source. If you build it successfully from source you will have to check for updates and install them mutually.   ```
sudo add-apt-repository ppa:hannes-janetzek/enlightenment-svn
``````
sudo apt-get update
``` ```
sudo apt-get install e17
```

---

### Post by eflix1 on 2012-11-11
Ok, I'm gonna install that package. Thank you!.

---

### Post by Frogs Hair on 2012-11-11
Clean up anything from your build attempt before proceeding or you may have broken packages. There is another possible option at the link which is a Ubuntu based distro.  [http://www.bodhilinux.com/](http://www.bodhilinux.com/)

---

