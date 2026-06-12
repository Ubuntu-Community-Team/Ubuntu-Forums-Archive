---
title: "gnuplot 5.0 and x11"
date: 2015-09-14
forum: Installation &amp; Upgrades
---

### Post by BuboBubo on 2015-09-14
Hi everyone, 

Please bear with me, I'm new to the forum, and excuse me if 
I'm breaking forum rules.

I have Ubuntu 14.04, and months ago I installed new gnuplot 5.0.
After the installation, I don't have gnuplot terminals x11 and wxt.

The rest of the terminals are working great, but for some fast 
checks, I would prefer to have x11. 

'sudo apt-get insall gnuplot-x11' installs gnuplot-x11 version 4.6.4-2,
and it is not useful with gnuplot 5.0 version. 

I don't have gnuplot-nox installed, I've tried to purge gnuplot
and install everything again, and it's not working. 

Please, do you have some ideas how should I fix it? 
Thank you a lot!

---

### Post by steeldriver on 2015-09-14
Hello and welcome to the forums

How exactly did you install it? If you built the package from source, what options/ additional arguments did you give to the ./configure script?

---

### Post by BuboBubo on 2015-09-14
Thanks!
I downloaded it from here:
[http://sourceforge.net/projects/gnuplot/files/](http://sourceforge.net/projects/gnuplot/files/)

I didn't give any additional arguments to configure script. All I did was:

$ ./configure
$ make
$ sudo make install 

However, when I run ./configure again, I see these warnings:

[COLOR=#800000]configure: WARNING: The wxWidgets terminal will not be compiled.[/COLOR]
[COLOR=#800000]checking for PANGO_1_10_2... no[/COLOR]
[COLOR=#800000]checking for CAIROPDF... configure: WARNING:[/COLOR]
[COLOR=#800000]Package requirements (       cairo >= 1.2 cairo-pdf >= 1.2 pango >= 1.10 pangocairo >= 1.10 glib-2.0) were not met:[/COLOR]
[COLOR=#800000]
[/COLOR]
[COLOR=#800000]No package 'cairo' found[/COLOR]
[COLOR=#800000]No package 'cairo-pdf' found[/COLOR]
[COLOR=#800000]No package 'pango' found[/COLOR]
[COLOR=#800000]No package 'pangocairo' found[/COLOR]
[COLOR=#800000]No package 'glib-2.0' found[/COLOR]
[COLOR=#800000]configure: WARNING: The cairo terminals will not be compiled.[/COLOR]
[COLOR=#800000]checking for QT... configure: WARNING:[/COLOR]
[COLOR=#800000]Package requirements (Qt5Core Qt5Gui Qt5Network Qt5Svg Qt5PrintSupport) were not met:[/COLOR]
[COLOR=#800000]No package 'Qt5Core' found[/COLOR]
[COLOR=#800000]No package 'Qt5Gui' found[/COLOR]
[COLOR=#800000]No package 'Qt5Network' found[/COLOR]
[COLOR=#800000]No package 'Qt5Svg' found[/COLOR]
[COLOR=#800000]No package 'Qt5PrintSupport' found[/COLOR]


.... And at the end:



[COLOR=#800000]** Configuration summary for gnuplot 5.0.1:[/COLOR]
[COLOR=#800000]
[/COLOR]
[COLOR=#800000]gnuplot will be compiled with the following terminals:[/COLOR]
[COLOR=#800000]
[/COLOR]
[COLOR=#800000]  Standalone terminals: yes (always builtin)[/COLOR]
[COLOR=#800000]    canvas, cgm, context, corel, dumb, dxf, eepic, emf, emtex,[/COLOR]
[COLOR=#800000]    epslatex, fig, hpgl,latex, metafont, metapost, mif, pcl5,[/COLOR]
[COLOR=#800000]    postscript, pslatex, pstex, pstricks, qms, svg,[/COLOR]
[COLOR=#800000]    tek40xx, tek410x, texdraw, tgif, tkcanvas, tpic, vttek[/COLOR]
[COLOR=#800000]
[/COLOR]
[COLOR=#800000]  dot-matrix terminals: no (use --with-bitmap-terminals to enable)[/COLOR]
[COLOR=#800000]    epson, nec, okidata, tandy, and seiko dp414 printers[/COLOR]
[COLOR=#800000]    hp500c, hpdj, hpljii, hppj, pbm, sixel, starc[/COLOR]
[COLOR=#800000]
[/COLOR]
[COLOR=#800000]  X Window System terminal: no (requires X libraries)[/COLOR]
[COLOR=#800000]  PDFlib pdf terminal: no (use --with-pdf to enable)[/COLOR]
[COLOR=#800000]  linux terminal (vga console): no (use --with-linux-vga to enable)[/COLOR]
[COLOR=#800000]  vgagl terminal ((s)vga console): no (use --with-linux-vga to enable)[/COLOR]
[COLOR=#800000]  ggi terminal: no (use --with-ggi to enable, requires libggi)[/COLOR]
[COLOR=#800000]  gpic terminal: no   (use --with-gpic to enable)[/COLOR]
[COLOR=#800000]  mif terminal: no   (use --with-mif to enable)[/COLOR]
[COLOR=#800000]  caca terminal: no (requires libcaca >= 0.99.beta15)[/COLOR]
[COLOR=#800000]  aqua terminal (OSX): no[/COLOR]
[COLOR=#800000]  libgd-based png, jpeg, and gif terminals: no (see config.log) [/COLOR]
[COLOR=#800000]  cairo-based terminals: no (requires cairo>1.2, pango>1.10)[/COLOR]
[COLOR=#800000]  lua/TikZ terminal: no [/COLOR]
[COLOR=#800000]  wxt terminal: no (requires C++, wxWidgets>2.6, cairo>0.9, pango>1.10)[/COLOR]
[COLOR=#800000]  Qt terminal: no (use --with-qt or --with-qt=qt4 to enable[/COLOR]


So, I already got half of my answer. But how do I update wxWidgets, cario and pango packages?
Thanks for your help :)

---

### Post by steeldriver on 2015-09-14
So I guess it simply skips building the x11/wxt terminal types if it fails to find the necessary development components

I apparently *have* built it (including both x11 and wxt terminal types) - but I can't remember the exact hoops I had to jump through

```
$ src/gnuplot

    [B]G N U P L O T
    Version 5.0 patchlevel 0    last modified 2015-01-01[/B] 

    Copyright (C) 1986-1993, 1998, 2004, 2007-2015
    Thomas Williams, Colin Kelley and many others

    gnuplot home:     [http://www.gnuplot.info](http://www.gnuplot.info)
    faq, bugs, etc:   type "help FAQ"
    immediate help:   type "help"  (plot window: hit 'h')

Terminal type set to 'wxt'
gnuplot> set term

Available terminal types:
       cairolatex  LaTeX picture environment using graphicx package and Cairo backend
           canvas  HTML Canvas object
              cgm  Computer Graphics Metafile
        .
        .
        .
             tpic  TPIC -- LaTeX picture environment with tpic \specials
          unknown  Unknown terminal type - not a plotting device
            vttek  VT-like tek40xx terminal emulator
              [B]wxt  wxWidgets cross-platform windowed terminal
              x11  X11 Window System
             xlib  X11 Window System (gnulib_x11 dump)
            xterm  Xterm Tektronix 4014 Mode[/B]
gnuplot>
```

I did a bit of reverse fu on the WX_LIBS from my own config.log - based on that, my best guess of the required packages for a wxt terminal type is

```

libatk1.0-dev
libcairo2-dev
libfontconfig1-dev
libfreetype6-dev
libgdk-pixbuf2.0-dev
libglib2.0-dev
libgtk2.0-dev
libpango1.0-dev
libwxbase3.0-dev
libwxgtk3.0-dev

```

Likely installing these will pull in a superset of the requirements for the x11 terminal as well - try it and see what your config.log looks like after

---

### Post by tgalati4 on 2015-09-14
Try adding some libraries and recompile.  Understand that using a newer version may depend on newer versions of libraries than you have installed.

> tgalati4@Mint17 ~ $ apt-cache depends gnuplot
gnuplot
 |Depends: gnuplot-nox
    gnuplot-qt
    gnuplot-x11
 |Depends: gnuplot-x11
    gnuplot-qt
  Depends: gnuplot-qt
  Suggests: feedgnuplot
  Suggests: gnuplot-doc
  Suggests: libgnuplot-iostream-dev
  Suggests: python-gnuplot
tgalati4@Mint17 ~ $ apt-cache depends gnuplot-x11
gnuplot-x11
  Depends: aglfn
  Depends: libc6
  Depends: libcairo2
  Depends: libedit2
  Depends: libgcc1
  Depends: libgd3
  Depends: libglib2.0-0
  Depends: liblua5.1-0
  Depends: libpango-1.0-0
  Depends: libpangocairo-1.0-0
  Depends: libstdc++6
  Depends: libwxbase2.8-0
  Depends: libwxgtk2.8-0
  Depends: libx11-6
  Suggests: gnuplot-doc
  Conflicts: gnuplot-nox
    gnuplot-qt
  Conflicts: gnuplot-nox:i386
    gnuplot-qt:i386
  Conflicts: gnuplot-qt
  Conflicts: gnuplot-qt:i386
  Conflicts: gnuplot-x11:i386


---

### Post by BuboBubo on 2015-09-18
Thank you. 

I've installed all the libraries, and run the gnuplot installation once more.
I have x11! Out of some reason, wxt is still not installed, but I'm already 
happy with x11. 

Cheers!

---

### Post by tgalati4 on 2015-09-18
There are a lot of support libraries that are needed for wxWidgets to work correctly.

```
apt-cache search wxt
apt-cache search wxWidgets
```

At a minimum:

Depends: libwxbase2.8-0
Depends: libwxgtk2.8-0

---

