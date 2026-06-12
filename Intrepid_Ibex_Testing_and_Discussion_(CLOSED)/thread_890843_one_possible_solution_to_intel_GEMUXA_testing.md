---
title: "one possible solution to intel GEM/UXA testing"
date: 2008-08-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by 7oby on 2008-08-15
_[GEM]("http://lwn.net/Articles/283793/")_ (Graphics Execution Manager) is a new memory manager for the GPU, which replaces the former _[TTM]("http://lwn.net/Articles/257417/")_ (translation table maps). This new memory manager GEM is picked up by intel drivers for Linux.

Unfortunately GEM has dependencies to the kernel, 2D (EXA) as well as 3D acceleration code (MesaGL). The APIs are not yet stable and change frequently. For an overview read _[here]("http://www.rojtberg.net/67/exa-uxa-dri-gem-ttm/")_. Ultimately GEM/UXA _[won't make it]("http://ubuntuforums.org/showpost.php?p=5459591&postcount=18")_ into Ubuntu 8.10 (Intrepid). Just one example (of many): The intel video driver will require libdrm 2.4.0, but there's _[2.3.x in the Intrepid]("http://packages.ubuntu.com/de/intrepid/libdrm2")_ repository currently.

I was looking for a solution to **testing GEM/UXA development progress** from time to time without **breaking my entire ubuntu installation**. I encourage **advanced users** to **propose improvements** or point to mistakes I've done. **Other users**, who previously may have failed compiling and installing all required components, may find something useful for their own efforts.

There are quite some dependencies such as:
. GEM enabled kernel
. libdrm >= 2.4.0
. GEM based MesaGL
. GEM based 2d acceleration code (UXA)

I can't provide a guide for every possible failure you might encounter. Therefore I suggest you have a least these skills:
. able to install missing packages in you ubuntu installion
. have worked with one version control system before (CVS, SVN, git). Or at least know the concepts
. can read shell scripts to some degree
. have successfully compiled something else before (e.g. kernel)

Let's start:

**1. GEM kernel**
First I tried patching my 2.6.26 and 2.6.27 kernel source code with the _[patches sent to LKML]("http://thread.gmane.org/gmane.linux.kernel/715029/focus=715030")_. One of the patches is broken by misformatting (see all the " <at>  <at> " in the code). And _[those patches]("http://people.freedesktop.org/~keithp/gem_patches/")_ seem to miss drm, i915 kernel module patches. I didn't bother trying to fix this after browsing _[this posting]("http://thread.gmane.org/gmane.linux.kernel/715029/focus=715030")_.

I needed a fool proof thing and just grabbed a complete patched kernel:
[http://git.kernel.org/?p=linux/kernel/git/anholt/drm-intel.git;a=shortlog;h=drm-intel-next](http://git.kernel.org/?p=linux/kernel/git/anholt/drm-intel.git;a=shortlog;h=drm-intel-next)

you need to do something like that:
```

git clone git://git.kernel.org/pub/scm/linux/kernel/git/anholt/drm-intel linux-2.6-gem-patched
cd linux-2.6-gem-patched
git-checkout --track -b drm-intel-next origin/drm-intel-next
```
More on _[git usage here]("http://linux.yyz.us/git-howto.html")_.

After that copy your .config, configure your kernel and build. Maybe this looks like this for you:
```

make menuconfig
fakeroot make-kpkg --initrd --append-to-version=-gem kernel-image kernel-headers
cd ..
sudo dpkg -i linux-image-2.6.27-rc2-gem_2.6.27-rc2-gem-10.00.Custom_i386.deb
sudo dpkg -i linux-headers-2.6.27-rc2-gem_2.6.27-rc2-gem-10.00.Custom_i386.deb
```
More on _[Ubuntu kernel compilation]("https://help.ubuntu.com/community/Kernel/Compile")_.

The 2.6.26 kernel introduces PAT (page attribute tables) instead of MTRR. I had some trouble with PAT and the intel drivers (though I didn't test the GEM one). Anyway: I have disabled PAT in the kernel booting option "nopat".

**2. Xorg, mesagl, libdrm, intel-video**

I started with a complete script found _[here]("http://wiki.x.org/wiki/Development/git")_ and modified it slightly to compile sucessfully. It builds everything to /opt/gfx-test and leaves your current installation untouched. The reason why we can use the master branches is that since ~9th August the drm-gem branches (xf86-video-intel, mesa and drm) _[merged into their corresponding master branch]("http://virtuousgeek.org/blog/index.php/2008/08/09/xf86_video_intel_2_5_merge_status")_.

```
#!/bin/sh
PREFIX="/opt/gfx-test"

MAKE="make -j3" 

REPOS="\
git://git.freedesktop.org/git/xorg/util/macros \
git://git.freedesktop.org/git/xorg/proto/x11proto \
git://git.freedesktop.org/git/xorg/proto/xextproto \
git://git.freedesktop.org/git/xorg/proto/videoproto \
git://git.freedesktop.org/git/xorg/proto/renderproto \
git://git.freedesktop.org/git/xorg/proto/inputproto \
git://git.freedesktop.org/git/xorg/lib/libxtrans \
git://git.freedesktop.org/git/xorg/lib/libX11 \
git://git.freedesktop.org/git/xorg/lib/libXext \
git://git.freedesktop.org/git/xorg/lib/libXi \
git://git.freedesktop.org/git/xorg/lib/libxkbfile \
git://git.freedesktop.org/git/xorg/lib/libfontenc \
git://git.freedesktop.org/git/xorg/lib/libXfont \
git://git.freedesktop.org/git/xorg/lib/libXfixes \
git://git.freedesktop.org/git/xorg/lib/libXdamage \
git://git.freedesktop.org/git/xorg/lib/libXvMC \
git://git.freedesktop.org/git/xorg/lib/libXxf86vm \
git://git.freedesktop.org/git/xorg/proto/dri2proto \
git://git.freedesktop.org/git/xorg/proto/glproto \
git://git.freedesktop.org/git/xorg/lib/libpciaccess \
git://git.freedesktop.org/git/pixman \
git://git.freedesktop.org/git/xcb/proto \
git://git.freedesktop.org/git/xcb/pthread-stubs \
git://git.freedesktop.org/git/xcb/libxcb \
git://git.freedesktop.org/git/xorg/proto/randrproto \
git://git.freedesktop.org/git/mesa/drm \
git://git.freedesktop.org/git/mesa/mesa \
git://git.freedesktop.org/git/xorg/xserver \
git://git.freedesktop.org/git/xorg/driver/xf86-input-synaptics \
git://git.freedesktop.org/git/xorg/driver/xf86-input-keyboard \
git://git.freedesktop.org/git/xorg/driver/xf86-video-intel"

modules="\
x11proto \
xextproto \
videoproto \
renderproto \
inputproto \
libxtrans \
proto \
pthread-stubs \
libxcb \
libX11 \
libXext \
libXi \
libxkbfile \
libfontenc \
libXfont \
libXvMC \
libXxf86vm \
libXfixes \
libXdamage \
dri2proto \
glproto \
libpciaccess \
pixman \
randrproto"

init()
{
        for repo in $REPOS; do
                echo "Cloning $repo";
                git clone $repo;
        done
        cd macros
        echo "Building macros"
        ./autogen.sh --prefix="$PREFIX";
        ($MAKE);
        make install
        cd ..
}

update_modules()
{
        for module in $modules; do
                cd $module
                git pull
                cd ..
        done
}

build ()
{
        export ACLOCAL="aclocal -I$PREFIX/share/aclocal"
        export PKG_CONFIG_PATH="$PREFIX/lib/pkgconfig"
        for i in $modules; do
                cd $i
                echo "Building $i"
                ./autogen.sh --prefix="$PREFIX";
                if [ $? -ne 0 ]; then
                        echo "Failed to configure $i."
                        exit
                fi
                ($MAKE);
                make install
                cd ..
        done
        # build drm
        cd drm
        ./autogen.sh --prefix="$PREFIX" --enable-udev
        ($MAKE)
        make -C linux-core
        # assuming you're on Linux, otherwise use bsd-core
        make install
        cd ..
#build mesa
        cd mesa
        ./autogen.sh --prefix=$PREFIX --with-driver=dri --disable-glut
        if [ $? -ne 0 ]; then
                echo "Failed to configure Mesa."
                exit
        fi
        ($MAKE)
        make install
        mkdir -p $PREFIX/bin
        install -m755 progs/xdemos/{glxinfo,glxgears} $PREFIX/bin/
        cd ..
#buildxserver
        cd xserver
        ./autogen.sh --prefix=$PREFIX --enable-builtin-fonts
        if [ $? -ne 0 ]; then
                echo "Failed to configure X server."
                exit
        fi
        ($MAKE)
        make install
        chown root $PREFIX/bin/Xorg;
        chmod +s $PREFIX/bin/Xorg
        cd ..
#mouse
        cd xf86-input-synaptics
        ./autogen.sh --prefix=$PREFIX
        ($MAKE)
        make install
        cd ..
#keyboard
         
        cd xf86-input-keyboard
        ./autogen.sh --prefix=$PREFIX
        ($MAKE)
        make install
        cd ..
#intel
        cd xf86-video-intel
        ./autogen.sh --prefix=$PREFIX
        ($MAKE)
        make install
        cd ..
}

case "$1" in 
        init)
                init
                ;;
        build)
                build
                ;;
        update)
                update_modules
                ;;
        *)
                echo "Usage: $0 init | build | update"
                exit 3
esac
```

There aren't many changes I needed to do. According to [this](http://gitweb.freedesktop.org/?p=mesa/drm.git;a=commit;h=9101a0205c897fea28e6a3d875111a83ad7f7732) I added:
[FONT="Fixedsys"]
        # build drm
        cd drm
        ./autogen.sh --prefix="$PREFIX" [COLOR="Red"]--enable-udev[/COLOR][/FONT]

I needed the touchpad driver instead of the mouse driver. You might have to change that:
[FONT="Fixedsys"]REPOS="\
[...]
git://git.freedesktop.org/git/xorg/driver/xf86-input-[COLOR="Red"]synaptics[/COLOR]
[...]
#mouse
        cd xf86-input-[COLOR="Red"]synaptics[/COLOR][/FONT]
More recent versions of the synaptics drivers required git://git.freedesktop.org/git/xorg/lib/libXi so I added this to the list of modules as well.

This script isn't particular smart, but therefore at least easy to understand. For example it doesn't support incremental builds. If compilation fails and you enter a directory to trigger building make sure to have the environment variables ACLOCAL and PKG_CONFIG_PATH set accordingly.

Build will **fail** the first couple of times (like 10x). You need to figure out which x11-[...]-proto package is missing and install it using aptitude or your favorite package manager in ubuntu.

Also
```
        chown root $PREFIX/bin/Xorg;
        chmod +s $PREFIX/bin/Xorg
```
will fail since it requires administrator rights. Apply it manually or add sudo to script:

```
sudo chown root /opt/gfx-test/bin/Xorg
sudo chmod +s /opt/gfx-test/bin/Xorg
sudo chown root /opt/gfx-test/lib/xorg/modules/drivers/*
```
I don't remember whether the last statement is really required.

This was the difficult part. If everything builds and installs, you're almost done.

**3. Launch it**
There are two ways of using the GEM enabled driver. The current EXA 2D accelerated way, which is supposed to be the more stable one. The second way UXA is intended for DRI2 use.

I'm having some difficulties with EXA and 3D accleration ([bug #17486]("https://bugs.freedesktop.org/show_bug.cgi?id=17486")). EXA is still the default (_[click here]("http://gitweb.freedesktop.org/?p=xorg/driver/xf86-video-intel.git;a=commit;h=8f10bfb127bfe73d83d58f1f306fb9a4dfd825d6")_).

UXA is intended for DRI2 use, which currently means you are required to have the (dri2) branch of xf86-video-intel compiled._[Read here]("http://keithp.com/blogs/UMA_Acceleration_Architecture/")_ for information about UXA. To enable UXA modify your /etc/X11/xorg.conf accordingly:

```
Section "Device"
        Identifier      "Configured Video Device"
        Option          "AccelMethod"           "UXA"
        Option          "Tiling"                "No"
EndSection
```

UXA acceleration on GM965 only works with tiling disabled and I'm also having some problems with 3D ([bug #17486]("https://bugs.freedesktop.org/show_bug.cgi?id=17486")). Although Eric mentions in his blog to edit [hw/xfree86/Makefile.am]("http://anholt.livejournal.com/39544.html"), this is no longer necessary since [this xserver commit]("http://gitweb.freedesktop.org/?p=xorg/xserver.git;a=commit;h=66a87517bd80b21e107df9d57968d81a92f91fd5"). Kristian mentions in his posting to xorg mailing list of [an Option "DRI2"]("http://lists.freedesktop.org/archives/xorg/2008-October/039404.html") which is necessary, but I can't confirm that. Works for me without.

It doesn't hurt having UXA enabled even when starting your "normal" old Non-GEM ubuntu X.org. It will fall back to the default EXA gracefully with AccelMethod=UXA. Turning off tiling has a negative performance impact on DualChannel or FlexMode enabled systems. If your memory runs in single channel mode there shouldn't be a difference between turning on/off tiling.

I also had problems with big screens. The memory allocation failed in the X.org.0.log ([bug #17490]("https://bugs.freedesktop.org/show_bug.cgi?id=17490")):
```
#       SubSection "Display"
#               Virtual 3200 3000
#       EndSubSection
```

Now you are set and should be able to launch x:
```
export LD_LIBRARY_PATH=/opt/gfx-test/lib
startx -- /opt/gfx-test/bin/Xorg -verbose -nolisten tcp
```
You may also change "ServerArgsLocal" in /etc/kde3/kdm/kdmrc or whatever desktop you use.

If it breaks you'll find an x.log here: /opt/gfx-test/var/log/Xorg.0.log

If you have difficulties you may also check this guide, which is quite similar:
[http://hoegsberg.blogspot.com/2008/02/building-and-installing-drmdrix-stack.html](http://hoegsberg.blogspot.com/2008/02/building-and-installing-drmdrix-stack.html)

Intel asked to test their GEM enabled drivers [here](http://lists.freedesktop.org/archives/xorg/2008-August/037960.html). If you encounter problems or bugs, a good place to read is the [bugdatabase here](https://bugs.freedesktop.org/buglist.cgi?query_format=advanced&short_desc_type=allwordssubstr&short_desc=&product=xorg&component=Driver%2Fintel&long_desc_type=substring&long_desc=&bug_file_loc_type=allwordssubstr&bug_file_loc=&status_whiteboard_type=allwordssubstr&status_whiteboard=&keywords_type=allwords&keywords=&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&emailassigned_to1=1&emailtype1=substring&email1=&emailassigned_to2=1&emailreporter2=1&emailqa_contact2=1&emailcc2=1&emailtype2=substring&email2=&bugidtype=include&bug_id=&chfieldfrom=&chfieldto=Now&chfieldvalue=&cmdtype=doit&order=Reuse+same+sort+as+last+time&field0-0-0=noop&type0-0-0=noop&value0-0-0=). This is also a good place to file new bugs.

**Open Issues**

1. *Keyboard*
You might have these messages in Xorg.0.log:
```
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(EE) XKB: Couldn't open rules file /opt/gfx-test/share/X11/xkb/rules/base
(EE) XKB: No components provided for device Virtual core keyboard
(WW) Couldn't load XKB keymap, falling back to pre-XKB keymap

```

I started trying to fix this by first making files of package xkb-data available to Xorg:
mv /opt/gfx-test/share/X11/xkb /opt/gfx-test/share/X11/xkb.bak
ln -s /usr/share/X11/xkb /opt/gfx-test/share/X11/xkb
This resulted in
```
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(EE) Error compiling keymap (server-0)
(EE) XKB: Couldn't compile keymap
(WW) Couldn't load XKB keymap, falling back to pre-XKB keymap
```
I continued fixing with
ln -s /usr/bin/setxkbmap /opt/gfx-test/bin/setxkbmap
ln -s /usr/bin/xkbcomp /opt/gfx-test/bin/xkbcomp

Ultimately this lead X crashing. I didn't test too much more and stopped here (time boxing). This is a little bit unfortunate, since VT-Switching (Crtl + Alt + F1) currently doesn't work and I can't tell whether it's because of a broken keyboard mapping or regressions in intel VT-Switching code. Suggestions welcome. I only tested KDE 3.5.9, neither gnome nor evdev autoconfiguration.

[COLOR="Red"]fixed[/COLOR]: After upgrading kubuntu 8.04 -> 8.10-rc, the issue was fixed. I still needed
```
ln -s /usr/share/X11/xkb /opt/gfx-test/share/X11/xkb
ln -s /usr/bin/setxkbmap /opt/gfx-test/bin/setxkbmap
ln -s /usr/bin/xkbcomp /opt/gfx-test/bin/xkbcomp
```But that's it. Setting the keyboard worked as well as Ctrl + Alt + Fn console switching. Maybe the setxkbmap, xkbcomp that shipped with 8.04 was not compatible with current git master xserver.

2. *Performance*
glxgears performance dropped from 700fps to 250fps when going from TTM EXA -> GEM EXA.

Rememeber that all compiles described here don't strip the debugging information of the libraries and executables and makeing those files huge and pollute CPU caches. I stripped the most important ones on the command line, but performance didn't increase.

**History of changes to this posting**

I recognized some people picked this guide up. Some things change over time (e.g. bugs, walkarounds and some compile options) and this history helps you to update your build chain accordingly:

2008/09/04:
. added link to patch EXA screen corruption
. updated status on EXA + UXA acceleration
. added --track option to git checkout command to trace drm-gem-merge branch of gem enabled kernel
. added --enable-udev to autogen.sh of drm for better ubuntu compatibility

2008/09/07:
. added drm bug #17446 information

2008/09/09:
. added "open issues" section
. added link to bug #17490

2008/09/11:
. removed link to [bug #17446]("https://bugs.freedesktop.org/show_bug.cgi?id=17446") since it's fixed
. add [bug #17531]("https://bugs.freedesktop.org/show_bug.cgi?id=17531")

2008/09/17:
. removed "--disable-dri2" flag from xserver autogen.sh since dri2 is now free of TTM bits and compiles fine
. removed fixed [bug #17531]("https://bugs.freedesktop.org/show_bug.cgi?id=17531")
. removed fixed [bug #17304]("https://bugs.freedesktop.org/show_bug.cgi?id=17304")

2008/10/06:
. updated GEM kernel git repository according to Eric's posting [here]("http://anholt.livejournal.com/39544.html").

2008/10/07:
. corrected typo in git-checkout kernel command

2008/10/16
. provided more uptodate DRI2 information in UXA section

2008/10/24
. added libXi to the list of modules, since it's required by more recent synaptics drivers.

2008/10/26
. keyboard issue fixed by upgrading kubuntu 8.04 -> 8.10-rc

**Blogs:**
[Eric Anholt]("http://anholt.livejournal.com/") *** [Carl Worth]("http://www.cworth.org/blog/") *** [Keith Packard]("http://keithp.com/blog/") *** [Jesse Barnes]("http://virtuousgeek.org/blog/") *** [Dave Airlie]("http://airlied.livejournal.com/") *** [Kristian Hogsberg]("http://hoegsberg.blogspot.com")

---

### Post by barbro on 2008-08-30
Nice guide...
works fine until i try to start X, then the server crashes.
My Xorg.0.log is appended... Any ideas how to get it running?
```


This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.5.99.1
Release Date: (unreleased)
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.27-rc4-gem i686 
Current Operating System: Linux barbro 2.6.27-rc4-gem #1 SMP Sun Aug 31 00:42:07 CEST 2008 i686
Build Date: 31 August 2008  02:07:49AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/opt/gfx-test/var/log/Xorg.0.log", Time: Sun Aug 31 02:40:53 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "nVidia Corporation G80 [GeForce 8800 GTS]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(==) FontPath set to:
	built-ins
(==) ModulePath set to "/opt/gfx-test/lib/xorg/modules"
(II) Loader magic: 0x3ae0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 3.1
	X.Org Server Extension : 1.1
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0@0:2:0) unknown vendor (0x8086) unknown chipset (0x29c2) rev 2, Mem @ 0xf6100000/0, 0xe0000000/0, 0xf6000000/0, I/O @ 0x0000e200/0
(--) PCI: (0@4:0:0) unknown vendor (0x14f1) unknown chipset (0x8800) rev 3, Mem @ 0xf3000000/0
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /opt/gfx-test/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.99.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /opt/gfx-test/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.99.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /opt/gfx-test/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.5.99.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "dri"
(II) Loading /opt/gfx-test/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.99.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(WW) Warning, couldn't open module dri2
(II) UnloadModule: "dri2"
(EE) Failed to load module "dri2" (module does not exist, 0)
(II) LoadModule: "intel"
(II) Loading /opt/gfx-test/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.5.99.1, module version = 2.5.96
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "kbd"
(II) Loading /opt/gfx-test/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.5.99.1, module version = 1.3.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 3.1
(II) LoadModule: "mouse"
(II) Loading /opt/gfx-test/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.5.99.1, module version = 1.3.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 3.1
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33,
	Mobile Intel® GM45 Express Chipset,
	Intel Integrated Graphics Device, G45/G43, Q45/Q43
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /opt/gfx-test/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.99.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /opt/gfx-test/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.99.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(**) intel(0): Option "AccelMethod" "UXA"
(II) intel(0): Integrated Graphics Chipset: Intel(R) G33
(--) intel(0): Chipset: "G33"
(--) intel(0): Linear framebuffer at 0xE0000000
(--) intel(0): IO registers at addr 0xF6100000
(**) intel(0): Using UXA for acceleration
(II) intel(0): 2 display pipes available.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Generic Monitor
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): EDID vendor "SAM", prod id 187
(II) intel(0): Using EDID range info for horizontal sync
(II) intel(0): Using EDID range info for vertical refresh
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): EDID vendor "SAM", prod id 187
(II) intel(0): Output VGA connected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output VGA using initial mode 1280x1024
(II) intel(0): detected 1024 kB GTT.
(II) intel(0): detected 7164 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Intel XvMC decoder disabled
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /opt/gfx-test/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.5.99.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /opt/gfx-test/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(WW) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 8128 kB
(II) intel(0): VESA VBE OEM: Intel(r)Q33/Q35/G33 Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r)Q33/Q35/G33 Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(**) intel(0): Display dimensions: (380, 300) mm
(**) intel(0): DPI set to (93, 118)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /opt/gfx-test/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.99.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 488704 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 1954812 kB available
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) intel(0): [drm] Registers = 0xf6100000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): [DRI] installation complete
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x0e000000 (pgoffset 57344)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x006ff000:            end of stolen memory
(II) intel(0): 0x006ff000-0x0dffffff: DRI memory manager (222212 kB)
(II) intel(0): 0x0e000000-0x0fffffff: classic textures (32768 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): BO memory allocation layout:
(II) intel(0): 0x006ff000:            start of memory manager
(II) intel(0): 0x01000000-0x01afffff: depth buffer (11264 kB) X tiled
(II) intel(0): 0x02000000-0x02afffff: back buffer (11264 kB) X tiled
(II) intel(0): 0x03000000-0x03aeffff: front buffer (11200 kB) X tiled
(II) intel(0): 0x00720000-0x00720fff: overlay registers (4 kB)
(II) intel(0): 0x00721000-0x00728fff: logical 3D context (32 kB)
(II) intel(0): 0x00729000-0x00732fff: HW cursors (40 kB)
(II) intel(0): 0x0e000000:            end of memory manager
(WW) intel(0): PRB0_CTL (0x0001f001) indicates ring buffer enabled
(WW) intel(0): Existing errors found in hardware state.
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Pipe B is off
(II) intel(0):   Display plane B is now disabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe A
(II) intel(0): [drm] dma control initialized, using IRQ 219
(II) intel(0): [drm] mapped front buffer at 0xe3000000, handle = 0xe3000000
(II) intel(0): [drm] mapped back buffer at 0xe2000000, handle = 0xe2000000
(II) intel(0): [drm] mapped depth buffer at 0xe1000000, handle = 0xe1000000
(II) intel(0): [drm] mapped classic textures at 0xee000000, handle = 0xee000000
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(II) intel(0): Set up textured video
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Enabled
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: drmOpenMinor returns 12
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
(II) AIGLX: Loaded and initialized /opt/gfx-test/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 376 x 301
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "se"
(**) Generic Keyboard: XkbLayout: "se"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(EE) XKB: Couldn't open rules file /opt/gfx-test/share/X11/xkb/rules/base
(EE) XKB: No components provided for device Virtual core keyboard
(WW) Couldn't load XKB keymap, falling back to pre-XKB keymap
(EE) XKB: Couldn't open rules file /opt/gfx-test/share/X11/xkb/rules/xorg
(EE) XKB: No components provided for device Generic Keyboard
(WW) Couldn't load XKB keymap, falling back to pre-XKB keymap
(**) Configured Mouse: (accel) keeping acceleration scheme 1
(**) Configured Mouse: (accel) filter chain progression: 2.00
(**) Configured Mouse: (accel) filter stage 0: 20.00 ms
(**) Configured Mouse: (accel) set acceleration profile 0
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) intel(0): EDID vendor "SAM", prod id 187
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): EDID vendor "SAM", prod id 187
(II) intel(0): EDID vendor "SAM", prod id 187
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): EDID vendor "SAM", prod id 187
(II) intel(0): EDID vendor "SAM", prod id 187
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): EDID vendor "SAM", prod id 187
(II) intel(0): EDID vendor "SAM", prod id 187
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): EDID vendor "SAM", prod id 187

Backtrace:
0: /opt/gfx-test/bin/Xorg(xf86SigHandler+0x79) [0x80c17f9]
1: [0xb8055400]
2: /opt/gfx-test/lib/dri/i915_dri.so(intelMakeCurrent+0x4c) [0xa78435ac]
3: /opt/gfx-test/lib/dri/i915_dri.so [0xa7820846]
4: /opt/gfx-test/lib/xorg/modules/extensions//libglx.so [0xb7c3734c]
5: /opt/gfx-test/lib/xorg/modules/extensions//libglx.so [0xb7c2bfe7]
6: /opt/gfx-test/lib/xorg/modules/extensions//libglx.so [0xb7c2e686]
7: /opt/gfx-test/bin/Xorg(Dispatch+0x2aa) [0x808baca]
8: /opt/gfx-test/bin/Xorg(main+0x3da) [0x807112a]
9: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c92685]
10: /opt/gfx-test/bin/Xorg [0x8070611]

Fatal server error:
Caught signal 11.  Server aborting


Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/opt/gfx-test/var/log/Xorg.0.log" for additional information.

(II) UnloadModule: "kbd"
(II) UnloadModule: "mouse"
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) intel(0): xf86UnbindGARTMemory: unbind key 0

```

Fixed in resent mesa master

---

### Post by mateusz.k on 2008-09-05
Here is what I get in dmesg after starting GDM

```

[drm] Initialized drm 1.1.0 20060810
pci 0000:00:02.0: setting latency timer to 64
[drm] Initialized i915 1.6.0 20080730 on minor 0
input: Virtual ThinkFinger Keyboard as /class/input/input12
wlan0: authenticate with AP 00:1e:2a:69:79:4a
wlan0: authenticated
wlan0: associate with AP 00:1e:2a:69:79:4a
wlan0: RX AssocResp from 00:1e:2a:69:79:4a (capab=0x411 status=0 aid=1)
wlan0: associated
------------[ cut here ]------------
WARNING: at kernel/softirq.c:136 local_bh_enable_ip+0x9b/0xd0()
Modules linked in: i915 drm kvm_intel kvm cdc_acm snd_seq_oss snd_seq_midi_event snd_seq snd_seq_device uinput snd_hda_intel snd_pcm_oss yenta_socket rsrc_nonstatic snd_mixer_oss iwlagn thinkpad_acpi snd_pcm iwlcore video rtc_cmos pcmcia_core snd_timer rfkill backlight snd_page_alloc mac80211 snd_hwdep hci_usb output snd cfg80211 bluetooth uhci_hcd intelfb i2c_algo_bit cfbcopyarea cfbimgblt cfbfillrect
Pid: 5496, comm: Xorg Not tainted 2.6.27-rc4-gem #4

Call Trace:
 <IRQ>  [<ffffffff8023a184>] warn_on_slowpath+0x64/0xb0
 [<ffffffff8022ef2d>] enqueue_entity+0xad/0x100
 [<ffffffff8023443e>] try_to_wake_up+0xee/0x1a0
 [<ffffffff8023fe3b>] local_bh_enable_ip+0x9b/0xd0
 [<ffffffffa01fb5d8>] drm_lock_take+0x78/0xe0 [drm]
 [<ffffffffa01faa68>] drm_locked_tasklet_func+0x48/0xb0 [drm]
 [<ffffffff8023f669>] tasklet_hi_action+0x59/0xd0
 [<ffffffff8024003a>] __do_softirq+0x6a/0xc0
 [<ffffffff8020cd1c>] call_softirq+0x1c/0x30
 [<ffffffff8020eda5>] do_softirq+0x35/0x70
 [<ffffffff8023fcf5>] irq_exit+0xa5/0xb0
 [<ffffffff8020f031>] do_IRQ+0x81/0x100
 [<ffffffff8020bfa1>] ret_from_intr+0x0/0xa
 <EOI>  [<ffffffff8066d9ec>] _spin_unlock_irq+0xc/0x30
 [<ffffffff8023ebcc>] do_setitimer+0x39c/0x3c0
 [<ffffffff8023ecad>] sys_setitimer+0xbd/0xe0
 [<ffffffff802bb9a5>] sys_select+0x185/0x1d0
 [<ffffffff8020ba9b>] system_call_fastpath+0x16/0x1b

---[ end trace 1e12e8a2a941de5f ]---

```

---

### Post by darnabas on 2008-09-08
hi~ 

thanks for the instructions.  They were very helpful.

I've checkout the kernel version suggested from the instructions regarding the Bug report 17446 posted in the instructions. Unfortunately, I'm running into

**"i915: Unknown symbol pci_read_base" **

error when i try to load the i915.ko module.

any thoughts that come to your mind concerning this issue?

thanks in advance!

---

### Post by 7oby on 2008-09-09
> **darnabas said:**
> 
**"i915: Unknown symbol pci_read_base" **

error when i try to load the i915.ko module.

It's not sufficient to just load those modues. GEM requires some more kernel patches and in this case this one:
[http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-08/msg00127.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-08/msg00127.html)

That means you really need to boot that kernel that you have built. It's not sufficient to just load the i915.ko (unless you have a sufficiently patched kernel).

---

### Post by barbro on 2008-09-11
I need to build drm with head at modesetting-gem otherwise building xf86-video-intel fail. 

Another thing that i noticed yesterday is that when i build drm and modules i don't get any i915.ko only i810.ko and some others that i don't care about. Does this happen to you too?

---

### Post by 7oby on 2008-09-11
> **barbro said:**
> I need to build drm with head at modesetting-gem otherwise building xf86-video-intel fail.
xf86-video-intel and drm both on master branch compile fine here.

Also I don't see those very recent commits of master
. intel: move drm calls to exec buffers to libdrm_intel.
. intel: Move IRQ emit/wait from callbacks into the bufmgr.
. Move intel libdrm stuff to libdrm_intel.so
show up on the modesetting-gem branch of drm. However those changes resulted in changes of xf86-video-intel, which will make your build definitly fail.

On the other hand: Those very recent commits I can compile, but break the 2d driver when launching currently (see [bug #17531]("https://bugs.freedesktop.org/show_bug.cgi?id=17531")).

> **barbro said:**
> Another thing that i noticed yesterday is that when i build drm and modules i don't get any i915.ko only i810.ko and some others that i don't care about. Does this happen to you too?
Due to this commit:
[http://gitweb.freedesktop.org/?p=mesa/drm.git;a=commit;h=280d415957c0af099c44aaecb69a06c68c86aebb](http://gitweb.freedesktop.org/?p=mesa/drm.git;a=commit;h=280d415957c0af099c44aaecb69a06c68c86aebb)
you need to do a

export OS_HAS_GEM=1

on the console before compiling to get i915.ko.

However I don't use "make -C linux-core" in the drm directory for building the drm kernel modules. I use those in Eric's kernel i915.ko, drm.ko since those seem to be better maintained (more uptodate).

---

### Post by Starks on 2008-09-11
We need a GEM/UXA PPA repo.

<________<

---

### Post by 7oby on 2008-09-13
> **Starks said:**
> We need a GEM/UXA PPA repo.

The idea in general is good. There are two drivers to track:

1. track GEM EXA intel 2.5.0 release
2. track GEM UXA DRI2 intel ongoing development [+ kernel based modesetting]

Both have these in common:

. GEM enabled kernel based on intrepid
. GEM aware libdrm
. GEM mesa (which has to be master right now. mesa_7_2_branch is not sufficient)

Based on these two exclusive package choices:

1. track EXA: xf86-video-intel-2.5-branch
2. track UXA/DRI2: xf86-video-intel master + Xorg DRI2 extension

Up to now it was too early for a PPA repro I think. Too many dependency changes and too many errors which required rapid posting on intel xorg bugzilla and even bisect skills. Even Debian experimental only tracks the stable intel 2.4.2 driver as of today:
[http://packages.debian.org/experimental/xserver-xorg-video-intel](http://packages.debian.org/experimental/xserver-xorg-video-intel)

---

### Post by Starks on 2008-09-13
I've seen 2.4.2 packages for Hardy with GEM/UXA patched in, but it utterly breaks a system.

---

### Post by barbro on 2008-09-16
By making a make clean in your drm directory bug #17531 is solved.
Now things really looking up,

---

### Post by 7oby on 2008-09-17
> **barbro said:**
> By making a make clean in your drm directory bug #17531 is solved.
That's actually me who wrote Comment#2 here:
[https://bugs.freedesktop.org/show_bug.cgi?id=17531#c2](https://bugs.freedesktop.org/show_bug.cgi?id=17531#c2)

There've been some improvements in 3D and compiz as well:
[https://bugs.freedesktop.org/show_bug.cgi?id=17486](https://bugs.freedesktop.org/show_bug.cgi?id=17486)

Performance wise the recent post of Eric Anholt on his blog reveals some information:
[http://anholt.livejournal.com/39405.html](http://anholt.livejournal.com/39405.html)

I've added links to blogs of the most prominent contributors to the intel driver and infrastructure below my first posting.

In case you guys miss something, please post, I'd be happy to add that. I'd even consider pushing this to some Wiki such that more people can add their information and stuff regardings this issue.

---

### Post by barbro on 2008-09-17
After building today i get the famous White cube when running compiz.
I'm running the follwing with heads at: 
mesa: (intel-2008-q3)4a310d6bd3767d217c433112bc2945a2e001de4e (X stalls on master)
intel: (dri2)8a54e3be5c5057fe8e3c52c03401fdada7978c45
drm: (master)ee6bcabc506e4d506fb65447c405f8514ab1f4e1
eric's kernel: (drm-gem-merge)c90fab4943289b51cfe28113db0f8e2908d965cd

This problem I used to solve just by compiling new drm kernel modules. Trying to to this i run into some problems. They don't build if i pass export OS_HAS_GEM=1 and its said in an earlier post that i'm supposed to use Eric's kernel since they are more up-to-date.

Any ides how to get rid of "the white cube of death"?

---

### Post by 7oby on 2008-09-17
Since you've compiled the (dri2) branch of the 2D driver you currently HAVE to use UXA. Did you do enable that one in Xorg.conf?

Did you try EXA as well? If you use EXA you have to compile the (master) branch of the intel 2d driver. The EXA branch should be more stable than the UXA/DRI2 story. In addition: You have to have a DRI2 enabled xserver for UXA currently. Did you notice that I removed the "--disable-dri2" build flag from xserver yesterday?

What I don't understand from your posting: Are you running Eric's kernel or just the drm.ko and i915.ko? It's required to run Eric's kernel since it contains more pachtes than just the GEM enabled drm.ko and i915.ko. Building OS_HAS_GEM=1 is NOT required for eric's kernel. This environment variable is only required when building GEM drm.ko and i915.ko in the mesa/drm git project.

Some logs are just written to stderr or something like that. What I sometimes do if I don't find any debugging information in dmesg or /opt/gfx-test/var/log/Xorg.0.log is to log into my machine from remote (ssh) and spawn X from there. This way I see stderr or other messages on the remote machine even if visual image on the main machine is completely broken.

---

### Post by barbro on 2008-09-17
had to do a make clean in mesa also...
Thanks

---

### Post by Starks on 2008-09-17
any chance at having a few debs tossed in?

<__<

---

### Post by barbro on 2008-09-17
i'm up and running and I can confirm [Bug 17486 commet #10]("https://bugs.freedesktop.org/show_bug.cgi?id=17486#c10") if running uxa + dri2. 
The thing is if i'm running dri2 can't use the mouse to interact with my whole desktop only a small area. Or at least the screen doesn't update if i try to interact with the desktop outside the small area where desktop interaction works. 


Still uxa without dri2 and exa works...

---

### Post by 7oby on 2008-09-18
> **barbro said:**
> The thing is if i'm running dri2 can't use the mouse to interact with my whole desktop only a small area.
It's the same here.

I'm surprised how many obvious bugs I recently had to file and which had to be removed before any GEM based 2D driver would fly. Your chipset G33 with GMA 3100 graphics core is very different from the X3100 of the GM965 that I'm using. But it's again interesting to see that most of the bugs will also show up on your machine.

I started this post 4 weeks ago and for example for your chipset a patch just 2 days old was required to get 3D working:
[http://cgit.freedesktop.org/~anholt/linux-2.6/commit/?h=drm-gem-merge&id=c90fab4943289b51cfe28113db0f8e2908d965cd](http://cgit.freedesktop.org/~anholt/linux-2.6/commit/?h=drm-gem-merge&id=c90fab4943289b51cfe28113db0f8e2908d965cd)

Jesse just updated his blog on some issues:
[http://virtuousgeek.org/blog/index.php/jbarnes/2008/09/17/too_much_travel](http://virtuousgeek.org/blog/index.php/jbarnes/2008/09/17/too_much_travel)

> **barbro said:**
> Still uxa without dri2 and exa works...
Haven't tried UXA without DRI2 yet, will do that soon.

---

### Post by barbro on 2008-09-18
Yeah, lets hope the GTT patches solves our problems!

---

### Post by warlomak on 2008-10-29
The kernel 2.6.28rc2 already includes GEM patches, who tried to create deb's for libdrm ?

intel 2.5.0 drivers here:
[https://launchpad.net/~thjaeger/+archive](https://launchpad.net/~thjaeger/+archive)

need libdrm libdrm >=2.4.0 deb for ubuntu 8.10 x64

---

