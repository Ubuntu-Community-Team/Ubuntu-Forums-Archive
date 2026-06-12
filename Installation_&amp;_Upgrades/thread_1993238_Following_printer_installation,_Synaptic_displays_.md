---
title: "Following printer installation, Synaptic displays error message, and then crashes."
date: 2012-06-01
forum: Installation &amp; Upgrades
---

### Post by rewyllys on 2012-06-01
After reinstalling my Brother MFC-8820D multifunction machine (which now is printing correctly), my attempts to use the Synaptic Package Manager yield the following error message:

"E: The package mfc8820dlpr:i386 needs to be reinstalled, but I can't find an archive for it." 

When I close the popup displaying this error message, Synaptic closes.

I need Synaptic. What can I do to fix this problem?

Edit: I've discovered that this error also prevents the Software Center and the Update Manager from working.

Help, please.

---

### Post by rewyllys on 2012-06-01
This is a follow-up to my first post in this thread.

I tried re-installing Synaptic, which resulted in the following lines in a Terminal:
```
ron@ron-desktop-linux:~$ sudo aptitude reinstall synaptic
The following packages will be REINSTALLED:
  synaptic 
The following packages will be REMOVED:
  bluez-alsa:i386{u} glib-networking:i386{u} 
  gstreamer0.10-plugins-good:i386{u} gstreamer0.10-x:i386{u} 
  gtk2-engines:i386{u} gtk2-engines-murrine:i386{u} 
  gtk2-engines-oxygen:i386{u} gtk2-engines-pixbuf:i386{u} ia32-libs{u} 
  ia32-libs-multiarch:i386{u} ibus-gtk:i386{u} libaa1:i386{u} 
  libaio1:i386{u} libao-common{u} libao4:i386{u} libatk1.0-0:i386{u} 
  libaudio2:i386{u} libaudiofile1:i386{u} libavc1394-0:i386{u} 
  libcaca0:i386{u} libcairo-gobject2:i386{u} libcairo2:i386{u} 
  libcanberra-gtk-module:i386{u} libcanberra-gtk0:i386{u} 
  libcanberra0:i386{u} libcap2:i386{u} libcroco3:i386{u} 
  libcupsimage2:i386{u} libcurl3:i386{u} libdatrie1:i386{u} 
  libdbus-glib-1-2:i386{u} libdv4:i386{u} libesd0:i386{u} 
  libgail-common:i386{u} libgail18:i386{u} libgconf-2-4:i386{u} 
  libgdbm3:i386{u} libgdk-pixbuf2.0-0:i386{u} libgettextpo0:i386{u} 
  libgnome-keyring0:i386{u} libgomp1:i386{u} libgtk2.0-0:i386{u} 
  libgudev-1.0-0:i386{u} libibus-1.0-0:i386{u} libidn11:i386{u} 
  libiec61883-0:i386{u} libjasper1:i386{u} libmad0:i386{u} 
  libmikmod2:i386{u} libmng1:i386{u} libmysqlclient18:i386{u} 
  libnspr4:i386{u} libnss3:i386{u} libodbc1:i386{u} libpango1.0-0:i386{u} 
  libpixman-1-0:i386{u} libproxy1:i386{u} libpulse-mainloop-glib0:i386{u} 
  libpulsedsp:i386{u} libqt4-dbus:i386{u} libqt4-declarative:i386{u} 
  libqt4-designer:i386{u} libqt4-network:i386{u} libqt4-opengl:i386{u} 
  libqt4-qt3support:i386{u} libqt4-script:i386{u} 
  libqt4-scripttools:i386{u} libqt4-sql:i386{u} libqt4-sql-mysql:i386{u} 
  libqt4-svg:i386{u} libqt4-test:i386{u} libqt4-xml:i386{u} 
  libqt4-xmlpatterns:i386{u} libqtcore4:i386{u} libqtgui4:i386{u} 
  libqtwebkit4:i386{u} libraw1394-11:i386{u} librsvg2-2:i386{u} 
  librsvg2-common:i386{u} librtmp0:i386{u} libsdl-image1.2:i386{u} 
  libsdl-mixer1.2:i386{u} libsdl-net1.2:i386{u} libsdl-ttf2.0-0{u} 
  libsdl-ttf2.0-0:i386{u} libsdl1.2debian:i386{u} libshout3:i386{u} 
  libsoup-gnome2.4-1:i386{u} libsoup2.4-1:i386{u} libspeex1:i386{u} 
  libssl0.9.8:i386{u} libstdc++5:i386{u} libtag1-vanilla:i386{u} 
  libtag1c2a:i386{u} libtdb1:i386{u} libthai0:i386{u} libunistring0:i386{u} 
  libvorbisfile3:i386{u} libwavpack1:i386{u} libwxbase2.8-0{u} 
  libwxgtk2.8-0{u} libxaw7:i386{u} libxcb-render0:i386{u} 
  libxcb-shm0:i386{u} libxft2:i386{u} libxmu6:i386{u} libxp6:i386{u} 
  libxss1:i386{u} libxtst6:i386{u} libxv1:i386{u} mysql-common{u} 
  odbcinst1debian2:i386{u} xaw3dg:i386{u} 
0 packages upgraded, 0 newly installed, 1 reinstalled, 113 to remove and 55 not upgraded.
Need to get 0 B of archives. After unpacking 143 MB will be freed.
Do you want to continue? [Y/n/?] y
E: I wasn't able to locate a file for the mfc8820dlpr package. This might mean you need to manually fix this package.
E: I wasn't able to locate a file for the mfc8820dlpr package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download
ron@ron-desktop-linux:~$ locate mfc8820dlpr
/home/ron/BrotherScannerAndPrinter/mfc8820dlpr-1.1.2-1.i386.deb

```

I hope this gives someone an idea of what I need to do.  

How can I "manually fix" the mfc8820dlpr package?

Thanks in advance for any help.

---

### Post by rewyllys on 2012-06-01
Continuing the story of my attempts to solve this problem: 

I decided that since I have on my system a copy of the file that I **think** Synaptic is complaining about, I could try installing it directly.  Here is the Terminal output that resulted:
```
ron@ron-desktop-linux:~/BrotherScannerAndPrinter$ ls
BR8820_2.PPD
Brother Solutions Center   Brother Driver for Linux Distributions_files
Brother Solutions Center   Brother Driver for Linux Distributions.html
brscan-0.2.4-0.amd64.deb
cupswrapperMFC8820D-1.0.2-1.i386.deb
linux-brprinter-installer-1.0.3-1.gz
mfc8820dlpr-1.1.2-1.i386.deb
ron@ron-desktop-linux:~/BrotherScannerAndPrinter$ sudo apt-get install mfc8820dlpr-1.1.2-1.i386.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package mfc8820dlpr:i386 needs to be reinstalled, but I can't find an archive for it.
ron@ron-desktop-linux:~/BrotherScannerAndPrinter$
```

IOW, my attempt to re-install the actual package failed.

I continue to need help.  Please.

---

### Post by rewyllys on 2012-06-03
Bump.  

Help still needed, please.

---

