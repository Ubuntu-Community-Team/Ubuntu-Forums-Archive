---
title: "Update Manager always asks for a Partial Update!"
date: 2009-10-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dadedo123 on 2009-10-20
Since I installed Alpha 6. Over  a month now. Should I install it?

---

### Post by philinux on 2009-10-20
Not for now.

```
sudo apt-get update && sudo apt-get upgrade
```

Post back what it wants to do.

---

### Post by Peter09 on 2009-10-20
I have found that it is asking for a partial update because it wants to remove rtkit - which is a package that needs to be removed. When it asks for a partial update select it and look at the details, at the very top of the list (you may need to go upwards) you will find the remove rtkit instruction. If thats the only removal you can go ahead.

---

### Post by Sand &amp; Mercury on 2009-10-20
> **Peter09 said:**
> I have found that it is asking for a partial update because it wants to remove rtkit - which is a package that needs to be removed. When it asks for a partial update select it and look at the details, at the very top of the list (you may need to go upwards) you will find the remove rtkit instruction. If thats the only removal you can go ahead.

Thanks for the info, I was in that exact situation till now.

---

### Post by dadedo123 on 2009-10-20
> **philinux said:**
> Not for now.

```
sudo apt-get update && sudo apt-get upgrade
```

Post back what it wants to do.

> hassan@HassanX2008:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for hassan: 
Get:1 [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic Release.gpg [189B]
Ign [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic/main Translation-en_US
Ign [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic/restricted Translation-en_US
Ign [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic/universe Translation-en_US
Ign [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic/multiverse Translation-en_US
Hit [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic-updates Release.gpg
Ign [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic-updates/main Translation-en_US
Ign [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic-updates/restricted Translation-en_US
Ign [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic-updates/universe Translation-en_US
Ign [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic-updates/multiverse Translation-en_US
Hit [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic-security Release.gpg
Ign [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic-security/main Translation-en_US
Ign [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic-security/restricted Translation-en_US
Ign [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic-security/universe Translation-en_US
Ign [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic-security/multiverse Translation-en_US
Hit [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic Release
Err [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic Release                                                                                   
  
Hit [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic-updates Release                                                                           
Hit [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic-security Release                                                                          
Hit [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic-updates/main Packages                                                                     
Hit [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic-updates/restricted Packages
Hit [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic-updates/main Sources
Hit [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic-updates/restricted Sources
Hit [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic-updates/universe Packages
Hit [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic-updates/universe Sources
Hit [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic-updates/multiverse Packages
Hit [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic-updates/multiverse Sources
Hit [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic-security/main Packages
Hit [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic-security/restricted Packages
Hit [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic-security/main Sources
Hit [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic-security/restricted Sources
Hit [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic-security/universe Packages
Hit [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic-security/universe Sources
Hit [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic-security/multiverse Packages
Hit [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic-security/multiverse Sources
Fetched 189B in 40s (5B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ftp.stw-bonn.de](http://ftp.stw-bonn.de) karmic Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://ftp.stw-bonn.de/ubuntu/dists/karmic/Release](http://ftp.stw-bonn.de/ubuntu/dists/karmic/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  evolution-plugins ibus libpulse-browse0 libpulse-mainloop-glib0 libpulse0 linux-generic linux-headers-generic
  linux-image-generic pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf
  pulseaudio-module-udev pulseaudio-module-x11 pulseaudio-utils python-ibus ubuntu-netbook-remix
0 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.
hassan@HassanX2008:~$ 


here

---

### Post by philinux on 2009-10-20
Ok have you read the sticky regarding partials. 

This is what I do either use synaptic and get it to mark all upgrade. Click apply and see what it wants to do. That way you can avoid an update removing have your system. Others use dist-upgrade to check. Other use aptitude safe-upgrade.

Have alook at the man pages for apt-get and aptitude.

---

### Post by Sand &amp; Mercury on 2009-10-20
I believe the proper procedure here would be to post what it wants to do upon entering

sudo apt-get dist-upgrade

not just apt-get upgrade. Doing that won't allow apt to remove or add any new packages, which is why it's holding stuff back. From the looks of it though, it's the exact same setup as what I had before, so you can probably go ahead with that partial upgrade. Just to be sure though, make sure it only wants to remove rtkit -- if there's anything else, best be safe and post it here for folks to check over.

---

### Post by dadedo123 on 2009-10-20
> **Sand & Mercury said:**
> I believe the proper procedure here would be to post what it wants to do upon entering

sudo apt-get dist-upgrade

not just apt-get upgrade. Doing that won't allow apt to remove or add any new packages, which is why it's holding stuff back. From the looks of it though, it's the exact same setup as what I had before, so you can probably go ahead with that partial upgrade. Just to be sure though, make sure it only wants to remove rtkit -- if there's anything else, best be safe and post it here for folks to check over.

rtkit and libgd2-noxpm are going to get removed! Safe to upgrade?

---

### Post by slakkie on 2009-10-20
> **Sand & Mercury said:**
> I believe the proper procedure here would be to post what it wants to do upon entering

sudo apt-get dist-upgrade

not just apt-get upgrade. Doing that won't allow apt to remove or add any new packages, which is why it's holding stuff back. From the looks of it though, it's the exact same setup as what I had before, so you can probably go ahead with that partial upgrade. Just to be sure though, make sure it only wants to remove rtkit -- if there's anything else, best be safe and post it here for folks to check over.

The problem with advising people to use apt-get dist-upgrade/aptitude full-upgrade is that you can hose your system. 
The apt-get/aptitude update commands are much saner and will not remove packages unless you actually tell them to.

So the correct procedure would then be:

```

apt-get upgrade 
# or aptitude safe-upgrade
apt-get -s dist-upgrade
# or aptitude -s full-upgrade

```

See what happens, if this change is acceptable, run the dist/full upgrade without the -s flag.

Just saying run dist-upgrade is helping people to break their system.

---

### Post by miegiel on 2009-10-20
> **dadedo123 said:**
> rtkit and libgd2-noxpm are going to get removed! Safe to upgrade?

rtkit : yes

libgd2-noxpm : don't think so

```
usre@machine:~$ sudo apt-get -s remove libgd2-noxpm 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-psyco libksane0 libpth20 groff libkipi6 qalc
  libboost-program-options1.38.0 libkexiv2-7 libcln5 libboost-thread1.38.0
  libakonadiprivate1 libtorrent-rasterbar5 libqalculate4 mplayer-skin-blue
  libwmf-bin tuxtype-data-nonfree netpbm python-uniconvertor kdepimlibs5
  libnetpbm10 libgpgme11 libboost-filesystem1.38.0 miro-data kdepimlibs-data
  libboost-system1.38.0 python-libtorrent libkdcraw7 libboost-python1.38.0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  dolphin gnuplot-nox gnuplot-x11 imagemagick inkscape kdebase-bin
  kdebase-runtime kdebase-runtime-bin-kde4 kfind khelpcenter4 kipi-plugins
  konqueror konqueror-nsplugins konquest libgd2-noxpm libgraphviz4
  libkdegames5 libkonq5 libkonqsidebarplugin4 libmagick++2 libmagickcore2
  libmagickwand2 libxine1 libxine1-misc-plugins libxine1-plugins miro
  obex-data-server perlmagick phonon-backend-xine qalculate-gtk
  thunar-thumbnailers
0 upgraded, 0 newly installed, 31 to remove and 0 not upgraded.
Remv dolphin [4:4.3.2-0ubuntu1]
Remv qalculate-gtk [0.9.6-3]
Remv gnuplot-x11 [4.2.5-2]
Remv gnuplot-nox [4.2.5-2]
Remv thunar-thumbnailers [0.4.1-2]
Remv imagemagick [7:6.5.1.0-1.1ubuntu3]
Remv inkscape [0.47~pre4-0ubuntu1]
Remv konqueror [4:4.3.2-0ubuntu1]
Remv kdebase-bin [4:4.3.2-0ubuntu1]
Remv libkonqsidebarplugin4 [4:4.3.2-0ubuntu1]
Remv kfind [4:4.3.2-0ubuntu1]
Remv libkonq5 [4:4.3.2-0ubuntu1]
Remv konquest [4:4.3.2-0ubuntu1]
Remv libkdegames5 [4:4.3.2-0ubuntu1]
Remv konqueror-nsplugins [4:4.3.2-0ubuntu1]
Remv kipi-plugins [0.7.0-1ubuntu2]
Remv khelpcenter4 [4:4.3.2-0ubuntu2]
Remv kdebase-runtime [4:4.3.2-0ubuntu2] [kdebase-runtime-bin-kde4 ]
Remv kdebase-runtime-bin-kde4 [4:4.3.2-0ubuntu2]
Remv perlmagick [7:6.5.1.0-1.1ubuntu3]
Remv obex-data-server [0.4.4-2build1]
Remv miro [2.5.2-1ubuntu1]
Remv phonon-backend-xine [4:4.3.1-4ubuntu1]
Remv libxine1 [1.1.16.3-0ubuntu4]
Remv libxine1-plugins [1.1.16.3-0ubuntu4]
Remv libxine1-misc-plugins [1.1.16.3-0ubuntu4]
Remv libmagick++2 [7:6.5.1.0-1.1ubuntu3]
Remv libmagickcore2 [7:6.5.1.0-1.1ubuntu3] [libmagickwand2 ]
Remv libmagickwand2 [7:6.5.1.0-1.1ubuntu3]
Remv libgraphviz4 [2.20.2-3ubuntu5]
Remv libgd2-noxpm [2.0.36~rc1~dfsg-3ubuntu1]
```

This is my version of *libgd2-noxpm*
```
user@machine:~$ sudo aptitude show libgd2-noxpm
Package: libgd2-noxpm
State: installed
Automatically installed: no
Version: 2.0.36~rc1~dfsg-3ubuntu1
Priority: extra
Section: libs
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 651k
Depends: libc6 (>= 2.4), libfreetype6 (>= 2.3.5), libjpeg62, libpng12-0 (>=
         1.2.13-4), zlib1g (>= 1:1.1.4)
Suggests: libgd-tools
Conflicts: libgd2, libgd2-xpm
Provides: libgd2
Description: GD Graphics Library version 2 (without XPM support)
 GD is a graphics library. It allows your code to quickly draw images complete
 with lines, arcs, text, multiple colours, cut and paste from other images,
 flood fills, and write out the result as a PNG file. This is particularly
 useful in World Wide Web applications, where PNG is one of the formats accepted
 for inline images by most browsers. 
 
 This is the runtime package of the library, built without XPM (X pixmap) or
 fontconfig support.
Homepage: http://www.libgd.org/
```

*sudo apt-get -s "whatever"* makes apt-get simulate whatever you do (so no changes are made).

---

### Post by dadedo123 on 2009-10-20
> **miegiel said:**
> rtkit : yes

libgd2-noxpm : don't think so

```
usre@machine:~$ sudo apt-get -s remove libgd2-noxpm 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-psyco libksane0 libpth20 groff libkipi6 qalc
  libboost-program-options1.38.0 libkexiv2-7 libcln5 libboost-thread1.38.0
  libakonadiprivate1 libtorrent-rasterbar5 libqalculate4 mplayer-skin-blue
  libwmf-bin tuxtype-data-nonfree netpbm python-uniconvertor kdepimlibs5
  libnetpbm10 libgpgme11 libboost-filesystem1.38.0 miro-data kdepimlibs-data
  libboost-system1.38.0 python-libtorrent libkdcraw7 libboost-python1.38.0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  dolphin gnuplot-nox gnuplot-x11 imagemagick inkscape kdebase-bin
  kdebase-runtime kdebase-runtime-bin-kde4 kfind khelpcenter4 kipi-plugins
  konqueror konqueror-nsplugins konquest libgd2-noxpm libgraphviz4
  libkdegames5 libkonq5 libkonqsidebarplugin4 libmagick++2 libmagickcore2
  libmagickwand2 libxine1 libxine1-misc-plugins libxine1-plugins miro
  obex-data-server perlmagick phonon-backend-xine qalculate-gtk
  thunar-thumbnailers
0 upgraded, 0 newly installed, 31 to remove and 0 not upgraded.
Remv dolphin [4:4.3.2-0ubuntu1]
Remv qalculate-gtk [0.9.6-3]
Remv gnuplot-x11 [4.2.5-2]
Remv gnuplot-nox [4.2.5-2]
Remv thunar-thumbnailers [0.4.1-2]
Remv imagemagick [7:6.5.1.0-1.1ubuntu3]
Remv inkscape [0.47~pre4-0ubuntu1]
Remv konqueror [4:4.3.2-0ubuntu1]
Remv kdebase-bin [4:4.3.2-0ubuntu1]
Remv libkonqsidebarplugin4 [4:4.3.2-0ubuntu1]
Remv kfind [4:4.3.2-0ubuntu1]
Remv libkonq5 [4:4.3.2-0ubuntu1]
Remv konquest [4:4.3.2-0ubuntu1]
Remv libkdegames5 [4:4.3.2-0ubuntu1]
Remv konqueror-nsplugins [4:4.3.2-0ubuntu1]
Remv kipi-plugins [0.7.0-1ubuntu2]
Remv khelpcenter4 [4:4.3.2-0ubuntu2]
Remv kdebase-runtime [4:4.3.2-0ubuntu2] [kdebase-runtime-bin-kde4 ]
Remv kdebase-runtime-bin-kde4 [4:4.3.2-0ubuntu2]
Remv perlmagick [7:6.5.1.0-1.1ubuntu3]
Remv obex-data-server [0.4.4-2build1]
Remv miro [2.5.2-1ubuntu1]
Remv phonon-backend-xine [4:4.3.1-4ubuntu1]
Remv libxine1 [1.1.16.3-0ubuntu4]
Remv libxine1-plugins [1.1.16.3-0ubuntu4]
Remv libxine1-misc-plugins [1.1.16.3-0ubuntu4]
Remv libmagick++2 [7:6.5.1.0-1.1ubuntu3]
Remv libmagickcore2 [7:6.5.1.0-1.1ubuntu3] [libmagickwand2 ]
Remv libmagickwand2 [7:6.5.1.0-1.1ubuntu3]
Remv libgraphviz4 [2.20.2-3ubuntu5]
Remv libgd2-noxpm [2.0.36~rc1~dfsg-3ubuntu1]
```

This is my version of *libgd2-noxpm*
```
user@machine:~$ sudo aptitude show libgd2-noxpm
Package: libgd2-noxpm
State: installed
Automatically installed: no
Version: 2.0.36~rc1~dfsg-3ubuntu1
Priority: extra
Section: libs
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 651k
Depends: libc6 (>= 2.4), libfreetype6 (>= 2.3.5), libjpeg62, libpng12-0 (>=
         1.2.13-4), zlib1g (>= 1:1.1.4)
Suggests: libgd-tools
Conflicts: libgd2, libgd2-xpm
Provides: libgd2
Description: GD Graphics Library version 2 (without XPM support)
 GD is a graphics library. It allows your code to quickly draw images complete
 with lines, arcs, text, multiple colours, cut and paste from other images,
 flood fills, and write out the result as a PNG file. This is particularly
 useful in World Wide Web applications, where PNG is one of the formats accepted
 for inline images by most browsers. 
 
 This is the runtime package of the library, built without XPM (X pixmap) or
 fontconfig support.
Homepage: http://www.libgd.org/
```
How can I do a Partial Upgrade without removing "libgd2-noxpm"?

---

### Post by qamelian on 2009-10-20
> **dadedo123 said:**
> How can I do a Partial Upgrade without removing "libgd2-noxpm"?
It is safe to remove both. The libgd2-noxpm package will be replaced by libgd2-xpm.

---

### Post by dadedo123 on 2009-10-20
wohoo thank all! The Partial Update was annoying me. Now it will be gone after the update! yayy!

---

### Post by miegiel on 2009-10-20
> **dadedo123 said:**
> How can I do a Partial Upgrade without removing "libgd2-noxpm"?

I'm not really sure, but you can remove *rtkit*. Try
```
sudo apt-get -s remove rtkit
```
first. If the output doesn't scare you to death, remove it (same command without the -s switch)
And then do the apt-get update and upgrade routine.

When you got that behind you run
```
sudo aptitude show libgd2-noxpm
```
and compare your version of *libgd2-noxpm* with mine.

> **qamelian said:**
> It is safe to remove both. The libgd2-noxpm package will be replaced by libgd2-xpm.

oh ... ok :D

---

### Post by slakkie on 2009-10-20
migiel, apt-cache policy $package is a better way to figure out which version you have and which version will be installed.

---

### Post by miegiel on 2009-10-20
> **slakkie said:**
> migiel, apt-cache policy $package is a better way to figure out which version you have and which version will be installed.

Thanks, still so much to learn :)

---

