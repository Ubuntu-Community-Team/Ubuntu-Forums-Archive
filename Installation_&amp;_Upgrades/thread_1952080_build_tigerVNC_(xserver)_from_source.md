---
title: "build tigerVNC (xserver) from source"
date: 2012-04-03
forum: Installation &amp; Upgrades
---

### Post by pablop on 2012-04-03
I'm trying to build tigerVNC from source under ubuntu 11.10 32bit.

I'm following instructions from
[http://tigervnc.svn.sourceforge.net/viewvc/tigervnc/trunk/BUILDING.txt?revision=4879&view=markup](http://tigervnc.svn.sourceforge.net/viewvc/tigervnc/trunk/BUILDING.txt?revision=4879&view=markup)

In the configure step I'm getting a warning:
configure: WARNING: unrecognized options: --with-fontdir, --with-dri-driver-path

In the make step I'm getting an error:
In file included from glxdriswrast.c:39:0:
/usr/include/GL/internal/dri_interface.h:51:17: fatal error: drm.h: No such file or directory

Was there a change in xserver that replaced --with-fountdir and --with-dri-driver-path?

How can I fix the warning and the error?



This is what I'm trying to do following BUILDING.txt:

sudo apt-get install cmake

# download tigervnc source to /home/tigervnc-1.2.0
# download xserver-xorg-dev source to /home/xorg-server-1.10.4
apt-get source xserver-xorg-dev
mkdir build
cd build

mkdir unix
cp -R ../tigervnc-1.2.0/unix/xserver unix/

cp -R ../xorg-server-1.10.4/* unix/xserver/

cd unix/xserver
patch -p1 < ../../../tigervnc-1.2.0/unix/xserver110.patch
sudo apt-get install xutils-dev libtool
autoreconf -fiv

sudo apt-get install libssl-dev libgl1-mesa-dev x11proto-gl-dev x11proto-record-dev x11proto-resource-dev x11proto-scrnsaver-dev x11proto-bigreqs-dev x11proto-xcmisc-dev libxfont-dev x11proto-video-dev libxkbfile-dev

./configure --with-pic --without-dtrace --disable-static --disable-dri \
      --disable-xinerama --disable-xvfb --disable-xnest --disable-xorg \
      --disable-dmx --disable-xwin --disable-xephyr --disable-kdrive \
      --disable-config-dbus --disable-config-hal --disable-config-udev \
      --disable-dri2 --enable-install-libxf86config --enable-glx \
      --with-default-font-path="catalogue:/etc/X11/fontpath.d,built-ins" \
      --with-fontdir=/usr/share/X11/fonts \
      --with-xkb-path=/usr/share/X11/xkb \
      --with-xkb-output=/var/lib/xkb \
      --with-xkb-bin-directory=/usr/bin \
      --with-serverconfig-path=/usr/lib/xorg \
      --with-dri-driver-path=/usr/lib/dri

> configure: WARNING: unrecognized options: --with-fontdir, --with-dri-driver-path

make TIGERVNC_SRCDIR=../../../tigervnc-1.2.0

> In file included from glxdriswrast.c:39:0:
> /usr/include/GL/internal/dri_interface.h:51:17: fatal error: drm.h: No such file or directory

Thanks

---

### Post by Eoin McMahon on 2012-05-20
Hello, Pablop. 

I, too, was having trouble getting this source to build and I appreciate you giving all the apt-get installs that are necessary. I have now finally built this, and the best answer I can give is to tell you what mistakes I made along the way.

First, I missed the instruction in the BUILDING.txt file: 
> (this procedure assumes that the viewer
has already been built, per above.)You will probably need to 
```
sudo apt-get install cmake
```first, then follow the instructions:
```
cd {build_directory}
  cmake -G "Unix Makefiles" [additional CMake flags] {source_directory}
  make
```(I didn't put in any additional CMake flags). This is necessary because it creates Makefiles you will later need. I carried on to build the server side in the same build directory.

I'm not sure whether this made a difference or not, but I built the source in my xorg-xserver directory in the usual way before doing the  copy to my vncserver build directory:
```

cd {xorg-xserver-1.10.4 source directory}
./configure
make

```I then followed the instructions:
> > cd {build_directory}


  > cp -R {source_directory}/unix/xserver unix/

  > cp -R {xorg_source}/* unix/xserver/
    (NOTE: {xorg_source} is the directory containing the Xorg source for the
    machine on which you are building TigerVNC.  The most recent versions of
    Red Hat/CentOS/Fedora, for instance, provide an RPM called
    "xorg-x11-server-source", which installs the Xorg source under
    /usr/share/xorg-x11-server-source.)

  > cd unix/xserver/
  > patch -p1 < {source_directory}/unix/xserver{version}.patch
    (where {version} matches the X server version you are building, such as
    "17" for version 1.7.x.)It is not necessary to make a unix directory if you have just cmake-d the viewer side.

Now I hit a problem. The autoreconf line prints a bunch of warning messages which, when I looked into them, seemed to indicate that there was something wrong with the format of the configure.ac file that the whole building system is based on. These can be very tricky and are very difficult to write so that they run properly on many different systems. On ubuntu, this one has a "mismatched quote" problem that causes autoreconf to miss out about 40 lines around lines 1180-1220. To try to fix it, I used my Eclipse IDE with a plugin from Incubation called Autotools Support, which interprets the difficult syntax of a configure.ac file. I edited it until all the marked errors and warnings disappeared. 

I've included a patch file that does this edit. Copy it to some convenient location.

If you patch at this point (when you are in the unix/xserver directory) using:
```
 patch --verbose -p0 < {location of  fix-configure-ac-patch.txt }

```then it should report each edit it does. 

The parameters that configure warned you about can, I think, be safely dropped. They are certainly not read in by the configure program. 

The parameter you are told to give to make (TIGERVNC_SRCDIR) is only mentioned in one set of Makefiles: unix/xserver/hw/vnc/Makefile.am , where it is *overwritten* in line 1. In this context, ${top_srcdir} is the location where you run configure from, so it's two directories up from this file at unix/xserver/ . What I did was to edit the first line of this file, to point at my {source directory} from my {build directory}/unix/xserver. 
As written, this line points to the build directory itself, so you need to navigate from there to {source directory} and add that to the end of line 1.
In my case, my {build directory} is at {source directory}/build/attemptNN/ (where NN is large!) so I ended up with:
```
TIGERVNC_SRCDIR=${top_srcdir}/../../../../
```[I should say, use gedit to edit the file, and save the new version back to your {build directory}/unix/xserver/hw/vnc/Makefile.am ]

One final kludge to solve the actual error reported (it's just the first thing to go wrong, I got rid of a few other problems you should never have to see): 
Use a file browser to check if you have a directory at /usr/include/drm. If you do, it should contain a file called drm.h. I confess that I flailed around a bit, and don't know whether this file is there on a clean ubuntu or if I just accumulated it over the years. If you can't find it, it's in package libdrm-dev, so do:
```
sudo apt-get install libdrm-dev
```I still couldn't get the build to see it, so I'm afraid I resorted to:
```
sudo cp /usr/include/drm/drm.h /usr/include/drm.h
```which is naughty, but it works.

 Then you can go ahead with:
```
autoreconf -fiv

 ./configure --with-pic --without-dtrace --disable-static \
--disable-dri --disable-xinerama --disable-xvfb --disable-xnest \
--disable-xorg --disable-dmx --disable-xwin --disable-xephyr \
 --disable-kdrive --disable-config-dbus --disable-config-hal \
--disable-config-udev --disable-dri2 --enable-install-libxf86config \
--enable-glx --with-default-font-path="catalogue:/etc/X11/fontpath.d,built-ins"  \
--with-xkb-path=/usr/share/X11/xkb --with-xkb-output=/var/lib/xkb \
--with-xkb-bin-directory=/usr/bin --with-serverconfig-path=/usr/lib/xorg 

make

```...and that should do the trick! If only I could remember why I needed to build this thing from source in the first place.

Please let me know if you have any problems. Good luck!

---

