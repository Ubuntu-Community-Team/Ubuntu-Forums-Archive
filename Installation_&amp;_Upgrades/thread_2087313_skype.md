---
title: "skype?"
date: 2012-11-23
forum: Installation &amp; Upgrades
---

### Post by il lupo on 2012-11-23
Hello, All--

I'm curious.  Does anybody know when Skype was added to the repositories?  Yesterday, my update manager informed me that Skype could be upgraded, though it was not marked.  That was strange, though I was not complaining, and I did what I've always done:  Go to Skype's website and download the newest .deb file.  After installing it, it worked fine.  I spent about an hour videochatting with my parents for Thanksgiving.

Today, my update manager informed me that Skype was available for upgrade, and it was even marked for such.  It is my habit to use the gui to read about the programs and the changes while using the terminal to do the actual work.  Aptitude showed me that a shocking 91 programs were to be removed to update Skype:

 bluez-alsa:i386{u} glib-networking:i386{u} 
  gstreamer0.10-plugins-good:i386{u} gstreamer0.10-x:i386{u} 
  gtk2-engines:i386{u} gtk2-engines-murrine:i386{u} 
  gtk2-engines-oxygen:i386{u} gtk2-engines-pixbuf:i386{u} ia32-libs{u} 
  ia32-libs-multiarch:i386{u} ibus-gtk:i386{u} lib32asound2{u} 
  libaa1:i386{u} libaio1:i386{u} libao4:i386{u} libatk1.0-0:i386{u} 
  libaudiofile1:i386{u} libavc1394-0:i386{u} libcaca0:i386{u} 
  libcairo-gobject2:i386{u} libcairo2:i386{u} 
  libcanberra-gtk-module:i386{u} libcanberra-gtk0:i386{u} 
  libcanberra0:i386{u} libcap2:i386{u} libcroco3:i386{u} 
  libcupsimage2:i386{u} libcurl3:i386{u} libdbus-glib-1-2:i386{u} 
  libdv4:i386{u} libesd0:i386{u} libgail-common:i386{u} libgail18:i386{u} 
  libgconf-2-4:i386{u} libgdbm3:i386{u} libgdk-pixbuf2.0-0:i386{u} 
  libgettextpo0:i386{u} libgnome-keyring0:i386{u} libgomp1:i386{u} 
  libgtk2.0-0:i386{u} libgudev-1.0-0:i386{u} libibus-1.0-0:i386{u} 
  libidn11:i386{u} libiec61883-0:i386{u} libjasper1:i386{u} libmad0:i386{u} 
  libmikmod2:i386{u} libnspr4:i386{u} libnss3:i386{u} libodbc1:i386{u} 
  libpango1.0-0:i386{u} libpixman-1-0:i386{u} libproxy1:i386{u} 
  libpulse-mainloop-glib0:i386{u} libpulsedsp:i386{u} 
  libqt4-designer:i386{u} libqt4-opengl:i386{u} libqt4-qt3support:i386{u} 
  libqt4-scripttools:i386{u} libqt4-svg:i386{u} libqt4-test:i386{u} 
  libraw1394-11:i386{u} librsvg2-2:i386{u} librsvg2-common:i386{u} 
  librtmp0:i386{u} libsdl-image1.2:i386{u} libsdl-mixer1.2:i386{u} 
  libsdl-net1.2:i386{u} libsdl-ttf2.0-0:i386{u} libsdl1.2debian:i386{u} 
  libshout3:i386{u} libsoup-gnome2.4-1:i386{u} libsoup2.4-1:i386{u} 
  libspeex1:i386{u} libssl0.9.8:i386{u} libstdc++5:i386{u} 
  libtag1-vanilla:i386{u} libtag1c2a:i386{u} libtdb1:i386{u} 
  libunistring0:i386{u} libvorbisfile3:i386{u} libwavpack1:i386{u} 
  libxaw7:i386{u} libxcb-render0:i386{u} libxcb-shm0:i386{u} 
  libxft2:i386{u} libxmu6:i386{u} libxp6:i386{u} libxtst6:i386{u} 
  odbcinst1debian2:i386{u} xaw3dg:i386{u}

Does this look safe to anyone?  Why would i want to do this?  i'm actually running ubuntu studio, and anything that looks as though it's messing with streamers and sound libraries strikes me as suspicious.  And, as i mentioned, Skype is working just fine.

Any advice and information is well appreciated.

il lupo

---

### Post by zombifier25 on 2012-11-23
The latest Skype is multiarch, which means you no longer need to use 32bit libraries on 64bit systems in order to make Skype run. If you are indeed using 64bit Ubuntu, then those packages are safe to remove.

---

### Post by il lupo on 2012-11-23
Oh, my fault.  I am running 64bit.  I ran the update and the test call worked perfectly.  Skype seems to have been in the repositories for a while.  I've had the specific software source activated, but this is the first time I've been notified of an update.

Thanks for the help, zombifier25!

---

