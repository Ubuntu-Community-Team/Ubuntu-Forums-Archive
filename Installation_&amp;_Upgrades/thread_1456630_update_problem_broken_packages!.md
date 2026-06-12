---
title: "update problem? broken packages?!"
date: 2010-04-17
forum: Installation &amp; Upgrades
---

### Post by HHx66 on 2010-04-17
Okay, I added the PPA backport for Kubuntu, I did sudo apt-get upgrade, etc, etc, I was trying to get the newest Amarok, and now it says I have broken packages, and nothing I do will fix them. I try to fix them at the terminal and get:

```
Reading package lists... Done                                      
Building dependency tree                                           
Reading state information... Done                                  
Correcting dependencies... Done                                    
The following packages were automatically installed and are no longer required:
  libswt-gnome-gtk-3.4-jni libndesk-dbus1.0-cil libxrandr-dev                  
  kdebase-runtime-data-common wine-gecko zenity clamav libtaglib2.0-cil comerr-dev
  libxfixes-dev libmono-cairo2.0-cil libndesk-dbus-glib1.0-cil x11proto-xinerama-dev
  libxi-dev libqt4-phonon-dev podsleuth libsqlite0 java-wrappers libcommons-cli-java
  clamav-base libkrb5-dev libmono-posix2.0-cil liblcms1-dev libclamav6              
  libgnome2.24-cil x11proto-randr-dev libxinerama-dev libgssrpc4 x11proto-fixes-dev 
  libgnome-vfs2.0-cil libxmu-dev libglade2.0-cil libart2.0-cil avidemux-plugins     
  libcal3d12 libgconf2.0-cil libkadm5clnt6 libpq-dev clamav-freshclam libxmu-headers
  libtommath0 libcommons-lang-java libxft-dev libkdb5-4 libmng-dev libgtk2.0-cil    
  libsqlite0-dev xmame-sdl liblog4j1.2-java xmame-common libkadm5srv6 libxcursor-dev
Use 'apt-get autoremove' to remove them.                                            
The following extra packages will be installed:                                     
  kdelibs5 kdelibs5-data kdelibs5-dev oxygen-icon-theme                             
  plasma-scriptengine-javascript                                                    
Suggested packages:                                                                 
  hspell                                                                            
The following packages will be REMOVED:                                             
  kde-icons-oxygen                                                                  
The following NEW packages will be installed:                                       
  oxygen-icon-theme plasma-scriptengine-javascript                                  
The following packages will be upgraded:                                            
  kdelibs5 kdelibs5-data kdelibs5-dev                                               
3 upgraded, 2 newly installed, 1 to remove and 164 not upgraded.                    
3 not fully installed or removed.                                                   
Need to get 0B/28.0MB of archives.                                                  
After this operation, 4,702kB of additional disk space will be used.                
Do you want to continue [Y/n]? y                                                    
(Reading database ... 207483 files and directories currently installed.)            
Preparing to replace kdelibs5-data 4:4.3.5-0ubuntu1~karmic1 (using .../kdelibs5-data_4%3a4.4.2-0ubuntu1~karmic1~ppa3_all.deb) ...                                           
Unpacking replacement kdelibs5-data ...                                               
dpkg: error processing /var/cache/apt/archives/kdelibs5-data_4%3a4.4.2-0ubuntu1~karmic1~ppa3_all.deb (--unpack):                                                            
 trying to overwrite '/usr/share/kde4/servicetypes/plasma-applet-popupapplet.desktop', which is also in package kdelibs5-dev 4:4.3.5-0ubuntu1~karmic1                       
Preparing to replace kdelibs5-dev 4:4.3.5-0ubuntu1~karmic1 (using .../kdelibs5-dev_4%3a4.4.2-0ubuntu1~karmic1~ppa3_amd64.deb) ...                                           
Unpacking replacement kdelibs5-dev ...                                                
dpkg: error processing /var/cache/apt/archives/kdelibs5-dev_4%3a4.4.2-0ubuntu1~karmic1~ppa3_amd64.deb (--unpack):                                                           
 trying to overwrite '/usr/share/kde4/apps/cmake/modules/FindKDevPlatform.cmake', which is also in package kdevplatform-dev 0:0.9.95a-0ubuntu1                              
Preparing to replace kdelibs5 4:4.3.5-0ubuntu1~karmic1 (using .../kdelibs5_4%3a4.4.2-0ubuntu1~karmic1~ppa3_amd64.deb) ...                                                   
Unpacking replacement kdelibs5 ...                                                    
Replacing files in old package kdebase-workspace-libs4+5 ...                          
dpkg: error processing /var/cache/apt/archives/kdelibs5_4%3a4.4.2-0ubuntu1~karmic1~ppa3_amd64.deb (--unpack):                                                               
 trying to overwrite '/usr/lib/libnepomuk.so', which is also in package kdelibs5-dev 4:4.3.5-0ubuntu1~karmic1                                                               
Processing triggers for man-db ...                                                    
Processing triggers for shared-mime-info ...                                          
Unknown media type in type 'all/all'                                                  

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs5-data_4%3a4.4.2-0ubuntu1~karmic1~ppa3_all.deb
 /var/cache/apt/archives/kdelibs5-dev_4%3a4.4.2-0ubuntu1~karmic1~ppa3_amd64.deb
 /var/cache/apt/archives/kdelibs5_4%3a4.4.2-0ubuntu1~karmic1~ppa3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

The broken packages it says in synaptic are:

kdebase-runtime
kdelibs5-dev
kdelibs-bin
libplasma3

---

### Post by zvacet on 2010-04-17
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade

sudo apt-get -f install
```

---

