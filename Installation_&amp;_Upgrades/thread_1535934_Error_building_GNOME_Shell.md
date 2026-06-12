---
title: "Error building GNOME Shell"
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by wersdaluv on 2010-07-21
Been trying to build GNOME Shell, because PPA versions and the one from the official repo don't work. I'm on Lucid, where the versions of GNOME Shell that I've tried are extremely slow. This is the case for my two laptops (both have Intel GM965, X3100).

All stages built fine until I reached stage 20 out of 21. I got this error message while building:
```
*** Checking out gnome-shell *** [20/21]
git clone git://git.gnome.org/gnome-shell
Initialized empty Git repository in /home/allan/gnome-shell/source/gnome-shell/.git/
remote: Counting objects: 11637, done.
remote: Compressing objects: 100% (4775/4775), done.
remote: Total 11637 (delta 8858), reused 8833 (delta 6623)
Receiving objects: 100% (11637/11637), 2.65 MiB | 372 KiB/s, done.
Resolving deltas: 100% (8858/8858), done.
git pull --rebase
Current branch master is up to date.
*** Configuring gnome-shell *** [20/21]
./autogen.sh --prefix /home/allan/gnome-shell/install --libdir '/home/allan/gnome-shell/install/lib'  --disable-static --disable-gtk-doc 
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.65
checking for automake >= 1.9...
  testing automake-1.11... found 1.11.1
checking for libtool >= 1.5...
  testing libtoolize... found 2.2.6b
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.25.12
checking for intltool >= 0.30...
  testing intltoolize... found 0.41.0
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.22
checking for gnome-common >= 2.3.0...
  testing gnome-doc-common... found 2.28.0
Checking for required M4 macros...
Checking for forbidden M4 macros...
Processing ./configure.ac
Running libtoolize...
libtoolize: putting auxiliary files in AC_CONFIG_AUX_DIR, `config'.
libtoolize: copying file `config/ltmain.sh'
libtoolize: putting macros in AC_CONFIG_MACRO_DIR, `m4'.
libtoolize: copying file `m4/libtool.m4'
libtoolize: copying file `m4/ltoptions.m4'
libtoolize: copying file `m4/ltsugar.m4'
libtoolize: copying file `m4/ltversion.m4'
libtoolize: copying file `m4/lt~obsolete.m4'
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Running intltoolize...
Running gnome-doc-common...
Running aclocal-1.11...
Running autoconf...
Running autoheader...
Running automake-1.11...
configure.ac:17: installing `config/compile'
configure.ac:21: installing `config/config.guess'
configure.ac:21: installing `config/config.sub'
configure.ac:9: installing `config/install-sh'
configure.ac:9: installing `config/missing'
src/Makefile.am: installing `config/depcomp'
Running ./configure --enable-maintainer-mode --prefix /home/allan/gnome-shell/install --libdir /home/allan/gnome-shell/install/lib --disable-static --disable-gtk-doc ...
configure: WARNING: unrecognized options: --disable-gtk-doc
checking for a BSD-compatible install... /usr/bin/install-check
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking whether NLS is requested... yes
checking for intltool >= 0.26... 0.41.0 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.10.1
checking for XML::Parser... ok
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.22... yes
checking for gconftool-2... /home/allan/gnome-shell/install/bin/gconftool-2
Using config source xml:merged:/home/allan/gnome-shell/install/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
checking for a Python interpreter with version >= 2.5... python
checking for python... /usr/bin/python
checking for python version... 2.6
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.6/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.6/site-packages
checking for GStreamer (needed for recording functionality)... yes
checking for TEST_SHELL_RECORDER... yes
checking for MUTTER_PLUGIN... yes
checking for sn_startup_sequence_get_application_id... no
checking for TIDY... yes
checking for ST... yes
checking for GDMUSER... yes
checking for TRAY... yes
checking for fdwalk... no
checking for mallinfo... yes
checking sys/resource.h usability... yes
checking sys/resource.h presence... yes
checking for sys/resource.h... yes
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
checking for GLIB - version >= 2.0.0... yes (version 2.25.12)
checking for mutter... /home/allan/gnome-shell/install/bin/mutter
checking if mutter was compiled with GTK+-3.0... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating data/Makefile
config.status: creating js/Makefile
config.status: creating js/misc/Makefile
config.status: creating js/ui/Makefile
config.status: creating js/perf/Makefile
config.status: creating js/prefs/Makefile
config.status: creating src/Makefile
config.status: creating tests/Makefile
config.status: creating po/Makefile.in
config.status: creating man/Makefile
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing libtool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands
configure: WARNING: unrecognized options: --disable-gtk-doc
Now type `make' to compile gnome-shell
*** Building gnome-shell *** [20/21]
make  
make  all-recursive
make[1]: Entering directory `/home/allan/gnome-shell/source/gnome-shell'
Making all in data
make[2]: Entering directory `/home/allan/gnome-shell/source/gnome-shell/data'
  GEN    gnome-shell.desktop.in
  GEN    gnome-shell.desktop
  GEN    gnome-shell-clock-preferences.desktop.in
  GEN    gnome-shell-clock-preferences.desktop
LC_ALL=C /usr/bin/intltool-merge -x -u /tmp org.gnome.shell.gschema.xml.in org.gnome.shell.gschema.xml
Merging translations into org.gnome.shell.gschema.xml.
CREATED org.gnome.shell.gschema.xml
  GEN    org.gnome.shell.gschema.valid
  GEN    gschemas.compiled
rm gnome-shell-clock-preferences.desktop.in gnome-shell.desktop.in
make[2]: Leaving directory `/home/allan/gnome-shell/source/gnome-shell/data'
Making all in js
make[2]: Entering directory `/home/allan/gnome-shell/source/gnome-shell/js'
Making all in misc
make[3]: Entering directory `/home/allan/gnome-shell/source/gnome-shell/js/misc'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/allan/gnome-shell/source/gnome-shell/js/misc'
Making all in ui
make[3]: Entering directory `/home/allan/gnome-shell/source/gnome-shell/js/ui'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/allan/gnome-shell/source/gnome-shell/js/ui'
Making all in perf
make[3]: Entering directory `/home/allan/gnome-shell/source/gnome-shell/js/perf'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/allan/gnome-shell/source/gnome-shell/js/perf'
Making all in prefs
make[3]: Entering directory `/home/allan/gnome-shell/source/gnome-shell/js/prefs'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/allan/gnome-shell/source/gnome-shell/js/prefs'
make[3]: Entering directory `/home/allan/gnome-shell/source/gnome-shell/js'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/allan/gnome-shell/source/gnome-shell/js'
make[2]: Leaving directory `/home/allan/gnome-shell/source/gnome-shell/js'
Making all in src
make[2]: Entering directory `/home/allan/gnome-shell/source/gnome-shell/src'
  GEN    stamp-st-enum-types.h
  GEN    st-enum-types.c
  GEN    stamp-st-marshal.h
  GEN    st-marshal.c
  GEN    st.h
  GEN    stamp-na-marshal.h
  GEN    na-marshal.c
  GEN    stamp-shell-marshal.h
  GEN    shell-marshal.c
  GEN    stamp-shell-enum-types.h
  GEN    shell-enum-types.c
make  all-am
make[3]: Entering directory `/home/allan/gnome-shell/source/gnome-shell/src'
  CC     libgdmuser_1_0_la-gdm-user.lo
  CC     libgdmuser_1_0_la-gdm-user-manager.lo
  CCLD   libgdmuser-1.0.la
  CC     libst_1_0_la-st-adjustment.lo
  CC     libst_1_0_la-st-bin.lo
  CC     libst_1_0_la-st-border-image.lo
  CC     libst_1_0_la-st-box-layout.lo
  CC     libst_1_0_la-st-box-layout-child.lo
  CC     libst_1_0_la-st-button.lo
  CC     libst_1_0_la-st-clickable.lo
  CC     libst_1_0_la-st-clipboard.lo
  CC     libst_1_0_la-st-container.lo
  CC     libst_1_0_la-st-drawing-area.lo
  CC     libst_1_0_la-st-entry.lo
  CC     libst_1_0_la-st-group.lo
  CC     libst_1_0_la-st-im-text.lo
  CC     libst_1_0_la-st-label.lo
  CC     libst_1_0_la-st-overflow-box.lo
  CC     libst_1_0_la-st-private.lo
  CC     libst_1_0_la-st-scrollable.lo
  CC     libst_1_0_la-st-scroll-bar.lo
  CC     libst_1_0_la-st-scroll-view.lo
  CC     libst_1_0_la-st-shadow.lo
  CC     libst_1_0_la-st-subtexture.lo
  CC     libst_1_0_la-st-table.lo
  CC     libst_1_0_la-st-table-child.lo
  CC     libst_1_0_la-st-texture-cache.lo
  CC     libst_1_0_la-st-theme.lo
  CC     libst_1_0_la-st-theme-context.lo
  CC     libst_1_0_la-st-theme-node.lo
  CC     libst_1_0_la-st-theme-node-drawing.lo
  CC     libst_1_0_la-st-theme-node-transition.lo
  CC     libst_1_0_la-st-tooltip.lo
  CC     libst_1_0_la-st-widget.lo
  CC     libst_1_0_la-st-enum-types.lo
  CC     libst_1_0_la-st-marshal.lo
  CCLD   libst-1.0.la
  CC     libtray_la-na-tray-child.lo
  CC     libtray_la-na-tray-manager.lo
  CC     libtray_la-na-marshal.lo
  CCLD   libtray.la
  CC     libgnome_shell_la-shell-marshal.lo
  CC     libgnome_shell_la-shell-enum-types.lo
  CC     libgnome_shell_la-shell-recorder-src.lo
  CC     libgnome_shell_la-gnome-shell-plugin.lo
  CC     libgnome_shell_la-shell-app.lo
  CC     libgnome_shell_la-shell-app-system.lo
  CC     libgnome_shell_la-shell-app-usage.lo
  CC     libgnome_shell_la-shell-arrow.lo
  CC     libgnome_shell_la-shell-doc-system.lo
  CC     libgnome_shell_la-shell-drawing.lo
  CC     libgnome_shell_la-shell-embedded-window.lo
  CC     libgnome_shell_la-shell-generic-container.lo
  CC     libgnome_shell_la-shell-gtk-embed.lo
  CC     libgnome_shell_la-shell-process.lo
  CC     libgnome_shell_la-shell-global.lo
  CC     libgnome_shell_la-shell-perf-log.lo
  CC     libgnome_shell_la-shell-slicer.lo
  CC     libgnome_shell_la-shell-stack.lo
  CC     libgnome_shell_la-shell-tray-manager.lo
  CC     libgnome_shell_la-shell-uri-util.lo
  CC     libgnome_shell_la-shell-window-tracker.lo
  CC     libgnome_shell_la-shell-wm.lo
  CC     libgnome_shell_la-shell-xfixes-cursor.lo
  CC     libgnome_shell_la-shell-recorder.lo
  CCLD   libgnome-shell.la
  CC     test_theme-test-theme.o
  CCLD   test-theme
/home/allan/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_variant_new_bytestring_array'
/home/allan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_value_set_variant'
/home/allan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_new_bytestring'
/home/allan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_param_spec_variant'
/home/allan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_is_floating'
/home/allan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_dcgettext'
/home/allan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_value_get_variant'
/home/allan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_error_get_type'
/home/allan/gnome-shell/install/lib/libgtk-x11-3.0.so: undefined reference to `g_cclosure_marshal_VOID__VARIANT'
/home/allan/gnome-shell/install/lib/libgdk-x11-3.0.so: undefined reference to `g_source_set_name'
/home/allan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_value_dup_variant'
/home/allan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_compare'
/home/allan/gnome-shell/install/lib/libgio-2.0.so: undefined reference to `g_variant_get_bytestring'
collect2: ld returned 1 exit status
make[3]: *** [test-theme] Error 1
make[3]: Leaving directory `/home/allan/gnome-shell/source/gnome-shell/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/allan/gnome-shell/source/gnome-shell/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/allan/gnome-shell/source/gnome-shell'
make: *** [all] Error 2
*** Error during phase build of gnome-shell: ########## Error running make   *** [20/21]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"

```

What's the fix?

---

### Post by mixint27 on 2010-07-28
bump! I get stuck here too.

---

### Post by alphonce on 2010-07-28
here's the bug with a fix:
[https://bugzilla.gnome.org/show_bug.cgi?id=623952]("https://bugzilla.gnome.org/show_bug.cgi?id=623952")

trying the fix now =)

---

### Post by jcress410 on 2010-09-19
any advice if I've tried all the fixes at 

[https://bugzilla.gnome.org/show_bug.cgi?id=623952](https://bugzilla.gnome.org/show_bug.cgi?id=623952) 

and i'm still not able to finish compiling?

---

