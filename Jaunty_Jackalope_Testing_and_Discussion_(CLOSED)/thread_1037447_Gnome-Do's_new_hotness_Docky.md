---
title: "Gnome-Do's new hotness: Docky"
date: 2009-01-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mewithafez on 2009-01-11
[http://do.davebsd.com/wiki/index.php?title=Docky]("http://do.davebsd.com/wiki/index.php?title=Docky")

This could be it; it is available at [https://launchpad.net/do]("https://launchpad.net/do") and basically what it is is a setting for gnome-do that allows it to function as a combo dock/entry panel like AWM but better integrated into the desktop. In Jaunty we are only up to 6.1 or so, this is available in 7.9.5 so while it would take a ton of work to get it stable and up to date, it brings the power of a combined spotlight/quicksilver and dock to app launching.

Please give it a go, or just look at the wiki page and post any impressions here!

EDIT: See Gourgi's post (post #6) for instructions on how best to install from source.

DOUBLE EDIT: See Andrewsomething's post (post #14) for intrepid debs on a PPA.

---

### Post by Kosimo on 2009-01-11
> **mewithafez said:**
> [http://do.davebsd.com/wiki/index.php?title=Docky]("http://do.davebsd.com/wiki/index.php?title=Docky")

This could be it; it is available at [https://launchpad.net/do]("https://launchpad.net/do") and basically what it is is a setting for gnome-do that allows it to function as a combo dock/entry panel like AWM but better integrated into the desktop. In Jaunty we are only up to 6.1 or so, this is available in 7.9.5 so while it would take a ton of work to get it stable and up to date, it brings the power of a combined spotlight/quicksilver and dock to app launching.

Please give it a go, or just look at the wiki page and post any impressions here!

There's any way to install latest alpha 0.8 in intrepid? I've got the source code but I couldn't compile due to some library old versions

---

### Post by Gourgi on 2009-01-11
> **mewithafez said:**
> [http://do.davebsd.com/wiki/index.php?title=Docky]("http://do.davebsd.com/wiki/index.php?title=Docky")

This could be it; it is available at [https://launchpad.net/do]("https://launchpad.net/do") 
how can one install it in jaunty ?
i really liked it !!!

---

### Post by mewithafez on 2009-01-11
I haven't had the chance to install from source either; working and balancing things but I'd guess you could follow these directions and find success:

[http://do.davebsd.com/wiki/index.php?title=Installing_Do#From_Source]("http://do.davebsd.com/wiki/index.php?title=Installing_Do#From_Source")

---

### Post by ronacc on 2009-01-11
I tried to build the 0.7.95.1 source from launchpad but the deps for gnome-sharp-2 are broken right now and it needs that to build .

---

### Post by Gourgi on 2009-01-11
ok i messed around and finally got it install in my jaunty amd 64 :D
looks pretty cool :guitar:

[[IMG]http://img57.imageshack.us/img57/8489/screenshotnk9.th.jpg[/IMG]](http://img57.imageshack.us/my.php?image=screenshotnk9.jpg)
[[IMG]http://img158.imageshack.us/img158/6095/screenshotfk1.th.jpg[/IMG]](http://img158.imageshack.us/my.php?image=screenshotfk1.jpg)
it needs bits of improvement but i think it is really great for an 'alpha' version 
i **definitely** want it in Jaunty Final :p

i'm writing the steps i followed in case anyone wants to install it as well under jaunty since i haven;t found a PPA or .deb availbale yet 

1) firstly lets install the dependencies 
```
sudo apt-get build-dep gnome-do
sudo apt-get install automake bzr mono-gmcs libmono-cairo2.0-cil ca-certificates libtool intltool libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libgnome-vfs2.0-cil   gtk-sharp2-examples gnome-desktop-sharp2 libgconf2-dev build-essential 
```

2) we have to remove any other instance of gnome-do installed in our system
```
sudo apt-get remove gnome-do gnome-do-plugins 
```

3) let's get the newest Do's source
```
bzr branch lp:do
```

4) finally let's install it! 
```
cd do 
./autogen.sh
make
sudo make install
```

5) Enjoy ;)

i also attach the output of './autogen.sh' , 'make' and 'sudo make install' in case anyone cares :D

[COLOR="Red"]autogen.sh[/COLOR] output:

```
$./autogen.sh 
I am going to run ./configure with no arguments - if you wish 
to pass any to it, please specify them on the ./autogen.sh command line.
Running libtoolize ...
libtoolize: putting auxiliary files in `.'.
libtoolize: copying file `./ltmain.sh'
libtoolize: putting macros in AC_CONFIG_MACRO_DIR, `m4'.
libtoolize: copying file `m4/libtool.m4'
libtoolize: copying file `m4/ltoptions.m4'
libtoolize: copying file `m4/ltsugar.m4'
libtoolize: copying file `m4/ltversion.m4'
libtoolize: copying file `m4/lt~obsolete.m4'
Running aclocal -I . -I m4/shamrock  ...
Running automake --gnu  ...
configure.ac:48: installing `./config.guess'
configure.ac:48: installing `./config.sub'
Running autoconf ...
Running intltoolize --force --copy --automake ...
Running ./configure ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a pax tar archive... gnutar
checking whether NLS is requested... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for intltool >= 0.35.0... 0.40.5 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking for catalogs to be installed...  ar ast bg br ca cs da de el en_AU en_CA en_GB es et fa fi fr ga hu id is it ja lt lv mk nb nl nn pl pt_BR pt ru sk sl sr sv ta te th tr uk vi zh_CN zh_HK zh_TW
checking for pkg-config... /usr/bin/pkg-config
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for ANSI C header files... (cached) yes
checking for gmcs... /usr/bin/gmcs
checking for LINQ flag for mcs... none needed
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
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
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking pkg-config is at least version 0.9.0... yes
checking for LIBDO... yes
checking for GCONF_SHARP_20... yes
checking for GLADE_SHARP_20... yes
checking for GLIB_SHARP_20... yes
checking for GNOME_DESKTOP_SHARP_20... yes
checking for GNOME_KEYRING_SHARP... yes
checking for GNOME_SHARP_20... yes
checking for GNOME_VFS_SHARP_20... yes
checking for GTK_SHARP_20... yes
checking for MONO_ADDINS... yes
checking for MONO_ADDINS_GUI... yes
checking for MONO_ADDINS_SETUP... yes
checking for NDESK_DBUS_10... yes
checking for NDESK_DBUS_GLIB_10... yes
checking for NOTIFY_SHARP... yes
checking for WNCK_SHARP_10... yes
checking for NUNIT... no
configure: creating ./config.status
config.status: creating Do/Do.exe.config
config.status: creating Do/Makefile
config.status: creating Do/gnome-do
config.status: creating Do/src/AssemblyInfo.cs
config.status: creating Do.DBus/Makefile
config.status: creating Do.DBus/src/AssemblyInfo.cs
config.status: creating Do.Interface.Linux/Makefile
config.status: creating Do.Interface.Linux/src/AssemblyInfo.cs
config.status: creating Do.Interface.Linux.Classic/Makefile
config.status: creating Do.Interface.Linux.Docky/Makefile
config.status: creating Do.Interface.Linux.GlassFrame/Makefile
config.status: creating Do.Interface.Linux.HUD/Makefile
config.status: creating Do.Interface.Linux.Mini/Makefile
config.status: creating Do.Platform/Makefile
config.status: creating Do.Platform/src/AssemblyInfo.cs
config.status: creating Do.Platform.Linux/Makefile
config.status: creating Do.Platform.Linux/src/AssemblyInfo.cs
config.status: creating Do.Platform.OSX/AssemblyInfo.cs
config.status: creating Do.Platform.Windows/AssemblyInfo.cs
config.status: creating Do.Universe/Makefile
config.status: creating Do.Universe/src/AssemblyInfo.cs
config.status: creating libdo/Makefile
config.status: creating Makefile
config.status: creating data/Makefile
config.status: creating data/icons/Makefile
config.status: creating data/icons/hicolor/16x16/Makefile
config.status: creating data/icons/hicolor/16x16/apps/Makefile
config.status: creating data/icons/hicolor/22x22/Makefile
config.status: creating data/icons/hicolor/22x22/apps/Makefile
config.status: creating data/icons/hicolor/24x24/Makefile
config.status: creating data/icons/hicolor/24x24/apps/Makefile
config.status: creating data/icons/hicolor/32x32/Makefile
config.status: creating data/icons/hicolor/32x32/apps/Makefile
config.status: creating data/icons/hicolor/48x48/Makefile
config.status: creating data/icons/hicolor/48x48/apps/Makefile
config.status: creating data/icons/hicolor/Makefile
config.status: creating data/icons/hicolor/scalable/Makefile
config.status: creating data/icons/hicolor/scalable/apps/Makefile
config.status: creating m4/Makefile
config.status: creating po/Makefile.in
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: executing libtool commands
config.status: executing po/stamp-it commands
# INTLTOOL_MAKEFILE
gourgi@ gourgi:~/temp/installs/do$ 
```

[COLOR="Red"]make[/COLOR] output : 
```
$ make
Making all in .
make[1]: Entering directory `/home/gourgi/temp/installs/do'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/gourgi/temp/installs/do'
Making all in Do.Universe
make[1]: Entering directory `/home/gourgi/temp/installs/do/Do.Universe'
Compiling Do.Universe.dll...
make[1]: Leaving directory `/home/gourgi/temp/installs/do/Do.Universe'
Making all in Do.Platform
make[1]: Entering directory `/home/gourgi/temp/installs/do/Do.Platform'
Compiling Do.Platform.dll...
make[1]: Leaving directory `/home/gourgi/temp/installs/do/Do.Platform'
Making all in Do.Interface.Linux
make[1]: Entering directory `/home/gourgi/temp/installs/do/Do.Interface.Linux'
Compiling Do.Interface.Linux.dll...
make[1]: Leaving directory `/home/gourgi/temp/installs/do/Do.Interface.Linux'
Making all in Do.Interface.Linux.Classic
make[1]: Entering directory `/home/gourgi/temp/installs/do/Do.Interface.Linux.Classic'
Compiling Do.Interface.Linux.Classic.dll...
make[1]: Leaving directory `/home/gourgi/temp/installs/do/Do.Interface.Linux.Classic'
Making all in Do.Interface.Linux.Docky
make[1]: Entering directory `/home/gourgi/temp/installs/do/Do.Interface.Linux.Docky'
Compiling Do.Interface.Linux.Docky.dll...
./src/Docky.Interface/DockArea.cs(149,30): warning CS0108: `Docky.Interface.DockArea.PopupMenu' hides inherited member `Gtk.Widget.PopupMenu'. Use the new keyword if hiding was intended
/usr/lib/mono/gac/gtk-sharp/2.12.0.0__35e10195dab3c99f/gtk-sharp.dll (Location of the symbol related to previous warning)
./src/Docky.Interface/DockItemProvider.cs(317,56): warning CS0184: The given expression is never of the provided (`Do.Universe.ItemSource') type
./src/Docky.Interface/DockWindow.cs(94,22): warning CS0169: The private method `Docky.Interface.DockWindow.OnEventBoxMotion()' is never used
./src/Docky.Interface/DockWindow.cs(45,22): warning CS0414: The private field `Docky.Interface.DockWindow.reposition_timer' is assigned but its value is never used
./src/XLib/Xlib.cs(82,35): warning CS0169: The private method `Docky.XLib.Xlib.XChangeProperty(System.IntPtr, System.IntPtr, System.IntPtr, System.IntPtr, int, int, uint[], int)' is never used
Compilation succeeded - 5 warning(s)
make[1]: Leaving directory `/home/gourgi/temp/installs/do/Do.Interface.Linux.Docky'
Making all in Do.Interface.Linux.GlassFrame
make[1]: Entering directory `/home/gourgi/temp/installs/do/Do.Interface.Linux.GlassFrame'
Compiling Do.Interface.Linux.GlassFrame.dll...
make[1]: Leaving directory `/home/gourgi/temp/installs/do/Do.Interface.Linux.GlassFrame'
Making all in Do.Interface.Linux.HUD
make[1]: Entering directory `/home/gourgi/temp/installs/do/Do.Interface.Linux.HUD'
Compiling Do.Interface.Linux.HUD.dll...
make[1]: Leaving directory `/home/gourgi/temp/installs/do/Do.Interface.Linux.HUD'
Making all in Do.Interface.Linux.Mini
make[1]: Entering directory `/home/gourgi/temp/installs/do/Do.Interface.Linux.Mini'
Compiling Do.Interface.Linux.Mini.dll...
make[1]: Leaving directory `/home/gourgi/temp/installs/do/Do.Interface.Linux.Mini'
Making all in Do.Platform.Linux
make[1]: Entering directory `/home/gourgi/temp/installs/do/Do.Platform.Linux'
Compiling Do.Platform.Linux.dll...
./src/Do.Platform/Do.Platform.Linux/TrayIconService.cs(57,37): warning CS0618: `Gtk.StatusIcon.FromPixbuf' is obsolete: `use the Pixbuf property instead'
./src/Do.Widgets/AbstractLoginWidget.cs(223,22): warning CS0169: The private method `Do.Platform.Linux.AbstractLoginWidget.OnUsernameEntryActivated(object, System.EventArgs)' is never used
Compilation succeeded - 2 warning(s)
make[1]: Leaving directory `/home/gourgi/temp/installs/do/Do.Platform.Linux'
Making all in Do.DBus
make[1]: Entering directory `/home/gourgi/temp/installs/do/Do.DBus'
Compiling Do.DBus.dll...
make[1]: Leaving directory `/home/gourgi/temp/installs/do/Do.DBus'
Making all in Do
make[1]: Entering directory `/home/gourgi/temp/installs/do/Do'
Compiling Do.exe...
./src/Do.Core/UniverseManager.cs(177,41): warning CS1030: #warning: `The Log is not threadsafe...'
./src/Do.UI/ColorConfigurationWidget.cs(72,30): warning CS0169: The private method `Do.UI.ColorConfigurationWidget.DisableButtons()' is never used
Compilation succeeded - 2 warning(s)
make[1]: Leaving directory `/home/gourgi/temp/installs/do/Do'
Making all in po
make[1]: Entering directory `/home/gourgi/temp/installs/do/po'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/gourgi/temp/installs/do/po'
Making all in libdo
make[1]: Entering directory `/home/gourgi/temp/installs/do/libdo'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/gourgi/temp/installs/do/libdo'
Making all in m4
make[1]: Entering directory `/home/gourgi/temp/installs/do/m4'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/gourgi/temp/installs/do/m4'
Making all in data
make[1]: Entering directory `/home/gourgi/temp/installs/do/data'
Making all in icons
make[2]: Entering directory `/home/gourgi/temp/installs/do/data/icons'
Making all in hicolor
make[3]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor'
Making all in 16x16
make[4]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/16x16'
Making all in apps
make[5]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/16x16/apps'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/16x16/apps'
make[5]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/16x16'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/16x16'
make[4]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/16x16'
Making all in 22x22
make[4]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/22x22'
Making all in apps
make[5]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/22x22/apps'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/22x22/apps'
make[5]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/22x22'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/22x22'
make[4]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/22x22'
Making all in 24x24
make[4]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/24x24'
Making all in apps
make[5]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/24x24/apps'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/24x24/apps'
make[5]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/24x24'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/24x24'
make[4]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/24x24'
Making all in 32x32
make[4]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/32x32'
Making all in apps
make[5]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/32x32/apps'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/32x32/apps'
make[5]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/32x32'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/32x32'
make[4]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/32x32'
Making all in 48x48
make[4]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/48x48'
Making all in apps
make[5]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/48x48/apps'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/48x48/apps'
make[5]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/48x48'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/48x48'
make[4]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/48x48'
Making all in scalable
make[4]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/scalable'
Making all in apps
make[5]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/scalable/apps'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/scalable/apps'
make[5]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/scalable'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/scalable'
make[4]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/scalable'
make[4]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor'
make[3]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor'
make[3]: Entering directory `/home/gourgi/temp/installs/do/data/icons'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/gourgi/temp/installs/do/data/icons'
make[2]: Leaving directory `/home/gourgi/temp/installs/do/data/icons'
make[2]: Entering directory `/home/gourgi/temp/installs/do/data'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/gourgi/temp/installs/do/data'
make[1]: Leaving directory `/home/gourgi/temp/installs/do/data'

```

[COLOR="Red"]sudo make install[/COLOR] output :
```
$ sudo make install
Making install in .
make[1]: Entering directory `/home/gourgi/temp/installs/do'
make[2]: Entering directory `/home/gourgi/temp/installs/do'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/gourgi/temp/installs/do'
make[1]: Leaving directory `/home/gourgi/temp/installs/do'
Making install in Do.Universe
make[1]: Entering directory `/home/gourgi/temp/installs/do/Do.Universe'
make[2]: Entering directory `/home/gourgi/temp/installs/do/Do.Universe'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/gnome-do" || /bin/mkdir -p "/usr/local/lib/gnome-do"
 /usr/bin/install -c -m 644 '../build/Do.Universe.dll' '/usr/local/lib/gnome-do/Do.Universe.dll'
 /usr/bin/install -c -m 644 '../build/Do.Universe.dll.mdb' '/usr/local/lib/gnome-do/Do.Universe.dll.mdb'
test -z "/usr/local/lib/gnome-do" || /bin/mkdir -p "/usr/local/lib/gnome-do"
test -z "/usr/local/lib/pkgconfig" || /bin/mkdir -p "/usr/local/lib/pkgconfig"
 /usr/bin/install -c -m 644 'do.universe.pc' '/usr/local/lib/pkgconfig/do.universe.pc'
make[2]: Leaving directory `/home/gourgi/temp/installs/do/Do.Universe'
make[1]: Leaving directory `/home/gourgi/temp/installs/do/Do.Universe'
Making install in Do.Platform
make[1]: Entering directory `/home/gourgi/temp/installs/do/Do.Platform'
make[2]: Entering directory `/home/gourgi/temp/installs/do/Do.Platform'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/gnome-do" || /bin/mkdir -p "/usr/local/lib/gnome-do"
 /usr/bin/install -c -m 644 '../build/Do.Platform.dll' '/usr/local/lib/gnome-do/Do.Platform.dll'
 /usr/bin/install -c -m 644 '../build/Do.Platform.dll.mdb' '/usr/local/lib/gnome-do/Do.Platform.dll.mdb'
test -z "/usr/local/lib/gnome-do" || /bin/mkdir -p "/usr/local/lib/gnome-do"
test -z "/usr/local/lib/pkgconfig" || /bin/mkdir -p "/usr/local/lib/pkgconfig"
 /usr/bin/install -c -m 644 'do.platform.pc' '/usr/local/lib/pkgconfig/do.platform.pc'
make[2]: Leaving directory `/home/gourgi/temp/installs/do/Do.Platform'
make[1]: Leaving directory `/home/gourgi/temp/installs/do/Do.Platform'
Making install in Do.Interface.Linux
make[1]: Entering directory `/home/gourgi/temp/installs/do/Do.Interface.Linux'
make[2]: Entering directory `/home/gourgi/temp/installs/do/Do.Interface.Linux'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/gnome-do" || /bin/mkdir -p "/usr/local/lib/gnome-do"
 /usr/bin/install -c -m 644 '../build/Do.Interface.Linux.dll' '/usr/local/lib/gnome-do/Do.Interface.Linux.dll'
 /usr/bin/install -c -m 644 '../build/Do.Interface.Linux.dll.mdb' '/usr/local/lib/gnome-do/Do.Interface.Linux.dll.mdb'
test -z "/usr/local/lib/gnome-do" || /bin/mkdir -p "/usr/local/lib/gnome-do"
test -z "/usr/local/lib/pkgconfig" || /bin/mkdir -p "/usr/local/lib/pkgconfig"
 /usr/bin/install -c -m 644 'do.interface.linux.pc' '/usr/local/lib/pkgconfig/do.interface.linux.pc'
make[2]: Leaving directory `/home/gourgi/temp/installs/do/Do.Interface.Linux'
make[1]: Leaving directory `/home/gourgi/temp/installs/do/Do.Interface.Linux'
Making install in Do.Interface.Linux.Classic
make[1]: Entering directory `/home/gourgi/temp/installs/do/Do.Interface.Linux.Classic'
make[2]: Entering directory `/home/gourgi/temp/installs/do/Do.Interface.Linux.Classic'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/gnome-do" || /bin/mkdir -p "/usr/local/lib/gnome-do"
 /usr/bin/install -c -m 644 '../build/Do.Interface.Linux.Classic.dll' '/usr/local/lib/gnome-do/Do.Interface.Linux.Classic.dll'
 /usr/bin/install -c -m 644 '../build/Do.Interface.Linux.Classic.dll.mdb' '/usr/local/lib/gnome-do/Do.Interface.Linux.Classic.dll.mdb'
test -z "/usr/local/lib/gnome-do" || /bin/mkdir -p "/usr/local/lib/gnome-do"
test -z "/usr/local/lib/pkgconfig" || /bin/mkdir -p "/usr/local/lib/pkgconfig"
make[2]: Leaving directory `/home/gourgi/temp/installs/do/Do.Interface.Linux.Classic'
make[1]: Leaving directory `/home/gourgi/temp/installs/do/Do.Interface.Linux.Classic'
Making install in Do.Interface.Linux.Docky
make[1]: Entering directory `/home/gourgi/temp/installs/do/Do.Interface.Linux.Docky'
make[2]: Entering directory `/home/gourgi/temp/installs/do/Do.Interface.Linux.Docky'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/gnome-do" || /bin/mkdir -p "/usr/local/lib/gnome-do"
 /usr/bin/install -c -m 644 '../build/Do.Interface.Linux.Docky.dll' '/usr/local/lib/gnome-do/Do.Interface.Linux.Docky.dll'
 /usr/bin/install -c -m 644 '../build/Do.Interface.Linux.Docky.dll.mdb' '/usr/local/lib/gnome-do/Do.Interface.Linux.Docky.dll.mdb'
 /usr/bin/install -c -m 644 'Do.Interface.Linux.Docky.dll.config' '/usr/local/lib/gnome-do/Do.Interface.Linux.Docky.dll.config'
test -z "/usr/local/lib/gnome-do" || /bin/mkdir -p "/usr/local/lib/gnome-do"
test -z "/usr/local/lib/pkgconfig" || /bin/mkdir -p "/usr/local/lib/pkgconfig"
make[2]: Leaving directory `/home/gourgi/temp/installs/do/Do.Interface.Linux.Docky'
make[1]: Leaving directory `/home/gourgi/temp/installs/do/Do.Interface.Linux.Docky'
Making install in Do.Interface.Linux.GlassFrame
make[1]: Entering directory `/home/gourgi/temp/installs/do/Do.Interface.Linux.GlassFrame'
make[2]: Entering directory `/home/gourgi/temp/installs/do/Do.Interface.Linux.GlassFrame'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/gnome-do" || /bin/mkdir -p "/usr/local/lib/gnome-do"
 /usr/bin/install -c -m 644 '../build/Do.Interface.Linux.GlassFrame.dll' '/usr/local/lib/gnome-do/Do.Interface.Linux.GlassFrame.dll'
 /usr/bin/install -c -m 644 '../build/Do.Interface.Linux.GlassFrame.dll.mdb' '/usr/local/lib/gnome-do/Do.Interface.Linux.GlassFrame.dll.mdb'
test -z "/usr/local/lib/gnome-do" || /bin/mkdir -p "/usr/local/lib/gnome-do"
test -z "/usr/local/lib/pkgconfig" || /bin/mkdir -p "/usr/local/lib/pkgconfig"
make[2]: Leaving directory `/home/gourgi/temp/installs/do/Do.Interface.Linux.GlassFrame'
make[1]: Leaving directory `/home/gourgi/temp/installs/do/Do.Interface.Linux.GlassFrame'
Making install in Do.Interface.Linux.HUD
make[1]: Entering directory `/home/gourgi/temp/installs/do/Do.Interface.Linux.HUD'
make[2]: Entering directory `/home/gourgi/temp/installs/do/Do.Interface.Linux.HUD'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/gnome-do" || /bin/mkdir -p "/usr/local/lib/gnome-do"
 /usr/bin/install -c -m 644 '../build/Do.Interface.Linux.HUD.dll' '/usr/local/lib/gnome-do/Do.Interface.Linux.HUD.dll'
 /usr/bin/install -c -m 644 '../build/Do.Interface.Linux.HUD.dll.mdb' '/usr/local/lib/gnome-do/Do.Interface.Linux.HUD.dll.mdb'
test -z "/usr/local/lib/gnome-do" || /bin/mkdir -p "/usr/local/lib/gnome-do"
test -z "/usr/local/lib/pkgconfig" || /bin/mkdir -p "/usr/local/lib/pkgconfig"
make[2]: Leaving directory `/home/gourgi/temp/installs/do/Do.Interface.Linux.HUD'
make[1]: Leaving directory `/home/gourgi/temp/installs/do/Do.Interface.Linux.HUD'
Making install in Do.Interface.Linux.Mini
make[1]: Entering directory `/home/gourgi/temp/installs/do/Do.Interface.Linux.Mini'
make[2]: Entering directory `/home/gourgi/temp/installs/do/Do.Interface.Linux.Mini'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/gnome-do" || /bin/mkdir -p "/usr/local/lib/gnome-do"
 /usr/bin/install -c -m 644 '../build/Do.Interface.Linux.Mini.dll' '/usr/local/lib/gnome-do/Do.Interface.Linux.Mini.dll'
 /usr/bin/install -c -m 644 '../build/Do.Interface.Linux.Mini.dll.mdb' '/usr/local/lib/gnome-do/Do.Interface.Linux.Mini.dll.mdb'
test -z "/usr/local/lib/gnome-do" || /bin/mkdir -p "/usr/local/lib/gnome-do"
test -z "/usr/local/lib/pkgconfig" || /bin/mkdir -p "/usr/local/lib/pkgconfig"
make[2]: Leaving directory `/home/gourgi/temp/installs/do/Do.Interface.Linux.Mini'
make[1]: Leaving directory `/home/gourgi/temp/installs/do/Do.Interface.Linux.Mini'
Making install in Do.Platform.Linux
make[1]: Entering directory `/home/gourgi/temp/installs/do/Do.Platform.Linux'
make[2]: Entering directory `/home/gourgi/temp/installs/do/Do.Platform.Linux'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/gnome-do" || /bin/mkdir -p "/usr/local/lib/gnome-do"
 /usr/bin/install -c -m 644 '../build/Do.Platform.Linux.dll' '/usr/local/lib/gnome-do/Do.Platform.Linux.dll'
 /usr/bin/install -c -m 644 '../build/Do.Platform.Linux.dll.mdb' '/usr/local/lib/gnome-do/Do.Platform.Linux.dll.mdb'
test -z "/usr/local/lib/gnome-do" || /bin/mkdir -p "/usr/local/lib/gnome-do"
test -z "/usr/local/lib/pkgconfig" || /bin/mkdir -p "/usr/local/lib/pkgconfig"
 /usr/bin/install -c -m 644 'do.platform.linux.pc' '/usr/local/lib/pkgconfig/do.platform.linux.pc'
make[2]: Leaving directory `/home/gourgi/temp/installs/do/Do.Platform.Linux'
make[1]: Leaving directory `/home/gourgi/temp/installs/do/Do.Platform.Linux'
Making install in Do.DBus
make[1]: Entering directory `/home/gourgi/temp/installs/do/Do.DBus'
make[2]: Entering directory `/home/gourgi/temp/installs/do/Do.DBus'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/gnome-do" || /bin/mkdir -p "/usr/local/lib/gnome-do"
 /usr/bin/install -c -m 644 '../build/Do.DBus.dll' '/usr/local/lib/gnome-do/Do.DBus.dll'
 /usr/bin/install -c -m 644 '../build/Do.DBus.dll.mdb' '/usr/local/lib/gnome-do/Do.DBus.dll.mdb'
test -z "/usr/local/lib/gnome-do" || /bin/mkdir -p "/usr/local/lib/gnome-do"
test -z "/usr/local/lib/pkgconfig" || /bin/mkdir -p "/usr/local/lib/pkgconfig"
 /usr/bin/install -c -m 644 'do.dbus.pc' '/usr/local/lib/pkgconfig/do.dbus.pc'
make[2]: Leaving directory `/home/gourgi/temp/installs/do/Do.DBus'
make[1]: Leaving directory `/home/gourgi/temp/installs/do/Do.DBus'
Making install in Do
make[1]: Entering directory `/home/gourgi/temp/installs/do/Do'
make[2]: Entering directory `/home/gourgi/temp/installs/do/Do'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
 /usr/bin/install -c 'gnome-do' '/usr/local/bin/gnome-do'
test -z "/usr/local/share/applications" || /bin/mkdir -p "/usr/local/share/applications"
 /usr/bin/install -c -m 644 'gnome-do.desktop' '/usr/local/share/applications/gnome-do.desktop'
test -z "/usr/local/lib/gnome-do" || /bin/mkdir -p "/usr/local/lib/gnome-do"
 /usr/bin/install -c -m 644 '../build/Do.exe.mdb' '/usr/local/lib/gnome-do/Do.exe.mdb'
 /usr/bin/install -c -m 644 'Do.exe.config' '/usr/local/lib/gnome-do/Do.exe.config'
test -z "/usr/local/lib/gnome-do" || /bin/mkdir -p "/usr/local/lib/gnome-do"
 /usr/bin/install -c '../build/Do.exe' '/usr/local/lib/gnome-do/Do.exe'
test -z "/usr/local/lib/pkgconfig" || /bin/mkdir -p "/usr/local/lib/pkgconfig"
make[2]: Leaving directory `/home/gourgi/temp/installs/do/Do'
make[1]: Leaving directory `/home/gourgi/temp/installs/do/Do'
Making install in po
make[1]: Entering directory `/home/gourgi/temp/installs/do/po'
linguas="ar ast bg br ca cs da de el en_AU en_CA en_GB es et fa fi fr ga hu id is it ja lt lv mk nb nl nn pl pt_BR pt ru sk sl sr sv ta te th tr uk vi zh_CN zh_HK zh_TW "; \
	for lang in $linguas; do \
	  dir=/usr/local/share/locale/$lang/LC_MESSAGES; \
	  /bin/sh /home/gourgi/temp/installs/do/install-sh -d $dir; \
	  if test -r $lang.gmo; then \
	    /usr/bin/install -c -m 644 $lang.gmo $dir/gnome-do.mo; \
	    echo "installing $lang.gmo as $dir/gnome-do.mo"; \
	  else \
	    /usr/bin/install -c -m 644 ./$lang.gmo $dir/gnome-do.mo; \
	    echo "installing ./$lang.gmo as" \
		 "$dir/gnome-do.mo"; \
	  fi; \
	  if test -r $lang.gmo.m; then \
	    /usr/bin/install -c -m 644 $lang.gmo.m $dir/gnome-do.mo.m; \
	    echo "installing $lang.gmo.m as $dir/gnome-do.mo.m"; \
	  else \
	    if test -r ./$lang.gmo.m ; then \
	      /usr/bin/install -c -m 644 ./$lang.gmo.m \
		$dir/gnome-do.mo.m; \
	      echo "installing ./$lang.gmo.m as" \
		   "$dir/gnome-do.mo.m"; \
	    else \
	      true; \
	    fi; \
	  fi; \
	done
installing ar.gmo as /usr/local/share/locale/ar/LC_MESSAGES/gnome-do.mo
installing ast.gmo as /usr/local/share/locale/ast/LC_MESSAGES/gnome-do.mo
installing bg.gmo as /usr/local/share/locale/bg/LC_MESSAGES/gnome-do.mo
installing br.gmo as /usr/local/share/locale/br/LC_MESSAGES/gnome-do.mo
installing ca.gmo as /usr/local/share/locale/ca/LC_MESSAGES/gnome-do.mo
installing cs.gmo as /usr/local/share/locale/cs/LC_MESSAGES/gnome-do.mo
installing da.gmo as /usr/local/share/locale/da/LC_MESSAGES/gnome-do.mo
installing de.gmo as /usr/local/share/locale/de/LC_MESSAGES/gnome-do.mo
installing el.gmo as /usr/local/share/locale/el/LC_MESSAGES/gnome-do.mo
installing en_AU.gmo as /usr/local/share/locale/en_AU/LC_MESSAGES/gnome-do.mo
installing en_CA.gmo as /usr/local/share/locale/en_CA/LC_MESSAGES/gnome-do.mo
installing en_GB.gmo as /usr/local/share/locale/en_GB/LC_MESSAGES/gnome-do.mo
installing es.gmo as /usr/local/share/locale/es/LC_MESSAGES/gnome-do.mo
installing et.gmo as /usr/local/share/locale/et/LC_MESSAGES/gnome-do.mo
installing fa.gmo as /usr/local/share/locale/fa/LC_MESSAGES/gnome-do.mo
installing fi.gmo as /usr/local/share/locale/fi/LC_MESSAGES/gnome-do.mo
installing fr.gmo as /usr/local/share/locale/fr/LC_MESSAGES/gnome-do.mo
installing ga.gmo as /usr/local/share/locale/ga/LC_MESSAGES/gnome-do.mo
installing hu.gmo as /usr/local/share/locale/hu/LC_MESSAGES/gnome-do.mo
installing id.gmo as /usr/local/share/locale/id/LC_MESSAGES/gnome-do.mo
installing is.gmo as /usr/local/share/locale/is/LC_MESSAGES/gnome-do.mo
installing it.gmo as /usr/local/share/locale/it/LC_MESSAGES/gnome-do.mo
installing ja.gmo as /usr/local/share/locale/ja/LC_MESSAGES/gnome-do.mo
installing lt.gmo as /usr/local/share/locale/lt/LC_MESSAGES/gnome-do.mo
installing lv.gmo as /usr/local/share/locale/lv/LC_MESSAGES/gnome-do.mo
installing mk.gmo as /usr/local/share/locale/mk/LC_MESSAGES/gnome-do.mo
installing nb.gmo as /usr/local/share/locale/nb/LC_MESSAGES/gnome-do.mo
installing nl.gmo as /usr/local/share/locale/nl/LC_MESSAGES/gnome-do.mo
installing nn.gmo as /usr/local/share/locale/nn/LC_MESSAGES/gnome-do.mo
installing pl.gmo as /usr/local/share/locale/pl/LC_MESSAGES/gnome-do.mo
installing pt_BR.gmo as /usr/local/share/locale/pt_BR/LC_MESSAGES/gnome-do.mo
installing pt.gmo as /usr/local/share/locale/pt/LC_MESSAGES/gnome-do.mo
installing ru.gmo as /usr/local/share/locale/ru/LC_MESSAGES/gnome-do.mo
installing sk.gmo as /usr/local/share/locale/sk/LC_MESSAGES/gnome-do.mo
installing sl.gmo as /usr/local/share/locale/sl/LC_MESSAGES/gnome-do.mo
installing sr.gmo as /usr/local/share/locale/sr/LC_MESSAGES/gnome-do.mo
installing sv.gmo as /usr/local/share/locale/sv/LC_MESSAGES/gnome-do.mo
installing ta.gmo as /usr/local/share/locale/ta/LC_MESSAGES/gnome-do.mo
installing te.gmo as /usr/local/share/locale/te/LC_MESSAGES/gnome-do.mo
installing th.gmo as /usr/local/share/locale/th/LC_MESSAGES/gnome-do.mo
installing tr.gmo as /usr/local/share/locale/tr/LC_MESSAGES/gnome-do.mo
installing uk.gmo as /usr/local/share/locale/uk/LC_MESSAGES/gnome-do.mo
installing vi.gmo as /usr/local/share/locale/vi/LC_MESSAGES/gnome-do.mo
installing zh_CN.gmo as /usr/local/share/locale/zh_CN/LC_MESSAGES/gnome-do.mo
installing zh_HK.gmo as /usr/local/share/locale/zh_HK/LC_MESSAGES/gnome-do.mo
installing zh_TW.gmo as /usr/local/share/locale/zh_TW/LC_MESSAGES/gnome-do.mo
make[1]: Leaving directory `/home/gourgi/temp/installs/do/po'
Making install in libdo
make[1]: Entering directory `/home/gourgi/temp/installs/do/libdo'
make[2]: Entering directory `/home/gourgi/temp/installs/do/libdo'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/gnome-do" || /bin/mkdir -p "/usr/local/lib/gnome-do"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'libdo.la' '/usr/local/lib/gnome-do/libdo.la'
libtool: install: /usr/bin/install -c .libs/libdo.so /usr/local/lib/gnome-do/libdo.so
libtool: install: /usr/bin/install -c .libs/libdo.lai /usr/local/lib/gnome-do/libdo.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /usr/local/lib/gnome-do
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/gnome-do

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[2]: Leaving directory `/home/gourgi/temp/installs/do/libdo'
make[1]: Leaving directory `/home/gourgi/temp/installs/do/libdo'
Making install in m4
make[1]: Entering directory `/home/gourgi/temp/installs/do/m4'
make[2]: Entering directory `/home/gourgi/temp/installs/do/m4'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/gourgi/temp/installs/do/m4'
make[1]: Leaving directory `/home/gourgi/temp/installs/do/m4'
Making install in data
make[1]: Entering directory `/home/gourgi/temp/installs/do/data'
Making install in icons
make[2]: Entering directory `/home/gourgi/temp/installs/do/data/icons'
Making install in hicolor
make[3]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor'
Making install in 16x16
make[4]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/16x16'
Making install in apps
make[5]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/16x16/apps'
make[6]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/16x16/apps'
make[6]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/icons/hicolor/16x16/apps" || /bin/mkdir -p "/usr/local/share/icons/hicolor/16x16/apps"
 /usr/bin/install -c -m 644 'gnome-do.png' '/usr/local/share/icons/hicolor/16x16/apps/gnome-do.png'
make[6]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/16x16/apps'
make[5]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/16x16/apps'
make[5]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/16x16'
make[6]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/16x16'
make[6]: Nothing to be done for `install-exec-am'.
make[6]: Nothing to be done for `install-data-am'.
make[6]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/16x16'
make[5]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/16x16'
make[4]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/16x16'
Making install in 22x22
make[4]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/22x22'
Making install in apps
make[5]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/22x22/apps'
make[6]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/22x22/apps'
make[6]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/icons/hicolor/22x22/apps" || /bin/mkdir -p "/usr/local/share/icons/hicolor/22x22/apps"
 /usr/bin/install -c -m 644 'gnome-do.png' '/usr/local/share/icons/hicolor/22x22/apps/gnome-do.png'
make[6]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/22x22/apps'
make[5]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/22x22/apps'
make[5]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/22x22'
make[6]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/22x22'
make[6]: Nothing to be done for `install-exec-am'.
make[6]: Nothing to be done for `install-data-am'.
make[6]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/22x22'
make[5]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/22x22'
make[4]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/22x22'
Making install in 24x24
make[4]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/24x24'
Making install in apps
make[5]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/24x24/apps'
make[6]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/24x24/apps'
make[6]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/icons/hicolor/24x24/apps" || /bin/mkdir -p "/usr/local/share/icons/hicolor/24x24/apps"
 /usr/bin/install -c -m 644 'gnome-do.png' '/usr/local/share/icons/hicolor/24x24/apps/gnome-do.png'
make[6]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/24x24/apps'
make[5]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/24x24/apps'
make[5]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/24x24'
make[6]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/24x24'
make[6]: Nothing to be done for `install-exec-am'.
make[6]: Nothing to be done for `install-data-am'.
make[6]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/24x24'
make[5]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/24x24'
make[4]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/24x24'
Making install in 32x32
make[4]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/32x32'
Making install in apps
make[5]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/32x32/apps'
make[6]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/32x32/apps'
make[6]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/icons/hicolor/32x32/apps" || /bin/mkdir -p "/usr/local/share/icons/hicolor/32x32/apps"
 /usr/bin/install -c -m 644 'gnome-do.png' '/usr/local/share/icons/hicolor/32x32/apps/gnome-do.png'
make[6]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/32x32/apps'
make[5]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/32x32/apps'
make[5]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/32x32'
make[6]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/32x32'
make[6]: Nothing to be done for `install-exec-am'.
make[6]: Nothing to be done for `install-data-am'.
make[6]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/32x32'
make[5]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/32x32'
make[4]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/32x32'
Making install in 48x48
make[4]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/48x48'
Making install in apps
make[5]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/48x48/apps'
make[6]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/48x48/apps'
make[6]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/icons/hicolor/48x48/apps" || /bin/mkdir -p "/usr/local/share/icons/hicolor/48x48/apps"
 /usr/bin/install -c -m 644 'gnome-do.png' '/usr/local/share/icons/hicolor/48x48/apps/gnome-do.png'
make[6]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/48x48/apps'
make[5]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/48x48/apps'
make[5]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/48x48'
make[6]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/48x48'
make[6]: Nothing to be done for `install-exec-am'.
make[6]: Nothing to be done for `install-data-am'.
make[6]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/48x48'
make[5]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/48x48'
make[4]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/48x48'
Making install in scalable
make[4]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/scalable'
Making install in apps
make[5]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/scalable/apps'
make[6]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/scalable/apps'
make[6]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/icons/hicolor/scalable/apps" || /bin/mkdir -p "/usr/local/share/icons/hicolor/scalable/apps"
 /usr/bin/install -c -m 644 'gnome-do.svg' '/usr/local/share/icons/hicolor/scalable/apps/gnome-do.svg'
make[6]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/scalable/apps'
make[5]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/scalable/apps'
make[5]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/scalable'
make[6]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor/scalable'
make[6]: Nothing to be done for `install-exec-am'.
make[6]: Nothing to be done for `install-data-am'.
make[6]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/scalable'
make[5]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/scalable'
make[4]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor/scalable'
make[4]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor'
make[5]: Entering directory `/home/gourgi/temp/installs/do/data/icons/hicolor'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor'
make[4]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor'
make[3]: Leaving directory `/home/gourgi/temp/installs/do/data/icons/hicolor'
make[3]: Entering directory `/home/gourgi/temp/installs/do/data/icons'
make[4]: Entering directory `/home/gourgi/temp/installs/do/data/icons'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/gourgi/temp/installs/do/data/icons'
make[3]: Leaving directory `/home/gourgi/temp/installs/do/data/icons'
make[2]: Leaving directory `/home/gourgi/temp/installs/do/data/icons'
make[2]: Entering directory `/home/gourgi/temp/installs/do/data'
make[3]: Entering directory `/home/gourgi/temp/installs/do/data'
make[3]: Nothing to be done for `install-exec-am'.
GCONF_CONFIG_SOURCE=xml:merged:/etc/gconf/gconf.xml.defaults \
	/usr/bin/gconftool-2 --makefile-install-rule gnome-do.schemas
Attached schema `/schemas/apps/gnome-do/preferences/Do/CorePreferences/AlwaysShowResults' to key `/apps/gnome-do/preferences/Do/CorePreferences/AlwaysShowResults'
Installed schema `/schemas/apps/gnome-do/preferences/Do/CorePreferences/AlwaysShowResults' for locale `C'
Attached schema `/schemas/apps/gnome-do/preferences/Do/CorePreferences/QuietStart' to key `/apps/gnome-do/preferences/Do/CorePreferences/QuietStart'
Installed schema `/schemas/apps/gnome-do/preferences/Do/CorePreferences/QuietStart' for locale `C'
Attached schema `/schemas/apps/gnome-do/preferences/Do/CorePreferences/SummonKeyBinding' to key `/apps/gnome-do/preferences/Do/CorePreferences/SummonKeyBinding'
Installed schema `/schemas/apps/gnome-do/preferences/Do/CorePreferences/SummonKeyBinding' for locale `C'
Attached schema `/schemas/apps/gnome-do/preferences/Do/CorePreferences/TextModeKeyBinding' to key `/apps/gnome-do/preferences/Do/CorePreferences/TextModeKeyBinding'
Installed schema `/schemas/apps/gnome-do/preferences/Do/CorePreferences/TextModeKeyBinding' for locale `C'
Attached schema `/schemas/apps/gnome-do/preferences/Do/CorePreferences/Theme' to key `/apps/gnome-do/preferences/Do/CorePreferences/Theme'
Installed schema `/schemas/apps/gnome-do/preferences/Do/CorePreferences/Theme' for locale `C'
test -z "/usr/local/etc/gconf/schemas" || /bin/mkdir -p "/usr/local/etc/gconf/schemas"
 /usr/bin/install -c -m 644 'gnome-do.schemas' '/usr/local/etc/gconf/schemas/gnome-do.schemas'
make[3]: Leaving directory `/home/gourgi/temp/installs/do/data'
make[2]: Leaving directory `/home/gourgi/temp/installs/do/data'
make[1]: Leaving directory `/home/gourgi/temp/installs/do/data'
```


[COLOR="Red"]PS[/COLOR]: for some unknown reason i had to './autogen' twice in order to 'make' it , otherwise 'make' failed.

---

### Post by Gourgi on 2009-01-11
and for the 'Docky' preferences :
gconf-editor - > /apps/gnome-do/preferences/Docky/Utilities/DockPreferences
):P


i can't load any plugins though :(

---

### Post by ronacc on 2009-01-11
I started to try the bzr version but the build-deps wanted to remove things I didn't want removed .

---

### Post by ShirishAg75 on 2009-01-11
does anybody know what kind of memory this consumes?

Can somebody do some memory profiling of the desktop with and without docky?

---

### Post by RAOF on 2009-01-11
Seems to be on a par with normal Do usage here; ~33MB with few plugins loaded.  That'll get a bit bigger with more plugins.

Edit: 42 Mb with my full compliment of normal plugins enabled.

---

### Post by ronacc on 2009-01-11
I will if I can get it to build , submitted bug # 316250 on gnome-sharp2 ,when that gets fixed I'll try again and report back .

---

### Post by Gourgi on 2009-01-11
> **ShirishAg75 said:**
> does anybody know what kind of memory this consumes?

Can somebody do some memory profiling of the desktop with and without docky?
i could try it
can you guide me through this ?
i'm not pretty familiar with memory related commands

---

### Post by ShirishAg75 on 2009-01-11
You could try capturing two things.

the simplest one would be just having the output of 

```
$ free
```

A more elaborate and more correct would be something like this. 

```


$ ps -eo pid,ppid,rss,vsize,pcpu,pmem,cmd -ww --sort=pid


```

The only thing it would need to be done every 10-15 secs or so for sometime and then do another after installing docky and doing a restart to see how it functions therein in the next session. 

I'm sure somebody could post a small shell script or something so this can be done automatically. 

The results would have to be tabulated in a graph to know and see what the differences are

If somebody knows of a better way/utility for doing the same  would love to know.

---

### Post by andrewsomething on 2009-01-12
Intrepid debs are avaliable in the Do-Testers PPA:

[https://edge.launchpad.net/~do-testers/+archive](https://edge.launchpad.net/~do-testers/+archive)

---

### Post by Kosimo on 2009-01-12
> **andrewsomething said:**
> Intrepid debs are avaliable in the Do-Testers PPA:

[https://edge.launchpad.net/~do-testers/+archive](https://edge.launchpad.net/~do-testers/+archive)

Thank you!

---

### Post by klim8 on 2009-01-12
We will have to wait, the gnome-do-plugins build failed:

```

...
make[2]: Entering directory `/build/buildd/gnome-do-plugins-0.7.95.1/Microblogging'
Compiling Microblog.dll...
./src/Configuration.cs(26,7): error CS0246: The type or namespace name `Twitterizer' could not be found. Are you missing a using directive or an assembly reference?
Compilation failed: 1 error(s), 0 warnings
make[2]: *** [../build/Microblog.dll] Error 1
make[2]: Leaving directory `/build/buildd/gnome-do-plugins-0.7.95.1/Microblogging'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/build/buildd/gnome-do-plugins-0.7.95.1'
dh_auto_build: command returned error code 512
...

```

---

### Post by smbm on 2009-01-12
I've made some Intrepid packages with checkinstall.

[http://ubuntuforums.org/showthread.php?p=6539839#post6539839](http://ubuntuforums.org/showthread.php?p=6539839#post6539839)

---

### Post by yelo3 on 2009-01-12
... Jaunty packages??

---

### Post by smbm on 2009-01-12
Sorry, not running Jaunty, thought you might be interested anyway.

---

### Post by flomar on 2009-01-12
Wow this is great, newer liked docks like AWN because of their minor gnome desktop integration, this is different! thanks for the packages!

flo

---

### Post by smbm on 2009-01-12
> **flomar said:**
> Wow this is great, newer liked docks like AWN because of their minor gnome desktop integration, this is different! thanks for the packages!

flo

Do they work ok for you? I've been hearing of mixed results.

---

### Post by emshains on 2009-01-12
No matter how many times do I run configure or autogen, make fails and tells me this: 
```
Making all in .
make[1]: Entering directory `/home/emils/gnome-do'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/emils/gnome-do'
Making all in Do.Universe
make[1]: Entering directory `/home/emils/gnome-do/Do.Universe'
Compiling Do.Universe.dll...
make[1]: Leaving directory `/home/emils/gnome-do/Do.Universe'
Making all in Do.Platform
make[1]: Entering directory `/home/emils/gnome-do/Do.Platform'
Compiling Do.Platform.dll...
./src/Do.Platform/Do.Platform.Preferences/PreferencesImplementation.cs(103,22): warning CS0169: The private method `Do.Platform.Preferences.PreferencesImplementation<TOwner>.Set<T>(Do.Platform.IPreferencesService, string, T)' is never used
./src/Do.Platform/Do.Platform.Preferences/PreferencesImplementation.cs(118,22): warning CS0169: The private method `Do.Platform.Preferences.PreferencesImplementation<TOwner>.TryGet<T>(Do.Platform.IPreferencesService, string, T, out T)' is never used
./src/Do.Platform/Do.Platform.Preferences/PreferencesImplementation.cs(130,22): warning CS0169: The private method `Do.Platform.Preferences.PreferencesImplementation<TOwner>.TryGet<T>(Do.Platform.IPreferencesService, string, out T)' is never used
Compilation succeeded - 3 warning(s)
make[1]: Leaving directory `/home/emils/gnome-do/Do.Platform'
Making all in Do.Interface.Linux
make[1]: Entering directory `/home/emils/gnome-do/Do.Interface.Linux'
Compiling Do.Interface.Linux.dll...
./src/Do.Interface/Do.Interface.AnimationBase/BezelColors.cs(107,73): error CS1501: No overload for method `ShadeColor' takes `1' arguments
./src/Do.Interface/Do.Interface.AnimationBase/BezelColors.cs(108,77): error CS1501: No overload for method `ShadeColor' takes `1' arguments
./src/Do.Interface/Do.Interface.AnimationBase/BezelColors.cs(109,77): error CS1501: No overload for method `ShadeColor' takes `1' arguments
./src/Do.Interface/Do.Interface.AnimationBase/BezelColors.cs(110,73): error CS1501: No overload for method `ShadeColor' takes `1' arguments
./src/Do.Interface/Do.Interface.AnimationBase/BezelColors.cs(111,73): error CS1501: No overload for method `ShadeColor' takes `1' arguments
Compilation failed: 5 error(s), 0 warnings
make[1]: *** [../build/Do.Interface.Linux.dll] Error 1
make[1]: Leaving directory `/home/emils/gnome-do/Do.Interface.Linux'
make: *** [all-recursive] Error 1

```

I have to run the config/autogen as root though, otherwise I get permission problems...

---

### Post by emshains on 2009-01-12
I tried your packages on Hardy, and got no results. This really sucks.

---

### Post by Lorenz on 2009-01-12
somehow I end up with version 7.9 after following the how-to on page 1 :-?

---

### Post by Neon Lights on 2009-01-12
Following Gourgi's instructions, it built fine on intrepid. But I do have a million and one PPA's added.

It IS quite awesome though. It needs some polishing up, like only showing windows on the current workspace, etc. But it will be amazing. I love Do. :D I'm gonna be using from now on. haha.

Also, Lorenz, I believe 7.9 = 8.0 Alpha 1.

---

### Post by Lorenz on 2009-01-12
> **Neon Lights said:**
> Following Gourgi's instructions, it built fine on intrepid. But I do have a million and one PPA's added.

It IS quite awesome though. It needs some polishing up, like only showing windows on the current workspace, etc. But it will be amazing. I love Do. :D I'm gonna be using from now on. haha.

Also, Lorenz, I believe 7.9 = 8.0 Alpha 1.

Ah, thanks for the hint!
For some reason, I cannot change the appearance though, so it seems no shiny dock for me :(

---

### Post by RAOF on 2009-01-12
> **emshains said:**
> I tried your packages on Hardy, and got no results. This really sucks.

You'll need to install a newer mono for it to work on Hardy.  That's available [here](http://directhex.mfgames.com/hardy.html), backported by a member of the Debian mono team, so it's not too crazy. The new Do uses a bunch of features only found in mono 1.9 and greater.

Also, gnome-do-plugins (finally) built in the do-testers ppa (for Intrepid).  You should no longer need self-compiled plugins (again, for intrepid).

Jaunty packages are my next project.

---

### Post by flomar on 2009-01-12
> **smbm said:**
> Do they work ok for you? I've been hearing of mixed results.

With the plugins package from the PPA the plugins seem to work now, not all though(Files and Folder does not eg.). But we have to keep in mind, that these are testers packages and i'm pretty impressed with their stability!

---

### Post by zekopeko on 2009-01-12
> **flomar said:**
> With the plugins package from the PPA the plugins seem to work now, not all though(Files and Folder does not eg.). But we have to keep in mind, that these are testers packages and i'm pretty impressed with their stability!

if you are referring to the lack of visual feedback once you add the folders try adding a folder and then closing the preferences window and restarting Do. Then open the FnF plugins configure window and see if the folder you just added is in the list. i think it adds the folder but you don't get it instantly in the list.

---

### Post by evilkastel on 2009-01-12
Hmm i compiled it in INtrepid amd64, was quite easy. but how do i get the plugins working with docky? the PPA is not working for my... are the packages there only for i386?

Edit: Nevermind, i got the package updated and it's running like a charm. I'm loving this app.

---

### Post by RAOF on 2009-01-12
> **evilkastel said:**
> Hmm i compiled it in INtrepid amd64, was quite easy. but how do i get the plugins working with docky? the PPA is not working for my... are the packages there only for i386?

Urgh, yes.  Mono is broken on amd64 on the PPA buildds, so gnome-do hasn't built there.  The plugins would work, though.

---

### Post by kurros on 2009-01-12
> **Lorenz said:**
> Ah, thanks for the hint!
For some reason, I cannot change the appearance though, so it seems no shiny dock for me :(

Make sure you have a compositing manager enabled (in metacity or compiz).

---

### Post by ronacc on 2009-01-12
> **RAOF said:**
> Urgh, yes.  Mono is broken on amd64 on the PPA buildds, so gnome-do hasn't built there.  The plugins would work, though.

ah that explains why it won't build on my 64bit jaunty . configures ok but make fails with a command not found about 6 lines in .

---

### Post by RAOF on 2009-01-12
> **ronacc said:**
> ah that explains why it won't build on my 64bit jaunty . configures ok but make fails with a command not found about 6 lines in .

No, that's not the problem.  I've been building it on my x86-64 Jaunty install for ages (one of the reasons why it took a couple of iterations to make it actually build against Intrepid ;)).

---

### Post by Gourgi on 2009-01-12
yep it successfully build for me on amd64
i've written it in my post before

i successfully build the plugins today (well at least most of them :) )

one thing is for sure : Integration Rocks :guitar:

---

### Post by ronacc on 2009-01-12
ok then what am I missing ? like I said it configures cleanly with no warnings or errors but when I run make this is what I get .

```
ron@rondesktopb:~/tmp/build/gdppa/gnome-do-0.7.95$ make
Making all in .
make[1]: Entering directory `/home/ron/tmp/build/gdppa/gnome-do-0.7.95'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/ron/tmp/build/gdppa/gnome-do-0.7.95'
Making all in Do.Universe
make[1]: Entering directory `/home/ron/tmp/build/gdppa/gnome-do-0.7.95/Do.Universe'
Compiling Do.Universe.dll...
/bin/bash: no: command not found
make[1]: *** [../build/Do.Universe.dll] Error 127
make[1]: Leaving directory `/home/ron/tmp/build/gdppa/gnome-do-0.7.95/Do.Universe'
make: *** [all-recursive] Error 1
ron@rondesktopb:~/tmp/build/gdppa/gnome-do-0.7.95$ 


```

---

### Post by jwagener on 2009-01-14
installed and played a little bit with do+docky for the last hour.
seems pretty stable and its fun to work with it. indexing the contact infos of my google contacts, was the thing i was missing in 0.6, well, now im happy :) 
i just reduced the size of the icons and removed the automated icons with gconf-editor. 
changing the functions of the arrow keys in docky makes no sense to me, is there an option to change that?

very well done!

---

### Post by RAOF on 2009-01-14
> **ronacc said:**
> ok then what am I missing ? like I said it configures cleanly with no warnings or errors but when I run make this is what I get .

```
ron@rondesktopb:~/tmp/build/gdppa/gnome-do-0.7.95$ make
Making all in .
make[1]: Entering directory `/home/ron/tmp/build/gdppa/gnome-do-0.7.95'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/ron/tmp/build/gdppa/gnome-do-0.7.95'
Making all in Do.Universe
make[1]: Entering directory `/home/ron/tmp/build/gdppa/gnome-do-0.7.95/Do.Universe'
Compiling Do.Universe.dll...
/bin/bash: no: command not found
make[1]: *** [../build/Do.Universe.dll] Error 127
make[1]: Leaving directory `/home/ron/tmp/build/gdppa/gnome-do-0.7.95/Do.Universe'
make: *** [all-recursive] Error 1
ron@rondesktopb:~/tmp/build/gdppa/gnome-do-0.7.95$ 


```

Sorry!  I thought I'd replied to this.

This indicates that configure didn't find a gmcs binary (the fact that configure doesn't fail is a bug).  This will be the case if you've got mono 2.0 from an unofficial repository, don't have mono-devel installed, or have some other sort of mono-related craziness happening.

---

### Post by flomar on 2009-01-14
> **zekopeko said:**
> if you are referring to the lack of visual feedback once you add the folders try adding a folder and then closing the preferences window and restarting Do. Then open the FnF plugins configure window and see if the folder you just added is in the list. i think it adds the folder but you don't get it instantly in the list.

You are right, im referring to the lack of visual feedback, moreover gnome do freezes everytime i try to activate the FnF plugin, so i have to pkill it. on restart there is still no FnF plugin active - see corresponding bugreport: [https://bugs.launchpad.net/do/+bug/316992](https://bugs.launchpad.net/do/+bug/316992)

flo

---

### Post by ronacc on 2009-01-14
@raof  Thanks it was mono-devl . added that made clean and reconfigured and it built and installed ok . Since this is from a ppa how do I report the configure bug ? or is it already known ?

---

### Post by Lorenz on 2009-01-14
> **kurros said:**
> Make sure you have a compositing manager enabled (in metacity or compiz).

That was it, thanks!

---

### Post by RAOF on 2009-01-14
> **ronacc said:**
> @raof  Thanks it was mono-devl . added that made clean and reconfigured and it built and installed ok . Since this is from a ppa how do I report the configure bug ? or is it already known ?

Known and fixed in trunk.  I just hadn't quite got around to it (and had nicked that piece of buildsystem from Banshee, which now has a patch sitting on their bugzilla).

---

### Post by ace214 on 2009-01-14
Thanks for posting this. Replaced my AWN with it. :D

---

### Post by portis on 2009-01-14
Thanks for the recommendation. But the Files and Folders plugin doesnot work, even after I recompile and replace this plugin from source.

The configuration page of Files and Folders is blank, and I got these errors:

Do.FilesAndFolders.FileItemSource "Files and Folders" encountered an error in UpdateItems: An exception was thrown by the type initializer for Do.FilesAndFolders.Plugin.
Do.FilesAndFolders.MoveAction "Move to..." encountered an error in SupportsItem: An exception was thrown by the type initializer for Do.FilesAndFolders.Plugin.
Do.FilesAndFolders.CopyAction "Copy to..." encountered an error in SupportsItem: An exception was thrown by the type initializer for Do.FilesAndFolders.Plugin.
Do.FilesAndFolders.MoveToTrashAction "Move to Trash" encountered an error in SupportsItem: An exception was thrown by the type initializer for Do.FilesAndFolders.Plugin.
Do.FilesAndFolders.NewFileAction "Create New File" encountered an error in SupportsItem: An exception was thrown by the type initializer for Do.FilesAndFolders.Plugin.
Do.FilesAndFolders.NewFolderAction "Create New Folder" encountered an error in SupportsItem: An exception was thrown by the type initializer for Do.FilesAndFolders.Plugin.
Do.FilesAndFolders.RenameAction "Rename file..." encountered an error in SupportsItem: An exception was thrown by the type initializer for Do.FilesAndFolders.Plugin.

I then downgraded to 0.6.1.0-0ubuntu3, and that worked. Anyone knows a solution? Thanks.

---

### Post by ace214 on 2009-01-14
> **portis said:**
> But the Files and Folders plugin doesnot work
Yeah, I had the same problem, but I didn't want to downgrade and lose the dock. Thought about filing a bug.

---

### Post by christophski on 2009-01-14
this is really great, i just tried it and it installed perfectly. But, i can't get my plugins to work properly and i'd like to revert to a stable version. How do I uninstall this version?

---

### Post by ace214 on 2009-01-14
> **christophski said:**
> this is really great, i just tried it and it installed perfectly. But, i can't get my plugins to work properly and i'd like to revert to a stable version. How do I uninstall this version?
You can remove the PPA from your sources list and then reinstall or you can open Synaptic, find the gnome-do package and the plugins package, go to the Package menu (on the top menu bar), click Force version and then choose the 6.1 version.

---

### Post by Geekkit on 2009-01-14
> **RAOF said:**
> Seems to be on a par with normal Do usage here; ~33MB with few plugins loaded.  That'll get a bit bigger with more plugins.

Edit: 42 Mb with my full compliment of normal plugins enabled.

42 MB for a dock bar?! I'm sorry but that's just absurd. That's one piece of eye candy that I won't bother with even if I do have 3 GB of RAM.

---

### Post by Leno. on 2009-01-14
> **Geekkit said:**
> 42 MB for a dock bar?! I'm sorry but that's just absurd. That's one piece of eye candy that I won't bother with even if I do have 3 GB of RAM.
 
My old GNOME Do used 300 MB RAM and I still used it, so this is a welcome update :P

BTW: Mine uses 27 MB

---

### Post by RAOF on 2009-01-14
> **Geekkit said:**
> 42 MB for a dock bar?! I'm sorry but that's just absurd. That's one piece of eye candy that I won't bother with even if I do have 3 GB of RAM.

Not 42Mb for a dock bar.  42Mb for GNOME Do, while using the docky interface.  For comparison this makes it 4 times larger than gnome-panel for me, and gnome-panel doesn't allow me to:
[list]
[*] post to identi.ca
[*] send an email to one of my gmail contacts
[*] maximize my firefox windows.
[*] suspend my laptop
[*] shell into my SSH hosts
[*] ...etc
[/list]

Basically, it's much more than a dock.  Its not even primarily a dock.

---

### Post by scaine on 2009-01-14
Gnome Do is incredible - if you don't think so, you probably haven't given it a chance.  It's one of those apps that genuinely changes the way you use your PC, but doesn't force the change.

I like the concept of adding a dock to it, but I'm afraid it's just a little imposing on my screen and I'm not a fan of hiding docks.  Any chance a future Docky will allow the resize of the dock/icons?  Also, it would be nice to allow the resize of the parabolic effect - I like a really subtle zoom on my Cairo-Dock PC up the stairs and Docky's zoom is huge.

Cracking to see so much innovative development on this excellent tool though.  Well done to everyone involved, and thanks!

---

### Post by flomar on 2009-01-14
@scaine,
you can already resize your dock, vertically by dragging it on the separator, just left of the trash icon. horizontally by dragging at the far left/right end of the dock.
any option you cant find in the settings dialog you find via the GConf-Editor under /apps/gnome-do/preferences/Docky/Utilities/DockPreferences

flo

---

### Post by Geekkit on 2009-01-14
> **RAOF said:**
> Not 42Mb for a dock bar.  42Mb for GNOME Do, while using the docky interface.  For comparison this makes it 4 times larger than gnome-panel for me, and gnome-panel doesn't allow me to:
[list]
[*] post to identi.ca
[*] send an email to one of my gmail contacts
[*] maximize my firefox windows.
[*] suspend my laptop
[*] shell into my SSH hosts
[*] ...etc
[/list]

Basically, it's much more than a dock.  Its not even primarily a dock.

Thanks for the correction. That's still a little steep though. I'll give it a look in a few months when the dust settles.

---

### Post by ronacc on 2009-01-14
is there a way to set which applications automaticly appear in docky (not plugins) ? or  is the only way to get rid of the ones I don't wan't in my dock to one by one rt click and remove them ? I checked both gnome-do preferences and gconf-editor .

---

### Post by RAOF on 2009-01-14
> **ronacc said:**
> is there a way to set which applications automaticly appear in docky (not plugins) ? or  is the only way to get rid of the ones I don't wan't in my dock to one by one rt click and remove them ? I checked both gnome-do preferences and gconf-editor .

You can add apps you want to Docky by dragging their .desktop file onto the dock.  Similarly, you can remove one by dragging the icon off the dock.

You can't completely control the set of icons on the dock; it's populated by the most-frequently-used items in Do.  Well, I suppose you could, actually, by adding all the launchers you wanted and then resizing the dock so that they were all that get shown.  Maybe.

---

### Post by ronacc on 2009-01-14
thanks for the info , They might consider that as an "enhancement" making the aps "opt in" , my dock keeps populating itself with apps I have never even opened , when I dump one it just adds the next , right now it seems to be working its way through the games menu .

---

### Post by RAOF on 2009-01-14
> **ronacc said:**
> thanks for the info , They might consider that as an "enhancement" making the aps "opt in" , my dock keeps populating itself with apps I have never even opened , when I dump one it just adds the next , right now it seems to be working its way through the games menu .

It'll do that until Do has learnt enough of your freqeuently-used items. I'm not sure whether opt-in apps would be accepted, really; it's a bit against the concept of the interface ;).  Maybe.

---

### Post by Neon Lights on 2009-01-15
mhm, I'm at 25mb here, with some plugins. Muchh better than gnome-panel, which sometimes gets up to 100mb. (if that's a bug, I don't even know where to begin to report it -.-)

This is the only dock-like thing I've kept more than a day. I love it. <3 I would love if it could extend without adding icons (a la 7).

Gnome-Do is so awesome. <3

---

### Post by plun on 2009-01-15
Back in business...   What a beauty..:p


-  A little confused about that Docky is a theme....nevertheless found it after reading the wiki...8)


-  Noticed a bug.....  the trash cannot be empty during first run (maybe also later)


```
System.IO.DirectoryNotFoundException: Directory '/home/plun/.local/share/Trash/files' not found.

``` 

To the plugins....):P

---

### Post by Kobalt on 2009-01-15
I just started testing this thing : sweet lord it's a great great tool, it stands prefectly on my eeePC.

---

### Post by ronacc on 2009-01-15
@ kobalt  I haven't tried it on my eee yet but you are right it should be  much better than that stupid "netbook" interface , which makes my 4g look positively claustrophobic .

---

### Post by flomar on 2009-01-16
> **ronacc said:**
> @ kobalt  I haven't tried it on my eee yet but you are right it should be  much better than that stupid "netbook" interface , which makes my 4g look positively claustrophobic .

i had the same idea, and installed the new 'easy peasy 1.0' (former ubuntu-eee) on my 701 4G. you can basically have a complete clean desktop with no panels, icons or starters.
i did automatically hide docky, deleted the bottom panel and hide the top (for stuff like switching wifi its still handy).
with compiz fusion activated also the animations (which you can turn off) work perfectly fluent.

flo

---

### Post by ronacc on 2009-01-16
@ flomar  I had already done every thing you sugested except install gnome-do ( I just learned about that from this thread ) I installed gnome-do from synaptic and dockey didn't showup as a choice in preferences>apearence>theme so I purged the default version and added the ppa and installed 7.95.1 and now the themes choice is greyed out , how did you get dockey to show up ?

edit: OOPS my bad I didn't have compiz enabled , all is well now , disregard.

---

### Post by cszikszoy on 2009-01-16
> **ronacc said:**
> edit: OOPS my bad I didn't have compiz enabled , all is well now , disregard.

You can also use metacity's compositing engine if you don't feel like enabling compiz.

---

### Post by DBO on 2009-01-17
> **ronacc said:**
> thanks for the info , They might consider that as an "enhancement" making the aps "opt in" , my dock keeps populating itself with apps I have never even opened , when I dump one it just adds the next , right now it seems to be working its way through the games menu .

That little annoyance will be fixed in the next alpha

---

### Post by perfectska04 on 2009-01-17
I just tried the latest version from the PPA and all I can say is WOW. I don't even like docks and I hate wasting screen space, but this Docky interface is so useful and endearing that I can't bring myself to stop using it.

It's easier than setting up cairo-dock and is even better than AWN for icons sizes of 48x48px or larger, since it uses all scalable icons - making all my launchers look sharp and clear.

The only two things to note is that it REALLY needs options to disable those automatic icons and to not let maximized windows go under the dock area (AWN has this option).

---

### Post by bpl07 on 2009-01-17
I agree, I love this feature.  The only suggestion I have (although this is probably not the place for it) is to include an option similar to Windows 7's new way of doing the quick launch... if I have the application open, convert it to a taskbar like icon with information about what's happening in the window (title), that way when I'm using gmail I can know if someone has im'd me.  Does that make sense?

Also, has anyone noticed a problem when adding a plugin?  Gnome-do freezes up and I have to log out and log back in to get the functionality back.

---

### Post by go7Ul1ai on 2009-01-17
Hello,

I am really interested in trying this version of GNOME Do but I am on 8.10, I have tried adding the GNOME Do Development PPA and it displays an error when reloading sources.

Thanks for any help in advance,

Edit: Okay, I installed by source but I don't think I installed it properly, some of the images are really blurred..

---

### Post by flomar on 2009-01-17
@perfectska04, maximized windows do not go under docky on my machine, except of course if you activate automatic hiding of the dock.

@bpl07, i think thats a known issue, in this alpha state some are already working and some are not. im not sure if the developers do want a bugreport for every plugin not working (there are not too few), anyway thats the place to file bugreports -> [https://bugs.launchpad.net/do](https://bugs.launchpad.net/do)

---

### Post by perfectska04 on 2009-01-17
> **flomar said:**
> @perfectska04, maximized windows do not go under docky on my machine, except of course if you activate automatic hiding of the dock.

Is it possible this is a bug only in the amd64 package, then? Automatic hiding is not enabled, yet when I maximize the window it goes under the dock.

I'm attaching a screenshot of this happening, just in case.

---

### Post by zekopeko on 2009-01-17
> **perfectska04 said:**
> Is it possible this is a bug only in the amd64 package, then? Automatic hiding is not enabled, yet when I maximize the window it goes under the dock.

I'm attaching a screenshot of this happening, just in case.

right click the gnome-do dock icon and select windows overlap option. i'm running from trunk so maybe it hasn't been packaged to the ppa.

---

### Post by zekopeko on 2009-01-17
> **flomar said:**
> @perfectska04, maximized windows do not go under docky on my machine, except of course if you activate automatic hiding of the dock.

@bpl07, i think thats a known issue, in this alpha state some are already working and some are not. im not sure if the developers do want a bugreport for every plugin not working (there are not too few), anyway thats the place to file bugreports -> [https://bugs.launchpad.net/do](https://bugs.launchpad.net/do)

the plugins are on a diffrent page. all bug against the plugins should be filed in

[https://bugs.launchpad.net/do-plugins](https://bugs.launchpad.net/do-plugins)

---

### Post by zekopeko on 2009-01-17
> **lee.jarratt said:**
> Hello,

I am really interested in trying this version of GNOME Do but I am on 8.10, I have tried adding the GNOME Do Development PPA and it displays an error when reloading sources.

Thanks for any help in advance,

Edit: Okay, I installed by source but I don't think I installed it properly, some of the images are really blurred..

if you could post the error maybe we could help you.

---

### Post by perfectska04 on 2009-01-17
> **zekopeko said:**
> right click the gnome-do dock icon and select windows overlap option. i'm running from trunk so maybe it hasn't been packaged to the ppa.

Thanks for the info, that is probably it as I don't see that option. I'll try to build it from source instead of the PPA.

---

### Post by flomar on 2009-01-18
Alpha 3 is in the PPA Repositories and it of course rocks even a little bit more ;)
> **perfectska04 said:**
> Is it possible this is a bug only in the amd64 package, then? Automatic hiding is not enabled, yet when I maximize the window it goes under the dock.
The new alpha has an extra option in the submenu of the GNOME Do icon on the far left of docky, which should do away with your problem, check it out.

---

### Post by Lorenz on 2009-01-18
I got it to work fine, but it does freeze very often and can only be solved by killing the process. Is there someone with similar issues (8.10, ATI x1300)

---

### Post by flomar on 2009-01-18
> **Lorenz said:**
> I got it to work fine, but it does freeze very often and can only be solved by killing the process. Is there someone with similar issues (8.10, ATI x1300)

it seems to me as this is related to adding plugins, the more plugins you have enabled the higher the number of freezes. also it does freeze everytime i add plugins for the first time. i have to kill do once, but it starts up normally and the recently added plugins do work fine.

---

### Post by go7Ul1ai on 2009-01-18
> **zekopeko said:**
> if you could post the error maybe we could help you.

I don't know how to produce an error code etc for reference, but I can post a screenshot, the images are really blurred (some are), maybe it's the Human icon theme or it's my crappy graphics card? 

Lee

Screenshots:

[img]http://localhostr.com/files/b34fb0/gnome.[/img]
[img]http://localhostr.com/files/1fca40/blur%20to%20the%20chili.png[/img]

---

### Post by perfectska04 on 2009-01-18
> **flomar said:**
> Alpha 3 is in the PPA Repositories and it of course rocks even a little bit more ;)

The new alpha has an extra option in the submenu of the GNOME Do icon on the far left of docky, which should do away with your problem, check it out.

The new alpha works perfectly! Now it all works as expected and I can use it in my laptop perfectly... I might even install it in my parents' machine, since clicking on icons may be easier for them to manage their windows and applications.

> **lee.jarratt said:**
> I don't know how to produce an error code etc for reference, but I can post a screenshot, the images are really blurred (some are), maybe it's the Human icon theme or it's my crappy graphics card?

It should be the icon theme. Believe or not, the Human icon theme is very incomplete when it comes to having all its icons in scalable or other sizes. You can try the Human (Orange) version of my GNOME-Colors icons to fix your problem [(clicky here)]("http://www.gnome-look.org/content/show.php/GNOME-colors?content=82562"). Or you can also try one of the many other icon sets in [www.gnome-look.org](www.gnome-look.org) like Meliae, Hydroxygen or Crashbit.

---

### Post by Rabidmonkey1 on 2009-01-18
I installed the other day but for whatever reason, Gnome Do doesn't seem to be indexing my applications, which was absolutely key for me!  Anyone have any idea how to get it to index my applications?  Thanks!

---

### Post by perfectska04 on 2009-01-18
So far, so good. The new version is pretty stable, although it crashes whenever I try to add/remove plugins (which I won't be doing much as I've already set them up).

Perhaps other than increased stability, the team should also look to add the ability to "Close, Minimize/Restore" on right click to launchers on the left side of the separator, docky-only plugins (such as workspaces, etc) and the optiom to empty trash when right clicking on the trash can.

---

### Post by Rabidmonkey1 on 2009-01-18
> **lee.jarratt said:**
> I don't know how to produce an error code etc for reference, but I can post a screenshot, the images are really blurred (some are), maybe it's the Human icon theme or it's my crappy graphics card? 

Lee


That definitely looks like an icon/theme problem, not an error that would be the program's fault.  Some applications only come with lower res icons by default while others come with hi res .png icons; thus the difference in the quality.  It's definitely not a problem with your gfx card.

My suggestion - install a new icon theme. Gnome-look.org has plenty, and I'm a fan of the "eikon" icon pack, available here: [http://drop.io/fmrbpensador]("http://drop.io/fmrbpensador") (although it should be noted that this pack will not work perfectly, though it does work very very well, with newer versions of Gnome - simply because not all the icons are correctly linked to the right destination.  What I mean specifically is that several of your folders in the "Places" menu will appear with the default gnome gray icon - but that's the only problem I've found! Other than that, the entire theme is really attractive!)

Hope that helps.

---

### Post by go7Ul1ai on 2009-01-18
> **perfectska04 said:**
> The new alpha works perfectly! Now it all works as expected and I can use it in my laptop perfectly... I might even install it in my parents' machine, since clicking on icons may be easier for them to manage their windows and applications.



It should be the icon theme. Believe or not, the Human icon theme is very incomplete when it comes to having all its icons in scalable or other sizes. You can try the Human (Orange) version of my GNOME-Colors icons to fix your problem [(clicky here)]("http://www.gnome-look.org/content/show.php/GNOME-colors?content=82562"). Or you can also try one of the many other icon sets in [www.gnome-look.org](www.gnome-look.org) like Meliae, Hydroxygen or Crashbit.

Thanks, your theme is fantastic! Makes everything crystal clear and sharp, now look ^.^

Screenshot:
[img]http://localhostr.com/files/9b0d68/Screenshot.png[/img]

Thanks again :)

---

### Post by perfectska04 on 2009-01-18
> **lee.jarratt said:**
> Thanks, your theme is fantastic! Makes everything crystal clear and sharp, now look ^.^
Thanks again :)

No problem. The icons are sharp up to 256x256 px, so they will make Gnome-Do's regular non-dock interface look good as well, in case you'd rather use that.

---

### Post by RAOF on 2009-01-18
> **Rabidmonkey1 said:**
> I installed the other day but for whatever reason, Gnome Do doesn't seem to be indexing my applications, which was absolutely key for me!  Anyone have any idea how to get it to index my applications?  Thanks!

Kindly quit Do, and then run "gnome-do --debug"; that'll give you debug output to the terminal you've run it from.

Some people have reported errors with some .desktop files with strange encodings or translated strings; this seems to cause the Application item source to crash on startup, so applications are not indexed.

---

### Post by go7Ul1ai on 2009-01-18
Good to see GNOME Do Alpha 3.. I hope maybe in the future there will be functionality of resizing the height of Docky.

Also, I don't think changing the colour of Docky is possible in this release. I don't know if it's just me or not..

Edit: Okay I realised I can resize the height..

---

### Post by RAOF on 2009-01-18
> **lee.jarratt said:**
> Good to see GNOME Do Alpha 3.. I hope maybe in the future there will be functionality of resizing the height of Docky.
...

There already is, it's just really unintuitive.  If you mouse over the separator between the items on the left and the trash on the right, the cursor will change to a pair of vertical-resize arrows.  Drag away!

---

### Post by Gourgi on 2009-01-18
RAOF any news about packaging DO for Jaunty ?

---

### Post by ace214 on 2009-01-18
Is it just me, or does anyone else think there should be an Empty Trash right click option on the trash can?

---

### Post by go7Ul1ai on 2009-01-18
> **ace214 said:**
> Is it just me, or does anyone else think there should be an Empty Trash right click option on the trash can?

Just had a look at the 8.1 milestone in Launchpad, I think this is being worked on for that release.

---

### Post by RAOF on 2009-01-18
> **Gourgi said:**
> RAOF any news about packaging DO for Jaunty ?

It'll happen; I'm just a bit busy at the moment!

---

### Post by Gourgi on 2009-01-18
> **RAOF said:**
> It'll happen; I'm just a bit busy at the moment!

thanks for the info
i'm looking forward to it :)

---

### Post by Rabidmonkey1 on 2009-01-19
> **RAOF said:**
> Kindly quit Do, and then run "gnome-do --debug"; that'll give you debug output to the terminal you've run it from.

Some people have reported errors with some .desktop files with strange encodings or translated strings; this seems to cause the Application item source to crash on startup, so applications are not indexed.

Yes! You were correct; this is the terminal output when I run the debug command:

```
 Successfully located service of type ICoreService.
Do.Universe.Linux.ApplicationItemSource "Applications" encountered an error in UpdateItems: Error stating file '/home/bob/Desktop/Paid Intern Film TV Jobs Employment Broadcast Recruitment - mandy.com.desktop': No such file or directory.

```

Any idea what I can do to fix it?  I deleted that file ages ago...

---

### Post by BwackNinja on 2009-01-19
@Rabidmonkey1

I'd say to just do a
```
sudo updatedb
```
to make sure your files are all indexed properly again.

---

### Post by Rabidmonkey1 on 2009-01-19
> **BwackNinja said:**
> @Rabidmonkey1

I'd say to just do a
```
sudo updatedb
```
to make sure your files are all indexed properly again.

Thanks for the response.  I tried that but I still get the same error :(

---

### Post by mewithafez on 2009-01-19
> **RAOF said:**
> It'll happen; I'm just a bit busy at the moment!

Thanks for the hard work, and just wanted to let you know that the intrepid packages worked on jaunty when I tried them a little while back. All the best :)

---

### Post by saracen on 2009-01-19
Does anyone get 100% CPU usage and slow/jittery zooming of the icons when moving the mouse over docky?  I'm using the proprietary nvidia driver on a fairly new machine (core 2 duo).

---

### Post by RAOF on 2009-01-19
> **saracen said:**
> Does anyone get 100% CPU usage and slow/jittery zooming of the icons when moving the mouse over docky?  I'm using the proprietary nvidia driver on a fairly new machine (core 2 duo).

Welcome to the wonderful world of the nvidia driver's crappy 2d performance.

I'd guess you're using the 17*x* drivers?  You can run "nvidia-settings -s InitialPixmapPlacement=2", and then restart Do, which should improve matters.  This needs to be run each time X is started.

The nvidia-glx-180 drivers default to this option, so you shouldn't need it if you're using those.  If you're using those drivers and it's still slow, shout at nvidia to make 2d faster!

If you've got a geforce 6 or 7 (nv4x chip), don't mind testing a new driver, and don't need 3d at all, another option is the nouveau drivers.  They're much, much better at 2d than the nvidia drivers for me - madly moving the mouse over the dock results in ~20% usage of a single core, rather than the 100% the nvidia drivers require.

---

### Post by supernovus on 2009-01-19
Well, I got the new Gnome-Do installed, and wow, Docky is great. I've never found a good "dock-like" app for Linux (AWN just wasn't ~it~ somehow...) until now. Gnome-Do was already an awesome app, and this just makes it moreso! 

:popcorn:

---

### Post by scaine on 2009-01-19
Pardon my ignorance on Gnome-Do's internal workings, but is there a way to tie the Files and Folders plug-in with the Tracker?  I went through a couple of hours of pain having Tracker index everything on my NAS and it is kinda cool once it eventually completes.

It would be awesome if Gnome-Do knew about those files too without having to run its own scan and index...

---

### Post by mewithafez on 2009-01-19
> **scaine said:**
> Pardon my ignorance on Gnome-Do's internal workings, but is there a way to tie the Files and Folders plug-in with the Tracker?  I went through a couple of hours of pain having Tracker index everything on my NAS and it is kinda cool once it eventually completes.

It would be awesome if Gnome-Do knew about those files too without having to run its own scan and index...

I'm afraid that it is in the makings (there's a launchpad thing open on it); if you google it you can probably find some rudimentary stabs at it but I have found no completed tracker search plugin for Gnome-do. Please somebody prove me wrong though!

EDIT: look right below my post for where I am proved semi-wrong :D

---

### Post by RAOF on 2009-01-19
There's a tracker-search plugin in the gnome-do-plugins package; I'm not sure if it does what you want, though.

It should now be possible to write a proper live-search plugin using tracker/beagle, but no one's done it yet.

---

### Post by Rabidmonkey1 on 2009-01-19
So I renamed a random file to what the Gnome-do --debug output gave me, and it seemed to get rid of the original error, although I get a new one now:

```
[Services] Successfully located service of type ICoreService.
Do.Universe.Linux.ApplicationItemSource "Applications" encountered an error in UpdateItems: Object reference not set to an instance of an object.

```

Anyone know how to solve this?

---

### Post by gspat on 2009-01-19
OK, I've installed on jaunty with the PPA, and it seems ok, but I think I need a few days to accustom myself to it before I try to pass judgement on it!

Two things right away though:

1) docky is rather slow (as the fellow a few posts back mentioned) I'm ruuning nvidia 180.22 so there doesn't seem to be too much hope for that! (only using 34MB according to system manager) so I disabled docky and have just "standard do" active.. but even this is slow to activate.. sometimes up to ten - twelve seconds before the window shows up.

2) when I try to add plugins, the evolution contacts plugin will not install, saying it is already active??? how??? I've never used this app before so it should not be possible! (I run gnome-do in a terminal and then put a check beside Evolution 1.2 in the preferences... The terminal window then said it was already installed and the check mark goes away in the preferences window)

---

### Post by bpl07 on 2009-01-19
> **gspat said:**
> 
1) docky is rather slow (as the fellow a few posts back mentioned) I'm ruuning nvidia 180.22 so there doesn't seem to be too much hope for that!

I'm running docky with an ati xpress 1150, i.e. bottom of the barrel mobile integrated graphics, with the open source radeon driver, and it's blazing fast.  My main complaint about AWN was how slow it was, and this blows it away.  I'm using metacity for the compositor instead of compiz, maybe that has something to do with it?

---

### Post by gspat on 2009-01-19
> **bpl07 said:**
> I'm running docky with an ati xpress 1150, i.e. bottom of the barrel mobile integrated graphics, with the open source radeon driver, and it's blazing fast.  My main complaint about AWN was how slow it was, and this blows it away.  I'm using metacity for the compositor instead of compiz, maybe that has something to do with it?

I thought about that.. so I switched back to metacity to try, but now I can't seem to get docky to turn on? did the latest update change the preferences menus?

---

### Post by Gourgi on 2009-01-19
> **gspat said:**
> I thought about that.. so I switched back to metacity to try, but now I can't seem to get docky to turn on? did the latest update change the preferences menus?

run in a terminal :
```
gnome-do --debug
```
to see what is going on.

after that you can post bugs here 
[https://bugs.launchpad.net/do/+bugs](https://bugs.launchpad.net/do/+bugs)

and here , if it plugin-related bug
[https://bugs.launchpad.net/do-plugins](https://bugs.launchpad.net/do-plugins)

---

### Post by RAOF on 2009-01-19
Evolution won't work on Jaunty, sadly (the evolution-sharp bindings are broken).  Or Intrepid, for that matter!

There's a bug that's just been fixed in trunk which made summoning Do get progressively slower over time.  But 10-12 seconds is huge - are you **sure** you're actually using the nvidia drivers?  I'd expect that sort of time from the nv drivers!

---

### Post by RAOF on 2009-01-19
> **gspat said:**
> I thought about that.. so I switched back to metacity to try, but now I can't seem to get docky to turn on? did the latest update change the preferences menus?

You'll need to turn on metacity's compositor; you can find that in gconf-editor at /apps/metacity/general/compositing_manager.

---

### Post by gspat on 2009-01-19
I just rebooted the old girl and she seems to be working now... composting in metacity was on, it's just that before the reboot the theme preferences in gnome-do were greyed out, so nothing could be done with them. I didn't realize this was where the settings were, mostly because it didn't click with me that docky was a theme! The previous preferences had docky as a check mark, so I assumed it was missing, not moved.

It's much faster now, still sorta chuggy like a strobe light, but infinitely more usable... about the same speed now in either metacity or compiz.

Definately been using the nvidia 180.22 drivers... glx gears jumped from 50 before to 1900+ after getting that to work!

---

### Post by VeeDubb on 2009-01-19
FYI, If anybody is thinking about trying Docky, I've been running 7.96 on intrepid 64 bit for a day now, and so far, I LOVE IT.

It doesn't have quite as much functionality in terms of icon stacks, and I don't believe there is a notification area aplet for it, so you can't completely replace the gnome bard with it.

But, if you want to use it to replace your bottom bar, it's fantastic.  Very smooth and friendly.

And if you've never used gnome-do, start now whether you want to use docky or not.  It's an incredible piece of productivity and accessibility software once you get the hang of it.

---

### Post by jazzperm on 2009-01-20
Here is docky also getting slow over time. When I am not using compiz it has problems with the graphics: hald of screen gets black when docky appears. How do you set docky to use metacity in a proper way?

---

### Post by Gourgi on 2009-01-20
> **jazzperm said:**
> Here is docky also getting slow over time. When I am not using compiz it has problems with the graphics: hald of screen gets black when docky appears. How do you set docky to use metacity in a proper way?
RAOF already answered that:
> if you want to use Docky with metacity , You'll need to turn on metacity's compositor; you can find that in gconf-editor at /apps/metacity/general/compositing_manager.

---

### Post by foerdi on 2009-01-20
REALLY needs a notification area applet / area and more 3d animations

otherwise awn will stay (my) first choice

---

### Post by bpl07 on 2009-01-20
For those using an AMD64 version of ubuntu, I've noticed the AMD64 build for gnome-do in the ppa pretty much fails to build every time.  If you want to keep gnome-do updating with gnome-do-plugins, you can download the package at:

[https://launchpad.net/do/+download](https://launchpad.net/do/+download)

---

### Post by flomar on 2009-01-20
in the latest alpha 0.7.98 you can finally open folders as expected (files and folders plugin), thats so great!

---

### Post by saracen on 2009-01-20
> **RAOF said:**
> Welcome to the wonderful world of the nvidia driver's crappy 2d performance.

I'd guess you're using the 17*x* drivers?  You can run "nvidia-settings -s InitialPixmapPlacement=2", and then restart Do, which should improve matters.  This needs to be run each time X is started.

The nvidia-glx-180 drivers default to this option, so you shouldn't need it if you're using those.  If you're using those drivers and it's still slow, shout at nvidia to make 2d faster!

If you've got a geforce 6 or 7 (nv4x chip), don't mind testing a new driver, and don't need 3d at all, another option is the nouveau drivers.  They're much, much better at 2d than the nvidia drivers for me - madly moving the mouse over the dock results in ~20% usage of a single core, rather than the 100% the nvidia drivers require.
Thanks, that command solved the problem.  Although the switch isn't -s it's -a.  So for those who are also facing this problem "nvidia-settings -a InitialPixmapPlacement=2"

---

### Post by zekopeko on 2009-01-20
> **foerdi said:**
> REALLY needs a notification area applet / area and more 3d animations

otherwise awn will stay (my) first choice

then your gonna have to use awn for a long time. gnome-do strives to be simple and eye pleasing. after trying dockey awn looks quite complex (needlessly).

---

### Post by scaine on 2009-01-20
Was never a fan of AWN.  I tried Cairo-Dock and still use it on most of my machines, but it lacks an elegant notification applet, so you STILL need a gnome-bar around.  Shame.  I'd love to get rid of that completely.

Gnome-Do will always stay on my systems, but I must say that Docky is growing on me.  It actually works nicely auto-hidden and it's first dock I've used that does work well like that.

---

### Post by VeeDubb on 2009-01-20
> **scaine said:**
> Was never a fan of AWN.  I tried Cairo-Dock and still use it on most of my machines, but it lacks an elegant notification applet, so you STILL need a gnome-bar around.  Shame.  I'd love to get rid of that completely.

Gnome-Do will always stay on my systems, but I must say that Docky is growing on me.  It actually works nicely auto-hidden and it's first dock I've used that does work well like that.

This annoys me too.  I have yet to find any plugin for any dock that is a suitable notification area.

The notification area for AWN has been buggy and unreliable on every system I've tried it with (not to mention ugly, and yes, I've tried both of the notification area plugins I could find)

Ciaro-dock notification area is stable and nice looking, but clunky.  It doesn't sit down in the dock the way it should, it's a little thought bubble.  (which is idiotic) and I've also found that cairo is really unstable and hard to configure compared to AWN or docky.

If docky had main menu support and a REALLY notification area, that worked correctly, I'd be done with gnome bars for good.

---

### Post by BwackNinja on 2009-01-20
Hehe, I can expect a notification area eventually, but I wouldn't really expect a main menu...

---

### Post by sowelie on 2009-01-20
Wow, the new gnome do rules, I love docky!! Much better than AWN.

---

### Post by tawmas on 2009-01-21
> **flomar said:**
> in the latest alpha 0.7.98 you can finally open folders as expected (files and folders plugin), thats so great!

What did you do to make it work? It's still not working for me (0.7.98 here too, 32 bit, on Intrepid).

---

### Post by flomar on 2009-01-21
> **tawmas said:**
> What did you do to make it work? It's still not working for me (0.7.98 here too, 32 bit, on Intrepid).

the update itself fixed the bug with the files and folders *plugin*, dont confuse this with opening folder like this:
summon do -> /path/to/folder -> open
this bug can be fixed too though, see [https://bugs.launchpad.net/do/+bug/293507](https://bugs.launchpad.net/do/+bug/293507) for the solution (look for the PPA to mono2.0)

---

### Post by tawmas on 2009-01-21
> **flomar said:**
> the update itself fixed the bug with the files and folders *plugin*, dont confuse this with opening folder like this:
summon do -> /path/to/folder -> open
this bug can be fixed too though, see [https://bugs.launchpad.net/do/+bug/293507](https://bugs.launchpad.net/do/+bug/293507) for the solution (look for the PPA to mono2.0)

mmm... If I have a folder in the dock, left- or right-clicking it doesn't do anything. Isn't that the plugin?

---

### Post by milko on 2009-01-21
I'm another who can't quite adapt to Docky until there's a notification area added. I'm using a netbook so I only want one panel or dock in total. At the moment it has to be AWN, I've got the notification area on that to integrate fine now. The whole dock feels a little bit clunky though, I'd definitely rather switch to Docky.

---

### Post by BwackNinja on 2009-01-21
Is there any way to stop it from grouping the windows of the same program together into one icon?

---

### Post by foerdi on 2009-01-22
> **zekopeko said:**
> then your gonna have to use awn for a long time. gnome-do strives to be simple and eye pleasing. after trying dockey awn looks quite complex (needlessly).

there is no force in this endless perverted universe that can stop smart people... :KS

```
ferdi@ferdi-laptop:~$ stalonetray --geometry 140x24-4-4 -f 3 --skip-taskbar --sticky --grow-gravity W --icon-gravity SE --ignore-icon-resize TRUE --max-height 48 -i 24 --window-layer top

```

see attachment

i asked gnome-do devs already to implement stalonetray like awn-extras does

for people who can't wait can use the code mentioned above -  this notification will be still not in the docky dock (unless they call stalonetray from inside docky), but visible on the right down corner of the screen

---

### Post by flomar on 2009-01-22
> **tawmas said:**
> mmm... If I have a folder in the dock, left- or right-clicking it doesn't do anything. Isn't that the plugin?

depends on how the folder came there, if you dragged it there or did "summon->/path/to/folder->open" it is not the plugin.
you really need to configure the plugin in the preference dialog in order to index your folder well, if you didn't you are obviously not using the plugin when opening folders. however, both bugs are already or can be fixed easily!

[QUOTE=foerdi]ferdi@ferdi-laptop:~$ stalonetray --geometry 140x24-4-4 -f 3 --skip-taskbar --sticky --grow-gravity W --icon-gravity SE --ignore-icon-resize TRUE --max-height 48 -i 24 --window-layer top[/QUOTE]

Wow, thats great, this way i could remove my second panel on my EEE PC, Thanks for the hint! It love to see that somehow implemented in Docky (even 0.8+)

---

### Post by tawmas on 2009-01-22
> **flomar said:**
> depends on how the folder came there, if you dragged it there or did "summon->/path/to/folder->open" it is not the plugin.
you really need to configure the plugin in the preference dialog in order to index your folder well, if you didn't you are obviously not using the plugin when opening folders. however, both bugs are already or can be fixed easily!

I think I understand. I dragged it there. At work and on my eee (both intrepid 32bit), left-clicking does nothing but animate the folder icon, right-clicking brings up the menu but then nothing works except remove from panel.

At home, where I manually installed the intrepid amd64 debs over my amd64 jaunty, everything is working.

In all instances I have the files and folders plugin installed and with the default configuration, and I tested with my desktop and my home directory.

---

### Post by flomar on 2009-01-22
I'm not sure i understand now, did you have to install mono2.0 at work/eee to make it work and the same procedure did not work on your home maschine?

---

### Post by bpl07 on 2009-01-22
What I do to get around needing a notification area and menubar is to just put the panel at the bottom and make it autohide.  I still receive the notifications, but without the space waste.  I have docky set to come up much faster than the panel (discussed earlier in the thread, keys in gconf-editor), so I almost never un-hide both at the same time.  This could probably be accomplished in AWN too... I actually prefer this way to having the notification area in the dock.

---

### Post by tawmas on 2009-01-22
> **flomar said:**
> I'm not sure i understand now, did you have to install mono2.0 at work/eee to make it work and the same procedure did not work on your home maschine?

Oh, sorry about the confusion... I was talking about how I installed gnome-do and do-plugins. I didn't have the time to look into the bug yet, and I didn't recall that Jaunty is transitioning/has transitioned to mono 2.0, so at once I didn't make the link.

I'm quite in a hurry today, but I'll try and install mono 2.0 on my eee tonight and see if it does the trick for me.

Thanks again for you help.

---

### Post by Chrisj303 on 2009-01-22
Got a big problem here :/

I've installed the 0.7.98 .deb on my 8.10 x86 install - seemingly without a hitch.I've also installed the plug-ins, again, they appeared to install OK.

But when I startup Do, and type "gnome do preferences", and push enter - it just dissapears, nothing happens at all. It closes down. In fact, I can't get it to do *anything*!

What should I do now?

---

### Post by flomar on 2009-01-22
> **Chrisj303 said:**
> What should I do now?

i think it could be a buggy plugin the crashes Do. try deactivating all plugins and then adding them one by one. in between check if the plugin works fine.

---

### Post by tawmas on 2009-01-22
> **tawmas said:**
> I'm quite in a hurry today, but I'll try and install mono 2.0 on my eee tonight and see if it does the trick for me.

Yep! Installing mono 2.0 indeed solved my issues with folders!

BTW, today Ars published an interesting [comparison between Windows 7 new taskbar and the OS X dock]("http://arstechnica.com/articles/paedia/dock-and-windows-7-taskbar.ars"), which also contains some food for thought that could wrt the future development of Docky. For example, after reading that I'm no longer sure we need a tray plugin for Docky, or indeed a tray at all...

---

### Post by RAOF on 2009-01-22
Both Windows and OS X have a notification area.  While it can be overused (as it undobtedly is in Windows, and is becoming so in GNOME), it's still a useful halfway house between full-blown dialogs and transient notifications.

It's possible to write a notifiation area plugn for Docky right now; the trash icon was developed as a docky plugin to do some proof-of-concept work on Docky plugins.  This won't make 0.8, as we'd like to stabilise it for release, but might make 0.8.1, which should have a number of Docky-related improvements.

---

### Post by Gina on 2009-01-22
> **RAOF said:**
> Evolution won't work on Jaunty, sadly (the evolution-sharp bindings are broken).  Or Intrepid, for that matter!I'm afraid I have to disagree with the latter.  I use Evolution in Intrepid - I haven't tried in Jaunty as I only run Evolution and read email in my "safe" machine (P4) that is kept free of testing.  I run Intrepid on that virtually all the time.

---

### Post by RAOF on 2009-01-22
> **Gina said:**
> I'm afraid I have to disagree with the latter.  I use Evolution in Intrepid - I haven't tried in Jaunty as I only run Evolution and read email in my "safe" machine (P4) that is kept free of testing.  I run Intrepid on that virtually all the time.

I meant the GNOME Do evolution plugin, which is, or at least, should be, broken on Intrepid.  The evolution-sharp bindings certainly are broken!

---

### Post by Gina on 2009-01-22
Ah I see - I thought I must have been missing something.

---

### Post by gregh on 2009-01-22
Im new to Gnoem-Do so forgive me if this is a know issue. I have just installed 0.7.98 on Intrepid and it is very slow and stuttery when I mouse over the docky icons. I have desktop effects enabled. Is these a setting I should be looking at?

Thanks,

Greg

---

### Post by RAOF on 2009-01-22
> **gregh said:**
> Im new to Gnoem-Do so forgive me if this is a know issue. I have just installed 0.7.98 on Intrepid and it is very slow and stuttery when I mouse over the docky icons. I have desktop effects enabled. Is these a setting I should be looking at?

Thanks,

Greg

This:
> **RAOF said:**
> Welcome to the wonderful world of the nvidia driver's crappy 2d performance.

I'd guess you're using the 17*x* drivers?  You can run "nvidia-settings -a InitialPixmapPlacement=2", and then restart Do, which should improve matters.  This needs to be run each time X is started.

The nvidia-glx-180 drivers default to this option, so you shouldn't need it if you're using those.  If you're using those drivers and it's still slow, shout at nvidia to make 2d faster!

If you've got a geforce 6 or 7 (nv4x chip), don't mind testing a new driver, and don't need 3d at all, another option is the nouveau drivers.  They're much, much better at 2d than the nvidia drivers for me - madly moving the mouse over the dock results in ~20% usage of a single core, rather than the 100% the nvidia drivers require.

---

### Post by gregh on 2009-01-22
> **RAOF said:**
> This:

That solved it, disabled the nvidia driver and all fine now.

Thanks,

GReg

---

### Post by flomar on 2009-01-23
> **foerdi said:**
> ```
ferdi@ferdi-laptop:~$ stalonetray --geometry 140x24-4-4 -f 3 --skip-taskbar --sticky --grow-gravity W --icon-gravity SE --ignore-icon-resize TRUE --max-height 48 -i 24 --window-layer top

```

hey,

i've been trying out the stalonetray now, my problem is, that sometimes it really has all the icons in the new tray, sometimes there are no or not all of them in the new tray but remain in the old one (which i didnt delete for now). this happens only when autostarting stalonetray via gnome-session-manager. any hint how to make it work consistently?

---

### Post by DBO on 2009-01-25
Some quick answers to some of the questions I have seen here and on IRC.

**Docky Notification Area:**
Wow, lots more feedback on this one area than I ever expected.  I have to admit, I am not sure how to implement this one cleanly.  I am thinking of doing something that is a bit more of a radical departure from notification areas we have seen in the past.  It should still provide the same functionality, but feel more at home in a dock.  Don't be looking for this at least until 0.8.1 however.

**Docky Is Being Slow:**
Yeah I know.  For some reason a couple nvidia cards, regardless of drivers seem to have this issue.  If you do experience chugginess with Docky, there is a branch on LP that has some performance enhancements.  However this is not ready for mainline yet and will not be in until 0.8.1 or later.

**Main Menu Applet**
It's GNOME Do... so why?  I mean honestly, the main menu would be a lot slower than simply using the built in Summon functionality, which is ultimately the main purpose of Do.  It would undermine the entire point of Docky really.

**3D animations**
No

**The zoom is too Big/Small**
You can adjust the level of zoom used by docky.  The settings are in gconf under /apps/gnome-do/preferences/Docky/Utilities, the keys are ZoomPercent and IconSize.  I tend to use a ZoomPercent of 1.5 instead of the default 2.  Be weary though, some zoom sizes may result in fuzzy icons.  The basic rule goes like this (and this is why there is no user visible way to change this): Take the icon size listed in gconf, and multiply it by the zoom you set.  If the outcome (rounded down to the nearest integer) is a standard icon size, you will have pretty icons.  Otherwise, any icon in your set that is not an svg will probably come out pretty ugly.  You must restart Do for these settings to take effect.

In future versions there will be a user facing way of changing the zoom level (I am playing with ctrl+scrollwheel right now).

**Why do gconf values not take effect right away?**
Well I dont think gconf is a good way to allow users to interact with your program.  So Docky does not track changes to gconf, and instead treats it more like a persistent place for it to store data.  As mentioned before, messing with Docky's gconf settings could cause it to crash, eat your soul, key your car, and implode your hard drive.  You are warned =)

**Folders on the dock, got me some issues?**
I know about this one too.  I have made zero changes to this locally so far, but I have to rethink a little bit of how this is done.  Ideally I would let Do cover all the manual labor here, but it can be a bit tricky.  I think I will have a better working interface by 0.8.1

**Mono 1.9.1 and Docky**
Get mono 2.0.  Just do it if you can.  I try my best to hack around 1.9.1's issues, but it's not always easy or accurate.

---

### Post by tawmas on 2009-01-25
> **DBO said:**
> 
**Docky Notification Area:**
Wow, lots more feedback on this one area than I ever expected.  I have to admit, I am not sure how to implement this one cleanly.  I am thinking of doing something that is a bit more of a radical departure from notification areas we have seen in the past.  It should still provide the same functionality, but feel more at home in a dock.  Don't be looking for this at least until 0.8.1 however.

That looks intriguing! Something I'd be looking forward is some sort of integration between application icons in the dock and the notification icons. It would also be nice (although likely infeasible) if applications could change their dock icon to reflect their status (for example, evolution could superimpose the number of unread messages, while pidgin could show your online status).

> **DBO said:**
> 
**Why do gconf values not take effect right away?**
Well I dont think gconf is a good way to allow users to interact with your program.  So Docky does not track changes to gconf, and instead treats it more like a persistent place for it to store data.  As mentioned before, messing with Docky's gconf settings could cause it to crash, eat your soul, key your car, and implode your hard drive.  You are warned =)

Oh, is this also the reason why changing your icon theme (from System > Preferences > Appearance) doesn't update the icons shown in Docky?

---

### Post by ace214 on 2009-01-25
> **DBO said:**
> Some quick answers to some of the questions I have seen here and on IRC.
Thanks for this! It's always nice to hear from the developers, and yet another reason why Linux rocks.

---

### Post by ace214 on 2009-01-25
> **tawmas said:**
> It would also be nice (although likely infeasible) if applications could change their dock icon to reflect their status (for example, evolution could superimpose the number of unread messages, while pidgin could show your online status).

AWN could do this through Dbus plugins from the other application, like there was a plugin for Pidgin as you mention, and I used to use one for QuodLibet that would change the icon in AWN to the album art of the current song.

---

### Post by tawmas on 2009-01-25
> **ace214 said:**
> AWN could do this through Dbus plugins from the other application, like there was a plugin for Pidgin as you mention, and I used to use one for QuodLibet that would change the icon in AWN to the album art of the current song.

So, there's some hope. Thanks for this information.

And yet, I would like to see something more than just a bunch of plugins. Plugins are great, BTW, but they have shortcomings too. For once, they do nothing to facilitate a cohesive interface among applications. And they (or the bindings they need to work) tend to stay behind, so what works in one release can easily fail in the subsequent, causing endless frustration.

But I'm a dreamer, and I'm already happy with what I see in Docky and what has been announced for the near future.

---

### Post by ronacc on 2009-01-25
where does dockey get the icons it uses ? and is there a way to set what icons are used ? I have a couple of unrelated apps that show the same generic icon and one which shows a different one than the one that is the default for the desktop launcher for the same app .

---

### Post by Lorenz on 2009-01-26
I would love to use it, but it usually freezes right after starting it. Then I tried deactivating all plugins, still freezes on every second action I try to do. And I didn't find out yet how to set it to autohide. But it looks very promising already, somehow better integrated than AWN or other docks. Hope it will once just work out of the box :)

---

### Post by tawmas on 2009-01-26
> **Lorenz said:**
> And I didn't find out yet how to set it to autohide.

Right click the DO icon (the first to the left of the dock) and select Automatically hide. :-)

---

### Post by Gourgi on 2009-01-26
> **ronacc said:**
>  and one which shows a different one than the one that is the default for the desktop launcher for the same app .

can you post a screenshot of this one?
which app is it?

---

### Post by ronacc on 2009-01-26
@Gourgi here it is with the offending icons highlighted

---

### Post by Gourgi on 2009-01-26
> **ronacc said:**
> @Gourgi here it is with the offending icons highlighted

yes i understand now
AFAIK docky uses the your default theme
and i can't replicate your situation
if i create a launher, give it a different icon and then drag it to Docky , then the icon is the right one (the one i choosed)
maybe you could submit a bug for this ?
[https://bugs.launchpad.net/do](https://bugs.launchpad.net/do)

---

### Post by ronacc on 2009-01-26
none of those are Icons or apps that I drug onto dockey , they are ones that dockey automaticly populated itself with .also note that Opera is an app that like realplayer was not installed from the repos but from downloading the deb from their site , and yet IT has the correct icon .( the red "O" 6th from the left end )

---

### Post by tawmas on 2009-01-26
> **ronacc said:**
> none of those are Icons or apps that I drug onto dockey , they are ones that dockey automaticly populated itself with .also note that Opera is an app that like realplayer was not installed from the repos but from downloading the deb from their site , and yet IT has the correct icon .( the red "O" 6th from the left end )

I have that too (for example with Eclipse and gkrellm). This happens when the application identifies itself in a different way than the name in the launcher, and in most cases it should be a problem of the misbehaving application.

I believe [bug #317076]("https://bugs.edge.launchpad.net/do/+bug/317076") has some useful insight about that.

---

### Post by milko on 2009-01-26
> **DBO said:**
> Some quick answers to some of the questions I have seen here and on IRC.

**Docky Notification Area:**
Wow, lots more feedback on this one area than I ever expected.  I have to admit, I am not sure how to implement this one cleanly.  I am thinking of doing something that is a bit more of a radical departure from notification areas we have seen in the past.  It should still provide the same functionality, but feel more at home in a dock.  Don't be looking for this at least until 0.8.1 however.


Many thanks for the reply. And the application!

I agree the notification area is a tricky one. I wouldn't normally have associated it with a dock until I got into netbooks and trying to make a useful minimal interface for one - docks are really on the way to being this. It doesn't necessarily have to be a part of Docky if there's a workaround such as stalonetray though so I'm not certain what to suggest - I have to see my battery status, network manager and clock, and not via desktop widget things! Looking forward to seeing your radical departure.

---

### Post by lichtgestalt on 2009-01-27
Looks really prommising! I like it

Still I got some problems:
- In the description it states that I just have to install gnome-do in interpit - yet Docky is not included in interpids current version
- zoom doesn't work properly on non default settings (smaller icons)
- I compiled do from source, but I'm unable to get do-plugins working. First I couldn't get it to compile the banshee plugin, so deleted all lines containing the word banshee from configure.ac. Now I can compile without error message. But still it looks like it's not really compiling every thing. And in the preferences menu nothing shows up. Even compiling a few plugins manually and copying the resulting .dll to ~./local/share/gnome-do/plugins, ~./local/share/gnome-do/plugins-0.7.99.1 or /usr/local/share/gnome-do/plugins didn't work.
Any ideas?

---

### Post by lichtgestalt on 2009-01-27
Solved it:

- sudo apt-get install monodevelop
- bzr branch lp:do-plugins && cd do-plugins
- delete all lines containing the word "banshee" from configure.ac
- ./autogen.sh
- delete just the word "banshee" from Makefile
- make && sudo make install

it's a dirty hack, i know -.-

---

### Post by plun on 2009-01-30
Noticed that ver 0.8 is released.... ;)

[http://do.davebsd.com/](http://do.davebsd.com/)


Tried to change theme but its the same......

gconf-editor

> Valid entries are Classic, Glass Frame, and Mini. 

???

---

### Post by tawmas on 2009-01-30
Looks like amd64 packages failed to build... :-(

---

### Post by bpl07 on 2009-01-30
It always says they fail to build, but you can get them from the [Launchpad Do archive]("https://launchpad.net/do/+download").

---

### Post by tawmas on 2009-01-30
> **bpl07 said:**
> It always says they fail to build, but you can get them from the [Launchpad Do archive]("https://launchpad.net/do/+download").

Cool! Thanks for the tip!

---

### Post by Mazza558 on 2009-02-02
Is there a way to have docky on the top of the screen? I've seen a screenshot which shows it at the top.

---

### Post by flomar on 2009-02-02
i'm pretty sure thats a mockup. afaik theres no way to do that with 0.8.

flo

---

### Post by plun on 2009-02-02
> **Mazza558 said:**
> Is there a way to have docky on the top of the screen? I've seen a screenshot which shows it at the top.

Its probably the rewrite of AWN you have seen.

[[img]http://ubuntu-pics.de/thumb/9249/snapshot5_7t1jdy.png[/img]](http://ubuntu-pics.de/bild/9249/snapshot5_7t1jdy.png)

Twins....;)

---

### Post by RAOF on 2009-02-02
> **flomar said:**
> i'm pretty sure thats a mockup. afaik theres no way to do that with 0.8.

flo

Not a mockup, but not in the 0.8 release.  A repositionable dock is currently in a branch that will be merged for 0.8.1.

---

### Post by DBO on 2009-02-03
> **Mazza558 said:**
> Is there a way to have docky on the top of the screen? I've seen a screenshot which shows it at the top.

MWAHAHAHAHAH!!!!!!!
MWAHAHAHAHHAhahahahahahahahahahahahahaha!!!!!!!!!!!

I sometimes go around posting screenshots of things in docky that cant be done yet in the released version for my own fun and entertainment.... MWAHAHAHAHA.:D

You will have Top Dock soon enough.

---

### Post by theApokalypsis on 2009-02-03
I have one thing to say.

WOW.

x64 running 0.8. the integration is what gets me. Cairo, Kiba, AWN. they are good. but I might just be sticking with this.

also very great zooming. its like how I used to have RocketDock/ObjectDock in vista. smooth.

:D

---

### Post by patbuntu on 2009-02-03
> **RAOF said:**
> Not a mockup, but not in the 0.8 release.  A repositionable dock is currently in a branch that will be merged for 0.8.1.

Any chance this allows for vertical positioning at the left of the screen?

Excellent work - cheers

---

### Post by ELD on 2009-02-03
I really don't get this "Do" and "Docky" i get that Docky is basically like AWN, but what exactly is gnome do?

I have ready the docky website and it says this:
> providing a persistent mouse based Dock interface while remaining true to Do's keyboard only interaction
That seems a little off, how can it be mouse based while "remaining true" to a keyboard only interaction? :S

I really don't get all this, if some helpful soul could let me know that would be ideal.

---

### Post by uBeer on 2009-02-03
Well, as you use Do to perform all different kind of actions, your dock fills with the most used actions. After a while all your most used actions are available at a click away. For those spare moments you actually use the mouse.

And some people like the looks and use it as a replacement for the bottom gnome-panel. And maybe some people like it that if you use docky there is no big pop-up in the middle of the screen when you press Super+Space.

---

### Post by ELD on 2009-02-03
So how exactly do you use do to perform actions, i thought you do different things in the actual programs? So now we do everything through Do?

I know what a Dock is. But what do you mean by "there is no big pop-up in the middle of the screen when you press Super+Space.".

---

### Post by Mazza558 on 2009-02-03
The dock turns into a bar asking you to type, when you press the key combo.

---

### Post by uBeer on 2009-02-03
Well, you've probably never used Do, so I'll elaborate a bit.

To launch Do you press a key combination with Super+Space being the default. A box (shiny themed) will appear in the middle of your screen and then you can type the first letter(s) of the application you want to launch/use and you will see that it finds the application (a bit like what happens when you do this with Alt+F2).
Like the Awesome-bar of Firefox it learns what you use most.

But launching applications is by no means the only thing you can do with gnome-do. You can use a lot of plugins to extend the functionality. For example: you can search for files, make new Tomboy notes, search google, use google calculator, control your music player(play/pause/forward), all kinds of stuff.

I didn't get it at first as well, but as I started using it I saw some of the possibilities that it provides.

And then there is Docky, which just makes your most used actions visible and clickable. And instead of launching a box when you press Super+Space it changes the dock to an action thing.

I hope that helps a bit, but I think you'll understand more if you install it and try to use it (and read a bit of documentation, helped me a lot to start out!).
[http://do.davebsd.com/](http://do.davebsd.com/)

---

### Post by ELD on 2009-02-03
Now that is the clear explanation i was looking for! You have my thanks it does sound pretty cool i must admit.
I take it with Docky you can just stick applications on it anyway right?
Does it also act as a window manager?

---

### Post by flomar on 2009-02-03
> **ELD said:**
> Now that is the clear explanation i was looking for! You have my thanks it does sound pretty cool i must admit.
I take it with Docky you can just stick applications on it anyway right?
Does it also act as a window manager?

As starting applications with do is one of its main functionalities, yes you can also add this action to docky. either by dragging icons on docky or with performing the action on do and clicking a small plus symbol on docky just before you are about to press enter.
if with 'window manager' you mean, that its able to minimize/restore/maximize your windows, yes you can do this.
just check it out, you will learn quickly that usage is very intuitive and theres not much further explanation needed.

---

### Post by ELD on 2009-02-03
Thanks i would try it out but i am not on my own pc for a day or two and wanted to know a little before i try you see :)

---

### Post by RAOF on 2009-02-03
> **patbuntu said:**
> Any chance this allows for vertical positioning at the left of the screen?

Excellent work - cheers

Not until someone can come up with a way to make summon from a vertical dock look natural. :)

---

### Post by trazart on 2009-02-03
I'm trying the docky bar and i have a problem.

When i started the application I removed some links that appeared, firefox, pidging... just testing. Now they wont appear automatically again.

There must be some file somewhere with the applications that have been removed so they are not auto added again.

Can anyone help me to undo this?

---

### Post by AlexBellisBrown on 2009-02-03
Im currently using Docky instead of AWN, and i much MUCH prefer it. A lot of work has gone into it, and it works seamlessly here on Intrepid, i very much hope it gets included fully with Jaunty. :)

---

### Post by theApokalypsis on 2009-02-03
> **trazart said:**
> I'm trying the docky bar and i have a problem.

When i started the application I removed some links that appeared, firefox, pidging... just testing. Now they wont appear automatically again.

There must be some file somewhere with the applications that have been removed so they are not auto added again.

Can anyone help me to undo this?

perhaps just drag and drop them onto the dock from GNOME's panel menu?

---

### Post by RAOF on 2009-02-03
> **trazart said:**
> I'm trying the docky bar and i have a problem.

When i started the application I removed some links that appeared, firefox, pidging... just testing. Now they wont appear automatically again.

There must be some file somewhere with the applications that have been removed so they are not auto added again.

Can anyone help me to undo this?

The files you are after are in ~/.local/share/gnome-do, and you're probably after killing the **dock_desktop_files** file.

Hm. That should really be in ~/.config/gnome-do.  Wishlist bug time!

---

### Post by lee_connell on 2009-02-04
Gnome-Do and Docky are great, good job! Looking forward to seeing more progress on this.

I think it would look more consistent if the context menus matched that of the current gnome theme, at least the hover border should match the gnome menu selection color theme.

The trash icon should allow a context menu like the rest of the items, in particular a "empty trash" option.

again, great work!

Also the option to remove the "Summon Do" icon from the dock :)

---

### Post by theApokalypsis on 2009-02-04
Hopefully we will see some more eyecandyish looks coming out. I was going back and forth but I am finally sticking with it from now on.

ex. the background color control working.

---

### Post by sharq1 on 2009-02-04
Does anyone else has problem with for example uploading files to imageshack? I select a file, choose action (upload to imageshack), hit enter and docky freezes until the file is uploaded. Then comes the message: "Do is uploading your image... Please wait a moment..." and link to image shows up (sometimes i can copy it, but cant make it disappear, so i have to restart do). Everything else works great, much better than AWN or Cairo-dock.
PS. Gnome-Do 0.8, graphic drivers: nvidia 180.22

---

### Post by Mazza558 on 2009-02-04
I have the BZR trunk version of Docky, and I found the settng "Orientation" in Gconf - I assume this is what controls screen position?

---

### Post by trazart on 2009-02-04
> **RAOF said:**
> The files you are after are in ~/.local/share/gnome-do, and you're probably after killing the **dock_desktop_files** file.

Hm. That should really be in ~/.config/gnome-do.  Wishlist bug time!

Thank you :D

---

### Post by tawmas on 2009-02-04
I've just installed gnome-do on a freshly installed system, only to find that it crashes as soon as I select the docky interface.

Starting do from the command line, I saw that it was the trash plugin not finding the trash directory (I hadn't deleted a single file yet). The obvious workaround was to create a file and delete it! :-)

I'm going to file a bug about that later tonight if I don't find one in Launchpad. BTW, should this go against gnome-do or do-plugins?

---

### Post by plun on 2009-02-04
> **Mazza558 said:**
> I have the BZR trunk version of Docky, and I found the settng "Orientation" in Gconf - I assume this is what controls screen position?

Yup... upgraded my bzr install and the code is there  ;)

"Top" works just fine, also a new clock...:popcorn: 

A 3D bar would be great...

---

### Post by smbm on 2009-02-04
Don't suppose you could slap together a package could you?

I'm getting errors when trying to build!

---

### Post by plun on 2009-02-04
> **smbm said:**
> Don't suppose you could slap together a package could you?

I'm getting errors when trying to build!

I am running Jaunty and it builds just fine with Jauntys environment.

Using Gourgis howto
[http://ubuntuforums.org/showpost.php?p=6537377&postcount=6](http://ubuntuforums.org/showpost.php?p=6537377&postcount=6)


There are also ppa's for gnome-do, Intrepid
[https://edge.launchpad.net/~do-testers/+archive/ppa](https://edge.launchpad.net/~do-testers/+archive/ppa)
But not updated....


If I build one it probably just works with a Jaunty environment, checkinstall OK for my code.

---

### Post by scaine on 2009-02-04
I use auto-login on this laptop and Docky prompts me unlock my keyring on login if I have any Google plug-ins enabled, presumably to access my username/password (such as for Google Calendar).

Any workarounds?

I posted my congrats and thanks here :
[http://jassmith.wordpress.com/2009/01/29/gnomedo080release/](http://jassmith.wordpress.com/2009/01/29/gnomedo080release/)

RAOF, do you have any links to official bug tracker?  Docky is pretty exciting work and while raising bugs is as much as I can contribute, I'd still like to do what I can.  I'd also like to help update some of the help pages if I can find time - some of the plug-in help pages are completely blank.  Perhaps you could post how best to lend a hand?

---

### Post by zekopeko on 2009-02-04
[https://launchpad.net/do](https://launchpad.net/do)

for Gnome Do

[https://launchpad.net/do-plugins](https://launchpad.net/do-plugins) 

for Gnome Do Plugins

---

### Post by Gourgi on 2009-02-04
> **scaine said:**
> I use auto-login on this laptop and Docky prompts me unlock my keyring on login if I have any Google plug-ins enabled, presumably to access my username/password (such as for Google Calendar).

Any workarounds?

I posted my congrats and thanks here :
[http://jassmith.wordpress.com/2009/01/29/gnomedo080release/](http://jassmith.wordpress.com/2009/01/29/gnomedo080release/)

RAOF, do you have any links to official bug tracker?  Docky is pretty exciting work and while raising bugs is as much as I can contribute, I'd still like to do what I can.  I'd also like to help update some of the help pages if I can find time - some of the plug-in help pages are completely blank.  Perhaps you could post how best to lend a hand?
launchpad is the official bug tracker
[http://bugs.launchpad.net/do](http://bugs.launchpad.net/do)
as for the keyring better raise a bug or ask  the developers at #gnome-do

---

### Post by ace214 on 2009-02-04
I'm having trouble compiling the plugins right now...

I get this error in the autogen
```
checking for BANSHEE_INDEXER... configure: error: Package requirements (banshee-1-collection-indexer >= 1.4.2) were not met:

```

EDIT: found the solution and [where someone filed the bug and was turned down]("https://bugs.launchpad.net/do-plugins/+bug/321116"), but I really think the plugin should be optional... You shouldn't have to install an application your not going to use. It's not like it's a library or something.

---

### Post by RAOF on 2009-02-04
> **ace214 said:**
> ...
I've tried to find this and I think it wants me to install Banshee (which I don't want to do), but I don't understand why I wouldn't be able to compile the other plugins or something.

Because making plugins optional is boring, arduous work for little benefit :).  It'll happen eventually, though.

---

### Post by ace214 on 2009-02-04
> **RAOF said:**
> Because making plugins optional is boring, arduous work for little benefit :).  It'll happen eventually, though.
Seems like someone being able to compile the program is a big benefit to me...

---

### Post by RAOF on 2009-02-04
> **ace214 said:**
> Seems like someone being able to compile the program is a big benefit to me...

You *can* compile the program, though.  You just need to install Banshee!

---

### Post by ace214 on 2009-02-04
> **RAOF said:**
> You *can* compile the program, though.  You just need to install Banshee!
Well, when you install Banshee in Jaunty currently it removes f-spot, tomboy, and monodevelop. The dependencies are messed up. Obviously, that's not Do's problem, but the autogen doesn't complain about me not having VirtualBox, Thunderbird, Xmms2, Zim, MPD, or Epiphany installed.

As long as it's a temporary pain, I suppose I will stop whining... :D

---

### Post by RAOF on 2009-02-04
> **ace214 said:**
> Well, when you install Banshee in Jaunty currently it removes f-spot, tomboy, and monodevelop. The dependencies are messed up. Obviously, that's not Do's problem, but the autogen doesn't complain about me not having VirtualBox, Thunderbird, Xmms2, Zim, MPD, or Epiphany installed.
...

That's because the Banshee plugin links against Banshee (specifically, Banshee.CollectionIndexer.dll, which allows access to Banshee's library) at build-time.  The VirtualBox, Thunderbird, etc (in fact, most of the plugins) don't have any build-time links with the programs they control.

---

### Post by adredz on 2009-02-05
Hi I am getting error when I update my system with Do repos enabled. Below is the error..

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5DC4E17435661D98
W: You may want to run apt-get update to correct these problems
  

However if I disable/comment the Do repos, I don't get the error... What's the problem? Any help would be appreciated...

---

### Post by foerdi on 2009-02-05
> **adredz said:**
> Hi I am getting error when I update my system with Do repos enabled. Below is the error..

  

However if I disable/comment the Do repos, I don't get the error... What's the problem? Any help would be appreciated...

just type help.ubuntu.com - Ubuntu will help you, trust your God ehm i mean Canonical

[https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab)

You REALLY should not use third party repos, especially (alpha software) Do, if you don't know what you do.

---

### Post by Vaun on 2009-02-05
Try running this :

```
rm -rf ~/.local/share/gnome-do
```

```
make distclean
./autogen.sh --prefix=/usr
make
sudo make install
```

Or if using a debian package, reinstall.

For Tawmas.

---

### Post by ace214 on 2009-02-05
> **adredz said:**
> Hi I am getting error when I update my system with Do repos enabled. Below is the error..

  

However if I disable/comment the Do repos, I don't get the error... What's the problem? Any help would be appreciated...

Launchpad PPAs now have to be signed. If you look on the PPA page, it says "This repository is signed with  A5D19FDCAA6ABB440CD3464628A8205077558DD0 OpenPGP key. [Follow these instructions]("https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories")  for installing packages from this PPA."
The page tells you to basically save the key and add it to the authentication tab of your sources. Not sure if you are using the testers PPA or the core PPA or I would link to the PPA page. Just be sure you follow the instructions.

---

### Post by adredz on 2009-02-05
> **ace214 said:**
> Launchpad PPAs now have to be signed. If you look on the PPA page, it says "This repository is signed with  A5D19FDCAA6ABB440CD3464628A8205077558DD0 OpenPGP key. [Follow these instructions]("https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories")  for installing packages from this PPA."
The page tells you to basically save the key and add it to the authentication tab of your sources. Not sure if you are using the testers PPA or the core PPA or I would link to the PPA page. Just be sure you follow the instructions.

thank you, I am using the testers one...

EDIT: problem solved. thank you so much...

---

### Post by ELD on 2009-02-05
Well i got around to trying it today and i must say it does have potential, had to turn off the icon zooming as it seems rather slow and i have a 9500 nvidia with drivers on!!

---

### Post by alexmurray on 2009-02-06
> **ELD said:**
> Well i got around to trying it today and i must say it does have potential, had to turn off the icon zooming as it seems rather slow and i have a 9500 nvidia with drivers on!!
That's a known problem with the nvidia-glx-177 drivers - try installing the nvidia-glx-180 package instead at it should be fixed.

---

### Post by tawmas on 2009-02-06
> **Vaun said:**
> Try running this :

```
rm -rf ~/.local/share/gnome-do
```

```
make distclean
./autogen.sh --prefix=/usr
make
sudo make install
```

Or if using a debian package, reinstall.

For Tawmas.

I'm sorry, are you asking me to test an updated version of the trash plugin?

---

### Post by ELD on 2009-02-06
> **alexmurray said:**
> That's a known problem with the nvidia-glx-177 drivers - try installing the nvidia-glx-180 package instead at it should be fixed.

How do i do that in intrepid?

---

### Post by alexmurray on 2009-02-06
in a terminal run:

sudo apt-get install nvidia-glx-180

or open up Synaptic and select the package nvidia-glx-180 and install it.

---

### Post by theApokalypsis on 2009-02-08
in case someone didnt know...

been finding some interesting configs in gconf-editor for zooming widths percents etc for Docky.

i assume its already know but still cool :D

---

### Post by wayfarer_boy on 2009-02-11
In case anyone was still wondering how to get Docky to appear above all other windows, it's possible using ccsm (CompizConfig Settings Manager).  I've written a quick guide on the Do wiki: [http://do.davebsd.com/wiki/index.php?title=Docky#Window_rules_for_the_Docky_theme](http://do.davebsd.com/wiki/index.php?title=Docky#Window_rules_for_the_Docky_theme)

It's my first Wiki edit, so it may be in the wrong place and may be moved by the time you visit the page.  If that's the case, do a quick keyword search for ccsm.

And I'd also like to add that this release of GNOME-Do is AWESOME!!!  I've been reserving this statement for some time, but can now confidently say:

**I now have my Quicksilver replacement! The last remnants of Apple-related software withdrawl has just left the building.**

Thanks Dave.

---

### Post by wayfarer_boy on 2009-02-11
Darn... having done all that, and Do working above all windows for the last few hours, I now find that the Window rules have stopped working and Do is back to being behind other windows.  No ideas why that could be.

---

### Post by Gourgi on 2009-02-11
> **wayfarer_boy said:**
>  It's my first Wiki edit, so it may be in the wrong place and may be moved by the time you visit the page.
it is definetely not the right place for that. you should create a new article about it.
anyway Docky's option "Allow Windows Overlap" doesn't work with ??
it works here.

---

### Post by wayfarer_boy on 2009-02-11
You're right.  A quick revisit to gconf-editor and checking the "Allow Windows Overlap" helped there.  I'll remove the wiki edit.  Efkharisto Gourgi.

---

### Post by melenor on 2009-02-11
quick question anyone know how to reset Gnome-Do peferences all the way, so that the settings were the same as if it was the first time install. The reason for this is that when i switched to "Docky" i accidently deleted the things on the dock so that the only thing on it was the tasks, trash, seperator, and the main GnomeDo menu. 
Thanks.
I love the Dock just want more options, so that it will be better then AWN or Cairo-Dock.

Edit: another thing is that it says that we can drag things into a folder on GnomeDo, does this mean it is like a stack if so how do i do it?

---

### Post by Gourgi on 2009-02-11
@ melenor
drag and drop whatever application you like there ;)
i don't know about the folder thing though.

> **wayfarer_boy said:**
> Efkharisto Gourgi.&#928;&#945;&#961;&#945;&#954;&#945;&#955;&#974; wayfarer_boy:popcorn:

---

### Post by zekopeko on 2009-02-11
> **wayfarer_boy said:**
> In case anyone was still wondering how to get Docky to appear above all other windows, it's possible using ccsm (CompizConfig Settings Manager).  I've written a quick guide on the Do wiki: [http://do.davebsd.com/wiki/index.php?title=Docky#Window_rules_for_the_Docky_theme](http://do.davebsd.com/wiki/index.php?title=Docky#Window_rules_for_the_Docky_theme)

It's my first Wiki edit, so it may be in the wrong place and may be moved by the time you visit the page.  If that's the case, do a quick keyword search for ccsm.

And I'd also like to add that this release of GNOME-Do is AWESOME!!!  I've been reserving this statement for some time, but can now confidently say:

**I now have my Quicksilver replacement! The last remnants of Apple-related software withdrawl has just left the building.**

Thanks Dave.

or you could right click the Do icon and enable the option there.

---

### Post by melenor on 2009-02-11
i want those recently user Applications or most used what ever the defaults were.

---

### Post by ticopelp on 2009-02-11
Here's a problem I'm having, and hopefully someone can help me -- I installed Gnome-Do from the latest Intrepid repos from the Launchpad site, purged all my old Gnome-do data, and when I look at the gnome-do and gnome-do plugins in Synaptic it says they are version 0.8.0, but when I actually start Gnome-Do and go to "About" it claims it's version 0.6.1 and the Docky plugin is nowhere to be seen.

Thoughts?

---

### Post by melenor on 2009-02-11
is your ubuntu 32bit or 64bit, 64bit have to download the deb and install it that way.

---

### Post by theApokalypsis on 2009-02-11
if you are looking for that link for the 64 bit download....

[https://launchpad.net/do/+download]("https://launchpad.net/do/+download")

---

### Post by kenleyrob on 2009-02-12
I have it working almost perfectly on Jaunty AMD64. First I installed gnome-do from source using checkinstall so it showed up in synaptic, then installed the plugins from the ppa. If you don't use checkinstall to install gnome-do from source then installing the plugins from the ppa will not work. 

The only issue I have is I cannot seem to search my Banshee library, although the banshee plugin is installed and activated.

I think this dock is great. Not only as a dock but it will introduce people (like me) to the power of gnome do where before it may have been overlooked. I installed it to try the dock, but have been using the other functions equally as much.

---

### Post by melenor on 2009-02-12
So any know how to reset the setting of GnomeDo?

---

### Post by alphane on 2009-02-12
Has anyone tried the session manager plug in?  Is anyone else having to call it more than once to actually shutdown/reboot their machine?

---

### Post by taavikko on 2009-02-12
> **melenor said:**
> So any know how to reset the setting of GnomeDo?

Usually helps (with any application) to delete it's settings folder from
~/ (starts with a dot . )

Can't help with location, since not using any bling bling :)
Other than composite enabled metacity..

---

### Post by tawmas on 2009-02-12
> **alphane said:**
> Has anyone tried the session manager plug in?  Is anyone else having to call it more than once to actually shutdown/reboot their machine?

mmm... I have "lock session" working, but can't seem to be able to shut down or reboot. It never happened to me to call it more than once, I will have to try this.

---

### Post by scaine on 2009-02-12
@melenor : settings appear to be stored in ~/config/gnome-do

[EDIT: Whoops - talking nonsense - I've just checked that directory and it was empty.  The only other gnome-do reference I can find in my home drive is ~/.gconf/apps/gnome-do.  There some configuration available via gconf-editor, so that makes sense]

@alphane : same here - session plug-in does nothing on my machine.  Actually, just confirmed that lock screen does indeed work, but it won't shutdown/restart.  I've tried it twice, but never more than that.  If it doesn't work first time to be honest, I just untick the plug-in and work around it.  If you feel like posting a bug about this, I'll happily confirm it.

---

### Post by cubeist on 2009-02-12
session plugin works aok for me on a 64 bit machine.  I found instructions somewhere on the web to properly install gnome-do 0.8 for a 64bit machine.

First, purge your gnome-do 0.6 program
```
sudo apt-get purge gnome-do gnome-do-plugins
```

Next, download the 0.8 64 bit build from here:
[https://launchpad.net/do/+download]("https://launchpad.net/do/+download") (Don't forget to verify with the md5sum!)

Install that deb

Then add plugins with
```
sudo apt-get install gnome-do-plugins
```

Everything works great, even banshee and sessions...

---

### Post by conehead77 on 2009-02-12
> **cubeist said:**
> 
First, purge your gnome-do 0.6 program
```
sudo apt-get purge gnome-do gnome-do-plugins
```

Next, download the 0.8 64 bit build from here:
[https://launchpad.net/do/+download]("https://launchpad.net/do/+download") (Don't forget to verify with the md5sum!)

Install that deb

Then add plugins with
```
sudo apt-get install gnome-do-plugins
```

Everything works great, even banshee and sessions...

> **kenleyrob said:**
> I have it working almost perfectly on Jaunty AMD64. First I installed gnome-do from source using checkinstall so it showed up in synaptic, then installed the plugins from the ppa. If you don't use checkinstall to install gnome-do from source then installing the plugins from the ppa will not work. 

Both suggestions didnt work for me. I cant see official or community plugins, only if i select "all plugins" i can view (some of) them. When i click one it wont install instead the checkbox unchecks automatically everytime i try to install a plugin.

I even searched (after a updatedb) for every file with gnome-do in its name and manually removed them before installing gnome-do and the plugins. Seems something went wrong with my gnome-do...

---

### Post by cubeist on 2009-02-12
> **conehead77 said:**
> Both suggestions didnt work for me. I cant see official or community plugins, only if i select "all plugins" i can view (some of) them. When i click one it wont install instead the checkbox unchecks automatically everytime i try to install a plugin.

I even searched (after a updatedb) for every file with gnome-do in its name and manually removed them before installing gnome-do and the plugins. Seems something went wrong with my gnome-do...

I had to make sure the PPA for gnome-do was **not** in my sources list.  So after installing the custom deb from the link I posted you basically install the 0.6 plugins from the main registry...but all the new features of 0.8 do work...

Also, I had to make sure compositing in metacity was disabled (via the gconf editor)

---

### Post by conehead77 on 2009-02-12
> **cubeist said:**
> I had to make sure the PPA for gnome-do was **not** in my sources list.  So after installing the custom deb from the link I posted you basically install the 0.6 plugins from the main registry...but all the new features of 0.8 do work...

Also, I had to make sure compositing in metacity was disabled (via the gconf editor)

I disabled compiz, metacity compositing as you suggested and even disabled the universe repository so the old version wasnt showing in synaptic. Still the same problem. Well i give up for now and hope that a working version will eventually show up in the ordinary repositories...

edit: Thanks for your suggestions so far, Ubuntu is just so much more fun with do.

---

### Post by cubeist on 2009-02-12
Huh, I am really stumped... my last suggestion is to purge all 0.8 do files and go back to 0.6... at least you will have basic functionality

Don't forget to erase old plugins from your /home/user/.local/share/gnome-do folder

---

### Post by conehead77 on 2009-02-12
i get this kind of error:
```

ERROR: /home/stulli/.local/share/gnome-do/plugins-0.8.0/addins/Do.File.1.4/File.dll already exists
Installing "Do.File,1.4" addin...
The following add-ins will be installed:
 - Files and Folders v1.4
Installing Files and Folders v1.4

```

Anyways, its getting late. Will try to fix it tomorrow :)

---

### Post by jblackhall on 2009-02-12
> **conehead77 said:**
> i get this kind of error:
```

ERROR: /home/stulli/.local/share/gnome-do/plugins-0.8.0/addins/Do.File.1.4/File.dll already exists
Installing "Do.File,1.4" addin...
The following add-ins will be installed:
 - Files and Folders v1.4
Installing Files and Folders v1.4

```

Anyways, its getting late. Will try to fix it tomorrow :)

Hi, sorry I haven't had time to read this whole thing, so I apologize if what i'm saying has been suggested.  But one thing I noticed when upgrading Do (since I had some problems at first) was to first make sure you kill gnome-do.  Then, rename your ~/.local/share/gnome-do folder and that should fix your issue.  If not, kill do again, delete the plugins folder, and remove gnome-do and gnome-do-plugins and then install the new ones.

I had the problem of not killing gnome-do before doing some upgrades and trying to delete the plugins folder and things went wrong from that.

---

### Post by kenleyrob on 2009-02-16
> **cubeist said:**
> session plugin works aok for me on a 64 bit machine.  I found instructions somewhere on the web to properly install gnome-do 0.8 for a 64bit machine.

First, purge your gnome-do 0.6 program
```
sudo apt-get purge gnome-do gnome-do-plugins
```

Next, download the 0.8 64 bit build from here:
[https://launchpad.net/do/+download]("https://launchpad.net/do/+download") (Don't forget to verify with the md5sum!)

Install that deb

Then add plugins with
```
sudo apt-get install gnome-do-plugins
```

Everything works great, even banshee and sessions...

Are you using Intrepid? I am using Jaunty and there is only an Intrepid AMD64 .deb listed at the link you provided. It will still install for me, however it removes banshee, which is no good for me. 

Another problem I have is that there is now an update for gnome-do since I installed from source, even having removed the ppa from my repositories. If I say yes to this update then gnome do will no longer work. If I remove gnome do completely then install it again via synaptic, gnome do will not even open. So I am having to stick with the deb I made for myself of an earlier version.

Any suggestions?

---

### Post by Chrisj303 on 2009-02-16
I'm having a strange issue.

I have installed 0.80 (on my Ubuntu 8.10) and I had HORRIBLE performance.

I found this was due to my graphics card and driver - Nvidia 8600m GT.

The fix is to enter this into the terminal > nvidia-settings -a InitialPixmapPlacement=2
 - then restart Gnome-Do.

I have Do starting on boot, but it seems that i have to apply that fix everytime I reboot. Otherwise I have crappy performance.

Is this happening to anyone else? How would I go about automating this process until the bug is quashed?

---

### Post by cubeist on 2009-02-16
> **kenleyrob said:**
> Are you using Intrepid? I am using Jaunty and there is only an Intrepid AMD64 .deb listed at the link you provided. It will still install for me, however it removes banshee, which is no good for me. 

Another problem I have is that there is now an update for gnome-do since I installed from source, even having removed the ppa from my repositories. If I say yes to this update then gnome do will no longer work. If I remove gnome do completely then install it again via synaptic, gnome do will not even open. So I am having to stick with the deb I made for myself of an earlier version.

Any suggestions?

I am using intrepid.  I think your best bet for jaunty is to compile do directly from source because JJ has the latest up to date build packages.

If you compile from source and are still getting update messages, go into synaptic and select do and the use the "force version" from the menus...

Also, don't use the gnome-do PPA if compiling from source, that will just add a layer of confusion.

---

### Post by cubeist on 2009-02-16
> **Chrisj303 said:**
> I'm having a strange issue.

I have installed 0.80 (on my Ubuntu 8.10) and I had HORRIBLE performance.

I found this was due to my graphics card and driver - Nvidia 8600m GT.

The fix is to enter this into the terminal  - then restart Gnome-Do.

I have Do starting on boot, but it seems that i have to apply that fix everytime I reboot. Otherwise I have crappy performance.

Is this happening to anyone else? How would I go about automating this process until the bug is quashed?

If you want that setting  to remain you have to add it to your xorg.conf file under the section "Device" . At least I am pretty sure this is where you add it... Sorry, I am using ATI at the moment...

---

### Post by kenleyrob on 2009-02-17
> **cubeist said:**
> I am using intrepid.  I think your best bet for jaunty is to compile do directly from source because JJ has the latest up to date build packages.

If you compile from source and are still getting update messages, go into synaptic and select do and the use the "force version" from the menus...

Also, don't use the gnome-do PPA if compiling from source, that will just add a layer of confusion.

Thanks you, using "force version" I am no longer promted to upgrade to a version of do that doesn't work for me. Strange, as the version I have installed is 0.8.1, when the update was run I ended up with 0.8.0-1.

EDIT:  I actually had to use "Lock Version" to prevent the update from being prompted

---

### Post by hachel on 2009-02-17
hello, I scanned the first couple of pages for my problem (didn't know what to search for) and couldn't find anything:

My Docky sits below my windows, preventing them from properly maximizing. I can resize the window below docky but when I hit maximize it pops up above it again, see below.

thanks,

hachel

---

### Post by Chrisj303 on 2009-02-17
> **cubeist said:**
> If you want that setting  to remain you have to add it to your xorg.conf file under the section "Device" . At least I am pretty sure this is where you add it... Sorry, I am using ATI at the moment...

I've found a much easier solution to my problem (all by myself!)!

I added a simple command to my SESSIONS list. By creating a new entry, which I named "docky_FIX", and the command;
> nvidia-settings -a InitialPixmapPlacement=2

I no longer have to manually add this to the terminal and restart Gnome-Do on every boot!
The performance is just as fast, if not faster than OS X's dock.

I don't know how the SESSION entries are executed in regards to the order. But I seem to have been lucky, and have this command run before the "Gnome-Do" autostart command runs.

I'm running a Nvidia 8600m GT - but I can't see any reason why this fix wouldn't work for different Nvidia cards..
:D

---

### Post by binbash on 2009-02-17
> **hachel said:**
> hello, I scanned the first couple of pages for my problem (didn't know what to search for) and couldn't find anything:

My Docky sits below my windows, preventing them from properly maximizing. I can resize the window below docky but when I hit maximize it pops up above it again, see below.

thanks,

hachel

right click to the first purple icon and select allow window overlap

---

### Post by ace214 on 2009-02-17
> **hachel said:**
> hello, I scanned the first couple of pages for my problem (didn't know what to search for) and couldn't find anything:

My Docky sits below my windows, preventing them from properly maximizing. I can resize the window below docky but when I hit maximize it pops up above it again, see below.

thanks,

hachel

I think this is the behavior when you don't have it auto-hiding. Right click on the Do icon, and see if you have the "Automatically hide" option on. Then you just move your mouse to middle of the bottom of the screen to make it appear.

---

### Post by Chrisj303 on 2009-02-17
> **ace214 said:**
> I think this is the behavior when you don't have it auto-hiding. Right click on the Do icon, and see if you have the "Automatically hide" option on. Then you just move your mouse to middle of the bottom of the screen to make it appear.

No.

Its the "Allow Window Overlap" option - that needs to be checked.

This option is only visible if you have "Automatically Hide" unchecked.

---

### Post by rabid9797 on 2009-02-17
does anyone know how you can make the actual dock smaller?

EDIT: just kidding, you just resize the actual dock haha.

---

### Post by cszikszoy on 2009-02-17
> **rabid9797 said:**
> does anyone know how you can make the actual dock smaller?

If you hover your mouse on the right place (the dotted separator line) the cursor will turn into an arrow pointing both up and down.  Click and drag to adjust the size of the dock.

---

### Post by Chrisj303 on 2009-02-17
I hope the ability to change the color and opacity get added soon.

Its frustrating having the options there, but not working - and the black background really clashes with some of my backgrounds..

---

### Post by theApokalypsis on 2009-02-17
> **Chrisj303 said:**
> I hope the ability to change the color and opacity get added soon.

Its frustrating having the options there, but not working - and the black background really clashes with some of my backgrounds..


yeah im waiting too. although you can set opacity/saturation settings for gnome do in the Compiz Config Settings Manager so that the dock can be entirely itself more transparent. but until then..

---

### Post by cubeist on 2009-02-20
> **theApokalypsis said:**
> yeah im waiting too. although you can set opacity/saturation settings for gnome do in the Compiz Config Settings Manager so that the dock can be entirely itself more transparent. but until then..

True, you can use compiz to change the opacity, but then the icon opacity is also reduced! which only works for brighter icons...

But I can live without opacity if I could have the option to put the dock on the left or right of the screen... wide screen monitors are much better suited to left or right justified docks than top or bottom...

---

### Post by Neon Lights on 2009-02-20
hmm, anyone else having trouble getting Do to start? It complains about gconf-sharp when I started it from the terminal. D: Along with "[Error 22:03:42.029] Missing login credentials. Please set login information in plugin configuration." too.

---

### Post by MaX on 2009-03-01
How do I get to see what I write?
At this time I only have two icons on my Docky, Gnome-Do and Firefox.
When I do <Super>-Space I can't see what the heck I'm writing or what my hits are, this is especially hard when using Rhythmbox because all I see is a blank CD.

Could the docky expand to actually fit the text of what I'm writing, or at least shrink the text by orders of magnitude?

**Update:** Ok, so apparently you can resize the docky.... that wasn't at all apparent since most of the time the icons actually cover the borders to grab on to...

---

### Post by plun on 2009-03-02
Noticed a new function today with a icon zoom slider, nice !

[IMG]http://ubuntu-pics.de/bild/10403/snapshot18_tu5js4.png[/IMG]

---

### Post by scaine on 2009-03-02
Strange - I don't have that yet (UK based - I'll check if I'm using a mirror).  Incidentally, what are "advanced indicators".  They seem to make no difference when they're on or off.

---

### Post by Arlanthir on 2009-03-02
> **scaine said:**
> Strange - I don't have that yet (UK based - I'll check if I'm using a mirror).  Incidentally, what are "advanced indicators".  They seem to make no difference when they're on or off.

Advanced indicators translates as: "Should I draw two little bright dots under the application icon whenever there is more than one instance of it running?" :)

---

### Post by plun on 2009-03-02
> **scaine said:**
> Strange - I don't have that yet (UK based - I'll check if I'm using a mirror).  Incidentally, what are "advanced indicators".  They seem to make no difference when they're on or off.

I am running Gnome-do from source, 1st page within this thread and Gourgis howto,  mess No 6

---

### Post by scaine on 2009-03-02
Gotcha.  Source, eh?  Not for me, I'm afraid.  I'm running Docky from the testers PPA, so I'll be curious to see how often they package behind the svn (or bzr in this case, I suppose) releases.

I'm running 0.8.1 (r1031).  I got a very pretty little clock at my last update three days ago.  Still waiting for that notifiation area integration so that I can lose my top panel though.

I'm guessing that I'll be waiting for a while there, though!  :P

---

### Post by Stochastic on 2009-03-03
so I just downloaded and installed 8.0; now how do I install plugins?
edit: gah, now I see the link.

edit2: BAHH, but how do you install the plugins without the evolution-sharp package?

---

### Post by r.k.rafciol on 2009-03-07
Hey, docky is nice, but i have strange problem, when i reboot or logout gnome-do doesn't start as docky, it starts using default theme, although in preferences tab it's says that docky theme is in use.. (gnome-do 0.8 on jaunty alpha), anyone knows how i can autostart gnome-do as docky always and no to have to change themes?

i use compiz and emerald and i want to use them with gnome-do docky on gf7300gt...

---

### Post by mariner09 on 2009-03-07
I tried Docky on Jaunty and it seemed to have an issue with switching to other workspaces and restoring minimized apps.  It'll rotate to the workspace, but then I have to click the icon again to restore the app.  Is there anyway to change this behavior?

---

### Post by rax_m on 2009-03-08
*oops.. sorry, wrong forum!

---

### Post by tasmaniasedado on 2009-03-10
im new to ubuntu and linux, installed the 8.10 for first time a week ago
docky its great
i have an nvidia 7000 with 180.11
it does eat a lot of cpu (like %80 when moving the cursor over the docky, any fixes for that?
cant active some plugins
updated to mono 2.0 via console
(i did this: sudo apt-get install mono-2.0-devel , its ok?)
for example i check the rythmbox plugin, but it automatically UNchecks
mi version of gnome do is 0.8.0 (its the latest available right?)
i already tried reinstalling gnome do from synaptics
maybe the problem is because the first way i installed gnome do was from the add/remove aplicantions and it was an old version without docky

---

### Post by Sir_Sid on 2009-03-16
meh the dirty hack didnt work for me. I guess ill live without any plugins for now

---

### Post by zekopeko on 2009-03-16
> **tasmaniasedado said:**
> im new to ubuntu and linux, installed the 8.10 for first time a week ago
docky its great
i have an nvidia 7000 with 180.11
it does eat a lot of cpu (like %80 when moving the cursor over the docky, any fixes for that?
cant active some plugins
updated to mono 2.0 via console
(i did this: sudo apt-get install mono-2.0-devel , its ok?)
for example i check the rythmbox plugin, but it automatically UNchecks
mi version of gnome do is 0.8.0 (its the latest available right?)
i already tried reinstalling gnome do from synaptics
maybe the problem is because the first way i installed gnome do was from the add/remove aplicantions and it was an old version without docky

here is ppa for Do

[https://launchpad.net/~do-core/+archive/ppa](https://launchpad.net/~do-core/+archive/ppa)

newest Do is 0.8.1

---

### Post by timmy334 on 2009-04-01
I just installed Gnome-Do from bzr and Docky works. What is strange is that in order to get to the preferences to enable docky, you have to click in the arrow in the upper right corner of gnome-do. There is no option in gconf-editor to do this using the latest bzr. The "zoom icons" feature is gone, I think. I haven't seen it yet. It works fine. I like cairo-dock better, at least until docky gets more customizable.

---

### Post by dirtylobster on 2009-04-01
Gnome DO annoyingly starts by popping up when I log in to the guest account. Bug?

---

### Post by theApokalypsis on 2009-04-01
> **dirtylobster said:**
> Gnome DO annoyingly starts by popping up when I log in to the guest account. Bug?

in the general preferences you can set it to hide on first launch (quiet).

---

### Post by BGFG on 2009-04-02
Do is fast becoming my favourite app. I have one of those desks where the keyboard is on a pullout tray and the mouse is above on the table area, Do saves me te arm movement and extra clicks ;) I just need to get better at keyboard navigation...

---

### Post by suzypeppercorn on 2009-04-07
can anyone post the default settings in gconf for docky? i changed mine around and fubared the zooming. Now all of the icons zoom at once no matter which icon i am hovering over.

I tried a complete removal of everything docky and a restart followed by a reinstall of docky. However, my messed up settings were still there.

Thanks for any help

---

### Post by smbm on 2009-04-07
> **suzypeppercorn said:**
> can anyone post the default settings in gconf for docky? i changed mine around and fubared the zooming. Now all of the icons zoom at once no matter which icon i am hovering over.

I tried a complete removal of everything docky and a restart followed by a reinstall of docky. However, my messed up settings were still there.

Thanks for any help

I don't have the default settings here, you could try deleting this folder though:

```
~/.gconf/apps/gnome-do/preferences/Docky
```

Do it with out Gnome-do running. When you restart Do it should revert to the defaults, I'm not sure but you may also have to log out and in again.

One word of warning though this will cause you to lose any settings you might want to retain for Docky, it will erase them all. Use at your own risk.

Hopefully someone will be able to post a more elegant solution.

---

### Post by suzypeppercorn on 2009-04-07
That did the trick. I didn't even think to delete that folder. I thought the complete removal would have done that but oh well.

Thanks for the help man. My icons zooming just like they used to :)

---

### Post by ronacc on 2009-04-07
compleate removal with synaptic or purge with apt-get does not delete the config files in  ~/home . It sounds like it should but it doesn't .

---

### Post by ukblacknight on 2009-04-15
Does anyone know if it's possible to show mounted drives in Docky?  I'd prefer it if they were in the dock rather than on the desktop!

I've tried the mounter plugin and pinning it to the dock, but even if I change the action to Open rather than copy to clipboard, it will still just "copy to clipboard" rather than open it.  The only way I can open it from the dock is if I right click -> open.

Any ideas?

---

### Post by Flywaver on 2009-04-15
How the heck do we get rid of unwanted icons in Docky?

I don't want APTonCD, Help, Mouse, Sound and Giver shown! :(
I checked every preference and I disabled all plugins! :(

Cheers!

---

### Post by zekopeko on 2009-04-15
> **Flywaver said:**
> How the heck do we get rid of unwanted icons in Docky?

I don't want APTonCD, Help, Mouse, Sound and Giver shown! :(
I checked every preference and I disabled all plugins! :(

Cheers!

drag them of the dock.

---

### Post by Tibuda on 2009-04-15
> **Flywaver said:**
> How the heck do we get rid of unwanted icons in Docky?

I don't want APTonCD, Help, Mouse, Sound and Giver shown! :(
I checked every preference and I disabled all plugins! :(

Cheers!

To remove the automatic icons, move you mouse cursor over the right edge of the dock, press the move button and move the cursor to the left.

To remove launchers you have added yourself, drag them to the desktop.

---

### Post by Flywaver on 2009-04-15
cool! thanks a lot guys!

Cheers!

---

### Post by binbash on 2009-04-15
> **danielrmt said:**
> To remove the automatic icons, move you mouse cursor over the right edge of the dock, press the move button and move the cursor to the left.

To remove launchers you have added yourself, drag them to the desktop.

Thanks works like a charm.

Do you know how can i resize the docky?It is a little big here and i don't see any settings for this?(not width, height)

---

### Post by scaine on 2009-04-15
Just drag the top edge up or down to resize the height.  Although the only place you can actually "drag" the top bar is the far right hand side of the Dock, just above the separator between the launchers and the time/trash applets.

The amount of zoom can be customised in gconf-editor : apps/gnome-do/preferences/Docky/Utilities/DockPreferences and change ZoomPercent to, say, 1.4 (it'll annoyingly change this to 1.39999999, but ignore that).

---

### Post by binbash on 2009-04-15
I changed the icon size from 64 to 32 and the dock becomes smaller

---

### Post by Tibuda on 2009-04-15
Removed. Scaine answered it before me.

---

### Post by Copernicus1234 on 2009-04-17
I do feel a bit stupid for having to ask this, but... where can I download plugins? Seems I fail at finding them myself. :(

Edit: It was the compiled version that didnt list plugins. I removed it and installed gnome-do from the package manager instead, works flawlessly.

---

### Post by trill on 2009-04-20
Maybe I just missed it but how do you move docky to the top of the screen?

---

### Post by scaine on 2009-04-20
You can't (as of 0.8.1.3), but it's being work on for a future release.

---

### Post by trill on 2009-04-20
> **scaine said:**
> You can't (as of 0.8.1.3), but it's being work on for a future release.

But...
[http://www.youtube.com/watch?v=9LVag6i42Og](http://www.youtube.com/watch?v=9LVag6i42Og)

EDIT - Just used gconf-editor and changed orientation from Bottom to Top and it works great :D

---

### Post by DBO on 2009-04-22
> **trill said:**
> But...
[http://www.youtube.com/watch?v=9LVag6i42Og](http://www.youtube.com/watch?v=9LVag6i42Og)

EDIT - Just used gconf-editor and changed orientation from Bottom to Top and it works great :D

[http://dl.getdropbox.com/u/269345/DockyConfig.png](http://dl.getdropbox.com/u/269345/DockyConfig.png)

mwahahahahahaha

---

### Post by ace214 on 2009-04-22
> **DBO said:**
> [http://dl.getdropbox.com/u/269345/DockyConfig.png](http://dl.getdropbox.com/u/269345/DockyConfig.png)

mwahahahahahaha

Ooooooo...

I assume that's in the bzr version...

---

### Post by dt_ on 2009-04-22
> **DBO said:**
> [http://dl.getdropbox.com/u/269345/DockyConfig.png](http://dl.getdropbox.com/u/269345/DockyConfig.png)

mwahahahahahaha

Nice screenshot! :) Could you share the name of your desktop font and GTK theme? looks really nice.

Also, with regards to Gnome-DO (awesome program btw :D) -- is there any way to change the background of the dock, as in AWN? The dark gray is nice but I'd like to have more control over the customization.

Thanks!

---

### Post by DBO on 2009-04-23
> **dt_ said:**
> Nice screenshot! :) Could you share the name of your desktop font and GTK theme? looks really nice.

Also, with regards to Gnome-DO (awesome program btw :D) -- is there any way to change the background of the dock, as in AWN? The dark gray is nice but I'd like to have more control over the customization.

Thanks!

I am considering adding theming to Docky, but I am still wondering exactly how to handle that.  I have a feeling color will probably be out of the picture because of the need for a readable text mode.  We will probably do something like a h-scale that lets you set the color from white to black.

As for that being the bzr version, yes it is, except for the CPU Monitor Docklet which is currently unreleased all together.

---

