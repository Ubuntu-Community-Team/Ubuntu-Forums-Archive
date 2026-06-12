---
title: "installing GTK+ in Ubunutu"
date: 2015-05-06
forum: Installation &amp; Upgrades
---

### Post by mkmahmoud2100 on 2015-05-06
[FONT=Times New Roman][SIZE=3]INSTALL GTK+ FROM SCRATCH

[/SIZE][/FONT]

 
[LIST=1]
[*][FONT=Times New Roman][SIZE=3]install     pkg-config[/SIZE][/FONT] 
[*][FONT=Times New Roman][SIZE=3]install     GNU make or Gmake[/SIZE][/FONT] 
[*][FONT=Times New Roman][SIZE=3]install     GLIB[/SIZE][/FONT]
[LIST=1]
[*][FONT=Times New Roman][SIZE=3]%         tar xf glib-2.45.1.tar.gz       # unpack the sources [/SIZE][/FONT] 
[*]  [FONT=Times New Roman][SIZE=3]%         cd glib-2.45.1                  # change to the toplevel directory [/SIZE][/FONT] 
[*]  [FONT=Times New Roman][SIZE=3]%         ./configure                             # run the `configure'         script [/SIZE][/FONT] 
[*]  [FONT=Times New Roman][SIZE=3]%         make                                    # build GLIB  [/SIZE][/FONT] 
[*]  [FONT=Times New Roman][SIZE=3][         Become root if necessary ] [/SIZE][/FONT] 
[*]  [FONT=Times New Roman][SIZE=3]%         rm -rf /install-prefix/include/glib.h         /install-prefix/include/gmodule.h [/SIZE][/FONT] 
[*]  [FONT=Times New Roman][SIZE=3]%         make install                            # install GLIB [/SIZE][/FONT] 
[/LIST]
  
[*][FONT=Times New Roman][SIZE=3]install     GDK-pixbuf library[/SIZE][/FONT]
[LIST=1]
[*][FONT=Times New Roman][SIZE=3]configure:         error:  [/SIZE][/FONT] 
[*][FONT=Times New Roman][SIZE=3]***         GLIB 2.37.6 or better is required. The latest version of [/SIZE][/FONT] 
[*][FONT=Times New Roman][SIZE=3]***         GLIB is always available from [ftp://ftp.gtk.org/pub/gtk/](ftp://ftp.gtk.org/pub/gtk/). [/SIZE][/FONT] 
[/LIST]
    
[/LIST]
 [FONT=Times New Roman][SIZE=3]    Solution:[/SIZE][/FONT]
 
[LIST=1]
[*][FONT=Times New Roman][SIZE=3]To     check the [/SIZE][/FONT]**[FONT=Times New Roman][SIZE=3]PKG_CONFIG_PATH[/SIZE][/FONT]**[FONT=Times New Roman][SIZE=3]     value use the command echo [/SIZE][/FONT][FONT=Times New Roman][SIZE=3]$PKG_CONFIG_PATH[/SIZE][/FONT] 
[*][FONT=Times New Roman][SIZE=3]export     PKG_CONFIG_PATH=/usr/lib/pkgconfig [/SIZE][/FONT]     
     [FONT=Times New Roman][SIZE=3]or     export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig[/SIZE][/FONT]
     [FONT=Times New Roman][SIZE=3]it     gives the same error in the other option[/SIZE][/FONT] 
[*][FONT=Times New Roman][SIZE=3]$     LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH      [/SIZE][/FONT] 
[*][FONT=Times New Roman][SIZE=3]$     export LD_LIBRARY_PATH configure: error:  [/SIZE][/FONT]
     [FONT=Times New Roman][SIZE=3]***     Checks for TIFF loader failed. You can build without it by passing [/SIZE][/FONT]
     [FONT=Times New Roman][SIZE=3]***     --without-libtiff to configure but some programs using GTK+ may [/SIZE][/FONT]
     [FONT=Times New Roman][SIZE=3]***     not work properly [/SIZE][/FONT] 
[*][FONT=Times New Roman][SIZE=3]install     libtiff-tool from ubuntu software center[/SIZE][/FONT] 
[/LIST]
 

 
[LIST=1]
[*][FONT=Times New Roman][SIZE=3]Instal     Pango library[/SIZE][/FONT]
[LIST=1]
[*][FONT=Times New Roman][SIZE=3]configure:         error: *** Could not enable any backends. *** Must have at least         one backend to build Pango. [/SIZE][/FONT] 
[*][FONT=Times New Roman][SIZE=3]install         cairo[/SIZE][/FONT] 
[*][FONT=Times New Roman][SIZE=3]fontconfig         [/SIZE][/FONT] 
[*][FONT=Times New Roman][SIZE=3]FreeType         [/SIZE][/FONT] 
[*][FONT=Times New Roman][SIZE=3]HarfBuzz         [/SIZE][/FONT] 
[/LIST]
  
[*][FONT=Times New Roman][SIZE=3]install     ATK[/SIZE][/FONT] 
[*][FONT=Times New Roman][SIZE=3]gobject-introspection[/SIZE][/FONT]
[LIST=1]
[*][FONT=Times New Roman][SIZE=3]configure:         error: flex not found but required [/SIZE][/FONT] 
[*][FONT=Times New Roman][SIZE=3]install         flex “ in terminal write apt-get install flex”[/SIZE][/FONT] 
[*][FONT=Times New Roman][SIZE=3]error:         bison not found but required[/SIZE][/FONT] 
[*][FONT=Times New Roman][SIZE=3]install         bison from terminal or ubuntu software center “sudo apt-get         install bison”[/SIZE][/FONT] 
[/LIST]
    
[/LIST]


[FONT=Times New Roman][SIZE=3]External dependencies[/SIZE][/FONT]
 

 
[LIST=1]
[*][FONT=Times New Roman][SIZE=3]The     GNU libiconv library is needed to build GLib if your system doesn't     have the [/SIZE][/FONT][FONT=Times New Roman][SIZE=3]iconv()     [/SIZE][/FONT][FONT=Times New Roman][SIZE=3]function     for doing conversion between character encodings. Most modern     systems should have [/SIZE][/FONT][FONT=Times New Roman][SIZE=3]iconv()[/SIZE][/FONT][FONT=Times New Roman][SIZE=3].[/SIZE][/FONT] 
[*][FONT=Times New Roman][SIZE=3]The     libintl library from the GNU gettext package is needed if your     system doesn't have the [/SIZE][/FONT][FONT=Times New Roman][SIZE=3]gettext()     [/SIZE][/FONT][FONT=Times New Roman][SIZE=3]functionality     for handling message translation databases.[/SIZE][/FONT] 
[*][FONT=Times New Roman][SIZE=3]The     libraries from the X window system are needed to build Pango and     GTK+. You should already have these installed on your system, but     it's possible that you'll need to install the development     environment for these libraries that your operating system vendor     provides.[/SIZE][/FONT] 
[*][FONT=Times New Roman][SIZE=3]The     fontconfig library provides Pango with a standard way of locating     fonts and matching them against font names.[/SIZE][/FONT] 
[*][FONT=Times New Roman][SIZE=3]Cairo     is a graphics library that supports vector graphics and image     compositing. Both Pango and GTK+ use cairo for all of their drawing.[/SIZE][/FONT] 
[*][FONT=Times New Roman][SIZE=3]The     shared-mime-info package is not a hard dependency of GTK+, but it     contains definitions for mime types that are used by GIO and,     indirectly, by GTK+. gdk-pixbuf will use GIO for mime type detection     if possible. For this to work, shared-mime-info needs to be     installed and [/SIZE][/FONT][FONT=Times New Roman][SIZE=3]XDG_DATA_DIRS     [/SIZE][/FONT][FONT=Times New Roman][SIZE=3]set     accordingly at configure time. Otherwise, gdk-pixbuf falls back to     its built-in mime type detection[/SIZE][/FONT] 
[*][FONT=Times New Roman][SIZE=3]install     GTK+[/SIZE][/FONT] 
[/LIST]
 


 [FONT=Times New Roman][SIZE=3]    Good Luck from “Mahmoud Aburub”[/SIZE][/FONT]

---

### Post by dino99 on 2015-05-06
What that thread is supposed to explain ?

---

