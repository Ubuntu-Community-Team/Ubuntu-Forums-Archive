---
title: "Karmic Koala + Software Index broken"
date: 2011-04-11
forum: Installation &amp; Upgrades
---

### Post by raziyabhayani on 2011-04-11
Hello All, 

This is a grave problem, which I have been encountering over months. Intially I ignored it, then tried to fix it somehow or other, but did not get any solution. 

When ever I try to update my system or do a partial upgrade or upgrade or install or remove any program, I get a message "Software Index Broken" and main cause is "zteusbserial" package. It cannot be removed or fixed. Even if I try offline upgrade, it cribs about "zteusbserial" and hangs up. 

I desperately need to get out of this situation, please be advised as to how can I fix it?

---

### Post by mikewhatever on 2011-04-11
Just searched for 'zteusbserial', and it appears there is no such package in the repositories. What is it, and where did you get it from?

---

### Post by raziyabhayani on 2011-04-11
Further, after looking at many posts I tried this 

1. sudo apt-get update
2. sudo apt-get upgrade
3. sudo apt-get install 

With Ubuntu 10.10 ISO image on CD. 

I got following output for each of commands: 


mobicents@mobicents-laptop:~$ sudo apt-get update
[sudo] password for mobicents: 
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/main Translation-en_IN
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/restricted Translation-en_IN
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Translation-en_IN
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_IN          
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release.gpg                         
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty Release.gpg [189B]                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_IN    
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Translation-en_IN              
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main Translation-en_IN                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_IN
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_IN    
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages                       
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release               
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/restricted Translation-en_IN           
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages                       
  404 Not Found
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe Translation-en_IN             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/multiverse Translation-en_IN           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates Release.gpg [198B]           
Get:3 [http://dl.google.com](http://dl.google.com) testing Release.gpg [189B]                          
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main Translation-en_IN         
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/restricted Translation-en_IN   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/universe Translation-en_IN     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_IN   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty Release                                                          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates Release                                                                       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main Packages                                                                         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/restricted Packages                                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources                                        
Ign [http://dl.google.com](http://dl.google.com) testing/non-free Translation-en_IN                            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main Sources                                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/restricted Sources                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages                                                                                                            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe Packages                                                                                                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                                                                                                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages                                                                                                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources                                                                                                           
Get:4 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                                                                                                                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe Sources                                                                                                                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/multiverse Packages                                                                                                                 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/multiverse Sources                                                                                                                  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main Packages                                                                                                               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/restricted Packages                                                                                                         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main Sources                                                                                                                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/restricted Sources                                                                                                          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/universe Packages                                                                                                           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/universe Sources                                                                                                            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/multiverse Packages                                                                                                         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/multiverse Sources                                                                                                          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_IN                                                                                                                      
Get:5 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]                                                                                                                        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_IN                                                                                                                      
Get:6 [http://dl.google.com](http://dl.google.com) testing Release [2513B]                                                                                                                          
Get:7 [http://dl.google.com](http://dl.google.com) stable Release [2544B]                                                                                                                           
Get:8 [http://dl.google.com](http://dl.google.com) stable Release [1347B]                                                                                                                           
Get:9 [http://dl.google.com](http://dl.google.com) testing/non-free Packages [793B]                                                                                                                 
Get:10 [http://dl.google.com](http://dl.google.com) stable/main Packages [1082B]                                                                                                                    
Get:11 [http://dl.google.com](http://dl.google.com) stable/main Packages [737B]                                                                                                                     
Fetched 9978B in 38s (261B/s)                                                                                                                                               
W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/jaunty/main/binary-i386/Packages](http://wine.budgetdedicated.com/apt/dists/jaunty/main/binary-i386/Packages)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
mobicents@mobicents-laptop:~$ 
mobicents@mobicents-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  zteusbserial
The following packages have been kept back:
  bind9 bind9-host bind9utils dnsutils epiphany-browser-dbg epiphany-gecko firefox firefox-3.0 firefox-3.0-branding firefox-gnome-support flashblock g++ landscape-common
  libbind9-40 libdns45 libisc45 libisccc40 libisccfg40 liblwres40 linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic wvdial
The following packages will be upgraded:
  apache2-utils apache2.2-common apport apport-gtk apturl avahi-autoipd avahi-daemon avahi-utils bogofilter bogofilter-bdb bogofilter-common bzip2 cabextract cacao cups
  cups-bsd cups-client cups-common cupsys cupsys-bsd cupsys-client cupsys-common dhcp3-client dhcp3-common dkms dpkg epiphany-browser epiphany-browser-data fakeroot ffmpeg
  fglrx-modaliases firefox-3.0-gnome-support firefox-3.5 firefox-3.5-branding flashplugin-installer flashplugin-nonfree fuse-utils ghostscript ghostscript-x gimp gimp-data
  gimp-dbg gnome-screensaver google-chrome-beta google-talkplugin grub-common gzip kdelibs-data kdelibs4c2a language-pack-en language-pack-en-base language-pack-gnome-en
  language-pack-gnome-en-base lftp libaudiofile0 libavahi-client3 libavahi-common-data libavahi-common3 libavahi-compat-libdnssd1 libavahi-core5 libavahi-glib1
  libavahi-gobject0 libavahi-qt3-1 libavahi-ui0 libavdevice52 libavfilter0 libavformat52 libbz2-1.0 libc6 libc6-dev libc6-i686 libcups2 libcups2-dev libcupsimage2
  libcupsys2 libcupsys2-dev libexpat1 libexpat1-dev libfreetype6 libfreetype6-dev libfuse2 libgd2-noxpm libgdiplus libgimp2.0 libglib2.0-0 libglib2.0-0-dbg libgs8
  libhtml-parser-perl libicu38 libkadm55 libkpathsea4 libkrb5-dev libkrb53 libldap-2.4-2 libmysqlclient15-dev libmysqlclient15off libnspr4-0d libnspr4-0d-dbg libnss3-1d
  libnss3-1d-dbg libpcsclite1 libpng12-0 libpng12-dev libpoppler-glib4 libpoppler4 libpostproc51 libpq5 libpulse-browse0 libpulse0 libpulsecore9 libpurple0 libqt4-dbus
  libqt4-designer libqt4-network libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-xml libqtcore4 libqtgui4 libsmbclient libsndfile1 libsnmp-base
  libsnmp15 libssl0.9.8 libswscale0 libthai-data libthai0 libtiff4 libvorbis0a libvorbisenc2 libvorbisfile3 libvte-common libvte9 libwbclient0 libwww-perl libwxbase2.6-0
  libwxgtk2.6-0 linux-headers-2.6.28-15 linux-headers-2.6.28-15-generic linux-image-2.6.28-15-generic linux-libc-dev linux-restricted-modules-common mysql-client-5.0
  mysql-common mysql-server mysql-server-5.0 mysql-server-core-5.0 network-manager-gnome ntpdate openoffice.org-base-core openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-emailmerge openoffice.org-gnome openoffice.org-gtk openoffice.org-impress openoffice.org-math
  openoffice.org-style-human openoffice.org-writer openssl patch pidgin pidgin-data pm-utils poppler-utils pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf
  pulseaudio-module-hal pulseaudio-module-x11 pulseaudio-utils python-apport python-gtkhtml2 python-problem-report python-uno python-vte python-zopeinterface python2.4
  python2.4-minimal python2.5 python2.5-minimal qt4-qtconfig samba-common smbclient sudo sun-java6-bin sun-java6-jre sun-java6-plugin totem totem-common totem-dbg
  totem-gstreamer totem-mozilla totem-plugins transmission-common transmission-gtk ttf-opensymbol tzdata ubufox uno-libs3 update-manager update-manager-core ure w3m wget
  xserver-common xserver-xorg-core xulrunner-1.9 xulrunner-1.9-gnome-support xulrunner-1.9.1 yelp
215 upgraded, 0 newly installed, 1 to remove and 24 not upgraded.
1 not fully installed or removed.
Need to get 370MB/370MB of archives.
After this operation, 39.3MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main dpkg 1.14.24ubuntu1.2 [2355kB]
Err [http://dl.google.com](http://dl.google.com) stable/main google-chrome-beta 8.0.552.200-r65749
  404 Not Found
Get:2 [http://dl.google.com](http://dl.google.com) stable/main google-talkplugin 1.8.0.0-1 [6305kB]
Media change: please insert the disc labeled                                                                                                                                
 'Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)'
in the drive '/cdrom/' and press enter

Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main gzip 1.3.12-6ubuntu2.9.04.1 [102kB]                                                                                  
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libc6-dev 2.9-4ubuntu6.3 [3453kB]                                                                                    
Get:5 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libc6 2.9-4ubuntu6.3 [4471kB]                                                                                        
Get:6 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libc6-i686 2.9-4ubuntu6.3 [1246kB]                                                                                   
Get:7 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main linux-libc-dev 2.6.28-19.66 [768kB]                                                                                  
Get:8 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main bzip2 1.0.5-1ubuntu1.1 [46.4kB]                                                                                      
Get:9 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libbz2-1.0 1.0.5-1ubuntu1.1 [45.9kB]                                                                                 
Get:10 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libfreetype6-dev 2.3.9-4ubuntu0.3 [698kB]                                                                           
Get:11 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libfreetype6 2.3.9-4ubuntu0.3 [393kB]                                                                               
Get:12 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libglib2.0-0-dbg 2.20.1-0ubuntu2.1 [1192kB]                                                                         
Get:13 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libglib2.0-0 2.20.1-0ubuntu2.1 [777kB]                                                                              
Get:14 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libnspr4-0d-dbg 4.8.6-0ubuntu0.9.04.1 [292kB]                                                                       
Get:15 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libnspr4-0d 4.8.6-0ubuntu0.9.04.1 [126kB]                                                                           
Get:16 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libnss3-1d-dbg 3.12.8-0ubuntu0.9.04.1 [3198kB]                                                                      
Get:17 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libnss3-1d 3.12.8-0ubuntu0.9.04.1 [1114kB]                                                                          
Get:18 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libpng12-dev 1.2.27-2ubuntu2.2 [248kB]                                                                              
Get:19 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libpng12-0 1.2.27-2ubuntu2.2 [167kB]                                                                                
Get:20 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libssl0.9.8 0.9.8g-15ubuntu3.6 [2932kB]                                                                             
Get:21 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main wget 1.11.4-2ubuntu1.2 [242kB]                                                                                      
Get:22 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main language-pack-en 1:9.04+20100531 [2044B]                                                                            
Get:23 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main language-pack-en-base 1:9.04+20100531 [803kB]                                                                       
Get:24 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main language-pack-gnome-en 1:9.04+20100531.2 [2176B]                                                                    
Get:25 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main language-pack-gnome-en-base 1:9.04+20100531.2 [920kB]                                                               
Get:26 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main qt4-qtconfig 4.5.0-0ubuntu4.3 [80.2kB]                                                                              
Get:27 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libqt4-qt3support 4.5.0-0ubuntu4.3 [1048kB]                                                                         
Get:28 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libqt4-designer 4.5.0-0ubuntu4.3 [1821kB]                                                                           
Get:29 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libqt4-script 4.5.0-0ubuntu4.3 [345kB]                                                                              
Get:30 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libqt4-dbus 4.5.0-0ubuntu4.3 [175kB]                                                                                
Get:31 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libqt4-xml 4.5.0-0ubuntu4.3 [85.7kB]                                                                                
Get:32 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main mysql-common 5.1.30really5.0.75-0ubuntu10.5 [63.6kB]                                                                
Get:33 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libmysqlclient15off 5.1.30really5.0.75-0ubuntu10.5 [1843kB]                                                         
Get:34 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libqt4-sql-mysql 4.5.0-0ubuntu4.3 [23.5kB]                                                                          
Get:35 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libqt4-sql 4.5.0-0ubuntu4.3 [85.5kB]                                                                                
Get:36 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libqt4-network 4.5.0-0ubuntu4.3 [387kB]                                                                             
Get:37 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libtiff4 3.8.2-11ubuntu0.9.04.6 [127kB]                                                                             
Get:38 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libqtgui4 4.5.0-0ubuntu4.3 [3638kB]                                                                                 
Get:39 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libqtcore4 4.5.0-0ubuntu4.3 [1495kB]                                                                                
Get:40 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main linux-image-2.6.28-15-generic 2.6.28-15.52 [24.7MB]                                                                 
Get:41 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main mysql-server 5.1.30really5.0.75-0ubuntu10.5 [57.9kB]                                                                
Get:42 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main mysql-client-5.0 5.1.30really5.0.75-0ubuntu10.5 [7883kB]                                                            
Get:43 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main mysql-server-core-5.0 5.1.30really5.0.75-0ubuntu10.5 [3350kB]                                                       
Get:44 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main mysql-server-5.0 5.1.30really5.0.75-0ubuntu10.5 [23.6MB]                                                            
Get:45 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main openoffice.org-emailmerge 1:3.0.1-9ubuntu3.3 [6766B]                                                                
Get:46 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main epiphany-browser 2.26.1-0ubuntu1.9.04.1 [19.2kB]                                                                    
Get:47 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main xulrunner-1.9-gnome-support 1.9.0.19+nobinonly-0ubuntu0.9.04.1 [39.4kB]                                             
Get:48 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main xulrunner-1.9 1.9.0.19+nobinonly-0ubuntu0.9.04.1 [7568kB]                                                           
Get:49 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/multiverse sun-java6-plugin 6.22-0ubuntu1~9.04.1 [1906B]                                                                 
Get:50 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/multiverse sun-java6-bin 6.22-0ubuntu1~9.04.1 [29.7MB]                                                                   
Get:51 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/multiverse sun-java6-jre 6.22-0ubuntu1~9.04.1 [6427kB]                                                                   
Get:52 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main tzdata 2010m~repack-0ubuntu0.9.04 [682kB]                                                                           
Get:53 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main dhcp3-client 3.1.1-5ubuntu8.2 [254kB]                                                                               
Get:54 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main dhcp3-common 3.1.1-5ubuntu8.2 [316kB]                                                                               
Get:55 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main python2.4 2.4.6-1ubuntu3.2.9.04.1 [2833kB]                                                                          
Get:56 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main python2.4-minimal 2.4.6-1ubuntu3.2.9.04.1 [990kB]                                                                   
Get:57 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main python2.5 2.5.4-1ubuntu4.1 [2917kB]                                                                                 
Get:58 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main python2.5-minimal 2.5.4-1ubuntu4.1 [1191kB]                                                                         
Get:59 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libkrb5-dev 1.6.dfsg.4~beta1-5ubuntu2.4 [93.1kB]                                                                    
Get:60 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libkadm55 1.6.dfsg.4~beta1-5ubuntu2.4 [151kB]                                                                       
Get:61 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libkrb53 1.6.dfsg.4~beta1-5ubuntu2.4 [474kB]                                                                        
Get:62 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libldap-2.4-2 2.4.15-1ubuntu3.1 [192kB]                                                                             
Get:63 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libvte-common 1:0.20.0-0ubuntu2.1 [34.1kB]                                                                          
Get:64 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libvte9 1:0.20.0-0ubuntu2.1 [578kB]                                                                                 
Get:65 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main python-vte 1:0.20.0-0ubuntu2.1 [29.9kB]                                                                             
Get:66 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main update-manager 1:0.111.10 [773kB]                                                                                   
Get:67 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main update-manager-core 1:0.111.10 [170kB]                                                                              
Get:68 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main w3m 0.5.2-2ubuntu0.1 [1101kB]                                                                                       
Get:69 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main apache2-utils 2.2.11-2ubuntu2.7 [150kB]                                                                             
Get:70 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main apache2.2-common 2.2.11-2ubuntu2.7 [785kB]                                                                          
Get:71 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main python-problem-report 1.0-0ubuntu5.4 [72.1kB]                                                                       
Get:72 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main python-apport 1.0-0ubuntu5.4 [74.0kB]                                                                               
Get:73 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main apport 1.0-0ubuntu5.4 [113kB]                                                                                       
Get:74 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main apport-gtk 1.0-0ubuntu5.4 [68.0kB]                                                                                  
Get:75 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main apturl 0.3.3ubuntu1.2 [18.6kB]                                                                                      
Get:76 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main avahi-autoipd 0.6.23-4ubuntu4.1 [49.4kB]                                                                            
Get:77 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libavahi-common-data 0.6.23-4ubuntu4.1 [32.0kB]                                                                     
Get:78 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libavahi-common3 0.6.23-4ubuntu4.1 [23.2kB]                                                                         
Get:79 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libavahi-core5 0.6.23-4ubuntu4.1 [113kB]                                                                            
Get:80 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libexpat1-dev 2.0.1-4ubuntu0.9.04.1 [210kB]                                                                         
Get:81 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libexpat1 2.0.1-4ubuntu0.9.04.1 [132kB]                                                                             
Get:82 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main avahi-daemon 0.6.23-4ubuntu4.1 [63.7kB]                                                                             
Get:83 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libavahi-client3 0.6.23-4ubuntu4.1 [52.3kB]                                                                         
Get:84 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main avahi-utils 0.6.23-4ubuntu4.1 [27.4kB]                                                                              
Get:85 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main bogofilter-common 1.1.7-1ubuntu1.1 [149kB]                                                                          
Get:86 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main bogofilter-bdb 1.1.7-1ubuntu1.1 [216kB]                                                                             
Get:87 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main bogofilter 1.1.7-1ubuntu1.1 [988B]                                                                                  
Get:88 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/universe cabextract 1.2-3+lenny1build0.9.04.1 [55.6kB]                                                                   
Get:89 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/universe cacao 0.99.4-1ubuntu0.9.04.2 [575kB]                                                                            
Get:90 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libavahi-compat-libdnssd1 0.6.23-4ubuntu4.1 [16.6kB]                                                                
Get:91 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libcups2-dev 1.3.9-17ubuntu3.9 [346kB]                                                                              
Get:92 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libcups2 1.3.9-17ubuntu3.9 [175kB]                                                                                  
Get:93 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libcupsimage2 1.3.9-17ubuntu3.9 [51.5kB]                                                                            
Get:94 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libpoppler4 0.10.5-1ubuntu2.6 [687kB]                                                                               
Get:95 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main poppler-utils 0.10.5-1ubuntu2.6 [75.2kB]                                                                            
Get:96 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main ghostscript 8.64.dfsg.1-0ubuntu8.1 [794kB]                                                                          
Get:97 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libgs8 8.64.dfsg.1-0ubuntu8.1 [2326kB]                                                                              
Get:98 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main cups-common 1.3.9-17ubuntu3.9 [1166kB]                                                                              
Get:99 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main cups 1.3.9-17ubuntu3.9 [2145kB]                                                                                     
Get:100 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main cups-bsd 1.3.9-17ubuntu3.9 [36.2kB]                                                                                
Get:101 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main cups-client 1.3.9-17ubuntu3.9 [115kB]                                                                              
Get:102 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main epiphany-browser-data 2.26.1-0ubuntu1.9.04.1 [3601kB]                                                              
Get:103 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libavformat52 3:0.svn20090303-1ubuntu6.2 [708kB]                                                                   
Get:104 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libavdevice52 3:0.svn20090303-1ubuntu6.2 [70.1kB]                                                                  
Get:105 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libavfilter0 3:0.svn20090303-1ubuntu6.2 [45.0kB]                                                                   
Get:106 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libpostproc51 3:0.svn20090303-1ubuntu6.2 [68.4kB]                                                                  
Get:107 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libswscale0 3:0.svn20090303-1ubuntu6.2 [172kB]                                                                     
Get:108 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main ffmpeg 3:0.svn20090303-1ubuntu6.2 [233kB]                                                                          
Get:109 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main firefox-3.0-gnome-support 3.6.11+build3+nobinonly-0ubuntu0.9.04.1 [72.6kB]                                         
Get:110 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/universe firefox-3.5-branding 3.5.14+build3+nobinonly-0ubuntu0.9.04.1 [156kB]                                           
Get:111 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/universe xulrunner-1.9.1 1.9.1.14+build4+nobinonly-0ubuntu0.9.04.1 [8314kB]                                             
Get:112 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/universe firefox-3.5 3.5.14+build3+nobinonly-0ubuntu0.9.04.1 [928kB]                                                    
Get:113 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/multiverse flashplugin-installer 10.1.85.3ubuntu0.9.04.1 [19.6kB]                                                       
Get:114 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/multiverse flashplugin-nonfree 10.1.85.3ubuntu0.9.04.1 [1772B]                                                          
Get:115 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main fuse-utils 2.7.4-1.1ubuntu4.0.9.04.1 [21.1kB]                                                                      
Get:116 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libfuse2 2.7.4-1.1ubuntu4.0.9.04.1 [129kB]                                                                         
Get:117 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main ghostscript-x 8.64.dfsg.1-0ubuntu8.1 [66.4kB]                                                                      
Get:118 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main gimp-dbg 2.6.6-0ubuntu1.1 [13.0MB]                                                                                 
Get:119 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libgimp2.0 2.6.6-0ubuntu1.1 [591kB]                                                                                
Get:120 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main gimp-data 2.6.6-0ubuntu1.1 [1975kB]                                                                                
Get:121 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libpoppler-glib4 0.10.5-1ubuntu2.6 [61.4kB]                                                                        
Get:122 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main gimp 2.6.6-0ubuntu1.1 [4363kB]                                                                                     
Get:123 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main gnome-screensaver 2.24.0-0ubuntu6.1 [1432kB]                                                                       
Get:124 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libpulse0 1:0.9.14-0ubuntu20.3 [182kB]                                                                             
Get:125 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main kdelibs-data 4:3.5.10.dfsg.1-1ubuntu8.4 [6752kB]                                                                   
Get:126 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libavahi-qt3-1 0.6.23-4ubuntu4.1 [34.4kB]                                                                          
Get:127 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main sudo 1.6.9p17-1ubuntu3.3 [180kB]                                                                                   
Get:128 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main kdelibs4c2a 4:3.5.10.dfsg.1-1ubuntu8.4 [10.0MB]                                                                    
Get:129 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main lftp 3.7.8-1ubuntu0.1 [401kB]                                                                                      
Get:130 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libaudiofile0 0.2.6-7ubuntu1.9.04.1 [81.5kB]                                                                       
Get:131 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libavahi-glib1 0.6.23-4ubuntu4.1 [32.9kB]                                                                          
Get:132 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libavahi-gobject0 0.6.23-4ubuntu4.1 [17.8kB]                                                                       
Get:133 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libavahi-ui0 0.6.23-4ubuntu4.1 [21.2kB]                                                                            
Get:134 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libgd2-noxpm 2.0.36~rc1~dfsg-3ubuntu1.9.04.1 [209kB]                                                               
Get:135 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libgdiplus 2.0-1ubuntu0.1 [158kB]                                                                                  
Get:136 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libhtml-parser-perl 3.59-1ubuntu1.1 [112kB]                                                                        
Get:137 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libicu38 3.8.1-3ubuntu1.1 [5928kB]                                                                                 
Get:138 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libkpathsea4 2007.dfsg.2-4ubuntu2.1 [121kB]                                                                        
Get:139 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libmysqlclient15-dev 5.1.30really5.0.75-0ubuntu10.5 [7300kB]                                                       
Get:140 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libpcsclite1 1.4.102-1ubuntu2.1 [43.1kB]                                                                           
Get:141 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libpq5 8.3.12-0ubuntu9.04 [336kB]                                                                                  
Get:142 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libpulse-browse0 1:0.9.14-0ubuntu20.3 [31.5kB]                                                                     
Get:143 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libsndfile1 1.0.17-4ubuntu1.1 [198kB]                                                                              
Get:144 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libpulsecore9 1:0.9.14-0ubuntu20.3 [227kB]                                                                         
Get:145 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main pidgin-data 1:2.5.5-1ubuntu8.6 [1152kB]                                                                            
Get:146 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libpurple0 1:2.5.5-1ubuntu8.6 [1554kB]                                                                             
Get:147 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libwbclient0 2:3.3.2-1ubuntu3.6 [97.2kB]                                                                           
Get:148 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libsmbclient 2:3.3.2-1ubuntu3.6 [1348kB]                                                                           
Get:149 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libsnmp-base 5.4.1~dfsg-12ubuntu3.1 [529kB]                                                                        
Get:150 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libsnmp15 5.4.1~dfsg-12ubuntu3.1 [1119kB]                                                                          
Get:151 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libthai-data 0.1.9-4ubuntu0.9.04.2 [162kB]                                                                         
Get:152 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libthai0 0.1.9-4ubuntu0.9.04.2 [32.0kB]                                                                            
Get:153 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libvorbis0a 1.2.0.dfsg-3.1ubuntu0.9.04.2 [103kB]                                                                   
Get:154 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libvorbisenc2 1.2.0.dfsg-3.1ubuntu0.9.04.2 [77.9kB]                                                                
Get:155 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libvorbisfile3 1.2.0.dfsg-3.1ubuntu0.9.04.2 [21.8kB]                                                               
Get:156 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libwww-perl 5.820-1ubuntu0.1 [391kB]                                                                               
Get:157 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/universe libwxbase2.6-0 2.6.3.2.2-3ubuntu4.1 [543kB]                                                                    
Get:158 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/universe libwxgtk2.6-0 2.6.3.2.2-3ubuntu4.1 [2734kB]                                                                    
Get:159 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main linux-headers-2.6.28-15 2.6.28-15.52 [8699kB]                                                                      
Get:160 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main linux-headers-2.6.28-15-generic 2.6.28-15.52 [672kB]                                                               
Get:161 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/restricted linux-restricted-modules-common 2.6.28-19.24 [11.6kB]                                                        
Get:162 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main network-manager-gnome 0.7.1~rc4.1-0ubuntu2.1 [366kB]                                                               
Get:163 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main ntpdate 1:4.2.4p4+dfsg-7ubuntu5.2 [62.6kB]                                                                         
Get:164 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main ure 1.4.1+OOo3.0.1-9ubuntu3.3 [1393kB]                                                                             
Get:165 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main uno-libs3 1.4.1+OOo3.0.1-9ubuntu3.3 [1093kB]                                                                       
Get:166 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main openoffice.org-calc 1:3.0.1-9ubuntu3.3 [4019kB]                                                                    
Get:167 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main openoffice.org-impress 1:3.0.1-9ubuntu3.3 [447kB]                                                                  
Get:168 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main openoffice.org-draw 1:3.0.1-9ubuntu3.3 [1995kB]                                                                    
Get:169 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main openoffice.org-style-human 1:3.0.1-9ubuntu3.3 [3793kB]                                                             
Get:170 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main openoffice.org-common 1:3.0.1-9ubuntu3.3 [17.2MB]                                                                  
Get:171 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main openoffice.org-gtk 1:3.0.1-9ubuntu3.3 [156kB]                                                                      
Get:172 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main openoffice.org-gnome 1:3.0.1-9ubuntu3.3 [3014B]                                                                    
Get:173 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main python-uno 1:3.0.1-9ubuntu3.3 [90.6kB]                                                                             
Get:174 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main openoffice.org-math 1:3.0.1-9ubuntu3.3 [240kB]                                                                     
Get:175 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main ttf-opensymbol 1:3.0.1-9ubuntu3.3 [254kB]                                                                          
Get:176 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main openoffice.org-writer 1:3.0.1-9ubuntu3.3 [5604kB]                                                                  
Get:177 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main openoffice.org-base-core 1:3.0.1-9ubuntu3.3 [526kB]                                                                
Get:178 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main openoffice.org-core 1:3.0.1-9ubuntu3.3 [26.1MB]                                                                    
Get:179 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main openssl 0.9.8g-15ubuntu3.6 [398kB]                                                                                 
Get:180 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main pidgin 1:2.5.5-1ubuntu8.6 [520kB]                                                                                  
Get:181 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main pm-utils 1.2.2.4-0ubuntu5 [43.5kB]                                                                                 
Get:182 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main pulseaudio 1:0.9.14-0ubuntu20.3 [412kB]                                                                            
Get:183 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main pulseaudio-esound-compat 1:0.9.14-0ubuntu20.3 [30.3kB]                                                             
Get:184 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main pulseaudio-module-gconf 1:0.9.14-0ubuntu20.3 [12.5kB]                                                              
Get:185 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main pulseaudio-module-hal 1:0.9.14-0ubuntu20.3 [16.7kB]                                                                
Get:186 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main pulseaudio-utils 1:0.9.14-0ubuntu20.3 [177kB]                                                                      
Get:187 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main pulseaudio-module-x11 1:0.9.14-0ubuntu20.3 [18.0kB]                                                                
Get:188 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main python-gtkhtml2 2.19.1-0ubuntu14.9.04.1 [27.4kB]                                                                   
Get:189 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main python-zopeinterface 3.4.0-0ubuntu3.3 [146kB]                                                                      
Get:190 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main smbclient 2:3.3.2-1ubuntu3.6 [8100kB]                                                                              
Get:191 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main samba-common 2:3.3.2-1ubuntu3.6 [4061kB]                                                                           
Get:192 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main totem-dbg 2.26.1-0ubuntu5.1 [3183kB]                                                                               
Get:193 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main totem-common 2.26.1-0ubuntu5.1 [2081kB]                                                                            
Get:194 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main totem-plugins 2.26.1-0ubuntu5.1 [395kB]                                                                            
Get:195 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main totem-gstreamer 2.26.1-0ubuntu5.1 [886kB]                                                                          
Get:196 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main totem 2.26.1-0ubuntu5.1 [266kB]                                                                                    
Get:197 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main totem-mozilla 2.26.1-0ubuntu5.1 [266kB]                                                                            
Get:198 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main transmission-gtk 1.51-0ubuntu3.1 [335kB]                                                                           
Get:199 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main transmission-common 1.51-0ubuntu3.1 [146kB]                                                                        
Get:200 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main ubufox 0.9~rc2-0ubuntu0.9.04.2 [58.3kB]                                                                            
Get:201 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main xserver-common 2:1.6.0-0ubuntu14.2 [69.8kB]                                                                        
Get:202 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main xserver-xorg-core 2:1.6.0-0ubuntu14.2 [2179kB]                                                                     
Get:203 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main yelp 2.25.1-0ubuntu5.9.04.1 [368kB]                                                                                
Get:204 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/universe cupsys 1.3.9-17ubuntu3.9 [61.2kB]                                                                              
Get:205 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/universe cupsys-bsd 1.3.9-17ubuntu3.9 [61.2kB]                                                                          
Get:206 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/universe cupsys-client 1.3.9-17ubuntu3.9 [61.2kB]                                                                       
Get:207 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/universe cupsys-common 1.3.9-17ubuntu3.9 [4518B]                                                                        
Get:208 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main fglrx-modaliases 2:8.600-0ubuntu3 [11.3kB]                                                                         
Get:209 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main grub-common 1.96+20080724-12ubuntu2.1 [93.6kB]                                                                     
Get:210 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/universe libcupsys2 1.3.9-17ubuntu3.9 [61.2kB]                                                                          
Get:211 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libcupsys2-dev 1.3.9-17ubuntu3.9 [61.2kB]                                                                          
Fetched 346MB in 1h 50min 39s (52.1kB/s)                                                                                                                                    
Failed to fetch [http://dl.google.com/linux/deb/pool/main/g/google-chrome-beta/google-chrome-beta_8.0.552.200-r65749_i386.deb](http://dl.google.com/linux/deb/pool/main/g/google-chrome-beta/google-chrome-beta_8.0.552.200-r65749_i386.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
mobicents@mobicents-laptop:~$ run apt-get update --fix-missing
bash: run: command not found
mobicents@mobicents-laptop:~$ sudo apt-get update --fix-missing
[sudo] password for mobicents: 
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/main Translation-en_IN
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/restricted Translation-en_IN
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Translation-en_IN
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty Release.gpg                                                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                                                   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main Translation-en_IN                                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_IN                                        
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/restricted Translation-en_IN                                         
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release.gpg                                                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_IN                                  
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Translation-en_IN                                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_IN                                    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe Translation-en_IN                                           
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release                                                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_IN                                  
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages                                                     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/multiverse Translation-en_IN                                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                                                       
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages                                                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates Release.gpg          
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages                                                     
  404 Not Found
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                                                 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages                     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/restricted Translation-en_IN           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/universe Translation-en_IN             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                            
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_IN           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty Release                                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates Release                                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main Packages                                                       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/restricted Packages                            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main Sources                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/restricted Sources                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe Packages                              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe Sources         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/multiverse Packages      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/multiverse Sources       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main Packages    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main Sources     
Get:1 [http://dl.google.com](http://dl.google.com) testing Release.gpg [189B]            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/universe Sources 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/multiverse Sources
Ign [http://dl.google.com](http://dl.google.com) testing/non-free Translation-en_IN                                                                                                                 
Get:2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                                                                                                                        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_IN
Get:3 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]                                                                                                                        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_IN                                                                                                                      
Get:4 [http://dl.google.com](http://dl.google.com) testing Release [2513B]                                                                                                                          
Get:5 [http://dl.google.com](http://dl.google.com) stable Release [2544B]                                                                                                                           
Get:6 [http://dl.google.com](http://dl.google.com) stable Release [1347B]                                                                                                                           
Get:7 [http://dl.google.com](http://dl.google.com) testing/non-free Packages [793B]                                                                                                                 
Get:8 [http://dl.google.com](http://dl.google.com) stable/main Packages [1082B]                                                                                                                     
Get:9 [http://dl.google.com](http://dl.google.com) stable/main Packages [737B]          
Fetched 9591B in 58s (165B/s)
W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/jaunty/main/binary-i386/Packages](http://wine.budgetdedicated.com/apt/dists/jaunty/main/binary-i386/Packages)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
mobicents@mobicents-laptop:~$ sudo apt-get clean
mobicents@mobicents-laptop:~$ 


Please keep advised. I dont see any updates affected, what is the reason??? 

Now I am running 1,2, 3 again and I see that packages are again getting installed, why is that so??? Where did previous packages go??? 

Thanks and regards, 

Raziya

---

### Post by coffeecat on 2011-04-11
It would help if you answered mikewhatever's question:

> **mikewhatever said:**
> Just searched for 'zteusbserial', and it appears there is no such package in the repositories. What is it, and where did you get it from?

Also, you refer to Karmic Koala in your title, your apt-get output refers to Jaunty - which is now unsupported - and you appear to have set up the Karmic and Maverick CDs as sources. What exactly are you trying to do?

---

### Post by raziyabhayani on 2011-04-11
Hello Mike, 

I dont know what does that package do. The system was used by someone else, so I have no clues. 

Yes I am on Jaunty 9.04 trying to install 10.10 is that possible? 

I tried this, as guided by apt-get upgrade, apt-get upgrade --fix-missing and now I get this output 


mobicents@mobicents-laptop:~$ sudo apt-get upgrade --fix-missing 
[sudo] password for mobicents: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  zteusbserial
The following packages have been kept back:
  bind9 bind9-host bind9utils dnsutils epiphany-browser-dbg epiphany-gecko firefox firefox-3.0 firefox-3.0-branding firefox-gnome-support flashblock g++ landscape-common
  libbind9-40 libdns45 libisc45 libisccc40 libisccfg40 liblwres40 linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic wvdial
The following packages will be upgraded:
  apache2-utils apache2.2-common apport apport-gtk apturl avahi-autoipd avahi-daemon avahi-utils bogofilter bogofilter-bdb bogofilter-common bzip2 cabextract cacao cups
  cups-bsd cups-client cups-common cupsys cupsys-bsd cupsys-client cupsys-common dhcp3-client dhcp3-common dkms dpkg epiphany-browser epiphany-browser-data fakeroot ffmpeg
  fglrx-modaliases firefox-3.0-gnome-support firefox-3.5 firefox-3.5-branding flashplugin-installer flashplugin-nonfree fuse-utils ghostscript ghostscript-x gimp gimp-data
  gimp-dbg gnome-screensaver google-chrome-beta google-talkplugin grub-common gzip kdelibs-data kdelibs4c2a language-pack-en language-pack-en-base language-pack-gnome-en
  language-pack-gnome-en-base lftp libaudiofile0 libavahi-client3 libavahi-common-data libavahi-common3 libavahi-compat-libdnssd1 libavahi-core5 libavahi-glib1
  libavahi-gobject0 libavahi-qt3-1 libavahi-ui0 libavdevice52 libavfilter0 libavformat52 libbz2-1.0 libc6 libc6-dev libc6-i686 libcups2 libcups2-dev libcupsimage2
  libcupsys2 libcupsys2-dev libexpat1 libexpat1-dev libfreetype6 libfreetype6-dev libfuse2 libgd2-noxpm libgdiplus libgimp2.0 libglib2.0-0 libglib2.0-0-dbg libgs8
  libhtml-parser-perl libicu38 libkadm55 libkpathsea4 libkrb5-dev libkrb53 libldap-2.4-2 libmysqlclient15-dev libmysqlclient15off libnspr4-0d libnspr4-0d-dbg libnss3-1d
  libnss3-1d-dbg libpcsclite1 libpng12-0 libpng12-dev libpoppler-glib4 libpoppler4 libpostproc51 libpq5 libpulse-browse0 libpulse0 libpulsecore9 libpurple0 libqt4-dbus
  libqt4-designer libqt4-network libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-xml libqtcore4 libqtgui4 libsmbclient libsndfile1 libsnmp-base
  libsnmp15 libssl0.9.8 libswscale0 libthai-data libthai0 libtiff4 libvorbis0a libvorbisenc2 libvorbisfile3 libvte-common libvte9 libwbclient0 libwww-perl libwxbase2.6-0
  libwxgtk2.6-0 linux-headers-2.6.28-15 linux-headers-2.6.28-15-generic linux-image-2.6.28-15-generic linux-libc-dev linux-restricted-modules-common mysql-client-5.0
  mysql-common mysql-server mysql-server-5.0 mysql-server-core-5.0 network-manager-gnome ntpdate openoffice.org-base-core openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-emailmerge openoffice.org-gnome openoffice.org-gtk openoffice.org-impress openoffice.org-math
  openoffice.org-style-human openoffice.org-writer openssl patch pidgin pidgin-data pm-utils poppler-utils pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf
  pulseaudio-module-hal pulseaudio-module-x11 pulseaudio-utils python-apport python-gtkhtml2 python-problem-report python-uno python-vte python-zopeinterface python2.4
  python2.4-minimal python2.5 python2.5-minimal qt4-qtconfig samba-common smbclient sudo sun-java6-bin sun-java6-jre sun-java6-plugin totem totem-common totem-dbg
  totem-gstreamer totem-mozilla totem-plugins transmission-common transmission-gtk ttf-opensymbol tzdata ubufox uno-libs3 update-manager update-manager-core ure w3m wget
  xserver-common xserver-xorg-core xulrunner-1.9 xulrunner-1.9-gnome-support xulrunner-1.9.1 yelp
215 upgraded, 0 newly installed, 1 to remove and 24 not upgraded.
1 not fully installed or removed.
Need to get 24.0MB/370MB of archives.
After this operation, 39.3MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err [http://dl.google.com](http://dl.google.com) stable/main google-chrome-beta 8.0.552.200-r65749
  404 Not Found
Failed to fetch [http://dl.google.com/linux/deb/pool/main/g/google-chrome-beta/google-chrome-beta_8.0.552.200-r65749_i386.deb](http://dl.google.com/linux/deb/pool/main/g/google-chrome-beta/google-chrome-beta_8.0.552.200-r65749_i386.deb)  404 Not Found
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 138567 files and directories currently installed.)
Removing zteusbserial ...
ztemtvcdromd: no process killed
dpkg: error processing zteusbserial (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 zteusbserial
E: Sub-process /usr/bin/dpkg returned an error code (1)
mobicents@mobicents-laptop:~$ 


If you could please suggest what can be done here? 

Thanks and regards, 
Raziya

---

### Post by coffeecat on 2011-04-11
> **raziyabhayani said:**
> I dont know what does that package do. The system was used by someone else, so I have no clues. 

Always a problem inheriting a system from someone else. You can't always tell what problematic packages or repositories have been added. Googling "zteusbserial" suggests that it is for a serial modem. You would be best advised to uninstall it from Synaptic since it's causing problems and it doesn't sound as though you need it.

However...

> **raziyabhayani said:**
>  Yes I am on Jaunty 9.04 trying to install 10.10 is that possible? 

That's a good question and the answer is maybe. First, Jaunty is end-of-life and you need to look at this in order to get it up-to-date before upgrading to Karmic/9.10:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Even if you manage a successful upgrade to Karmic, you then have to upgrade Karmic > Lucid/10.04 and then Lucid/10.10 in order to get to 10.10. That's a lot of downloads and several hours. And there will be no guarantee that it will work at the end because you have at least two non-standard repositories - hence non-standard packages installed. These are the sort of things that cause package inconsistencies and upgrade failures.

It will take you about 30 minutes to install 10.10 fresh from a 10.10 live CD. You can run the CD live to ensure that your system is compatible with this version. That's what I would do in your situation.

Good luck with whatever you decide to do.

Oh, and a belated welcome to the forum!

---

### Post by raziyabhayani on 2011-04-11
Firstly, thanks a lot for your prompt reply, I really appreciate it alot. 

I cannot remove it using Synaptic Package Manager either, I tried that long back. It just doesn't get undone. 

Secondly, say if I do a fresh install from live CD for 10.10 what about my current data? It needs a backup? Or it stays good? 

Please keep advised, 

Thanks and regards.

---

### Post by mörgæs on 2011-04-11
Yes, you need to back up all your user files. More on this here:

[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by coffeecat on 2011-04-11
> **raziyabhayani said:**
> I cannot remove it using Synaptic Package Manager either, I tried that long back. It just doesn't get undone. 

It seems you are not alone. Do a google search with "site:ubuntuforums.org zteusbserial" (no quotes) and you'll see what I mean. I didn't see a definitive fix in any of those threads. Looks like a badly packaged app.

> **raziyabhayani said:**
> Secondly, say if I do a fresh install from live CD for 10.10 what about my current data? It needs a backup? Or it stays good? 

If you have a separate /home partition this *should* be untouched by the installer and your personal data and settings should be available in the fresh installation. Although, having said that, there may be stray zteusbserial configuration files in your home that would need cleaning out. But whether you have a separate /home or not you should backup your personal data anyway. There is always the (very) small risk of an installation going wrong leading to corruption of the hard drive.

Let's see what's on your hard drive now. Then we can advise best. The script I'm going to recommend you run is usually used for diagnosing boot problems, but since it provides all the information we need, it's convenient for this occasion. In Ubuntu, go to:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script according the instructions there. Post the contents of the RESULTS.txt file. Don't forget to enclose this between [noparse]```
 and 
```[/noparse] tags for clarity. You can use the # icon on the message toolbar for this.

---

### Post by raziyabhayani on 2011-04-11
Now, from your link for EOLUpgrade [https://help.ubuntu.com/community/EOLUpgrades/Jaunty](https://help.ubuntu.com/community/EOLUpgrades/Jaunty) I followed the steps. 

Heres the out put. What does it mean??? 


mobicents@mobicents-laptop:~$ sudo aptitude update && sudo aptitude safe-upgrade
[sudo] password for mobicents: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                                                      
Get:1 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty Release.gpg [189B]                                                                    
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/main Translation-en_IN                                                                   
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release.gpg                                                                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_IN                                                              
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/restricted Translation-en_IN                                                             
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Translation-en_IN                          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates Release.gpg                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_IN                
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release                                         
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/universe Translation-en_IN                       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main Translation-en_IN                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_IN                  
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages                                                                           
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/multiverse Translation-en_IN                                                             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/restricted Translation-en_IN                                                       
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages                                                                           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/universe Translation-en_IN                                                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_IN                                                        
Get:2 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-updates Release.gpg [198B]                                                             
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages                                                                           
  404 Not Found
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                                                                             
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-updates/main Translation-en_IN                   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_IN                                
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-updates/restricted Translation-en_IN                                                
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-updates/universe Translation-en_IN                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                                                                   
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-updates/multiverse Translation-en_IN                                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages                                                             
Get:3 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-security Release.gpg [198B]                                                        
Get:4 [http://dl.google.com](http://dl.google.com) testing Release.gpg [189B]                                                                          
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-security/main Translation-en_IN                                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                                                                    
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-security/restricted Translation-en_IN                                                
Ign [http://dl.google.com](http://dl.google.com) testing/non-free Translation-en_IN                                                                    
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-security/universe Translation-en_IN                                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources                                                              
Get:5 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                                                                           
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-security/multiverse Translation-en_IN                                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages                                                               
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_IN                                                                         
Get:6 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty Release [74.6kB]                                                                   
Get:7 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]                                                                                                  
Get:8 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-updates Release [57.9kB]                                                                             
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_IN                                                                                                                  
Get:9 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-security Release [57.9kB]                                                          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty Release.gpg                                                                                 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe Translation-en_IN                                                             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/multiverse Translation-en_IN                                                           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates Release                                                                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty Release                                                                                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main Packages                                                
Get:10 [http://dl.google.com](http://dl.google.com) testing Release [2513B]                                                                                                                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                                                                                                              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/restricted Packages                                                                                                          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main Sources                                                                                                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages                                                                                                           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/restricted Sources                                                                                                           
Get:11 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/main Packages [1253kB]                                                                                                          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/universe Packages                                                                                                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources                                                                                                            
Get:12 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/restricted Packages [8848B]                                                                                                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/universe Sources                                                                                                             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/multiverse Packages                                                                                                          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/multiverse Sources                                                                                                           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe Packages                                                                                                                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe Sources                                                                                                                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/multiverse Packages                                                                                                                  
Get:13 [http://dl.google.com](http://dl.google.com) stable Release [2544B]                                                                                                                           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/multiverse Sources                                                                                                                   
Get:14 [http://dl.google.com](http://dl.google.com) stable Release [1347B]                                                                                                                           
Get:15 [http://dl.google.com](http://dl.google.com) testing/non-free Packages [793B]                                                                                                                 
Get:16 [http://dl.google.com](http://dl.google.com) stable/main Packages [1082B]                                                                                                                     
Get:17 [http://dl.google.com](http://dl.google.com) stable/main Packages [737B]                                                                                                                      
Get:18 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/universe Packages [4757kB]                                                                                                      
Get:19 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/multiverse Packages [197kB]
Get:20 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-updates/main Packages [322kB]
Get:21 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-updates/restricted Packages [3789B]
Get:22 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-updates/universe Packages [153kB]                                                                                               
Get:23 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-updates/multiverse Packages [9952B]                                                                                             
Get:24 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-security/main Packages [242kB]                                                                                                  
Get:25 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-security/restricted Packages [2590B]                                                                                            
Get:26 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-security/universe Packages [121kB]                                                                                              
Get:27 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-security/multiverse Packages [4704B]                                                                                            
Fetched 7275kB in 27s (268kB/s)                                                                                                                                              
Reading package lists... Done

Current status: 4920 new [+501].
mobicents@mobicents-laptop:~$ sudo do-release-upgrade 
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading            
extracting 'karmic.tar.gz'
authenticate 'karmic.tar.gz' against 'karmic.tar.gz.gpg' 

Reading cache

Checking package manager
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
Done downloading            
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done

Updating repository information

Third party sources disabled 

Some third party entries in your sources.list were disabled. You can 
re-enable them after the upgrade with the 'software-properties' tool 
or your package manager. 

Done downloading            
Done downloading            
Done downloading            

Error during update 

A problem occurred during the update. This is usually some sort of 
network problem, please check your network connection and retry. 

W:Failed to fetch 
[http://in.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages) 
404 Not Found 
, E:Some index files failed to download, they have been ignored, or 
old ones used instead. 


Restoring original system state

Aborting
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done


Have I been upgraded or not yet??? 

Thanks. 

Awaiting reply.

---

### Post by coffeecat on 2011-04-11
I don't think you have been upgraded.

This:

> **raziyabhayani said:**
> W:Failed to fetch 
[http://in.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages) 
404 Not Found 
, E:Some index files failed to download, they have been ignored, or 
old ones used instead. 

The url is malformed. That should be either Packages.gz or Packages.bz2 at the end, not Packages. Why the package manager is doing that, I don't know.

Let me honest - I've been using Ubuntu since 2005 and I would not choose to upgrade what you have. You have non-standard and now non-existent repositories giving you 404s. I would find it a nightmare even if I had physical access to the machine.

---

### Post by mikewhatever on 2011-04-11
I also think it would be best to reinstall, especially since the current installation is originally not yours. Not to mention that Jaunty will only get upgraded to Karmic, which only has a few more weeks of support left.

---

### Post by Enigmapond on 2011-04-11
I agree. You should stop trying to do what you are doing, as it will give you an ulcer.. :) Just do a fresh install of 10.10 and all your issues will solve in approx 30mins. Good Luck. Also please, in the future. If you have a lot of data in the post please put it between the "code" bbcode...

```
like this...thank you
```

Cheers!

---

### Post by raziyabhayani on 2011-04-12
No changes occurred. So gave it a try again to encounter a bug. 

mobicents@mobicents-laptop:~$ sudo aptitude update && sudo aptitude safe-upgrade
[sudo] password for mobicents: 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates Release.gpg
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty Release.gpg                                                                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                                                                        
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main Translation-en_IN                                                            
Get:1 [http://dl.google.com](http://dl.google.com) testing Release.gpg [189B]                                                                              
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/restricted Translation-en_IN                                                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_IN                                                              
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release.gpg                                                                             
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/main Translation-en_IN                                                                   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/universe Translation-en_IN                                                         
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Translation-en_IN                                                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_IN                                                        
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/restricted Translation-en_IN                                                             
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release                                                                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_IN                                                          
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/universe Translation-en_IN                                                               
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_IN                                                       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty Release.gpg                                                                                
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages                                                                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_IN                                                        
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/multiverse Translation-en_IN                                                             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe Translation-en_IN                                                                 
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages                                                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                                                                             
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-updates Release.gpg                              
Ign [http://dl.google.com](http://dl.google.com) testing/non-free Translation-en_IN                                                     
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages                                   
  404 Not Found
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-updates/main Translation-en_IN                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                                                 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/multiverse Translation-en_IN                                         
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-updates/restricted Translation-en_IN                               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates Release                                                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty Release                                                                 
Get:2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                                                                              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main Packages                                                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/restricted Packages                                          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main Sources                                                 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/restricted Sources                                           
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-updates/universe Translation-en_IN                                 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/universe Packages                                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages                                           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/universe Sources                                             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/multiverse Packages                                          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/multiverse Sources                                           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe Packages                                                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe Sources                                                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/multiverse Packages                                                  
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-updates/multiverse Translation-en_IN                               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/multiverse Sources                                                   
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_IN                                                       
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-security Release.gpg       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                            
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-security/main Translation-en_IN              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources                      
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-security/restricted Translation-en_IN        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages                       
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-security/universe Translation-en_IN          
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-security/multiverse Translation-en_IN        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                        
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty Release                                      
Get:3 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages   
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-updates Release                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources                                           
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-security Release           
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/main Packages             
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/restricted Packages    
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/universe Packages      
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty/multiverse Packages    
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-updates/main Packages  
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-updates/restricted Packages
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_IN           
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-updates/universe Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-security/main Packages                                                                                                             
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-security/restricted Packages                                                                                                       
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-security/universe Packages                                                                                                         
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) jaunty-security/multiverse Packages                                                                                                       
Get:4 [http://dl.google.com](http://dl.google.com) testing Release [2513B]                                                                                                                           
Get:5 [http://dl.google.com](http://dl.google.com) stable Release [2544B]                                                                                                                            
Get:6 [http://dl.google.com](http://dl.google.com) stable Release [1347B]                                                                                                                            
Get:7 [http://dl.google.com](http://dl.google.com) testing/non-free Packages [793B]                                                                                                                  
Get:8 [http://dl.google.com](http://dl.google.com) stable/main Packages [1082B]                                                                                                                      
Get:9 [http://dl.google.com](http://dl.google.com) stable/main Packages [737B]                                                                                                                       
Fetched 9591B in 16s (597B/s)                                                                                                                                                
Reading package lists... Done

mobicents@mobicents-laptop:~$ sudo do-release-upgrade
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading            
extracting 'karmic.tar.gz'
authenticate 'karmic.tar.gz' against 'karmic.tar.gz.gpg' 

Reading cache

Checking package manager
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
Done downloading            
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done

Updating repository information

Third party sources disabled 

Some third party entries in your sources.list were disabled. You can 
re-enable them after the upgrade with the 'software-properties' tool 
or your package manager. 

Done downloading            

Checking package manager
Reading package lists: Donekarmic-security/multiverse Packages: 94   
Reading state information: Done
Reading state information: Done
Reading state information: Done

Invalid package information 

After your package information was updated the essential package 
'ubuntu-minimal' can not be found anymore. 
This indicates a serious error, please report this bug against the 
'update-manager' package and include the files in 
/var/log/dist-upgrade/ in the bug report. 


Restoring original system state

Aborting
Reading package lists: Done/main Packages: 97   97  : 97  ages: 97   4  
Reading state information: Done
Reading state information: Done
Reading state information: Done
mobicents@mobicents-laptop:~$

Reporting it to the team using "ubuntu-bug". 

In meanwhile can you guys suggest anything? 

Thanks and regards. 
Raziya

---

### Post by raziyabhayani on 2011-04-12
Thanks a lot for all your replies. I will do a fresh install then. One last question I have heard 10.10 has lot of issues in current stage and 10.04 is more stable. Any suggestions as to which one I can stick on? 

Thanks and regards. 
Raziya

---

### Post by mikewhatever on 2011-04-12
The rumor you've heard is not true. Both 10.04 and 10.10 are very stable, so that, in that sense, it doesn't matter what you choose.

---

