---
title: "LOCAL REPOSITORY.......Problem!!!"
date: 2007-08-09
forum: Installation &amp; Upgrades
---

### Post by darkmediator on 2007-08-09
Hi,

I successfully setted up local repository for Ubuntu. I followed this tute.
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Personal_Apt_Repository](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Personal_Apt_Repository)

But it seems to be facing only one problem. Here's the output first.


> 

WARNING: The following packages cannot be authenticated!
  python2.5 python2.5-minimal python python-minimal language-pack-en
  openoffice.org-style-human openoffice.org-calc python-uno
  openoffice.org-writer openoffice.org-impress openoffice.org-draw
  openoffice.org-filter-mobiledev openoffice.org-java-common
  openoffice.org-base libdbus-1-3 openoffice.org-gtk openoffice.org-gnome
  openoffice.org-evolution openoffice.org-math openoffice.org ttf-opensymbol
  libkrb53 libcurl3 libfreetype6 openoffice.org-core openoffice.org-common
  tzdata gpgv iptables vim-tiny vim-common libisc11 libdns22 libisccc0
  libisccfg1 libbind9-0 liblwres9 dnsutils file libmagic1 app-install-data
  app-install-data-commercial python-problem-report python-apport apport
  apport-gtk capplets-data dbus libedataserver1.2-9 libnspr4 libnss3
  libcamel1.2-10 libebook1.2-9 libecal1.2-7 libedata-book1.2-2
  libedata-cal1.2-6 libegroupwise1.2-13 evolution-data-server
  evolution-data-server-common firefox-gnome-support firefox gimp gimp-data
  libexif12 libgimp2.0 libpng12-0 gimp-python python-gdbm gnome-app-install
  gnome-btdownload libhal1 metacity-common libmetacity0 libpanel-applet2-0
  libslab0 gnome-control-center libgnome-window-settings1
  libedataserverui1.2-8 gnome-panel gnome-panel-data hwdb-client-common
  hwdb-client-gnome hal-device-manager lftp libexchange-storage1.2-3
  libhal-storage1 libmagick9 libsmbclient linux-generic
  linux-restricted-modules-common mesa-utils metacity ndiswrapper-common
  rdesktop smbclient samba-common tcpdump unattended-upgrades
  update-manager-core update-manager xscreensaver-data xscreensaver-gl
Install these packages without verification [y/N]? y
Get:1 [http://192.168.0.100](http://192.168.0.100) binary/ python2.5 2.5.1-0ubuntu1 [3088kB]
Get:2 [http://192.168.0.100](http://192.168.0.100) binary/ python2.5-minimal 2.5.1-0ubuntu1 [1168kB]
Get:3 [http://192.168.0.100](http://192.168.0.100) binary/ python 2.5.1-0ubuntu3 [141kB]
Get:4 [http://192.168.0.100](http://192.168.0.100) binary/ python-minimal 2.5.1-0ubuntu3 [13.6kB]
Err [http://192.168.0.100](http://192.168.0.100) binary/ language-pack-en 1:7.04+20070601
  404 Not Found
Get:5 [http://192.168.0.100](http://192.168.0.100) binary/ openoffice.org-style-human 2.2.0-1ubuntu4 [4483kB]
Get:6 [http://192.168.0.100](http://192.168.0.100) binary/ openoffice.org-calc 2.2.0-1ubuntu4 [5061kB]    
Get:7 [http://192.168.0.100](http://192.168.0.100) binary/ python-uno 2.2.0-1ubuntu4 [120kB]              
Get:8 [http://192.168.0.100](http://192.168.0.100) binary/ openoffice.org-writer 2.2.0-1ubuntu4 [5714kB]  
Get:9 [http://192.168.0.100](http://192.168.0.100) binary/ openoffice.org-impress 2.2.0-1ubuntu4 [653kB]  
Get:10 [http://192.168.0.100](http://192.168.0.100) binary/ openoffice.org-draw 2.2.0-1ubuntu4 [2312kB]   
Get:11 [http://192.168.0.100](http://192.168.0.100) binary/ openoffice.org-filter-mobiledev 2.2.0-1ubuntu4 [96.1kB]
Get:12 [http://192.168.0.100](http://192.168.0.100) binary/ openoffice.org-java-common 2.2.0-1ubuntu4 [2811kB]
Get:13 [http://192.168.0.100](http://192.168.0.100) binary/ openoffice.org-base 2.2.0-1ubuntu4 [3496kB]   
Get:14 [http://192.168.0.100](http://192.168.0.100) binary/ libdbus-1-3 1.0.2-1ubuntu4 [269kB]            
Get:15 [http://192.168.0.100](http://192.168.0.100) binary/ openoffice.org-gtk 2.2.0-1ubuntu4 [214kB]     
Get:16 [http://192.168.0.100](http://192.168.0.100) binary/ openoffice.org-gnome 2.2.0-1ubuntu4 [56.5kB]  
Get:17 [http://192.168.0.100](http://192.168.0.100) binary/ openoffice.org-evolution 2.2.0-1ubuntu4 [87.7kB]
Get:18 [http://192.168.0.100](http://192.168.0.100) binary/ openoffice.org-math 2.2.0-1ubuntu4 [299kB]    
Get:19 [http://192.168.0.100](http://192.168.0.100) binary/ openoffice.org 2.2.0-1ubuntu4 [3092B]         
Get:20 [http://192.168.0.100](http://192.168.0.100) binary/ ttf-opensymbol 2.2.0-1ubuntu4 [182kB]         
Get:21 [http://192.168.0.100](http://192.168.0.100) binary/ libkrb53 1.4.4-5ubuntu3.1 [412kB]             
Get:22 [http://192.168.0.100](http://192.168.0.100) binary/ libcurl3 7.15.5-1ubuntu2.1 [169kB]            
Get:23 [http://192.168.0.100](http://192.168.0.100) binary/ libfreetype6 2.2.1-5ubuntu1.1 [344kB]         
Get:24 [http://192.168.0.100](http://192.168.0.100) binary/ openoffice.org-core 2.2.0-1ubuntu4 [35.5MB]   
Get:25 [http://192.168.0.100](http://192.168.0.100) binary/ openoffice.org-common 2.2.0-1ubuntu4 [12.0MB] 
Get:26 [http://192.168.0.100](http://192.168.0.100) binary/ tzdata 2007f-0ubuntu0.7.4 [313kB]             
Get:27 [http://192.168.0.100](http://192.168.0.100) binary/ gpgv 1.4.6-2ubuntu3~feisty1 [146kB]           
Get:28 [http://192.168.0.100](http://192.168.0.100) binary/ iptables 1.3.6.0debian1-5ubuntu2.1 [374kB]    
Err [http://192.168.0.100](http://192.168.0.100) binary/ vim-tiny 1:7.0-164+1ubuntu7.1                    
  404 Not Found
Err [http://192.168.0.100](http://192.168.0.100) binary/ vim-common 1:7.0-164+1ubuntu7.1                  
  404 Not Found
Err [http://192.168.0.100](http://192.168.0.100) binary/ libisc11 1:9.3.4-2ubuntu2.1                      
  404 Not Found
Err [http://192.168.0.100](http://192.168.0.100) binary/ libdns22 1:9.3.4-2ubuntu2.1                      
  404 Not Found
Err [http://192.168.0.100](http://192.168.0.100) binary/ libisccc0 1:9.3.4-2ubuntu2.1                     
  404 Not Found
Err [http://192.168.0.100](http://192.168.0.100) binary/ libisccfg1 1:9.3.4-2ubuntu2.1                    
  404 Not Found
Err [http://192.168.0.100](http://192.168.0.100) binary/ libbind9-0 1:9.3.4-2ubuntu2.1                    
  404 Not Found
Err [http://192.168.0.100](http://192.168.0.100) binary/ liblwres9 1:9.3.4-2ubuntu2.1                     
  404 Not Found
Err [http://192.168.0.100](http://192.168.0.100) binary/ dnsutils 1:9.3.4-2ubuntu2.1                      
  404 Not Found
Get:29 [http://192.168.0.100](http://192.168.0.100) binary/ file 4.19-1ubuntu2.1 [33.0kB]                 
Get:30 [http://192.168.0.100](http://192.168.0.100) binary/ libmagic1 4.19-1ubuntu2.1 [313kB]             
Get:31 [http://192.168.0.100](http://192.168.0.100) binary/ app-install-data 0.3.31 [4539kB]              
Get:32 [http://192.168.0.100](http://192.168.0.100) binary/ app-install-data-commercial 7.2 [31.1kB]      
Get:33 [http://192.168.0.100](http://192.168.0.100) binary/ python-problem-report 0.76.1 [38.7kB]         
Get:34 [http://192.168.0.100](http://192.168.0.100) binary/ python-apport 0.76.1 [65.5kB]                 
Get:35 [http://192.168.0.100](http://192.168.0.100) binary/ apport 0.76.1 [54.6kB]                        
Get:36 [http://192.168.0.100](http://192.168.0.100) binary/ apport-gtk 0.76.1 [37.4kB]                    
Err [http://192.168.0.100](http://192.168.0.100) binary/ capplets-data 1:2.18.1-0ubuntu2.1                
  404 Not Found
Get:37 [http://192.168.0.100](http://192.168.0.100) binary/ dbus 1.0.2-1ubuntu4 [351kB]                   
Get:38 [http://192.168.0.100](http://192.168.0.100) binary/ libedataserver1.2-9 1.10.1-0ubuntu1.1 [125kB] 
Err [http://192.168.0.100](http://192.168.0.100) binary/ libnspr4 2:1.firefox2.0.0.5+1-0ubuntu1           
  404 Not Found
Err [http://192.168.0.100](http://192.168.0.100) binary/ libnss3 2:1.firefox2.0.0.5+1-0ubuntu1            
  404 Not Found
Get:39 [http://192.168.0.100](http://192.168.0.100) binary/ libcamel1.2-10 1.10.1-0ubuntu1.1 [339kB]      
Get:40 [http://192.168.0.100](http://192.168.0.100) binary/ libebook1.2-9 1.10.1-0ubuntu1.1 [136kB]       
Get:41 [http://192.168.0.100](http://192.168.0.100) binary/ libecal1.2-7 1.10.1-0ubuntu1.1 [307kB]        
Get:42 [http://192.168.0.100](http://192.168.0.100) binary/ libedata-book1.2-2 1.10.1-0ubuntu1.1 [101kB]  
Get:43 [http://192.168.0.100](http://192.168.0.100) binary/ libedata-cal1.2-6 1.10.1-0ubuntu1.1 [111kB]   
Get:44 [http://192.168.0.100](http://192.168.0.100) binary/ libegroupwise1.2-13 1.10.1-0ubuntu1.1 [114kB] 
Get:45 [http://192.168.0.100](http://192.168.0.100) binary/ evolution-data-server 1.10.1-0ubuntu1.1 [451kB]
Get:46 [http://192.168.0.100](http://192.168.0.100) binary/ evolution-data-server-common 1.10.1-0ubuntu1.1 [116kB]
Get:47 [http://192.168.0.100](http://192.168.0.100) binary/ firefox-gnome-support 2.0.0.5+1-0ubuntu1 [86.2kB]
Get:48 [http://192.168.0.100](http://192.168.0.100) binary/ firefox 2.0.0.5+1-0ubuntu1 [9262kB]           
Get:49 [http://192.168.0.100](http://192.168.0.100) binary/ gimp 2.2.13-1ubuntu4.2 [2969kB]               
Get:50 [http://192.168.0.100](http://192.168.0.100) binary/ gimp-data 2.2.13-1ubuntu4.2 [2105kB]          
Get:51 [http://192.168.0.100](http://192.168.0.100) binary/ libexif12 0.6.13-5ubuntu0.2 [67.2kB]          
Get:52 [http://192.168.0.100](http://192.168.0.100) binary/ libgimp2.0 2.2.13-1ubuntu4.2 [441kB]          
Get:53 [http://192.168.0.100](http://192.168.0.100) binary/ libpng12-0 1.2.15~beta5-1ubuntu1 [187kB]      
Get:54 [http://192.168.0.100](http://192.168.0.100) binary/ gimp-python 2.2.13-1ubuntu4.2 [140kB]         
Get:55 [http://192.168.0.100](http://192.168.0.100) binary/ python-gdbm 2.5.1-0ubuntu1 [14.2kB]           
Get:56 [http://192.168.0.100](http://192.168.0.100) binary/ gnome-app-install 0.3.31 [535kB]              
Get:57 [http://192.168.0.100](http://192.168.0.100) binary/ gnome-btdownload 0.0.28-1~feisty1 [35.8kB]    
Get:58 [http://192.168.0.100](http://192.168.0.100) binary/ libhal1 0.5.9-1ubuntu2~feisty1 [362kB]        
Err [http://192.168.0.100](http://192.168.0.100) binary/ metacity-common 1:2.18.2-0ubuntu1.1              
  404 Not Found
Err [http://192.168.0.100](http://192.168.0.100) binary/ libmetacity0 1:2.18.2-0ubuntu1.1                 
  404 Not Found
Err [http://192.168.0.100](http://192.168.0.100) binary/ libpanel-applet2-0 1:2.18.1-0ubuntu3.1           
  404 Not Found
Err [http://192.168.0.100](http://192.168.0.100) binary/ libslab0 1:2.18.1-0ubuntu2.1                     
  404 Not Found
Err [http://192.168.0.100](http://192.168.0.100) binary/ gnome-control-center 1:2.18.1-0ubuntu2.1         
  404 Not Found
Err [http://192.168.0.100](http://192.168.0.100) binary/ libgnome-window-settings1 1:2.18.1-0ubuntu2.1    
  404 Not Found
Get:59 [http://192.168.0.100](http://192.168.0.100) binary/ libedataserverui1.2-8 1.10.1-0ubuntu1.1 [124kB]
Err [http://192.168.0.100](http://192.168.0.100) binary/ gnome-panel 1:2.18.1-0ubuntu3.1                  
  404 Not Found
Err [http://192.168.0.100](http://192.168.0.100) binary/ gnome-panel-data 1:2.18.1-0ubuntu3.1             
  404 Not Found
Get:60 [http://192.168.0.100](http://192.168.0.100) binary/ hwdb-client-common 0.6.10.1 [86.1kB]          
Get:61 [http://192.168.0.100](http://192.168.0.100) binary/ hwdb-client-gnome 0.6.10.1 [1196kB]           
Get:62 [http://192.168.0.100](http://192.168.0.100) binary/ hal-device-manager 0.5.9-1ubuntu2~feisty1 [403kB]
Get:63 [http://192.168.0.100](http://192.168.0.100) binary/ lftp 3.5.11-1~feisty1 [535kB]                 
Get:64 [http://192.168.0.100](http://192.168.0.100) binary/ libexchange-storage1.2-3 1.10.1-0ubuntu1.1 [178kB]
Get:65 [http://192.168.0.100](http://192.168.0.100) binary/ libhal-storage1 0.5.9-1ubuntu2~feisty1 [360kB]
Err [http://192.168.0.100](http://192.168.0.100) binary/ libmagick9 7:6.2.4.5.dfsg1-0.14ubuntu0.1         
  404 Not Found
Get:66 [http://192.168.0.100](http://192.168.0.100) binary/ libsmbclient 3.0.24-2ubuntu1.2 [794kB]        
Get:67 [http://192.168.0.100](http://192.168.0.100) binary/ linux-generic 2.6.20.16.28.1 [24.5kB]         
Get:68 [http://192.168.0.100](http://192.168.0.100) binary/ linux-restricted-modules-common 2.6.20.5-16.29 [21.6kB]
Get:69 [http://192.168.0.100](http://192.168.0.100) binary/ mesa-utils 6.5.2-3ubuntu8 [45.0kB]            
Err [http://192.168.0.100](http://192.168.0.100) binary/ metacity 1:2.18.2-0ubuntu1.1                     
  404 Not Found
Get:70 [http://192.168.0.100](http://192.168.0.100) binary/ ndiswrapper-common 1.43-1ubuntu1 [19.1kB]     
Get:71 [http://192.168.0.100](http://192.168.0.100) binary/ rdesktop 1.5.0-1ubuntu1 [122kB]               
Get:72 [http://192.168.0.100](http://192.168.0.100) binary/ smbclient 3.0.24-2ubuntu1.2 [4016kB]          
Get:73 [http://192.168.0.100](http://192.168.0.100) binary/ samba-common 3.0.24-2ubuntu1.2 [2437kB]       
Get:74 [http://192.168.0.100](http://192.168.0.100) binary/ tcpdump 3.9.5-2ubuntu1 [303kB]                
Get:75 [http://192.168.0.100](http://192.168.0.100) binary/ unattended-upgrades 0.23ubuntu3 [6624B]       
Err [http://192.168.0.100](http://192.168.0.100) binary/ update-manager-core 1:0.59.23                    
  404 Not Found
Err [http://192.168.0.100](http://192.168.0.100) binary/ update-manager 1:0.59.23                         
  404 Not Found
Get:76 [http://192.168.0.100](http://192.168.0.100) binary/ xscreensaver-data 4.24-5ubuntu2.1 [398kB]     
Get:77 [http://192.168.0.100](http://192.168.0.100) binary/ xscreensaver-gl 4.24-5ubuntu2.1 [1637kB]      
Fetched 116MB in 2m7s (905kB/s)                                                
Failed to fetch [http://192.168.0.100/apt/binary/language-pack-en_1%3a7.04+20070601_all.deb](http://192.168.0.100/apt/binary/language-pack-en_1%3a7.04+20070601_all.deb)  404 Not Found
Failed to fetch [http://192.168.0.100/apt/binary/vim-tiny_1%3a7.0-164+1ubuntu7.1_i386.deb](http://192.168.0.100/apt/binary/vim-tiny_1%3a7.0-164+1ubuntu7.1_i386.deb)  404 Not Found
Failed to fetch [http://192.168.0.100/apt/binary/vim-common_1%3a7.0-164+1ubuntu7.1_i386.deb](http://192.168.0.100/apt/binary/vim-common_1%3a7.0-164+1ubuntu7.1_i386.deb)  404 Not Found
Failed to fetch [http://192.168.0.100/apt/binary/libisc11_1%3a9.3.4-2ubuntu2.1_i386.deb](http://192.168.0.100/apt/binary/libisc11_1%3a9.3.4-2ubuntu2.1_i386.deb)  404 Not Found
Failed to fetch [http://192.168.0.100/apt/binary/libdns22_1%3a9.3.4-2ubuntu2.1_i386.deb](http://192.168.0.100/apt/binary/libdns22_1%3a9.3.4-2ubuntu2.1_i386.deb)  404 Not Found
Failed to fetch [http://192.168.0.100/apt/binary/libisccc0_1%3a9.3.4-2ubuntu2.1_i386.deb](http://192.168.0.100/apt/binary/libisccc0_1%3a9.3.4-2ubuntu2.1_i386.deb)  404 Not Found
Failed to fetch [http://192.168.0.100/apt/binary/libisccfg1_1%3a9.3.4-2ubuntu2.1_i386.deb](http://192.168.0.100/apt/binary/libisccfg1_1%3a9.3.4-2ubuntu2.1_i386.deb)  404 Not Found
Failed to fetch [http://192.168.0.100/apt/binary/libbind9-0_1%3a9.3.4-2ubuntu2.1_i386.deb](http://192.168.0.100/apt/binary/libbind9-0_1%3a9.3.4-2ubuntu2.1_i386.deb)  404 Not Found
Failed to fetch [http://192.168.0.100/apt/binary/liblwres9_1%3a9.3.4-2ubuntu2.1_i386.deb](http://192.168.0.100/apt/binary/liblwres9_1%3a9.3.4-2ubuntu2.1_i386.deb)  404 Not Found
Failed to fetch [http://192.168.0.100/apt/binary/dnsutils_1%3a9.3.4-2ubuntu2.1_i386.deb](http://192.168.0.100/apt/binary/dnsutils_1%3a9.3.4-2ubuntu2.1_i386.deb)  404 Not Found
Failed to fetch [http://192.168.0.100/apt/binary/capplets-data_1%3a2.18.1-0ubuntu2.1_all.deb](http://192.168.0.100/apt/binary/capplets-data_1%3a2.18.1-0ubuntu2.1_all.deb)  404 Not Found
Failed to fetch [http://192.168.0.100/apt/binary/libnspr4_2%3a1.firefox2.0.0.5+1-0ubuntu1_i386.deb](http://192.168.0.100/apt/binary/libnspr4_2%3a1.firefox2.0.0.5+1-0ubuntu1_i386.deb)  404 Not Found
Failed to fetch [http://192.168.0.100/apt/binary/libnss3_2%3a1.firefox2.0.0.5+1-0ubuntu1_i386.deb](http://192.168.0.100/apt/binary/libnss3_2%3a1.firefox2.0.0.5+1-0ubuntu1_i386.deb)  404 Not Found
Failed to fetch [http://192.168.0.100/apt/binary/metacity-common_1%3a2.18.2-0ubuntu1.1_all.deb](http://192.168.0.100/apt/binary/metacity-common_1%3a2.18.2-0ubuntu1.1_all.deb)  404 Not Found
Failed to fetch [http://192.168.0.100/apt/binary/libmetacity0_1%3a2.18.2-0ubuntu1.1_i386.deb](http://192.168.0.100/apt/binary/libmetacity0_1%3a2.18.2-0ubuntu1.1_i386.deb)  404 Not Found
Failed to fetch [http://192.168.0.100/apt/binary/libpanel-applet2-0_1%3a2.18.1-0ubuntu3.1_i386.deb](http://192.168.0.100/apt/binary/libpanel-applet2-0_1%3a2.18.1-0ubuntu3.1_i386.deb)  404 Not Found
Failed to fetch [http://192.168.0.100/apt/binary/libslab0_1%3a2.18.1-0ubuntu2.1_i386.deb](http://192.168.0.100/apt/binary/libslab0_1%3a2.18.1-0ubuntu2.1_i386.deb)  404 Not Found
Failed to fetch [http://192.168.0.100/apt/binary/gnome-control-center_1%3a2.18.1-0ubuntu2.1_i386.deb](http://192.168.0.100/apt/binary/gnome-control-center_1%3a2.18.1-0ubuntu2.1_i386.deb)  404 Not Found
Failed to fetch [http://192.168.0.100/apt/binary/libgnome-window-settings1_1%3a2.18.1-0ubuntu2.1_i386.deb](http://192.168.0.100/apt/binary/libgnome-window-settings1_1%3a2.18.1-0ubuntu2.1_i386.deb)  404 Not Found
Failed to fetch [http://192.168.0.100/apt/binary/gnome-panel_1%3a2.18.1-0ubuntu3.1_i386.deb](http://192.168.0.100/apt/binary/gnome-panel_1%3a2.18.1-0ubuntu3.1_i386.deb)  404 Not Found
Failed to fetch [http://192.168.0.100/apt/binary/gnome-panel-data_1%3a2.18.1-0ubuntu3.1_all.deb](http://192.168.0.100/apt/binary/gnome-panel-data_1%3a2.18.1-0ubuntu3.1_all.deb)  404 Not Found
Failed to fetch [http://192.168.0.100/apt/binary/libmagick9_7%3a6.2.4.5.dfsg1-0.14ubuntu0.1_i386.deb](http://192.168.0.100/apt/binary/libmagick9_7%3a6.2.4.5.dfsg1-0.14ubuntu0.1_i386.deb)  404 Not Found
Failed to fetch [http://192.168.0.100/apt/binary/metacity_1%3a2.18.2-0ubuntu1.1_i386.deb](http://192.168.0.100/apt/binary/metacity_1%3a2.18.2-0ubuntu1.1_i386.deb)  404 Not Found
Failed to fetch [http://192.168.0.100/apt/binary/update-manager-core_1%3a0.59.23_i386.deb](http://192.168.0.100/apt/binary/update-manager-core_1%3a0.59.23_i386.deb)  404 Not Found
Failed to fetch [http://192.168.0.100/apt/binary/update-manager_1%3a0.59.23_all.deb](http://192.168.0.100/apt/binary/update-manager_1%3a0.59.23_all.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?






As you can see there are a lot of lines saying "Failed to fetch" while retrieving other packages perfectly. All these packages are the ones that were copied from cache to a local folder!! They all exist there in local folder.

Why is it not retrieving them? Also I noticed that the one who cannot be fetched have some % sign in it like "update-manager_**1%3a0**.59.23_all.deb". Whats the solution? Is it some apache problem? If so, then how to rectify it?

---

### Post by merlinus on 2007-08-09
404 not found means the file could not be located on the server.  Also, sometimes various servers are offline.

It also seemsyou may have repos that are not on the ubuntu trusted sources list.

You might try the following, in a terminal, to update /etc/apt/sources.list:

```

sudo aptitude update

```-merlin

---

### Post by darkmediator on 2007-08-10
No the server is not offline. Please read the output. The packages are there, but those which r not downoadable having some % sign on it.

On checking again, it seems that the copy of the output in my post above is having correct name of the packages. But it is having % sign in some packagesi n the repository! What is this problem?

---

