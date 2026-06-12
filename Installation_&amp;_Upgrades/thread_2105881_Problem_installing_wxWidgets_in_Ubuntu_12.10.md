---
title: "Problem installing wxWidgets in Ubuntu 12.10"
date: 2013-01-17
forum: Installation &amp; Upgrades
---

### Post by kevincmaker on 2013-01-17
Hello!

I have a problem in installing wxWidgets in Ubuntu 12.10. When I try to install it by following the instructions given in the wiki page of wxWidgets, I get an error message that says something like the path og GTK is not identified. Not sure about that; so below is the message that I get when I try to configure it.

```
kevin@kevin-PC:~/Software/wxwidgets/wxWidgets-2.9.4/gtk-build$ ../configure --enable-unicode CFLAGS="-fPIC" CXXFLAGS="-fPIC"
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for --disable-gui... no
checking for --enable-monolithic... no
checking for --enable-plugins... no
checking for --without-subdirs... no
checking for --enable-official_build... no
checking for --disable-all-features... no
checking for --enable-universal... no
checking for --enable-nanox... no
checking for --enable-gpe... no
checking for toolkit... gtk
checking for --with-libpng... yes
checking for --with-libjpeg... yes
checking for --with-libtiff... yes
checking for --with-libxpm... yes
checking for --with-libiconv... yes
checking for --with-libmspack... no
checking for --without-gtkprint... no
checking for --without-gnomeprint... no
checking for --with-gnomevfs... no
checking for --with-hildon... no
checking for --with-opengl... auto
checking for --with-dmalloc... no
checking for --with-sdl... no
checking for --with-regex... yes
checking for --with-zlib... yes
checking for --with-expat... yes
checking for --with-macosx-sdk... 
checking for --with-macosx-version-min... 
checking for --enable-debug... default
checking for --disable-debug_flag... no
checking for --enable-debug_info... no
checking for --enable-debug_gdb... no
checking for --enable-debug_cntxt... no
checking for --enable-mem_tracing... no
checking for --disable-shared... no
checking for --enable-stl... no
checking for --enable-std_containers... no
checking for --enable-std_iostreams... yes
checking for --enable-std_string... yes
checking for --enable-std_string_conv_in_wxstring... no
checking for --disable-unicode... no
checking for --enable-mslu... no
checking for --enable-utf8... no
checking for --enable-utf8only... no
checking for --enable-extended_rtti... no
checking for --disable-optimise... no
checking for --enable-profile... no
checking for --enable-no_rtti... no
checking for --enable-no_exceptions... no
checking for --enable-permissive... no
checking for --enable-no_deps... no
checking for --disable-vararg_macros... no
checking for --enable-universal_binary... no
checking for --enable-macosx_arch... no
checking for --enable-compat26... no
checking for --disable-compat28... no
checking for --disable-rpath... no
checking for --enable-objc_uniquifying... no
checking for --disable-visibility... no
checking for --disable-tls... no
checking for --enable-intl... yes
checking for --enable-xlocale... yes
checking for --enable-config... yes
checking for --enable-protocols... yes
checking for --enable-ftp... yes
checking for --enable-http... yes
checking for --enable-fileproto... yes
checking for --enable-sockets... yes
checking for --enable-ipv6... no
checking for --enable-ole... yes
checking for --enable-dataobj... yes
checking for --enable-ipc... yes
checking for --enable-baseevtloop... yes
checking for --enable-epollloop... yes
checking for --enable-selectloop... yes
checking for --enable-any... yes
checking for --enable-apple_ieee... yes
checking for --enable-arcstream... yes
checking for --enable-base64... yes
checking for --enable-backtrace... yes
checking for --enable-catch_segvs... yes
checking for --enable-cmdline... yes
checking for --enable-datetime... yes
checking for --enable-debugreport... yes
checking for --enable-dialupman... yes
checking for --enable-dynlib... yes
checking for --enable-dynamicloader... yes
checking for --enable-exceptions... yes
checking for --enable-ffile... yes
checking for --enable-file... yes
checking for --enable-filehistory... yes
checking for --enable-filesystem... yes
checking for --enable-fontenum... yes
checking for --enable-fontmap... yes
checking for --enable-fs_archive... yes
checking for --enable-fs_inet... yes
checking for --enable-fs_zip... yes
checking for --enable-fswatcher... yes
checking for --enable-geometry... yes
checking for --enable-log... yes
checking for --enable-longlong... yes
checking for --enable-mimetype... yes
checking for --enable-printfposparam... yes
checking for --enable-snglinst... yes
checking for --enable-sound... yes
checking for --enable-stdpaths... yes
checking for --enable-stopwatch... yes
checking for --enable-streams... yes
checking for --enable-sysoptions... yes
checking for --enable-tarstream... yes
checking for --enable-textbuf... yes
checking for --enable-textfile... yes
checking for --enable-timer... yes
checking for --enable-variant... yes
checking for --enable-zipstream... yes
checking for --enable-url... yes
checking for --enable-protocol... yes
checking for --enable-protocol_http... yes
checking for --enable-protocol_ftp... yes
checking for --enable-protocol_file... yes
checking for --enable-threads... yes
checking for --enable-iniconf... no
checking for --enable-regkey... yes
checking for --enable-docview... yes
checking for --enable-help... yes
checking for --enable-mshtmlhelp... yes
checking for --enable-html... yes
checking for --enable-htmlhelp... yes
checking for --enable-xrc... yes
checking for --enable-aui... yes
checking for --enable-propgrid... yes
checking for --enable-ribbon... yes
checking for --enable-stc... yes
checking for --enable-constraints... yes
checking for --enable-loggui... yes
checking for --enable-logwin... yes
checking for --enable-logdialog... yes
checking for --enable-mdi... yes
checking for --enable-mdidoc... yes
checking for --enable-mediactrl... auto
checking for --enable-gstreamer8... no
checking for --enable-richtext... yes
checking for --enable-postscript... yes
checking for --enable-printarch... yes
checking for --enable-svg... yes
checking for --enable-webkit... yes
checking for --enable-webview... yes
checking for --enable-graphics_ctx... yes
checking for --enable-clipboard... yes
checking for --enable-dnd... yes
checking for --disable-controls... no
checking for --enable-markup... yes
checking for --enable-accel... yes
checking for --enable-animatectrl... yes
checking for --enable-bannerwindow... yes
checking for --enable-artstd... yes
checking for --enable-arttango... auto
checking for --enable-bmpbutton... yes
checking for --enable-bmpcombobox... yes
checking for --enable-button... yes
checking for --enable-calendar... yes
checking for --enable-caret... yes
checking for --enable-checkbox... yes
checking for --enable-checklst... yes
checking for --enable-choice... yes
checking for --enable-choicebook... yes
checking for --enable-collpane... yes
checking for --enable-colourpicker... yes
checking for --enable-combobox... yes
checking for --enable-comboctrl... yes
checking for --enable-commandlinkbutton... yes
checking for --enable-dataviewctrl... yes
checking for --enable-datepick... yes
checking for --enable-detect_sm... yes
checking for --enable-dirpicker... yes
checking for --enable-display... yes
checking for --enable-editablebox... yes
checking for --enable-filectrl... yes
checking for --enable-filepicker... yes
checking for --enable-fontpicker... yes
checking for --enable-gauge... yes
checking for --enable-grid... yes
checking for --enable-headerctrl... yes
checking for --enable-hyperlink... yes
checking for --enable-imaglist... yes
checking for --enable-infobar... yes
checking for --enable-listbook... yes
checking for --enable-listbox... yes
checking for --enable-listctrl... yes
checking for --enable-notebook... yes
checking for --enable-notifmsg... yes
checking for --enable-odcombobox... yes
checking for --enable-popupwin... yes
checking for --enable-radiobox... yes
checking for --enable-radiobtn... yes
checking for --enable-richmsgdlg... yes
checking for --enable-richtooltip... yes
checking for --enable-rearrangectrl... yes
checking for --enable-sash... yes
checking for --enable-scrollbar... yes
checking for --enable-searchctrl... yes
checking for --enable-slider... yes
checking for --enable-spinbtn... yes
checking for --enable-spinctrl... yes
checking for --enable-splitter... yes
checking for --enable-statbmp... yes
checking for --enable-statbox... yes
checking for --enable-statline... yes
checking for --enable-stattext... yes
checking for --enable-statusbar... yes
checking for --enable-taskbaricon... yes
checking for --enable-tbarnative... yes
checking for --enable-textctrl... yes
checking for --enable-datepick... yes
checking for --enable-tipwindow... yes
checking for --enable-togglebtn... yes
checking for --enable-toolbar... yes
checking for --enable-toolbook... yes
checking for --enable-treebook... yes
checking for --enable-treectrl... yes
checking for --enable-treelist... yes
checking for --enable-commondlg... yes
checking for --enable-aboutdlg... yes
checking for --enable-choicedlg... yes
checking for --enable-coldlg... yes
checking for --enable-filedlg... yes
checking for --enable-finddlg... yes
checking for --enable-fontdlg... yes
checking for --enable-dirdlg... yes
checking for --enable-msgdlg... yes
checking for --enable-numberdlg... yes
checking for --enable-splash... yes
checking for --enable-textdlg... yes
checking for --enable-tipdlg... yes
checking for --enable-progressdlg... yes
checking for --enable-wizarddlg... yes
checking for --enable-menus... yes
checking for --enable-miniframe... yes
checking for --enable-tooltips... yes
checking for --enable-splines... yes
checking for --enable-mousewheel... yes
checking for --enable-validators... yes
checking for --enable-busyinfo... yes
checking for --enable-hotkey... auto
checking for --enable-joystick... yes
checking for --enable-metafile... auto
checking for --enable-dragimage... yes
checking for --enable-accessibility... no
checking for --enable-uiactionsim... yes
checking for --enable-dctransform... yes
checking for --enable-webviewwebkit... yes
checking for --enable-palette... yes
checking for --enable-image... yes
checking for --enable-gif... yes
checking for --enable-pcx... yes
checking for --enable-tga... yes
checking for --enable-iff... yes
checking for --enable-pnm... yes
checking for --enable-xpm... yes
checking for --enable-ico_cur... yes
checking for --enable-dccache... yes
checking for --enable-ps-in-msw... yes
checking for --enable-ownerdrawn... yes
checking for --enable-uxtheme... yes
checking for --enable-wxdib... yes
checking for --enable-webviewie... yes
checking for --enable-autoidman... no
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether we are using the Intel C compiler... no
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking whether gcc needs -traditional... no
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking whether we are using the Intel C++ compiler... no
checking whether we are using the Sun C++ compiler... no
checking for ar... ar
checking for strcasecmp() in string.h... yes
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
checking for langinfo.h... yes
checking for wchar.h... yes
checking for sys/select.h... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking size of short... 2
checking size of void *... 8
checking size of int... 4
checking size of long... 8
checking size of size_t... 8
checking size of long long... 8
checking size of wchar_t... 4
checking for va_copy... yes
checking whether the compiler supports variadic macros... yes
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking if large file support is available... yes
checking for _LARGEFILE_SOURCE value needed for large files... no
checking whether byte ordering is bigendian... no
checking for iostream... yes
checking if C++ compiler supports the explicit keyword... yes
checking for std::wstring in <string>... yes
checking for std::istream... yes
checking for std::ostream... yes
checking how to run the C++ preprocessor... g++ -E
checking type_traits usability... no
checking type_traits presence... no
checking for type_traits... no
checking tr1/type_traits usability... yes
checking tr1/type_traits presence... yes
checking for tr1/type_traits... yes
checking for __sync_fetch_and_add and __sync_sub_and_fetch builtins... yes
checking for libraries directories... /usr/lib/x86_64-linux-gnu /usr/lib
checking for cos... no
checking for floor... no
checking if floating point functions link without -lm... no
checking for sin... yes
checking for ceil... yes
checking if floating point functions link with -lm... yes
checking for strtoull... yes
configure: WARNING: Defaulting to the builtin regex library for Unicode build.
checking for zlib.h >= 1.1.4... no
checking for zlib.h... (cached) no
configure: WARNING: zlib library not found or too old, will use built-in instead
checking for png.h > 0.90... no
checking for png.h... (cached) no
configure: WARNING: system png library not found or too old, will use built-in instead
checking for jpeglib.h... no
configure: WARNING: system jpeg library not found, will use built-in instead
checking for tiffio.h... no
configure: WARNING: system tiff library not found, will use built-in instead
checking for expat.h... no
configure: WARNING: system expat library not found, will use built-in instead
checking for GTK+ version... 
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.4.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occurred. This usually means GTK+ is incorrectly installed.
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for GTK+ - version >= 3.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
checking for gtk-config... no
checking for GTK - version >= 1.2.7... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
checking for gtk-config... (cached) no
checking for GTK - version >= 1.2.3... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: error: 
The development files for GTK+ were not found. For GTK+ 2, please
ensure that pkg-config is in the path and that gtk+-2.0.pc is
installed. For GTK+ 1.2 please check that gtk-config is in the path,
and that the version is 1.2.3 or above. Also check that the
libraries returned by 'pkg-config gtk+-2.0 --libs' or 'gtk-config
--libs' are in the LD_LIBRARY_PATH or equivalent.

```

I am not an experienced Ubuntu user, so please don't mind my ignorance :)

---

### Post by Frogs Hair on 2013-01-17
If you are on 11.10 or higher you are using  Gnome 3 + and I am wondering if the program is compatible based on the output. There is a contact for IRC and email on the developer site so you can find out. [http://www.wxwidgets.org/support/](http://www.wxwidgets.org/support/)

```
configure: error: 
The development files for GTK+ were not found. For GTK+ 2, please
ensure that pkg-config is in the path and that gtk+-2.0.pc is
installed. For GTK+ 1.2 please check that gtk-config is in the path,
and that the version is 1.2.3 or above. Also check that the
libraries returned by 'pkg-config gtk+-2.0 --libs' or 'gtk-config
--libs' are in the LD_LIBRARY_PATH or equivalent.
```

---

