---
title: "problems with python-lazr.uri after upgrade to 10.04LTS 64bit"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by hectoralex on 2010-05-28
After upgrading to 10.04LTR 64bit I encountered this problem below... I have already tried -f / --configure to no avail.

Your help is appreciated.

@ASUS-AMD64:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up python-lazr.uri (1.0.2-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-lazr.uri (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 python-lazr.uri
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Ozymandias_117 on 2010-05-28
Did you try ```
sudo dpkg --configure -a
```

---

### Post by hectoralex on 2010-05-28
> **Ozymandias_117 said:**
> Did you try ```
sudo dpkg --configure -a
```

Hello Ozymandias, thank you for your reply. YES, I had previously tried this (I searched the forums prior to asking for help)... to no avail.  But I tried it anyway, no change on error code (1)... Here is the output once more.

"hector@ASUS-AMD64:~$ sudo dpkg --configure -a
[sudo] password for hector: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up python-lazr.uri (1.0.2-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-lazr.uri (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 python-lazr.uri
E: Sub-process /usr/bin/dpkg returned an error code (1)
hector@ASUS-AMD64:~$ "

---

### Post by Ozymandias_117 on 2010-05-28
Try ```
sudo aptitude purge python-lazr.uri 
``` then reinstall it.

---

### Post by hectoralex on 2010-05-29
> **Ozymandias_117 said:**
> Try ```
sudo aptitude purge python-lazr.uri 
``` then reinstall it.

Hi, Thank you for your reply... unfortunatley I am still experiencing the same problem... I am very tempted to re-install from scratch!

Here is the output

hector@ASUS-AMD64:~$ sudo aptitude purge python-lazr.uri
[sudo] password for hector: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  apport-symptoms{u} binutils-static{u} firefox-3.5-gnome-support{u} 
  gnome-blackjack{u} kde-icons-oxygen{u} kdebase-runtime-bin-kde4{u} 
  kdebase-runtime-data-common{u} khelpcenter4{u} latex-xft-fonts{u} 
  libass3{u} libbind9-50{u} libboo2.0-cil{u} libboost-filesystem1.38.0{u} 
  libboost-program-options1.38.0{u} libboost-python1.38.0{u} 
  libboost-regex1.38.0{u} libboost-system1.38.0{u} libboost-thread1.38.0{u} 
  libcelt0{u} libcompress-bzip2-perl{u} libcv1{u} libcvaux1{u} libdns53{u} 
  libevent-1.4-2{u} libexiv2-5{u} libfaad0{u} libffado1{u} libfreebob0{u} 
  libgdata5{u} libgssdp-1.0-1{u} libgupnp-1.0-2{u} libhighgui1{u} 
  libicu40{u} libindicate-gtk1{u} libindicate3{u} libisc50{u} libisccc50{u} 
  libisccfg50{u} libkexiv2-7{u} libknotificationitem1{u} liblo0ldbl{u} 
  liblwres50{u} liblzma0{u} libntfs-3g54{u} libopal3.6.4{u} libpq5{u} 
  libpt2.6.4{u} libpt2.6.4-plugins{u} libqt4-phonon{u} librasqal1{u} 
  libwxbase2.6-0{u} libwxgtk2.6-0{u} libx264-67{u} libxklavier15{u} 
  libxml++2.6-2{u} mplayer-nogui{u} mplayer-skins{u} 
  nvidia-185-kernel-source{u} nvidia-185-libvdpau{u} protobuf-compiler{u} 
  python-configglue{u} python-gtksourceview{u} python-lazr.uri{p} 
  python-nautilusburn{u} python-protobuf{u} python-pyinotify{u} 
  python-twisted-names{u} python-ubuntuone-client{u} 
  python-ubuntuone-storageprotocol{u} raptor-utils{u} redland-utils{u} 
  xulrunner-1.9.1{u} xulrunner-1.9.1-gnome-support{u} 
0 packages upgraded, 0 newly installed, 73 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 107MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 203000 files and directories currently installed.)
Removing python-lazr.uri ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing python-lazr.uri (--purge):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 python-lazr.uri
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

hector@ASUS-AMD64:~$ sudo aptitude install python-lazr.uri
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  apport-symptoms{u} binutils-static{u} firefox-3.5-gnome-support{u} 
  gnome-blackjack{u} kde-icons-oxygen{u} kdebase-runtime-bin-kde4{u} 
  kdebase-runtime-data-common{u} khelpcenter4{u} latex-xft-fonts{u} 
  libass3{u} libbind9-50{u} libboo2.0-cil{u} libboost-filesystem1.38.0{u} 
  libboost-program-options1.38.0{u} libboost-python1.38.0{u} 
  libboost-regex1.38.0{u} libboost-system1.38.0{u} libboost-thread1.38.0{u} 
  libcelt0{u} libcompress-bzip2-perl{u} libcv1{u} libcvaux1{u} libdns53{u} 
  libevent-1.4-2{u} libexiv2-5{u} libfaad0{u} libffado1{u} libfreebob0{u} 
  libgdata5{u} libgssdp-1.0-1{u} libgupnp-1.0-2{u} libhighgui1{u} 
  libicu40{u} libindicate-gtk1{u} libindicate3{u} libisc50{u} libisccc50{u} 
  libisccfg50{u} libkexiv2-7{u} libknotificationitem1{u} liblo0ldbl{u} 
  liblwres50{u} liblzma0{u} libntfs-3g54{u} libopal3.6.4{u} libpq5{u} 
  libpt2.6.4{u} libpt2.6.4-plugins{u} libqt4-phonon{u} librasqal1{u} 
  libwxbase2.6-0{u} libwxgtk2.6-0{u} libx264-67{u} libxklavier15{u} 
  libxml++2.6-2{u} mplayer-nogui{u} mplayer-skins{u} 
  nvidia-185-kernel-source{u} nvidia-185-libvdpau{u} protobuf-compiler{u} 
  python-configglue{u} python-gtksourceview{u} python-nautilusburn{u} 
  python-protobuf{u} python-pyinotify{u} python-twisted-names{u} 
  python-ubuntuone-client{u} python-ubuntuone-storageprotocol{u} 
  raptor-utils{u} redland-utils{u} xulrunner-1.9.1{u} 
  xulrunner-1.9.1-gnome-support{u} 
The following partially installed packages will be configured:
  python-lazr.uri 
0 packages upgraded, 0 newly installed, 72 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 107MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 203000 files and directories currently installed.)
Removing apport-symptoms ...
Removing binutils-static ...
Removing firefox-3.5-gnome-support ...
Removing gnome-blackjack ...
Removing kde-icons-oxygen ...
Removing kdebase-runtime-bin-kde4 ...
Removing kdebase-runtime-data-common ...
Removing khelpcenter4 ...
Removing latex-xft-fonts ...
Updating fontconfig cache for /usr/share/fonts/truetype/latex-xft-fonts
No CIDSupplement specified for ZenHei, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for ZenHei-CNS, defaulting to 0.
Removing libass3 ...
Removing libbind9-50 ...
Removing libboo2.0-cil ...
Removing libboo2.0-cil from Mono
Removing libboost-filesystem1.38.0 ...
Removing libboost-program-options1.38.0 ...
Removing libboost-python1.38.0 ...
Removing libboost-regex1.38.0 ...
Removing libboost-system1.38.0 ...
Removing libboost-thread1.38.0 ...
Removing libcelt0 ...
Removing libcompress-bzip2-perl ...
Removing libcvaux1 ...
Removing libhighgui1 ...
Removing libcv1 ...
Removing libisccfg50 ...
Removing libdns53 ...
Removing libevent-1.4-2 ...
Removing libkexiv2-7 ...
Removing libexiv2-5 ...
Removing libfaad0 ...
Removing libffado1 ...
Removing libfreebob0 ...
Removing libgdata5 ...
Removing libgupnp-1.0-2 ...
Removing libgssdp-1.0-1 ...
Removing libicu40 ...
Removing libindicate-gtk1 ...
Removing libindicate3 ...
Removing libisccc50 ...
Removing libisc50 ...
Removing libknotificationitem1 ...
Removing liblo0ldbl ...
Removing liblwres50 ...
Removing liblzma0 ...
Removing libntfs-3g54 ...
Removing libopal3.6.4 ...
Removing libpq5 ...
Removing libpt2.6.4-plugins ...
Removing libpt2.6.4 ...
Removing libqt4-phonon ...
Removing librasqal1 ...
Removing libwxgtk2.6-0 ...
Removing libwxbase2.6-0 ...
Removing libx264-67 ...
Removing libxklavier15 ...
Removing libxml++2.6-2 ...
Removing mplayer-nogui ...
Removing mplayer-skins ...
Removing nvidia-185-kernel-source ...
Removing nvidia-185-libvdpau ...
Removing protobuf-compiler ...
Removing python-configglue ...
Removing python-gtksourceview ...
Removing python-nautilusburn ...
Removing python-ubuntuone-client ...
Removing python-ubuntuone-storageprotocol ...
Removing python-protobuf ...
Removing python-pyinotify ...
Removing python-twisted-names ...
Removing raptor-utils ...
Removing redland-utils ...
Removing xulrunner-1.9.1-gnome-support ...
Removing xulrunner-1.9.1 ...
update-alternatives: using /usr/bin/xulrunner-1.9.2 to provide /usr/bin/xulrunner (xulrunner) in auto mode.
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Processing triggers for fontconfig ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Setting up python-lazr.uri (1.0.2-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-lazr.uri (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 python-lazr.uri
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

hector@ASUS-AMD64:~$

---

### Post by Ozymandias_117 on 2010-05-29
I've never had a problem that dpkg --configure -a hasn't fixed =\ I'm not sure what to tell you from there, sorry :(

---

### Post by hectoralex on 2010-05-29
> **Ozymandias_117 said:**
> I've never had a problem that dpkg --configure -a hasn't fixed =\ I'm not sure what to tell you from there, sorry :(

Thank You man, I appreciate you trying.  I'm the type of guy that does his research prior to asking for help... I couldn't find a solution, and since I don't know coding(i am not savvy enough in linux) I have my trigger finger on the button to wipe.  I will mark this thread solved by obliteration.

Thanks for your help.

---

