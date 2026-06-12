---
title: "Where are WORKING instructions for installing Google Earth on 64-bit Ubuntu 13.10?"
date: 2013-12-28
forum: Installation &amp; Upgrades
---

### Post by Jim_Granite on 2013-12-28
Googling, I see everyone has a problem installing Google Earth into 64-bit Ubuntu 13.10 due either to Canonical's deprecation of the ia32-libs (which apparently allows 34-bit programs to run in 64 bit) or to Google's bad packaging.
Either way, there's nothing I am going to be able to do about that - but I *should* be able to install Google Earth. Right?

In fact, I had it working, in the past:
- [Why doesn't Google Earth install properly on Ubuntu 13.10 using the documented me 		]("http://ubuntuforums.org/showthread.php?t=2183733")
But, now it stopped working.

Googling, I easily found a half dozen so-called additional 'solutions', none of which worked for me.
I'd be perfectly happy to try a working solution - **so - I only ask WHERE I can find that working solution?**

Note: These all failed miserably and if you need me to document why, I will be glad to:
[LIST]
[*][http://ubuntuforums.org/showthread.php?t=2162443&p=12819438#post12819438](http://ubuntuforums.org/showthread.php?t=2162443&p=12819438#post12819438) 
[*][http://linuxg.net/quicktip-how-to-properly-install-google-earth-6-on-ubuntu-13-10-saucy-salamander/](http://linuxg.net/quicktip-how-to-properly-install-google-earth-6-on-ubuntu-13-10-saucy-salamander/) 
[*][http://askubuntu.com/questions/366438/how-to-install-google-earth-64bit-in-ubuntu-13-10-ia32-libs-dependency-error](http://askubuntu.com/questions/366438/how-to-install-google-earth-64bit-in-ubuntu-13-10-ia32-libs-dependency-error) 
[*][http://askubuntu.com/questions/361084/how-to-install-ia32-libs](http://askubuntu.com/questions/361084/how-to-install-ia32-libs) 
[/LIST]
etc.

---

### Post by Jim_Granite on 2013-12-28
Here's a documention of what happens with the first of those references:
[http://ubuntuforums.org/showthread.php?t=2162443&p=12819438#post12819438](http://ubuntuforums.org/showthread.php?t=2162443&p=12819438#post12819438)

```

$ mkdir /tmp/earth
$ cd !$

$ script ./earth.log
=> Script started, file is ./googleearth.log
=> Can't connect to IBus.

$ sudo apt-get install libc6:i386 lsb-core
=> Reading package lists... Done
=>Building dependency tree       
=>Reading state information... Done
=>lsb-core is already the newest version.
=>libc6:i386 is already the newest version.
=>The following packages were automatically installed and are no longer required:
=>  apcalc-common linux-image-generic
=>Use 'apt-get autoremove' to remove them.
=>0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.

$ firefox [http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html)
 32 bit .deb (For                 Debian/Ubuntu)
                 64 bit .deb (For                 Debian/Ubuntu)  <=== select this one
                 32 bit .rpm (For                 Fedora/openSUSE)
                 64 bit .rpm (For                 Fedora/openSUSE)

Save as: /tmp/earth/google-earth-stable_current_amd64.deb

$ ls -ltr
=> -rw------- 1 46544886 Dec 28 18:09 google-earth-stable_current_amd64.deb

Navigate, in Nautilus, to /tmp/earth and right click on the deb file and select:
**Extract Here**

This creates a directory called:
/tmp/earth/google-earth-stable_current_amd64

$ ls -l google-earth-stable_current_amd64/DEBIAN/control 
=> -rw-r--r-- 1 443 Oct  7 12:40 google-earth-stable_current_amd64/DEBIAN/control

$ grep ^Depends google-earth-stable_current_amd64/DEBIAN/control 
=> Depends: lsb-core (>= 3.2), ia32-libs

$ vi !$
=> delete that one line which starts with "Depends" (leave all other lines intact).

$ rm google-earth-stable_current_amd64.deb
$ dpkg -b ./google-earth-stable_current_amd64
=> dpkg-deb: building package `google-earth-stable' in `./google-earth-stable_current_amd64.deb'.
$ ls -l ./google-earth-stable_current_amd64.deb
=> -rw-r--r-- 1 70155626 Dec 28 18:19 google-earth-stable_current_amd64.deb
$ sudo dpkg -i ./google-earth-stable_current_amd64.deb
=> (Reading database ... 257682 files and directories currently installed.)
=> Preparing to replace google-earth-stable 7.1.2.2041-r0 (using .../google-earth-stable_current_amd64.deb) ...
=> Unpacking replacement google-earth-stable ...
=> Setting up google-earth-stable (7.1.2.2041-r0) ...
=>Processing triggers for menu ...
=>Processing triggers for desktop-file-utils ...
=>Processing triggers for gnome-menus ...
=>Processing triggers for bamfdaemon ...
=>Rebuilding /usr/share/applications/bamf-2.index...
=>Processing triggers for mime-support ...
=>Processing triggers for man-db ...

$ $ ls -l `which google-earth`
=> lrwxrwxrwx 1 foo foo 34 Oct  7 12:40 /usr/bin/google-earth -> /opt/google/earth/free/googleearth

$ google-earth
=> [1228/182513:ERROR:net_util.cc(2195)] Not implemented reached in bool net::HaveOnlyLoopbackAddresses()
=>[1228/182513:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=>[1228/182513:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=>[1228/182513:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=>[1228/182513:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=>[1228/182514:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=>[1228/182514:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=>[1228/182514:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=>[1228/182514:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=>[1228/182514:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=>[1228/182514:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=>[1228/182514:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=>[1228/182514:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=>[1228/182514:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=>[1228/182514:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=>[1228/182514:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=>[1228/182514:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=>[1228/182514:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=>[1228/182514:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=>[1228/182514:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=>[1228/182514:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=>[1228/182514:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=>[1228/182514:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=>[1228/182514:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=>[1228/182514:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=>[1228/182514:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=>[1228/182514:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=>[1228/182514:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=>[1228/182514:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=>
=> Another crash happened while handling crash!

$ exit
=> exit
=> Script done, file is ./earth.log

```

---

### Post by Jim_Granite on 2013-12-28
Here's what happens with the second of those references:
[http://linuxg.net/quicktip-how-to-properly-install-google-earth-6-on-ubuntu-13-10-saucy-salamander/](http://linuxg.net/quicktip-how-to-properly-install-google-earth-6-on-ubuntu-13-10-saucy-salamander/)

```

$ mkdir /tmp/google
$ cd !$
$ wget https://dl.dropboxusercontent.com/u/209784349/mix/googleearth-package_1.1.0_all.deb
=> --2013-12-28 18:32:54--  https://dl.dropboxusercontent.com/u/209784349/mix/googleearth-package_1.1.0_all.deb
=>Resolving dl.dropboxusercontent.com (dl.dropboxusercontent.com)... 54.225.137.118
=>Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|54.225.137.118|:443... connected.
=>HTTP request sent, awaiting response... 200 OK
=>Length: 11956 (12K) [application/x-debian-package]
=>Saving to: &#8216;googleearth-package_1.1.0_all.deb&#8217;
=>
=>100%[===========================================================>] 11,956      --.-K/s   in 0s      
=>
=>2013-12-28 18:32:54 (179 MB/s) - &#8216;googleearth-package_1.1.0_all.deb&#8217; saved [11956/11956]

$ ls -l
=> -rw-r--r-- 1 11956 Dec 28 18:32 googleearth-package_1.1.0_all.deb

$ sudo dpkg -i googleearth-package_1.1.0_all.deb
=> (Reading database ... 257682 files and directories currently installed.)
=>Preparing to replace googleearth-package 1.1.0 (using googleearth-package_1.1.0_all.deb) ...
=>Unpacking replacement googleearth-package ...
=>Setting up googleearth-package (1.1.0) ...
=>Processing triggers for man-db ...

$ sudo apt-get install -f
=> Reading package lists... Done
=>Building dependency tree       
=>Reading state information... Done
=>The following packages were automatically installed and are no longer required:
=>  apcalc-common linux-image-generic
=>Use 'apt-get autoremove' to remove them.
=>0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.

$ make-googleearth-package
=> cat: /etc/mailname: No such file or directory
=> --2013-12-28 18:36:37--  http://dl.google.com/earth/client/current/GoogleEarthLinux.bin
=> Resolving dl.google.com (dl.google.com)... 74.125.239.135, 74.125.239.129, 74.125.239.137, ...
=> Connecting to dl.google.com (dl.google.com)|74.125.239.135|:80... connected.
=> HTTP request sent, awaiting response... 200 OK
=> Length: 33688483 (32M) [application/octet-stream]
=> Saving to: &#8216;GoogleEarthLinux.bin&#8217;
=> 
=> 100%[===========================================================>] 33,688,483  1.47MB/s   in 19s    
=> 
=> 2013-12-28 18:36:57 (1.69 MB/s) - &#8216;GoogleEarthLinux.bin&#8217; saved [33688483/33688483]
=> 
=> Google Earth for GNU/Linux 6.0.3.2197
=> Supported Google Earth version: 6.0.3.2197
=> ./
=> ./googleearth.xpm
=> ./desktop_icons/
=> ./desktop_icons/pro/
=> ./desktop_icons/pro/product_logo_128.png
=> ./desktop_icons/pro/product_logo_22.png
=> ./desktop_icons/pro/product_logo_64.png
=> ./desktop_icons/pro/product_logo_16.png
=> ./desktop_icons/pro/product_logo_256.png
=> ./desktop_icons/pro/product_logo_32.xpm
=> ./desktop_icons/pro/product_logo_24.png
=> ./desktop_icons/pro/product_logo_48.png
=> ./desktop_icons/pro/product_logo_32.png
=> ./desktop_icons/ec/
=> ./desktop_icons/ec/product_logo_128.png
=> ./desktop_icons/ec/product_logo_22.png
=> ./desktop_icons/ec/product_logo_64.png
=> ./desktop_icons/ec/product_logo_16.png
=> ./desktop_icons/ec/product_logo_256.png
=> ./desktop_icons/ec/product_logo_32.xpm
=> ./desktop_icons/ec/product_logo_24.png
=> ./desktop_icons/ec/product_logo_48.png
=> ./desktop_icons/ec/product_logo_32.png
=> ./desktop_icons/consumer/
=> ./desktop_icons/consumer/product_logo_128.png
=> ./desktop_icons/consumer/product_logo_22.png
=> ./desktop_icons/consumer/product_logo_64.png
=> ./desktop_icons/consumer/product_logo_16.png
=> ./desktop_icons/consumer/product_logo_256.png
=> ./desktop_icons/consumer/product_logo_32.xpm
=> ./desktop_icons/consumer/product_logo_24.png
=> ./desktop_icons/consumer/product_logo_48.png
=> ./desktop_icons/consumer/product_logo_32.png
=> ./setup.sh
=> ./googleearth-linux-x86.tar
=> ./setup.data/
=> ./setup.data/locale/
=> ./setup.data/locale/es/
=> ./setup.data/locale/es/LC_MESSAGES/
=> ./setup.data/locale/es/LC_MESSAGES/setup.mo
=> ./setup.data/locale/es/LC_MESSAGES/loki-uninstall.mo
=> ./setup.data/locale/fr/
=> ./setup.data/locale/fr/LC_MESSAGES/
=> ./setup.data/locale/fr/LC_MESSAGES/setup.mo
=> ./setup.data/locale/fr/LC_MESSAGES/loki-uninstall.mo
=> ./setup.data/locale/nl/
=> ./setup.data/locale/nl/LC_MESSAGES/
=> ./setup.data/locale/nl/LC_MESSAGES/setup.mo
=> ./setup.data/locale/nl/LC_MESSAGES/loki-uninstall.mo
=> ./setup.data/locale/sv/
=> ./setup.data/locale/sv/LC_MESSAGES/
=> ./setup.data/locale/sv/LC_MESSAGES/setup.mo
=> ./setup.data/locale/sv/LC_MESSAGES/loki-uninstall.mo
=> ./setup.data/locale/ru/
=> ./setup.data/locale/ru/LC_MESSAGES/
=> ./setup.data/locale/ru/LC_MESSAGES/setup.mo
=> ./setup.data/locale/ru/LC_MESSAGES/loki-uninstall.mo
=> ./setup.data/locale/it/
=> ./setup.data/locale/it/LC_MESSAGES/
=> ./setup.data/locale/it/LC_MESSAGES/setup.mo
=> ./setup.data/locale/it/LC_MESSAGES/loki-uninstall.mo
=> ./setup.data/locale/de/
=> ./setup.data/locale/de/LC_MESSAGES/
=> ./setup.data/locale/de/LC_MESSAGES/setup.mo
=> ./setup.data/locale/de/LC_MESSAGES/loki-uninstall.mo
=> ./setup.data/setup.xml
=> ./setup.data/setup.glade
=> ./setup.data/splash.xpm
=> ./setup.data/setup.gtk2.glade
=> ./setup.data/config.sh
=> ./setup.data/bin/
=> ./setup.data/bin/OpenBSD
=> ./setup.data/bin/NetBSD
=> ./setup.data/bin/Linux/
=> ./setup.data/bin/Linux/x86_64
=> ./setup.data/bin/Linux/x86/
=> ./setup.data/bin/Linux/x86/setup.gtk2
=> ./setup.data/bin/Linux/x86/uninstall
=> ./setup.data/bin/Linux/x86/setup.gtk
=> ./setup.data/bin/Linux/amd64
=> ./setup.data/bin/FreeBSD
=> ./README.linux
=> ./googleearth-icon.png
=> ./linux/
=> ./linux/xdg/
=> ./linux/xdg/xdg-desktop-menu
=> ./linux/xdg/xdg-desktop-icon
=> ./linux/xdg/xdg-mime
=> ./googleearth-data.tar
=> ./postinstall.sh
=> ./bin/
=> ./bin/googleearth
=> ./preuninstall.sh
=> Package: googleearth
=> Version: 6.0.3.2197+1.1.0-1
=> Section: non-free/science
=> Priority: optional
=> Maintainer:  <foo@notebook>
=> Architecture: amd64
=> Depends: fonts-liberation, libfreeimage3, lsb-core, libqtcore4, libgl1-mesa-glx, libglu1-mesa , libcurl3:i386, libsm6:i386, libfontconfig1:i386, libxt6:i386, libxrender1:i386, libxext6:i386, libgl1-mesa-glx:i386, libgl1-mesa-dri:i386
=> Suggests: lib32nss-mdns|libnss-mdns:i386, libgl1-nvidia-glx:i386, libgl1-fglrx-glx:i386
=> Description: Google Earth, a 3D map/planet viewer
=> Package built with googleearth-package.
=> dpkg-deb: building package `googleearth' in `./googleearth_6.0.3.2197+1.1.0-1_amd64.deb'.  
=> You can now install the package with e.g:
=> 
=> sudo dpkg -i googleearth_6.0.3.2197+1.1.0-1_amd64.deb
=> -----------------------------

$ sudo dpkg -i googleearth_6.0.3.2197+1.1.0-1_amd64.deb
=> (Reading database ... 257682 files and directories currently installed.)
=> Preparing to replace googleearth 6.0.3.2197+1.1.0-1 (using googleearth_6.0.3.2197+1.1.0-1_amd64.deb) ...
=> Unpacking replacement googleearth ...
=> Setting up googleearth (6.0.3.2197+1.1.0-1) ...
=> Processing triggers for mime-support ...
=> Processing triggers for menu ...
=> Processing triggers for desktop-file-utils ...
=> Processing triggers for gnome-menus ...
=> Processing triggers for bamfdaemon ...
=> Rebuilding /usr/share/applications/bamf-2.index...
=> Processing triggers for shared-mime-info ...
=> Unknown media type in type 'all/all'
=> Unknown media type in type 'all/allfiles'
=> Unknown media type in type 'uri/mms'
=> Unknown media type in type 'uri/mmst'
=> Unknown media type in type 'uri/mmsu'
=> Unknown media type in type 'uri/pnm'
=> Unknown media type in type 'uri/rtspt'
=> Unknown media type in type 'uri/rtspu'

$ sudo apt-get install libfreeimage3 lsb-core libcurl3 libsm6 libfontconfig1 libxt6 libxrender1 libxext6 libgl1-mesa-glx libgl1-mesa-dri
=> Reading package lists... Done
=> Building dependency tree       
=> Reading state information... Done
=> libfontconfig1 is already the newest version.
=> libgl1-mesa-dri is already the newest version.
=> libgl1-mesa-glx is already the newest version.
=> libsm6 is already the newest version.
=> libxext6 is already the newest version.
=> libxrender1 is already the newest version.
=> libxt6 is already the newest version.
=> lsb-core is already the newest version.
=> libfreeimage3 is already the newest version.
=> libfreeimage3 set to manually installed.
=> libcurl3 is already the newest version.
=> The following packages were automatically installed and are no longer required:
  => apcalc-common linux-image-generic
=> Use 'apt-get autoremove' to remove them.
=> 0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.

$ sudo apt-get install -f
=> Reading package lists... Done
=> Building dependency tree       
=> Reading state information... Done
=> The following packages were automatically installed and are no longer required:
  => apcalc-common linux-image-generic
=> Use 'apt-get autoremove' to remove them.
=> 0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.

$ which google-earth
=> /usr/bin/google-earth

$ ls -l `which google-earth`
=> lrwxrwxrwx 1 34 Oct  7 12:40 /usr/bin/google-earth -> /opt/google/earth/free/googleearth

$ google-earth
=> [1228/184210:ERROR:net_util.cc(2195)] Not implemented reached in bool net::HaveOnlyLoopbackAddresses()
=> [1228/184210:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=> [1228/184210:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=> [1228/184210:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=> [1228/184210:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=> [1228/184210:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=> [1228/184210:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=> [1228/184210:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=> [1228/184210:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=> [1228/184210:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=> [1228/184210:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=> [1228/184210:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=> [1228/184210:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=> [1228/184210:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=> [1228/184210:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=> [1228/184210:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=> [1228/184210:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=> [1228/184210:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=> [1228/184210:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=> [1228/184210:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=> [1228/184210:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=> [1228/184211:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=> [1228/184211:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=> [1228/184211:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=> [1228/184211:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=> [1228/184211:WARNING:backend_impl.cc(1875)] Destroying invalid entry.
=> [1228/184211:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=> [1228/184211:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=> [1228/184211:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=> [1228/184211:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
=> [1228/184211:WARNING:backend_impl.cc(1875)] Destroying invalid entry.
=> [1228/184211:WARNING:backend_impl.cc(1875)] Destroying invalid entry.
=> Segmentation fault (core dumped)

```

---

