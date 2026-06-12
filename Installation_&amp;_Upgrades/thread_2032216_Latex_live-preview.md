---
title: "Latex live-preview"
date: 2012-07-23
forum: Installation &amp; Upgrades
---

### Post by hierkommtdiemaus on 2012-07-23
Hello,

I'm trying to install the development version of kile in order to enjoy live preview. I'm following those instructions: 

[http://sourceforge.net/apps/mediawiki/kile/index.php?title=Live_Preview](http://sourceforge.net/apps/mediawiki/kile/index.php?title=Live_Preview)

However, I get error messages in the step

```
cmake ../src/okular -DCMAKE_INSTALL_PREFIX=$HOME/kile-livepreview/install -DCMAKE_BUILD_TYPE="Debug"
```

This is what cmake says:
```

ALL_PREFIX=$HOME/kile-livepreview/install -DCMAKE_BUILD_TYPE="Debug"
-- Found Qt-Version 4.8.1 (using /usr/bin/qmake)
-- Found X11: /usr/lib/i386-linux-gnu/libX11.so
-- Found KDE 4.8 include dir: /usr/include
-- Found KDE 4.8 library dir: /usr/lib
-- Found the KDE4 kconfig_compiler preprocessor: /usr/bin/kconfig_compiler
-- Found automoc4: /usr/bin/automoc4
-- WARNING: you are using the obsolete 'PKGCONFIG' macro, use FindPkgConfig
-- PKGCONFIG() indicates that libspectre is not installed (install the package which contains libspectre.pc if you want to support this feature)
-- Could NOT find LibSpectre  (missing:  LIBSPECTRE_LIBRARY LIBSPECTRE_FOUND) 
-- Could NOT find CHM  (missing:  CHM_INCLUDE_DIR CHM_LIBRARY) 
-- Could NOT find TIFF (missing:  TIFF_LIBRARY TIFF_INCLUDE_DIR) 
-- Found Freetype: -L/usr/lib/i386-linux-gnu -lfreetype -lz
-- Found ZLIB: /usr/lib/i386-linux-gnu/libz.so (found version "1.2.3.4")
-- Could NOT find EPub  (missing:  EPUB_LIBRARIES EPUB_INCLUDE_DIR) 
-- Could NOT find QCA2  (missing:  QCA2_LIBRARIES QCA2_INCLUDE_DIR) 

-----------------------------------------------------------------------------
-- The following external packages were located on your system.
-- This installation will have the extra features provided by these packages.
-----------------------------------------------------------------------------
   * QImageBlitz - An image effects library
   * DjVuLibre - A library for dealing with DjVu formatted files
   * FreeType - A font rendering engine
   * JPEG - A library for reading and writing JPEG image files.
   * ZLib - The Zlib compression library

-----------------------------------------------------------------------------
-- The following OPTIONAL packages could NOT be located on your system.
-- Consider installing them to enable more features from this software.
-----------------------------------------------------------------------------
   * Poppler-Qt4 (0.12.1 or higher)  <http://poppler.freedesktop.org>
     A PDF rendering library
     Support for PDF files in okular.
   * libspectre (0.2 or higher)  <http://libspectre.freedesktop.org/wiki/>
     A PostScript rendering library
     Support for PS files in okular.
   * CHM  <http://www.jedrea.com/chmlib>
     A library for dealing with Microsoft ITSS/CHM format files
     Support CHM files in okular.
   * libTIFF  <http://www.remotesensing.org/libtiff>
     A library for reading and writing TIFF formatted files,
     Support for TIFF files in okular.
   * libepub  <http://sourceforge.net/projects/ebook-tools>
     A library for reading EPub documents
     Support for EPub documents in Okular.
   * QCA (2.0.0 or higher)  <http://delta.affinix.com/qca/>
     Qt Cryptographic Architecture (QCA)
     Support for encrypted OpenDocument Text documents in Okular.

-----------------------------------------------------------------------------

CMake Error: The following variables are used in this project, but they are set to NOTFOUND.
Please set them or make sure they are set and tested correctly in the CMake files:
FREETYPE_INCLUDE_DIR (ADVANCED)
   used as include directory in directory /home/jan/kile-livepreview/src/okular/generators/dvi

-- Configuring incomplete, errors occurred!


```

I don't really know what to do. I already installed kdelibs5.

Furthermore, I'm confused that Poppler is not found: I installed both libpoppler-qt4-3 and libpoppler-qt4-dev.

Any help would be appreciated!

---

