---
title: "ImageMagick png support"
date: 2008-04-17
forum: Installation &amp; Upgrades
---

### Post by rompstar420 on 2008-04-17
I have ImageMagick installed, Ubuntu 7.10, but I don't think support for png files is working and I would like to begin by checking to see if the default configuration supports .png images, how do I check for that ?

And if it does not support it, how can I change it so that .png support is added ?

Thanks in advice.

The reason why I ask is, that I use a Gallery2 software for my picture gallery that I run off of my home server and when I made a watermark using a .png file, that is not being applied to the images and I am thinking that is because the .png support is not turned ON in ImageMagick.

---

### Post by noynac on 2008-04-17
> **rompstar420 said:**
> I have ImageMagick installed, Ubuntu 7.10, but I don't think support for png files is working and I would like to begin by checking to see if the default configuration supports .png images, how do I check for that ?

And if it does not support it, how can I change it so that .png support is added ?

Thanks in advice.

The reason why I ask is, that I use a Gallery2 software for my picture gallery that I run off of my home server and when I made a watermark using a .png file, that is not being applied to the images and I am thinking that is because the .png support is not turned ON in ImageMagick.

ImageMagick is a set of commandline tools as explained at:

[http://www.imagemagick.org/script/index.php](http://www.imagemagick.org/script/index.php)

The formats supported by ImageMagic include PNG:

[http://www.imagemagick.org/script/formats.php](http://www.imagemagick.org/script/formats.php)

I am not familiar with Gallery2, but you do not turn on PNG support in ImageMagick.  

If you want to check to see if ImageMagick is installed, either check Synaptic or type "import -help" (without quotes) in a terminal window

---

### Post by pmsaue0 on 2008-07-10
I am having the same issue -- not having PNG support.

[COLOR="Green"]convert -list configure[/COLOR]
shows this in the row [COLOR="Indigo"]DELEGATES: freetype zlib[/COLOR]
the delegate [COLOR="Indigo"]libpng[/COLOR] (or something like it) should be there

[COLOR="green"]convert -list format[/COLOR]
does not indicate PNG support of any kind

This is the installation process I went through:
[COLOR="green"]sudo apt-get update
sudo apt-get build-dep imagemagick
sudo aptitude install imagemagick[/COLOR]

[COLOR="green"]convert -version[/COLOR]
correctly states: V[COLOR="Indigo"]ersion: ImageMagick 6.4.2[/COLOR]

No PNG!  Is there a way to install a PNG delegate library and still use aptitude?

It seems that the version of imagemagick that aptitude is referencing does not have the correct/complete delegate libraries

Thoughts?

---

### Post by unutbu on 2008-07-10
I think the package you need is libpng12-0.
```

% apt-cache show imagemagick
Package: imagemagick
Priority: optional
Section: graphics
Installed-Size: 3156
Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Luciano Bello <luciano@linux.org.ar>
Architecture: i386
Version: 7:6.2.4.5.dfsg1-2ubuntu1
Replaces: imagemagick-doc, geomview (<= 1.8.0)
Depends: libbz2-1.0, libc6 (>= 2.6-1), libfreetype6 (>= 2.3.5), libice6 (>= 1:1.0.0), libjasper1 (>= 1.900.1), libjpeg62, liblcms1 (>= 1.15-1), libmagick9, 
**libpng12-0** (>= 1.2.13-4), libsm6, libtiff4, libx11-6, libxext6, libxml2 (>= 2.6.29), libxt6, zlib1g (>= 1:1.2.3.3.dfsg-1)
```

---

### Post by pmsaue0 on 2008-07-10
> **unutbu said:**
> I think the package you need is libpng12-0.
```

% apt-cache show imagemagick
Package: imagemagick
Priority: optional
Section: graphics
Installed-Size: 3156
Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Luciano Bello <luciano@linux.org.ar>
Architecture: i386
Version: 7:6.2.4.5.dfsg1-2ubuntu1
Replaces: imagemagick-doc, geomview (<= 1.8.0)
Depends: libbz2-1.0, libc6 (>= 2.6-1), libfreetype6 (>= 2.3.5), libice6 (>= 1:1.0.0), libjasper1 (>= 1.900.1), libjpeg62, liblcms1 (>= 1.15-1), libmagick9, 
**libpng12-0** (>= 1.2.13-4), libsm6, libtiff4, libx11-6, libxext6, libxml2 (>= 2.6.29), libxt6, zlib1g (>= 1:1.2.3.3.dfsg-1)
```
I receive the same information with "% apt-cache show imagemagick"  which is good, I suppose.  But I still do not have PNG support, as far as I know.

When I run the command:
[COLOR="Green"]convert z.png z.jpg[/COLOR]
I receive:
[COLOR="Indigo"]convert: no decode delegate for this image format `z.png'.
convert: missing an image filename `z.jpg'.[/COLOR]

Any ideas why this would be?

---

### Post by unutbu on 2008-07-10
Please forgive me if this is a dumb question.
Did you install libpng12-0?

---

### Post by pmsaue0 on 2008-07-10
> **unutbu said:**
> Please forgive me if this is a dumb question.
Did you install libpng12-0?
I have.  when i run [COLOR="Green"]sudo apt-get install libpng12-0[/COLOR] it says I already have the newest version.  I did a reboot as well.

are you able to do a simple png operation?
when you run [COLOR="green"]convert -list configure[/COLOR] what DELEGATES do you have listed

---

### Post by unutbu on 2008-07-10
These are interesting commands -- they are not in the man page or convert -help. Where are these documented?

```
% convert -list configure

Path: /usr/lib/ImageMagick-6.2.4/config/configure.xml

Name          Value
-------------------------------------------------------------------------------
CC            gcc
CFLAGS        -g -O2 -Wall -pthread
CONFIGURE     ./configure --prefix=/usr --mandir=${prefix}/share/man --infodir=${prefix}/share/info --with-gs-font-dir=/usr/share/fonts/type1/gsfonts --with-magick-plus-plus --enable-shared --enable-lzw --without-dps --without-fpx --without-perl --with-perl-options=INSTALLDIRS=vendor --x-includes=/usr/include/X11 --x-libraries=/usr/lib/X11
COPYRIGHT     Copyright (C) 1999-2005 ImageMagick Studio LLC
CPPFLAGS      -I/usr/include
CVS_BRANCH_TAG HEAD
CXX           g++
CXXFLAGS      -pthread
DEFS          -DHAVE_CONFIG_H
DISTCHECK_CONFIG_FLAGS --prefix=/usr --mandir=${prefix}/share/man --infodir=${prefix}/share/info --with-gs-font-dir=/usr/share/fonts/type1/gsfonts --with-magick-plus-plus --enable-shared --enable-lzw --without-dps --without-fpx --without-perl --with-perl-options=INSTALLDIRS=vendor --x-includes=/usr/include/X11 --x-libraries=/usr/lib/X11
EXEC-PREFIX   /usr
HOST          i686-pc-linux-gnu
LDFLAGS       -L/usr/lib -L/usr/lib/X11 -lfreetype -lz -L/usr/lib
LIB_VERSION   0x624
LIB_VERSION_NUMBER 6,2,4,5
LIBS          -lMagick -llcms -ltiff -lfreetype -ljasper -ljpeg -lpng -lXext -lXt -lSM -lICE -lX11 -lbz2 -lxml2 -lz -lpthread -lm -lpthread
NAME          ImageMagick
PCFLAGS       
PREFIX        /usr
QuantumDepth  16
RELEASE_DATE  10/02/07
VERSION       6.2.4
WEBSITE       http://www.imagemagick.org
```

```
% convert -list format
   Format  Module    Mode  Description
-------------------------------------------------------------------------------
        A* RAW       rw+   Raw alpha samples
      ART* ART       r--   PFS: 1st Publisher
           Format originally used on the Macintosh (MacPaint?) and later used
           for PFS: 1st Publisher clip art.  NOT the AOL ART format.
      AVI* AVI       r--   Microsoft Audio/Visual Interleaved
      AVS* AVS       rw+   AVS X image
        B* RAW       rw+   Raw blue samples
      BMP* BMP       rw-   Microsoft Windows bitmap image
     BMP2* BMP       -w-   Microsoft Windows bitmap image v2
     BMP3* BMP       -w-   Microsoft Windows bitmap image v3
        C* RAW       rw+   Raw cyan samples
    CACHE* CACHE     ---   Magick Persistent Cache image format
  CAPTION* CAPTION   r--   Image caption
      CIN* CIN       rw+   Cineon Image File
      CIP* CIP       -w-   Cisco IP phone image format
     CLIP* CLIP      -w+   Image Clip Mask
     CMYK* CMYK      rw+   Raw cyan, magenta, yellow, and black samples
    CMYKA* CMYK      rw+   Raw cyan, magenta, yellow, black, and opacity samples
      CUR* CUR       rw-   Microsoft icon
      CUT* CUT       r--   DR Halo
      DCM* DCM       r--   Digital Imaging and Communications in Medicine image
           DICOM is used by the medical community for images like X-rays.  The
           specification, "Digital Imaging and Communications in Medicine
           (DICOM)", is available at http://medical.nema.org/.  In particular,
           see part 5 which describes the image encoding (RLE, JPEG, JPEG-LS),
           and supplement 61 which adds JPEG-2000 encoding.
      DCX* PCX       rw+   ZSoft IBM PC multi-page Paintbrush
      DNG* DNG       r--   Digital Negative
      DPS  DPS       ---   Display Postscript Interpreter
      DPX* DPX       rw+   SMPTE 268M-2003 (DPX)
           File Format for Digital Moving-Picture Exchange (DPX) Version 2.0.
           See SMPTE 268M-2003 specification at http://www.smtpe.org
           
     EPDF  PDF       rw-   Encapsulated Portable Document Format
      EPI  PS        rw-   Encapsulated PostScript Interchange format
      EPS  PS        rw-   Encapsulated PostScript
     EPS2* PS2       -w-   Level II Encapsulated PostScript
     EPS3* PS3       -w+   Level III Encapsulated PostScript
     EPSF  PS        rw-   Encapsulated PostScript
     EPSI  PS        rw-   Encapsulated PostScript Interchange format
      EPT  EPT       rw-   Encapsulated PostScript with TIFF preview
     EPT2  EPT       rw-   Encapsulated PostScript Level II with TIFF preview
     EPT3  EPT       rw+   Encapsulated PostScript Level III with TIFF preview
      FAX* FAX       rw+   Group 3 FAX
           See TIFF format.  Note that FAX machines use non-square pixels which
           are 1.5 times wider than they are tall but computer displays use
           square pixels. FAX images may appear to be narrow unless they are
           explicitly resized using a resize specification of "150x100%".
     FITS* FITS      rw-   Flexible Image Transport System
  FRACTAL* PLASMA    r--   Plasma fractal image
        G* RAW       rw+   Raw green samples
       G3* FAX       rw-   Group 3 FAX
      GIF* GIF       rw+   CompuServe graphics interchange format
    GIF87* GIF       rw-   CompuServe graphics interchange format (version 87a)
 GRADIENT* GRADIENT  r--   Gradual passing from one shade to another
     GRAY* GRAY      rw+   Raw gray samples
HISTOGRAM* HISTOGRAM -w-   Histogram of the image
      HTM* HTML      -w-   Hypertext Markup Language and a client-side image map
     HTML* HTML      -w-   Hypertext Markup Language and a client-side image map
      ICB* TGA       rw+   Truevision Targa image
      ICO* ICON      rw-   Microsoft icon
     ICON* ICON      rw-   Microsoft icon
     INFO  INFO      -w+   The image format and characteristics
      JNG* PNG       rw-   JPEG Network Graphics
           See http://www.libpng.org/pub/mng/ for details about the JNG format.
           The JNG 1.0 specification is available there and at
           ftp://swrinde.nde.swri.edu/pub/mng/documents/.
      JP2* JP2       rw-   JPEG-2000 File Format Syntax
      JPC* JPC       rw-   JPEG-2000 Code Stream Syntax
     JPEG* JPEG      rw-   Joint Photographic Experts Group JFIF format (62)
      JPG* JPEG      rw-   Joint Photographic Experts Group JFIF format
      JPX* JPX       rw-   JPEG-2000 File Format Syntax
        K* RAW       rw+   Raw black samples
    LABEL* LABEL     r--   Image label
        M* RAW       rw+   Raw magenta samples
      M2V  MPEG      rw+   MPEG Video Stream
      MAP* MAP       rw-   Colormap intensities and indices
      MAT* MAT       r--   MATLAB image format
    MATTE* MATTE     -w+   MATTE format
     MIFF* MIFF      rw+   Magick Image File Format
      MNG* PNG       rw+   Multiple-image Network Graphics (libpng 1.2.15beta5)
           See http://www.libpng.org/pub/mng/ for details about the MNG format.
           The MNG 1.0 specification is available there and at
           ftp://swrinde.nde.swri.edu/pub/mng/documents/.
     MONO* MONO      rw-   Bi-level bitmap in least-significant-byte first order
      MPC* MPC       rw+   Magick Persistent Cache image format
     MPEG  MPEG      rw+   MPEG Video Stream
      MPG  MPEG      rw+   MPEG Video Stream
      MSL* MSL       rw+   Magick Scripting Language
      MTV* MTV       rw+   MTV Raytracing image format
      MVG* MVG       rw-   Magick Vector Graphics
     NULL* NULL      rw-   Constant image of uniform color
        O* RAW       rw+   Raw opacity samples
      OTB* OTB       rw-   On-the-air bitmap
      OTF* TTF       r--   Open Type font (Freetype 2.3.5)
       P7* PNM       rw+   Xv thumbnail format
      PAL* UYVY      rw-   16bit/pixel interleaved YUV
     PALM* PALM      rw+   Palm pixmap
  PATTERN* PATTERN   r--   Predefined pattern
      PBM* PNM       rw+   Portable bitmap format (black and white)
      PCD* PCD       rw-   Photo CD
     PCDS* PCD       rw-   Photo CD
      PCL* PCL       rw-   Printer Control Language
      PCT* PICT      rw-   Apple Macintosh QuickDraw/PICT
      PCX* PCX       rw-   ZSoft IBM PC Paintbrush
      PDB* PDB       rw+   Palm Database ImageViewer Format
      PDF  PDF       rw+   Portable Document Format
      PFA* TTF       r--   Postscript Type 1 font (ASCII) (Freetype 2.3.5)
      PFB* TTF       r--   Postscript Type 1 font (binary) (Freetype 2.3.5)
      PGM* PNM       rw+   Portable graymap format (gray scale)
      PGX* PGX       r--   JPEG-2000 VM Format
    PICON* XPM       rw-   Personal Icon
     PICT* PICT      rw-   Apple Macintosh QuickDraw/PICT
      PIX* PIX       r--   Alias/Wavefront RLE image format
    PJPEG* JPEG      rw-   Progessive Joint Photographic Experts Group JFIF
   PLASMA* PLASMA    r--   Plasma fractal image
      PNG* PNG       rw-   Portable Network Graphics (libpng 1.2.15beta5)
           See http://www.libpng.org/ for details about the PNG format.  The
           PNG 1.2 specification is available there and at
           ftp://swrinde.nde.swri.edu/pub/png/documents/.
    PNG24* PNG       rw-   24-bit RGB PNG, opaque only (zlib 1.2.3.3)
    PNG32* PNG       rw-   32-bit RGBA PNG, semitransparency OK
     PNG8* PNG       rw-   8-bit indexed PNG, binary transparency only
      PNM* PNM       rw+   Portable anymap
      PPM* PNM       rw+   Portable pixmap format (color)
  PREVIEW* PREVIEW   -w-   Show a preview an image enhancement, effect, or f/x
       PS  PS        rw+   PostScript
      PS2* PS2       -w+   Level II PostScript
      PS3* PS3       -w+   Level III PostScript
      PSD* PSD       rw+   Adobe Photoshop bitmap
     PTIF* TIFF      rw-   Pyramid encoded TIFF
      PWP* PWP       r--   Seattle Film Works
        R* RAW       rw+   Raw red samples
      RAS* SUN       rw+   SUN Rasterfile
      RGB* RGB       rw+   Raw red, green, and blue samples
     RGBA* RGB       rw+   Raw red, green, blue, and alpha samples
     RGBO* RGB       rw+   Raw red, green, blue, and opacity samples
      RLA* RLA       r--   Alias/Wavefront image
      RLE* RLE       r--   Utah Run length encoded image
      SCR* SCR       r--   ZX-Spectrum SCREEN$
      SCT* SCT       r--   Scitex HandShake
      SFW* SFW       r--   Seattle Film Works
      SGI* SGI       rw+   Irix RGB image
    SHTML* HTML      -w-   Hypertext Markup Language and a client-side image map
  STEGANO* STEGANO   r--   Steganographic image
      SUN* SUN       rw+   SUN Rasterfile
      SVG* SVG       rw+   Scalable Vector Graphics (XML 2.6.29)
     SVGZ* SVG       rw+   Compressed Scalable Vector Graphics (XML 2.6.29)
     TEXT* TXT       rw+   Text
      TGA* TGA       rw+   Truevision Targa image
      TIF* TIFF      rw+   Tagged Image File Format (42)
     TIFF* TIFF      rw+   Tagged Image File Format (42)
     TILE* TILE      r--   Tile image with a texture
      TIM* TIM       r--   PSX TIM
      TTC* TTF       r--   TrueType font collection (Freetype 2.3.5)
      TTF* TTF       r--   TrueType font (Freetype 2.3.5)
      TXT* TXT       rw+   Text
      UIL* UIL       -w-   X-Motif UIL table
     UYVY* UYVY      rw-   16bit/pixel interleaved YUV
      VDA* TGA       rw+   Truevision Targa image
    VICAR* VICAR     rw-   VICAR rasterfile format
      VID* VID       rw+   Visual Image Directory
     VIFF* VIFF      rw+   Khoros Visualization image
      VST* TGA       rw+   Truevision Targa image
     WBMP* WBMP      rw-   Wireless Bitmap (level 0) image
      WMF* WMF       ---   Windows Meta File
      WMZ* WMZ       ---   Compressed Windows Meta File
      WPG* WPG       r--   Word Perfect Graphics
        X* X         rw+   X Image
      XBM* XBM       rw-   X Windows system bitmap (black and white)
       XC* XC        r--   Constant image uniform color
      XCF* XCF       r--   GIMP image
      XPM* XPM       rw-   X Windows system pixmap (color)
       XV* VIFF      rw+   Khoros Visualization image
      XWD* XWD       rw-   X Windows system window dump (color)
        Y* RAW       rw+   Raw yellow samples
    YCbCr* YCbCr     rw+   Raw Y, Cb, and Cr samples
   YCbCrA* YCbCr     rw+   Raw Y, Cb, Cr, and opacity samples
      YUV* YUV       rw-   CCIR 601 4:1:1 or 4:2:2

* native blob support

convert: unable to open module file `/usr/lib/ImageMagick-6.2.4/modules-Q16/coders/magick.la': No such file or directory.
```

```
% convert -version
Version: ImageMagick 6.2.4 10/02/07 Q16 http://www.imagemagick.org
Copyright: Copyright (C) 1999-2005 ImageMagick Studio LLC
```

```
% convert T.png T.jpg
```

works for me.

---

### Post by pmsaue0 on 2008-07-10
Thank you for your thorough reply.  Yes, the man pages are weak.  I found the documentation for -list here: [http://www.imagemagick.org/script/command-line-options.php#list](http://www.imagemagick.org/script/command-line-options.php#list) 

Did you use aptitude when installing? install from source?

Here are my results

```

% convert -list configure

Path: /usr/local/lib/ImageMagick-6.4.2/config/configure.xml

Name          Value
-------------------------------------------------------------------------------
CC            gcc
CFLAGS        -g -O2 -Wall -W -pthread
CONFIGURE     ./configure 
COPYRIGHT     Copyright (C) 1999-2008 ImageMagick Studio LLC
CPPFLAGS      -I/usr/local/include/ImageMagick
CXX           g++
CXXFLAGS      -g -O2 -Wall -W -pthread
DEFS          -DHAVE_CONFIG_H
DELEGATES     freetype zlib
DISTCHECK_CONFIG_FLAGS --disable-deprecated --with-quantum-depth=16 --with-djvu=no --with-umem=no --with-fontpath= --with-fontconfig=no --with-lqr=no --with-rsvg=no --with-xml=no
EXEC-PREFIX   /usr/local
HOST          x86_64-unknown-linux-gnu
LDFLAGS       -L/usr/local/lib -lfreetype -lz
LIB_VERSION   0x642
LIB_VERSION_NUMBER 6,4,2,1
LIBS          -lMagickCore -lfreetype -lz -lm -lpthread 
NAME          ImageMagick
PCFLAGS       
PREFIX        /usr/local
QuantumDepth  16
RELEASE_DATE  07/10/08
VERSION       6.4.2
WEBSITE       http://www.imagemagick.org

```

```

% convert -list format
   Format  Module    Mode  Description
-------------------------------------------------------------------------------
        A* RAW       rw+   Raw alpha samples
       AI  PDF       rw-   Adobe Illustrator CS2
      ART* ART       rw-   PFS: 1st Publisher Clip Art
      ARW  DNG       r--   Sony Alpha Raw Image Format
      AVI* AVI       r--   Microsoft Audio/Visual Interleaved
      AVS* AVS       rw+   AVS X image
        B* RAW       rw+   Raw blue samples
      BMP* BMP       rw-   Microsoft Windows bitmap image
     BMP2* BMP       -w-   Microsoft Windows bitmap image v2
     BMP3* BMP       -w-   Microsoft Windows bitmap image v3
      BRF* BRAILLE   -w-   BRF ASCII Braille format
        C* RAW       rw+   Raw cyan samples
  CAPTION* CAPTION   r--   Image caption
      CIN* CIN       rw+   Cineon Image File
      CIP* CIP       -w-   Cisco IP phone image format
     CLIP* CLIP      -w+   Image Clip Mask
     CMYK* CMYK      rw+   Raw cyan, magenta, yellow, and black samples
    CMYKA* CMYK      rw+   Raw cyan, magenta, yellow, black, and opacity samples
      CR2  DNG       r--   Canon Digital Camera Raw Image Format
      CRW  DNG       r--   Canon Digital Camera Raw Image Format
      CUR* CUR       rw-   Microsoft icon
      CUT* CUT       r--   DR Halo
      DCM* DCM       r--   Digital Imaging and Communications in Medicine image
           DICOM is used by the medical community for images like X-rays.  The
           specification, "Digital Imaging and Communications in Medicine
           (DICOM)", is available at http://medical.nema.org/.  In particular,
           see part 5 which describes the image encoding (RLE, JPEG, JPEG-LS),
           and supplement 61 which adds JPEG-2000 encoding.
      DCR  DNG       r--   Kodak Digital Camera Raw Image File
      DCX* PCX       rw+   ZSoft IBM PC multi-page Paintbrush
      DDS* DDS       r--   Microsoft DirectDraw Surface
    DFONT* TTF       r--   Multi-face font package (Freetype 2.3.5)
      DNG  DNG       r--   Digital Negative
      DOT  DOT       ---   Graphviz
      DPS  DPS       ---   Display Postscript Interpreter
      DPX* DPX       rw+   SMPTE 268M-2003 (DPX 2.0)
           Digital Moving Picture Exchange Bitmap, Version 2.0.
           See SMPTE 268M-2003 specification at http://www.smtpe.org
           
     EPDF  PDF       rw-   Encapsulated Portable Document Format
      EPI  PS        rw-   Encapsulated PostScript Interchange format
      EPS  PS        rw-   Encapsulated PostScript
     EPS2* PS2       -w-   Level II Encapsulated PostScript
     EPS3* PS3       -w+   Level III Encapsulated PostScript
     EPSF  PS        rw-   Encapsulated PostScript
     EPSI  PS        rw-   Encapsulated PostScript Interchange format
      FAX* FAX       rw+   Group 3 FAX
           FAX machines use non-square pixels which are 1.5 times wider than they
           are tall but computer displays use square pixels, therefore FAX images
           may appear to be narrow unless they are explicitly resized using a
           geometry of "150x100%".
           
     FITS* FITS      rw-   Flexible Image Transport System
  FRACTAL* PLASMA    r--   Plasma fractal image
      FTS* FTS       rw-   Flexible Image Transport System
        G* RAW       rw+   Raw green samples
       G3* FAX       rw-   Group 3 FAX
      GIF* GIF       rw+   CompuServe graphics interchange format
    GIF87* GIF       rw-   CompuServe graphics interchange format (version 87a)
 GRADIENT* GRADIENT  r--   Gradual passing from one shade to another
     GRAY* GRAY      rw+   Raw gray samples
HISTOGRAM* HISTOGRAM -w-   Histogram of the image
      HTM* HTML      -w-   Hypertext Markup Language and a client-side image map
     HTML* HTML      -w-   Hypertext Markup Language and a client-side image map
      ICB* TGA       rw+   Truevision Targa image
      ICO* ICON      rw+   Microsoft icon
     ICON* ICON      rw-   Microsoft icon
     INFO  INFO      -w+   The image format and characteristics
      IPL* IPL       rw+   IPL Image Sequence
   ISOBRL* BRAILLE   -w-   ISO/TR 11548-1 format
        K* RAW       rw+   Raw black samples
      K25  DNG       r--   Kodak Digital Camera Raw Image Format
      KDC  DNG       r--   Kodak Digital Camera Raw Image Format
    LABEL* LABEL     r--   Image label
        M* RAW       rw+   Raw magenta samples
      M2V  MPEG      rw+   MPEG Video Stream
      MAP* MAP       rw-   Colormap intensities and indices
      MAT  MAT       rw+   MATLAB image format
    MATTE* MATTE     -w+   MATTE format
     MIFF* MIFF      rw+   Magick Image File Format
     MONO* MONO      rw-   Raw bi-level bitmap
      MPC* MPC       rw+   Magick Persistent Cache image format
     MPEG  MPEG      rw+   MPEG Video Stream
      MPG  MPEG      rw+   MPEG Video Stream
      MRW  DNG       r--   Sony (Minolta) Raw Image File
      MSL* MSL       ---   Magick Scripting Language
     MSVG* SVG       -w+   ImageMagick's own SVG internal renderer
      MTV* MTV       rw+   MTV Raytracing image format
      MVG* MVG       rw-   Magick Vector Graphics
      NEF  DNG       r--   Nikon Digital SLR Camera Raw Image File
     NULL* NULL      rw-   Constant image of uniform color
        O* RAW       rw+   Raw opacity samples
      ORF  DNG       r--   Olympus Digital Camera Raw Image File
      OTB* OTB       rw-   On-the-air bitmap
      OTF* TTF       r--   Open Type font (Freetype 2.3.5)
      PAL* UYVY      rw-   16bit/pixel interleaved YUV
     PALM* PALM      rw+   Palm pixmap
      PAM* PNM       rw+   Common 2-dimensional bitmap format
  PATTERN* PATTERN   r--   Predefined pattern
      PBM* PNM       rw+   Portable bitmap format (black and white)
      PCD* PCD       rw-   Photo CD
     PCDS* PCD       rw-   Photo CD
      PCL  PCL       rw-   Printer Control Language
      PCT* PICT      rw-   Apple Macintosh QuickDraw/PICT
      PCX* PCX       rw-   ZSoft IBM PC Paintbrush
      PDB* PDB       rw+   Palm Database ImageViewer Format
      PDF  PDF       rw+   Portable Document Format
     PDFA  PDF       rw+   Portable Document Archive Format
      PEF  DNG       r--   Pentax Electronic File
      PFA* TTF       r--   Postscript Type 1 font (ASCII) (Freetype 2.3.5)
      PFB* TTF       r--   Postscript Type 1 font (binary) (Freetype 2.3.5)
      PFM* PFM       rw+   Portable float format
      PGM* PNM       rw+   Portable graymap format (gray scale)
    PICON* XPM       rw-   Personal Icon
     PICT* PICT      rw-   Apple Macintosh QuickDraw/PICT
      PIX* PIX       r--   Alias/Wavefront RLE image format
   PLASMA* PLASMA    r--   Plasma fractal image
      PNM* PNM       rw+   Portable anymap
      PPM* PNM       rw+   Portable pixmap format (color)
  PREVIEW* PREVIEW   -w-   Show a preview an image enhancement, effect, or f/x
       PS  PS        rw+   PostScript
      PS2* PS2       -w+   Level II PostScript
      PS3* PS3       -w+   Level III PostScript
      PSD* PSD       rw+   Adobe Photoshop bitmap
      PWP* PWP       r--   Seattle Film Works
        R* RAW       rw+   Raw red samples
      RAF  DNG       r--   Fuji CCD-RAW Graphic File
      RAS* SUN       rw+   SUN Rasterfile
      RGB* RGB       rw+   Raw red, green, and blue samples
     RGBA* RGB       rw+   Raw red, green, blue, and alpha samples
     RGBO* RGB       rw+   Raw red, green, blue, and opacity samples
      RLA* RLA       r--   Alias/Wavefront image
      RLE* RLE       r--   Utah Run length encoded image
      SCR* SCR       r--   ZX-Spectrum SCREEN$
      SCT* SCT       r--   Scitex HandShake
      SFW* SFW       r--   Seattle Film Works
      SGI* SGI       rw+   Irix RGB image
    SHTML* HTML      -w-   Hypertext Markup Language and a client-side image map
      SR2  DNG       r--   Sony Raw Format 2
      SRF  DNG       r--   Sony Raw Format
  STEGANO* STEGANO   r--   Steganographic image
      SUN* SUN       rw+   SUN Rasterfile
      SVG* SVG       -w+   Scalable Vector Graphics
     SVGZ* SVG       -w+   Compressed Scalable Vector Graphics
     TEXT* TXT       rw-   Text
      TGA* TGA       rw+   Truevision Targa image
THUMBNAIL* THUMBNAIL -w+   EXIF Profile Thumbnail
     TILE* TILE      r--   Tile image with a texture
      TIM* TIM       r--   PSX TIM
      TTC* TTF       r--   TrueType font collection (Freetype 2.3.5)
      TTF* TTF       r--   TrueType font (Freetype 2.3.5)
      TXT* TXT       rw-   Text
     UBRL* BRAILLE   -w-   Unicode Text format
      UIL* UIL       -w-   X-Motif UIL table
     UYVY* UYVY      rw-   16bit/pixel interleaved YUV
      VDA* TGA       rw+   Truevision Targa image
    VICAR* VICAR     rw-   VICAR rasterfile format
      VID* VID       rw+   Visual Image Directory
     VIFF* VIFF      rw+   Khoros Visualization image
      VST* TGA       rw+   Truevision Targa image
     WBMP* WBMP      rw-   Wireless Bitmap (level 0) image
      WPG* WPG       r--   Word Perfect Graphics
      X3F  DNG       r--   Sigma Camera RAW Picture File
      XBM* XBM       rw-   X Windows system bitmap (black and white)
       XC* XC        r--   Constant image uniform color
      XCF* XCF       r--   GIMP image
      XPM* XPM       rw-   X Windows system pixmap (color)
      XPS  XPS       r--   Microsoft XML Paper Specification
       XV* VIFF      rw+   Khoros Visualization image
        Y* RAW       rw+   Raw yellow samples
    YCbCr* YCbCr     rw+   Raw Y, Cb, and Cr samples
   YCbCrA* YCbCr     rw+   Raw Y, Cb, Cr, and opacity samples
      YUV* YUV       rw-   CCIR 601 4:1:1 or 4:2:2

* native blob support

```

---

### Post by unutbu on 2008-07-10
I'm running gutsy, and I installed imagemagick with

```
% sudo apt-get install imagemagick
```

My version is 6.2.4, yours is 6.4.2. The latest Hardy package is version 6.3.7 ([http://packages.ubuntu.com/hardy/imagemagick](http://packages.ubuntu.com/hardy/imagemagick)).

Perhaps you have a non-official repo activated and it is giving you this newer version of imagemagick, but whoever compiled it didn't link in the graphics libs.

Notice the following line in convert -list configure: 

Mine says:
```
LIBS          -lMagick -llcms -ltiff -lfreetype -ljasper -ljpeg -lpng -lXext -lXt -lSM -lICE -lX11 -lbz2 -lxml2 -lz -lpthread -lm -lpthread
```

Yours says:
```
LIBS          -lMagickCore -lfreetype -lz -lm -lpthread 
```

I think this shows the libraries that were linked in at compile time. 
You have at least two options:

(1) Purge your current imagemagick installation, turn off all unofficial repos, and then reinstall imagemagick from the official repositories.

(2) Purge your current imagemagick and recompile the latest version (6.4.2), making sure the LIBS is configured to include the desired graphics libaries.

---

### Post by pmsaue0 on 2008-07-11
I really appreciate your help.  Thank you.
I now have a working version of imageMagick with the necessary delegate libs.  I had to run an apt-get remove, but the problem was that there was a source installation on the server that had to be removed as well.  The big problem was that apt-get thought imagemagick was removed when it wasn't... so we had to do some digging and remove the install reference.  Then we installed from source

Short story -- up and running :)

---

