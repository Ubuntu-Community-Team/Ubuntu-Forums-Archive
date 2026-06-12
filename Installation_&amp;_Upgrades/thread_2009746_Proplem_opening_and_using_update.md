---
title: "Proplem opening and using update"
date: 2012-06-24
forum: Installation &amp; Upgrades
---

### Post by killertm on 2012-06-24
This seems pretty over used but I am new to linux and dont know much about it but I'm having problems with update. I can open it and it starts to load then just shuts down on me every time and when I read a few posts I tried using terminal but I got this error: danny@dannyX41:~$ sudo apt-get update
[sudo] password for danny: 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease 
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg [198 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release [49.6 kB]                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release [49.6 kB]         
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]           
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources [934 kB]              
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [20.6 kB]      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [14 B]   
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [7,120 B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [713 B]  
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [65.9 kB]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [14 B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [17.4 kB]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [1,394 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources [5,470 B]       
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources [5,019 kB]        
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources [155 kB]        
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages [1,274 kB]      
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages [8,431 B] 
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages [4,796 kB]  
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [115 kB]      
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [1,379 B]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [27.7 kB] 
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [1,058 B]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [294 kB]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [2,439 B]
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [80.5 kB]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [2,049 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources [1,346 B]   
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources [14 B]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources [6,873 B]
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources [1,383 B]
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages [929 B]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages [6,117 B]
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages [999 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en     
Fetched 13.2 MB in 50s (259 kB/s)                                              
Reading package lists... Error!
E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.



honestly I have no idea what any of this means but would like to learn how to do this and fix any future problems

---

### Post by dgharmon on 2012-06-24
> **killertm said:**
> E: Read error - read (5: Input/output error) E: The package lists or status file could not be parsed or opened.

Sounds like a bad harddrive. Boot from the CD and run fsck -cfk /dev/hdx where hdx is the partition name of your system. Boot from CD, open a console and type the following, the bits after the # are comments.

$sudo -i # need to be root
$fdisk -l  # lists harddrives and partition numbers
$fsck -cfk /dev/hdx # check harddrive for badblocks

---

### Post by killertm on 2012-06-25
I'm posting this before trying your suggestion but I tried another find and it got me a little farther and now im receiving this
```
danny@dannyX41:~$ sudo apt-get update
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Reading package lists... Done
danny@dannyX41:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libts-0.0-0 libwildmidi1 libflite1 vorbis-tools libwildmidi-config
  libopenspc0 iw anjuta-common libfftw3-3 libgpod4 libenca0 libzvbi-common
  libspandsp2 libgpod-common libdvdread4 libcdaudio1 libopenal-data libcelt0-0
  libdirac-encoder0 libgdl-3-2 liba52-0.7.4 libgdl-3-common tsconf
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  acl adduser apport apt-utils aptdaemon at avahi-daemon base-files
  base-passwd bash bash-completion bind9-host bsdmainutils busybox-initramfs
  busybox-static ca-certificates console-setup consolekit cpio cpp cron
  cryptsetup cryptsetup-bin cups cups-common cups-filters dbus dbus-x11
  dconf-gsettings-backend dconf-service dictionaries-common dmsetup dosfstools
  dpkg e2fslibs e2fsprogs ecryptfs-utils ed eject enchant exo-utils file
  findutils firefox firefox-globalmenu firefox-locale-en fontconfig-config
  foomatic-db-compressed-ppds foomatic-db-engine foomatic-filters ftp fuse
  gcc-4.6-base gconf-service gconf-service-backend gconf2 gconf2-common
  genisoimage ghostscript ghostscript-cups gimp-data gir1.2-atk-1.0
  gir1.2-dbusmenu-glib-0.4 gir1.2-freedesktop gir1.2-gdkpixbuf-2.0
  gir1.2-glib-2.0 gir1.2-gtk-2.0 gir1.2-gtk-3.0 gir1.2-javascriptcoregtk-3.0
  gir1.2-pango-1.0 gir1.2-vte-2.90 gir1.2-webkit-3.0 glib-networking-common
  glib-networking-services gnome-icon-theme gnome-keyring gnome-system-tools
  gnupg groff-base gs-cjk-resource gsettings-desktop-schemas gsfonts
  gstreamer0.10-plugins-base gstreamer0.10-plugins-good
  gstreamer0.10-pulseaudio gstreamer0.10-tools gstreamer0.10-x
  gtk3-engines-unico gvfs gvfs-common gvfs-daemons gvfs-libs hdparm
  humanity-icon-theme im-switch indicator-messages indicator-sound
  indicator-status-provider-mc5 info initramfs-tools-bin initscripts insserv
  iproute iptables iso-codes kbd keyboard-configuration keyutils klibc-utils
  krb5-locales language-pack-en-base language-pack-gnome-en
  language-selector-common launchpad-integration libaa1 libaccountsservice0
  libacl1 libao-common libao4 libapt-inst1.4 libapt-pkg4.12 libasn1-8-heimdal
  libasound2 libasound2-plugins libasyncns0 libatasmart4 libatk1.0-0
  libatk1.0-data libatm1 libattr1 libavahi-client3 libavahi-common-data
  libavahi-common3 libavahi-core7 libavcodec53 libavutil51 libbabl-0.0-0
  libblkid1 libbluetooth3 libburn4 libbz2-1.0 libc-bin libc-dev-bin libc6
  libcaca0 libcairo-gobject2 libcairo-perl libcanberra0 libcap-ng0 libcap2
  libcap2-bin libcdparanoia0 libck-connector0 libclass-isa-perl libcolord1
  libcomerr2 libcroco3 libcryptsetup4 libcups2 libcupscgi1 libcupsfilters1
  libcupsimage2 libcupsmime1 libcupsppdc1 libdaemon0 libdatrie1 libdb5.1
  libdbusmenu-gtk3-4 libdbusmenu-gtk4 libdee-1.0-4 libdevmapper-event1.02.1
  libdevmapper1.02.1 libdns81 libdrm-intel1 libdrm-radeon1 libdv4 libecryptfs0
  libenchant1c2a libencode-locale-perl libexo-1-0 libexo-common libexpat1
  libfaac0 libfaad2 libfile-copy-recursive-perl libfile-listing-perl
  libfont-afm-perl libfontenc1 libfribidi0 libfs6 libgail-3-0 libgail18
  libgarcon-1-0 libgarcon-common libgcc1 libgck-1-0 libgdk-pixbuf2.0-common
  libgdl-3-common libgdome2-0 libgdu0 libgee2 libgeoclue0 libgimp2.0
  libgirepository-1.0-1 libgl1-mesa-glx libglapi-mesa libglib-perl
  libglib2.0-0 libglib2.0-bin libglu1-mesa libgmp10 libgnome-keyring-common
  libgnome-keyring0 libgnomevfs2-0 libgnomevfs2-common libgnutls26
  libgphoto2-2 libgphoto2-l10n libgphoto2-port0 libgpm2 libgs9 libgs9-common
  libgssapi3-heimdal libgstreamer-plugins-base0.10-0 libgstreamer0.10-0
  libgtk-3-0 libgtk-3-bin libgtk-3-common libgtk2-perl libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libgupnp-1.0-4 libgutenprint2
  libhcrypto4-heimdal libheimbase1-heimdal libheimntlm0-heimdal libhpmud0
  libhtml-form-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl
  libhttp-cookies-perl libhttp-daemon-perl libhttp-message-perl
  libhunspell-1.3-0 libhx509-5-heimdal libibus-1.0-0 libice6 libicu48
  libid3tag0 libidn11 libido-0.1-0 libido3-0.1-0 libiec61883-0 libieee1284-3
  libijs-0.35 libilmbase6 libimobiledevice2 libindicate5 libindicator3-7
  libindicator7 libio-socket-inet6-perl libio-socket-ssl-perl libisccc80
  libisofs6 libjack-jackd2-0 libjasper1 libjbig2dec0 libjpeg-turbo8 libjpeg8
  libjson0 libjte1 libkeyutils1 libklibc libkrb5-26-heimdal libkrb5-3
  libkrb5support0 liblaunchpad-integration-3.0-1 liblcms1 liblcms2-2
  libldap-2.4-2 liblocale-gettext-perl libltdl7 liblvm2app2.2
  liblwp-mediatypes-perl liblwp-protocol-https-perl liblwres80 liblzma5
  libmad0 libmailtools-perl libmhash2 libmjpegtools-1.9 libmng1 libmount1
  libmp3lame0 libmpc2 libmpfr4 libmtdev1 libncurses5 libncursesw5
  libnet-dbus-perl libnet-ssleay-perl libnetfilter-conntrack3 libnewt0.52
  libnfnetlink0 libnice10 libnih-dbus1 libnih1 libnl-genl-3-200 libnspr4
  libnss-mdns libnss3 libnss3-1d liboobs-1-5 libopenexr6 libopenobex1
  liborc-0.4-0 libp11-kit0 libpam-ck-connector libpam-gnome-keyring
  libpam-modules-bin libpam-runtime libpango1.0-0 libpaper-utils libpaper1
  libpciaccess0 libpcre3 libpcsclite1 libpipeline1 libpixman-1-0 libplist1
  libplymouth2 libpng12-0 libpolkit-agent-1-0 libpolkit-backend-1-0
  libpoppler-glib8 libpoppler19 libproxy1 libpulse0 libpulsedsp libraptor2-0
  librasqal3 libreadline6 libroken18-heimdal librsvg2-2 librsvg2-common
  librtmp0 libsane-common libsasl2-2 libsasl2-modules libschroedinger-1.0-0
  libselinux1 libsensors4 libsgutils2-2 libshout3 libslang2 libslp1 libsm6
  libsmbclient libsndfile1 libsnmp-base libsnmp15 libspeexdsp1 libsqlite3-0
  libss2 libstartup-notification0 libstdc++6 libswscale2 libtag1-vanilla
  libtag1c2a libtalloc2 libtdb1 libtext-charwidth-perl libtext-iconv-perl
  libthai-data libthai0 libtheora0 libthunarx-2-0 libtiff4 libtinfo5
  libupower-glib1 liburi-perl libutouch-frame1 libutouch-geis1
  libutouch-grail1 libv4lconvert0 libva1 libvisual-0.4-0 libvisual-0.4-plugins
  libvorbis0a libvorbisenc2 libvpx1 libvte-2.90-9 libvte-2.90-common
  libwebkitgtk-1.0-common libwind0-heimdal libwmf0.2-7 libwnck-common
  libwnck22 libwrap0 libwww-perl libwww-robotrules-perl libx11-6 libx11-data
  libx11-xcb1 libx264-120 libx86-1 libxatracker1 libxau6 libxaw7 libxcb-glx0
  libxcb-render0 libxcb-shape0 libxcb1 libxcomposite1 libxcursor1 libxdamage1
  libxfce4ui-1-0 libxfce4util-bin libxfce4util4 libxfcegui4-4 libxfconf-0-2
  libxfixes3 libxfont1 libxft2 libxi6 libxml-twig-perl libxmu6 libxpm4
  libxrandr2 libxrender1 libxt6 libxtst6 libxv1 libxvidcore4 libxvmc1
  libxxf86vm1 libyajl1 libyelp0 linux-libc-dev locales logrotate lshw lsof
  ltrace manpages mime-support mount mountall multiarch-support myspell-en-us
  netcat netcat-traditional original-awk parted passwd perl pkg-config
  plymouth plymouth-label pm-utils policykit-1 policykit-1-gnome poppler-utils
  popularity-contest powermgmt-base printer-driver-gutenprint
  printer-driver-min12xxw printer-driver-pnm2ppa pulseaudio python-apt
  python-apt-common python-aptdaemon.gtk3widgets python-cairo python-chardet
  python-crypto python-cups python-cupshelpers python-dbus-dev python-debian
  python-glade2 python-gnomekeyring python-gobject python-gobject-2
  python-gtk2 python-httplib2 python-keyring python-launchpadlib
  python-lazr.restfulclient python-lazr.uri python-libxml2 python-notify
  python-oauth python-openssl python-pam python-problem-report python-pycurl
  python-serial python-simplejson python-smbc python-twisted-core
  python-ubuntu-sso-client python-wadllib python-xapian python-xdg python-xkit
  python2.7 python2.7-minimal readline-common rsync rtkit sed strace syslinux
  system-config-printer-common system-config-printer-udev
  system-tools-backends sysvinit-utils tar thunar-data thunderbird
  thunderbird-globalmenu time tsconf ttf-dejavu-core ubuntu-keyring
  ubuntu-sso-client udev udisks unattended-upgrades upower upstart usbmuxd
  usbutils util-linux vbetool wget x11-apps x11-common x11-session-utils
  x11-utils x11-xfs-utils x11-xserver-utils xauth xbitmaps xdg-user-dirs
  xfce-keyboard-shortcuts xfce4-power-manager-data xfconf xfdesktop4-data
  xfonts-base xfonts-encodings xfonts-utils xinit xinput xkb-data
  xorg-docs-core xserver-xorg xserver-xorg-input-evdev
  xserver-xorg-input-mouse xul-ext-ubufox xz-lzma xz-utils yelp yelp-xsl
  zlib1g
Suggested packages:
  default-mta mail-transport-agent bash-doc whois vacation libarchive1 cpp-doc
  anacron checksecurity busybox cups-bsd hplip cups-pdf smbclient ispell
  emacsen-common jed-extra gpart e2fsck-static opencryptoki keyescrow-client
  cdtool setcd mlocate locate latex-xft-fonts firefox-gnome-support
  firefox-kde-support printer-driver-foo2zjs printer-driver-splix
  printer-driver-m2300w cjet printer-driver-c2050 printer-driver-ptouch
  printer-driver-c2esp foomatic-db-gutenprint gconf-defaults-service wodim
  cdrkit-doc ghostscript-x hpijs ntp gnome-control-center gnupg-curl gnupg-doc
  xloadimage imagemagick eog groff fonts-ipafont-mincho fonts-ipafont-gothic
  ttf-arphic-ukai ttf-arphic-uming fonts-unfonts-core gvfs-backends apmd
  zenity texinfo-doc-nonfree bootchart iproute-doc isoquery libgnome2-0
  konqueror libaudio2 libesd0 libesd-alsa0 libroar1 libsndio0 roaraudio-server
  libasound2-python glibc-doc libfont-freetype-perl libcanberra-gtk0
  libcanberra-pulse libcap-dev libdv-bin oss-compat libenchant-voikko geoclue
  libgnomevfs2-bin libgnomevfs2-extra gamin fam gnome-mime-data gnutls-bin
  gphoto2 gtkam gpm gstreamer-codec-install gnome-codec-install
  libgtk2-perl-doc gutenprint-locales libdata-dump-perl jackd2
  libjasper-runtime krb5-doc krb5-user liblcms-utils liblcms2-utils
  libcrypt-ssleay-perl libmime-base64-perl ttf-baekmuk ttf-arphic-gbsn00lp
  ttf-arphic-bsmi00lp ttf-arphic-gkai00mp ttf-arphic-bkai00mp pcscd
  poppler-data raptor2-utils rasqal-utils librsvg2-bin libsasl2-modules-otp
  libsasl2-modules-ldap libsasl2-modules-sql libsasl2-modules-gssapi-mit
  libsasl2-modules-gssapi-heimdal lm-sensors sg3-utils slpd openslp-doc
  snmp-mibs-downloader libwmf0.2-7-gtk libauthen-ntlm-perl
  libunicode-map8-perl libunicode-string-perl xml-twig-tools mailx nfs-common
  parted-doc libterm-readline-gnu-perl libterm-readline-perl-perl make
  cpufrequtils wireless-tools ethtool radeontool gutenprint-doc magicfilter
  apsfilter pavumeter paman paprefs pulseaudio-module-raop
  pulseaudio-esound-compat python-apt-dbg python-vte python-apt-doc
  python-crypto-dbg python-crypto-doc python-gtk2-doc python-gobject-2-dbg
  python-testresources python-openssl-doc python-openssl-dbg python-pam-dbg
  libcurl4-gnutls-dev python-pycurl-dbg python-wxgtk2.8 python-wxgtk2.6
  python-wxgtk python-tk python-qt3 xapian-doc python2.7-doc binutils
  binfmt-support openssh-client openssh-server os-prober sash ncompress
  thunderbird-gnome-support watershed xfsprogs reiserfsprogs mdadm bsd-mailx
  graphviz util-linux-locales mesa-utils nickle cairo-5c xfs xserver xorg-docs
  ttf-dejavu
Recommended packages:
  hunspell-en-us hunspell-dictionary myspell-dictionary
The following NEW packages will be installed:
  acl adduser apport apt-utils aptdaemon at avahi-daemon base-files
  base-passwd bash bash-completion bind9-host bsdmainutils busybox-initramfs
  busybox-static ca-certificates console-setup consolekit cpio cpp cron
  cryptsetup cryptsetup-bin cups cups-common cups-filters dbus dbus-x11
  dconf-gsettings-backend dconf-service dictionaries-common dmsetup dosfstools
  dpkg e2fslibs e2fsprogs ecryptfs-utils ed eject enchant exo-utils file
  findutils firefox firefox-locale-en fontconfig-config
  foomatic-db-compressed-ppds foomatic-db-engine foomatic-filters ftp fuse
  gcc-4.6-base gconf-service gconf-service-backend gconf2 gconf2-common
  genisoimage ghostscript ghostscript-cups gimp-data gir1.2-atk-1.0
  gir1.2-dbusmenu-glib-0.4 gir1.2-freedesktop gir1.2-gdkpixbuf-2.0
  gir1.2-glib-2.0 gir1.2-gtk-2.0 gir1.2-gtk-3.0 gir1.2-javascriptcoregtk-3.0
  gir1.2-pango-1.0 gir1.2-vte-2.90 gir1.2-webkit-3.0 glib-networking-common
  glib-networking-services gnome-icon-theme gnome-keyring gnome-system-tools
  gnupg groff-base gs-cjk-resource gsettings-desktop-schemas gsfonts
  gstreamer0.10-plugins-base gstreamer0.10-plugins-good
  gstreamer0.10-pulseaudio gstreamer0.10-tools gstreamer0.10-x
  gtk3-engines-unico gvfs gvfs-common gvfs-daemons gvfs-libs hdparm
  humanity-icon-theme im-switch indicator-messages indicator-sound
  indicator-status-provider-mc5 info initramfs-tools-bin initscripts insserv
  iproute iptables iso-codes kbd keyboard-configuration keyutils klibc-utils
  krb5-locales language-pack-en-base language-pack-gnome-en
  language-selector-common launchpad-integration libaa1 libaccountsservice0
  libacl1 libao-common libao4 libapt-inst1.4 libapt-pkg4.12 libasn1-8-heimdal
  libasound2 libasound2-plugins libasyncns0 libatasmart4 libatk1.0-0
  libatk1.0-data libatm1 libattr1 libavahi-client3 libavahi-common-data
  libavahi-common3 libavahi-core7 libavutil51 libbabl-0.0-0 libblkid1
  libbluetooth3 libburn4 libbz2-1.0 libc-bin libc-dev-bin libc6 libcaca0
  libcairo-gobject2 libcairo-perl libcanberra0 libcap-ng0 libcap2 libcap2-bin
  libcdparanoia0 libck-connector0 libclass-isa-perl libcolord1 libcomerr2
  libcroco3 libcryptsetup4 libcups2 libcupscgi1 libcupsfilters1 libcupsimage2
  libcupsmime1 libcupsppdc1 libdaemon0 libdatrie1 libdb5.1 libdbusmenu-gtk3-4
  libdbusmenu-gtk4 libdee-1.0-4 libdevmapper-event1.02.1 libdevmapper1.02.1
  libdns81 libdrm-intel1 libdrm-radeon1 libdv4 libecryptfs0 libenchant1c2a
  libencode-locale-perl libexo-1-0 libexo-common libexpat1 libfaac0 libfaad2
  libfile-copy-recursive-perl libfile-listing-perl libfont-afm-perl
  libfontenc1 libfribidi0 libfs6 libgail18 libgarcon-1-0 libgarcon-common
  libgcc1 libgck-1-0 libgdk-pixbuf2.0-common libgdl-3-common libgdome2-0
  libgdu0 libgee2 libgeoclue0 libgimp2.0 libgirepository-1.0-1 libgl1-mesa-glx
  libglapi-mesa libglib-perl libglib2.0-0 libglib2.0-bin libglu1-mesa libgmp10
  libgnome-keyring-common libgnome-keyring0 libgnomevfs2-0 libgnomevfs2-common
  libgnutls26 libgphoto2-2 libgphoto2-l10n libgphoto2-port0 libgpm2 libgs9
  libgs9-common libgssapi3-heimdal libgstreamer-plugins-base0.10-0
  libgstreamer0.10-0 libgtk-3-0 libgtk-3-bin libgtk2-perl libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libgupnp-1.0-4 libgutenprint2
  libhcrypto4-heimdal libheimbase1-heimdal libheimntlm0-heimdal libhpmud0
  libhtml-form-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl
  libhttp-cookies-perl libhttp-daemon-perl libhttp-message-perl
  libhunspell-1.3-0 libhx509-5-heimdal libibus-1.0-0 libice6 libicu48
  libid3tag0 libidn11 libido-0.1-0 libido3-0.1-0 libiec61883-0 libieee1284-3
  libijs-0.35 libilmbase6 libimobiledevice2 libindicate5 libindicator3-7
  libindicator7 libio-socket-inet6-perl libio-socket-ssl-perl libisccc80
  libisofs6 libjack-jackd2-0 libjasper1 libjbig2dec0 libjpeg-turbo8 libjpeg8
  libjson0 libjte1 libkeyutils1 libklibc libkrb5-26-heimdal libkrb5-3
  libkrb5support0 liblaunchpad-integration-3.0-1 liblcms1 liblcms2-2
  libldap-2.4-2 liblocale-gettext-perl libltdl7 liblvm2app2.2
  liblwp-mediatypes-perl liblwp-protocol-https-perl liblwres80 liblzma5
  libmad0 libmailtools-perl libmhash2 libmjpegtools-1.9 libmng1 libmount1
  libmp3lame0 libmpc2 libmpfr4 libmtdev1 libncurses5 libncursesw5
  libnet-dbus-perl libnet-ssleay-perl libnetfilter-conntrack3 libnewt0.52
  libnfnetlink0 libnice10 libnih-dbus1 libnih1 libnl-genl-3-200 libnspr4
  libnss-mdns libnss3 libnss3-1d liboobs-1-5 libopenexr6 libopenobex1
  liborc-0.4-0 libp11-kit0 libpam-ck-connector libpam-gnome-keyring
  libpam-modules-bin libpam-runtime libpango1.0-0 libpaper-utils libpaper1
  libpciaccess0 libpcre3 libpcsclite1 libpipeline1 libpixman-1-0 libplist1
  libplymouth2 libpng12-0 libpolkit-agent-1-0 libpolkit-backend-1-0
  libpoppler-glib8 libpoppler19 libproxy1 libpulse0 libpulsedsp libraptor2-0
  librasqal3 libreadline6 libroken18-heimdal librsvg2-2 librsvg2-common
  librtmp0 libsane-common libsasl2-2 libsasl2-modules libschroedinger-1.0-0
  libselinux1 libsensors4 libsgutils2-2 libshout3 libslang2 libslp1 libsm6
  libsmbclient libsndfile1 libsnmp-base libsnmp15 libspeexdsp1 libsqlite3-0
  libss2 libstartup-notification0 libstdc++6 libswscale2 libtag1-vanilla
  libtag1c2a libtalloc2 libtdb1 libtext-charwidth-perl libtext-iconv-perl
  libthai-data libthai0 libtheora0 libthunarx-2-0 libtiff4 libtinfo5
  libupower-glib1 liburi-perl libutouch-frame1 libutouch-geis1
  libutouch-grail1 libv4lconvert0 libva1 libvisual-0.4-0 libvisual-0.4-plugins
  libvorbis0a libvorbisenc2 libvpx1 libvte-2.90-9 libvte-2.90-common
  libwebkitgtk-1.0-common libwind0-heimdal libwmf0.2-7 libwnck-common
  libwnck22 libwrap0 libwww-perl libwww-robotrules-perl libx11-6 libx11-data
  libx11-xcb1 libx264-120 libx86-1 libxatracker1 libxau6 libxaw7 libxcb-glx0
  libxcb-render0 libxcb-shape0 libxcb1 libxcomposite1 libxcursor1 libxdamage1
  libxfce4ui-1-0 libxfce4util-bin libxfce4util4 libxfcegui4-4 libxfconf-0-2
  libxfixes3 libxfont1 libxft2 libxi6 libxml-twig-perl libxmu6 libxpm4
  libxrandr2 libxrender1 libxt6 libxtst6 libxv1 libxvidcore4 libxvmc1
  libxxf86vm1 libyajl1 libyelp0 linux-libc-dev locales logrotate lshw lsof
  ltrace manpages mime-support mount mountall multiarch-support myspell-en-us
  netcat netcat-traditional original-awk parted passwd perl pkg-config
  plymouth plymouth-label pm-utils policykit-1 policykit-1-gnome poppler-utils
  popularity-contest powermgmt-base printer-driver-gutenprint
  printer-driver-min12xxw printer-driver-pnm2ppa pulseaudio python-apt
  python-apt-common python-aptdaemon.gtk3widgets python-cairo python-chardet
  python-crypto python-cups python-cupshelpers python-dbus-dev python-debian
  python-glade2 python-gnomekeyring python-gobject python-gobject-2
  python-gtk2 python-httplib2 python-keyring python-launchpadlib
  python-lazr.restfulclient python-lazr.uri python-libxml2 python-notify
  python-oauth python-openssl python-pam python-problem-report python-pycurl
  python-serial python-simplejson python-smbc python-twisted-core
  python-ubuntu-sso-client python-wadllib python-xapian python-xdg python-xkit
  python2.7 python2.7-minimal readline-common rsync rtkit sed strace syslinux
  system-config-printer-common system-config-printer-udev
  system-tools-backends sysvinit-utils tar thunar-data thunderbird time tsconf
  ttf-dejavu-core ubuntu-keyring ubuntu-sso-client udev udisks
  unattended-upgrades upower upstart usbmuxd usbutils util-linux vbetool wget
  x11-apps x11-common x11-session-utils x11-utils x11-xfs-utils
  x11-xserver-utils xauth xbitmaps xdg-user-dirs xfce-keyboard-shortcuts
  xfce4-power-manager-data xfconf xfdesktop4-data xfonts-base xfonts-encodings
  xfonts-utils xinit xinput xkb-data xorg-docs-core xserver-xorg
  xserver-xorg-input-evdev xserver-xorg-input-mouse xul-ext-ubufox xz-lzma
  xz-utils yelp yelp-xsl zlib1g
The following packages will be upgraded:
  firefox-globalmenu libavcodec53 libgail-3-0 libgtk-3-common
  thunderbird-globalmenu
5 upgraded, 562 newly installed, 0 to remove and 16 not upgraded.
3 not fully installed or removed.
Need to get 0 B/194 MB of archives.
After this operation, 562 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: error: parsing file '/var/lib/dpkg/status' near line 7682 package 'xserver-xorg-video-radeon':
 EOF after field name `Desc'
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

whereas before I couldnt even try and download updates....... dont know if im doind this right but thanks for the support imma try your suggestion now

---

### Post by Shadius on 2012-06-25
Please use the "#" button in the message box to post the codes from Terminal. It'd make it easier for us to read. It'll give  you ```
 [CODE] tags. Paste the code in between the two tags.

Also, the output suggested that you run:
[CODE]sudo apt-get autoremove
```
to remove some packages that are no longer installed and needed.

---

### Post by killertm on 2012-06-25
```
 Depends: libxrender1 but it is not installed
             Depends: zlib1g (>= 1:1.1.4) but it is not installed
             PreDepends: multiarch-support but it is not installed
 libcdaudio1 : Depends: libc6 (>= 2.4) but it is not installed
 libcelt0-0 : Depends: libc6 (>= 2.4) but it is not installed
 libcurl3-gnutls : Depends: libc6 (>= 2.15) but it is not installed
                   Depends: libgnutls26 (>= 2.12.6.1-0) but it is not installed
                   Depends: libidn11 (>= 1.13) but it is not installed
                   Depends: libldap-2.4-2 (>= 2.4.7) but it is not installed
                   Depends: librtmp0 (>= 2.3) but it is not installed
                   Depends: zlib1g (>= 1:1.1.4) but it is not installed
                   Depends: ca-certificates but it is not installed
                   PreDepends: multiarch-support but it is not installed
 libdbus-1-3 : Depends: libc6 (>= 2.10) but it is not installed
               PreDepends: multiarch-support but it is not installed
               Recommends: dbus but it is not installed
 libdbus-glib-1-2 : Depends: libc6 (>= 2.3.6-6~) but it is not installed
                    Depends: libglib2.0-0 (>= 2.26.0) but it is not installed
                    PreDepends: multiarch-support but it is not installed
 libdbusmenu-glib4 : Depends: libc6 (>= 2.3.6-6~) but it is not installed
                     Depends: libglib2.0-0 (>= 2.31.8) but it is not installed
                     PreDepends: multiarch-support but it is not installed
 libdconf0 : Depends: libc6 (>= 2.4) but it is not installed
             Depends: libglib2.0-0 (>= 2.31.2) but it is not installed
             PreDepends: multiarch-support but it is not installed
 libdirac-encoder0 : Depends: libc6 (>= 2.4) but it is not installed
                     Depends: libgcc1 (>= 1:4.1.1) but it is not installed
                     Depends: libstdc++6 (>= 4.4.0) but it is not installed
 libdrm-nouveau1a : Depends: libc6 (>= 2.1.3) but it is not installed
                    PreDepends: multiarch-support but it is not installed
 libdrm2 : Depends: libc6 (>= 2.7) but it is not installed
           PreDepends: multiarch-support but it is not installed
 libdvdread4 : Depends: libc6 (>= 2.4) but it is not installed
               Recommends: libdvdnav4 but it is not installed
 libelf1 : Depends: libc6 (>= 2.4) but it is not installed
           PreDepends: multiarch-support but it is not installed
 libenca0 : Depends: libc6 (>= 2.4) but it is not installed
 libexif12 : Depends: libc6 (>= 2.4) but it is not installed
             PreDepends: multiarch-support but it is not installed
 libfarstream-0.1-0 : Depends: libc6 (>= 2.7) but it is not installed
                      Depends: libglib2.0-0 (>= 2.31.2) but it is not installed
                      Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.33) but it is not installed
                      Depends: libgstreamer0.10-0 (>= 0.10.33) but it is not installed
                      Depends: libnice10 (>= 0.1.0) but it is not installed
                      Depends: gstreamer0.10-plugins-base (>= 0.10.33) but it is not installed
                      Depends: gstreamer0.10-plugins-good (>= 0.10.29) but it is not installed
                      PreDepends: multiarch-support but it is not installed
 libffi6 : Depends: libc6 (>= 2.4) but it is not installed
           PreDepends: multiarch-support but it is not installed
 libfftw3-3 : Depends: libc6 (>= 2.11) but it is not installed
 libfile-basedir-perl : Depends: perl but it is not installed
 libflac8 : Depends: libc6 (>= 2.7) but it is not installed
            PreDepends: multiarch-support but it is not installed
 libflite1 : Depends: libasound2 (> 1.0.24.1)
             Depends: libc6 (>= 2.11) but it is not installed
 libfontconfig1 : Depends: libc6 (>= 2.7) but it is not installed
                  Depends: libexpat1 (>= 1.95.8) but it is not installed
                  Depends: fontconfig-config (= 2.8.0-3ubuntu9) but it is not installed
                  PreDepends: multiarch-support but it is not installed
 libfreetype6 : Depends: libc6 (>= 2.11) but it is not installed
                Depends: zlib1g (>= 1:1.1.4) but it is not installed
                PreDepends: multiarch-support but it is not installed
 libfuse2 : Depends: libc6 (>= 2.7) but it is not installed
 libgail-3-0 : Depends: libatk1.0-0 (>= 1.12.4) but it is not installed
               Depends: libc6 (>= 2.3.6-6~) but it is not installed
               Depends: libglib2.0-0 (>= 2.32.0) but it is not installed
               Depends: libgtk-3-0 (= 3.4.2-0ubuntu0.2) but it is not installed
               Depends: libpango1.0-0 (>= 1.30.0) but it is not installed
               PreDepends: multiarch-support but it is not installed
 libgconf-2-4 : Depends: libc6 (>= 2.4) but it is not installed
                Depends: libglib2.0-0 (>= 2.25.9) but it is not installed
                Depends: gconf2-common (= 3.2.5-0ubuntu2) but it is not installed
                PreDepends: multiarch-support but it is not installed
                Recommends: gconf-service but it is not installed
 libgconf2-4 : Depends: gconf-service but it is not installed
 libgcr-3-1 : Depends: libc6 (>= 2.15) but it is not installed
              Depends: libgck-1-0 (>= 3.2.2) but it is not installed
              Depends: libglib2.0-0 (>= 2.31.8) but it is not installed
              Depends: libgtk-3-0 (>= 3.1.4) but it is not installed
              Depends: libp11-kit0 (>= 0.6) but it is not installed
              Depends: libpango1.0-0 (>= 1.18.0) but it is not installed
 libgcrypt11 : Depends: libc6 (>= 2.15) but it is not installed
               PreDepends: multiarch-support but it is not installed
 libgd2-xpm : Depends: libc6 (>= 2.11) but it is not installed
              Depends: libjpeg8 (>= 8c) but it is not installed
              Depends: libpng12-0 (>= 1.2.13-4) but it is not installed
              Depends: libxpm4 but it is not installed
              Depends: zlib1g (>= 1:1.1.4) but it is not installed
              PreDepends: multiarch-support but it is not installed
 libgdbm3 : Depends: libc6 (>= 2.1.3) but it is not installed
            PreDepends: multiarch-support but it is not installed
 libgdk-pixbuf2.0-0 : Depends: libc6 (>= 2.11) but it is not installed
                      Depends: libglib2.0-0 (>= 2.31.18) but it is not installed
                      Depends: libjasper1 but it is not installed
                      Depends: libjpeg8 (>= 8c) but it is not installed
                      Depends: libpng12-0 (>= 1.2.13-4) but it is not installed
                      Depends: libtiff4 but it is not installed
                      Depends: libx11-6 but it is not installed
                      Depends: libgdk-pixbuf2.0-common (= 2.26.1-1) but it is not installed
                      PreDepends: multiarch-support but it is not installed
 libgdl-3-2 : Depends: libc6 (>= 2.4) but it is not installed
              Depends: libglib2.0-0 (>= 2.28.0) but it is not installed
              Depends: libgtk-3-0 (>= 3.0.0) but it is not installed
              Depends: libgdl-3-common (= 3.3.91-1) but it is not installed
              PreDepends: multiarch-support but it is not installed
 libgdome2-cpp-smart0c2a : Depends: libc6 (>= 2.1.3) but it is not installed
                           Depends: libgcc1 (>= 1:4.1.1) but it is not installed
                           Depends: libgdome2-0 but it is not installed
                           Depends: libglib2.0-0 (>= 2.12.0) but it is not installed
                           Depends: libstdc++6 (>= 4.2.1) but it is not installed
 libgegl-0.0-0 : Depends: libbabl-0.0-0 but it is not installed
                 Depends: libc6 (>= 2.11) but it is not installed
                 Depends: libgcc1 (>= 1:4.1.1) but it is not installed
                 Depends: libglib2.0-0 (>= 2.24.0) but it is not installed
                 Depends: libjpeg8 (>= 8c) but it is not installed
                 Depends: libopenexr6 (>= 1.6.1) but it is not installed
                 Depends: libpango1.0-0 (>= 1.14.0) but it is not installed
                 Depends: libpng12-0 (>= 1.2.13-4) but it is not installed
                 Depends: librsvg2-2 (>= 2.14.4) but it is not installed
                 Depends: libstdc++6 (>= 4.1.1) but it is not installed
 libgeoip1 : Depends: libc6 (>= 2.8) but it is not installed
             Depends: zlib1g (>= 1:1.1.4) but it is not installed
             Recommends: geoip-database
 libgl1-mesa-dri : Depends: libc6 (>= 2.4) but it is not installed
                   Depends: libdrm-intel1 (>= 2.4.27) but it is not installed
                   Depends: libdrm-radeon1 (>= 2.4.17) but it is not installed
                   Depends: libexpat1 (>= 1.95.8) but it is not installed
                   Depends: libgcc1 (>= 1:4.1.1) but it is not installed
                   Depends: libstdc++6 (>= 4.1.1) but it is not installed
 libglade2-0 : Depends: libatk1.0-0 (>= 1.12.4) but it is not installed
               Depends: libc6 (>= 2.4) but it is not installed
               Depends: libglib2.0-0 (>= 2.24.0) but it is not installed
               Depends: libgtk2.0-0 (>= 2.8.0) but it is not installed
               Depends: libpango1.0-0 (>= 1.14.0) but it is not installed
               PreDepends: multiarch-support but it is not installed
 libgpg-error0 : Depends: libc6 (>= 2.1.3) but it is not installed
                 PreDepends: multiarch-support but it is not installed
 libgpod-common : Depends: libc6 (>= 2.4) but it is not installed
                  Depends: libglib2.0-0 (>= 2.16.0) but it is not installed
                  Depends: libimobiledevice2 (>= 0.9.7) but it is not installed
                  Depends: libplist1 (>= 0.16) but it is not installed
                  Depends: libsgutils2-2 (>= 1.27) but it is not installed
 libgpod4 : Depends: libc6 (>= 2.4) but it is not installed
            Depends: libglib2.0-0 (>= 2.24.0) but it is not installed
            Depends: libimobiledevice2 (>= 0.9.7) but it is not installed
            Depends: libplist1 (>= 0.16) but it is not installed
            Depends: libsqlite3-0 (>= 3.5.9) but it is not installed
            Depends: zlib1g (>= 1:1.2.0) but it is not installed
 libgrip0 : Depends: libc6 (>= 2.3.6-6~) but it is not installed
            Depends: libglib2.0-0 (>= 2.28.6) but it is not installed
            Depends: libgtk-3-0 (>= 3.0.8-0ubuntu1) but it is not installed
            Depends: libutouch-geis1 (>= 1.0.8) but it is not installed
 libgsm1 : Depends: libc6 (>= 2.3.4) but it is not installed
 libgssapi-krb5-2 : Depends: libc6 (>= 2.7) but it is not installed
                    Depends: libcomerr2 (>= 1.34) but it is not installed
                    Depends: libkrb5-3 (= 1.10+dfsg~beta1-2ubuntu0.1) but it is not installed
                    Depends: libkrb5support0 (>= 1.7dfsg~beta2) but it is not installed
                    PreDepends: multiarch-support but it is not installed
 libgssdp-1.0-3 : Depends: libc6 (>= 2.7) but it is not installed
                  Depends: libglib2.0-0 (>= 2.22.0) but it is not installed
 libgstreamer-perl : Depends: perl (>= 5.14.2-3build1) but it is not installed
                     Depends: libc6 (>= 2.1.3) but it is not installed
                     Depends: libglib2.0-0 (>= 2.12.0) but it is not installed
                     Depends: libgstreamer0.10-0 (>= 0.10.33) but it is not installed
                     Depends: libglib-perl but it is not installed
                     Recommends: gstreamer0.10-plugins-base but it is not installed
                     Recommends: gstreamer0.10-alsa but it is not installed
 libgtk-3-common : Depends: dconf-gsettings-backend but it is not installed or
                            gsettings-backend
                   Recommends: libgtk-3-0 but it is not installed
 libgtk2-trayicon-perl : Depends: perl (>= 5.14.2-3build1) but it is not installed
                         Depends: libc6 (>= 2.4) but it is not installed
                         Depends: libglib2.0-0 (>= 2.16.0) but it is not installed
                         Depends: libgtk2.0-0 (>= 2.8.0) but it is not installed
                         Depends: libglib-perl (>= 1.00) but it is not installed
                         Depends: libgtk2-perl (>= 1.00) but it is not installed
 libgtkspell0 : Depends: libc6 (>= 2.3.6-6~) but it is not installed
                Depends: libenchant1c2a (>= 1.6) but it is not installed
                Depends: libglib2.0-0 (>= 2.16.0) but it is not installed
                Depends: libgtk2.0-0 (>= 2.8.0) but it is not installed
 libgudev-1.0-0 : Depends: libc6 (>= 2.2) but it is not installed
                  Depends: libglib2.0-0 (>= 2.22.0) but it is not installed
                  PreDepends: multiarch-support but it is not installed
 libgupnp-igd-1.0-4 : Depends: libc6 (>= 2.4) but it is not installed
                      Depends: libglib2.0-0 (>= 2.31.2) but it is not installed
                      Depends: libgupnp-1.0-4 (>= 0.18.0) but it is not installed
                      PreDepends: multiarch-support but it is not installed
 libhtml-format-perl : Depends: perl but it is not installed
                       Depends: libfont-afm-perl but it is not installed
                       Depends: libhtml-tree-perl but it is not installed
 libhttp-date-perl : Depends: perl but it is not installed
 libhttp-negotiate-perl : Depends: perl but it is not installed
                          Depends: libhttp-message-perl but it is not installed
 libical0 : Depends: libc6 (>= 2.7) but it is not installed
 libindicator-messages-status-provider1 : Depends: libc6 (>= 2.3.6-6~) but it is not installed
                                          Depends: libglib2.0-0 (>= 2.14.0) but it is not installed
 libisc83 : Depends: libc6 (>= 2.15) but it is not installed
 libisccfg82 : Depends: libc6 (>= 2.4) but it is not installed
               Depends: libdns81 but it is not installed
               Depends: libisccc80 but it is not installed
 libjavascriptcoregtk-1.0-0 : Depends: libc6 (>= 2.4) but it is not installed
                              Depends: libgcc1 (>= 1:4.1.1) but it is not installed
                              Depends: libglib2.0-0 (>= 2.31.2) but it is not installed
                              Depends: libicu48 (>= 4.8-1) but it is not installed
                              Depends: libstdc++6 (>= 4.1.1) but it is not installed
 libjavascriptcoregtk-3.0-0 : Depends: libc6 (>= 2.4) but it is not installed
                              Depends: libgcc1 (>= 1:4.1.1) but it is not installed
                              Depends: libglib2.0-0 (>= 2.31.2) but it is not installed
                              Depends: libicu48 (>= 4.8-1) but it is not installed
                              Depends: libstdc++6 (>= 4.1.1) but it is not installed
 libk5crypto3 : Depends: libc6 (>= 2.4) but it is not installed
                Depends: libkrb5support0 (>= 1.7dfsg~beta2) but it is not installed
                PreDepends: multiarch-support but it is not installed
 libllvm3.0 : Depends: libc6 (>= 2.11) but it is not installed
              Depends: libgcc1 (>= 1:4.1.1) but it is not installed
              Depends: libstdc++6 (>= 4.6) but it is not installed
              PreDepends: multiarch-support but it is not installed
 libloudmouth1-0 : Depends: libasyncns0 (>= 0.3) but it is not installed
                   Depends: libc6 (>= 2.7) but it is not installed
                   Depends: libglib2.0-0 (>= 2.16.0) but it is not installed
                   Depends: libgnutls26 (>= 2.12.6.1-0) but it is not installed
                   Depends: libidn11 (>= 1.13) but it is not installed
 libmagic1 : Depends: libc6 (>= 2.8) but it is not installed
             Depends: zlib1g (>= 1:1.1.4) but it is not installed
 libnet-http-perl : Depends: perl but it is not installed
                    Recommends: libio-socket-ssl-perl (>= 1.38) but it is not installed
 libnl-3-200 : Depends: libc6 (>= 2.8) but it is not installed
 libnm-util2 : Depends: libc6 (>= 2.4) but it is not installed
               Depends: libglib2.0-0 (>= 2.31.8) but it is not installed
               Depends: libnspr4 (>= 1.8.0.10) but it is not installed
               Depends: libnss3 (>= 3.12.0~1.9b1) but it is not installed
 libnotify-bin : Depends: libc6 (>= 2.3.4) but it is not installed
                 Depends: libglib2.0-0 (>= 2.26) but it is not installed
 libnotify4 : Depends: libc6 (>= 2.7) but it is not installed
              Depends: libglib2.0-0 (>= 2.26.0) but it is not installed
              PreDepends: multiarch-support but it is not installed
              Recommends: notification-daemon
 libogg0 : Depends: libc6 (>= 2.4) but it is not installed
           PreDepends: multiarch-support but it is not installed
 libopenspc0 : Depends: libc6 (>= 2.3.4-1) but it is not installed
               Depends: zlib1g (>= 1:1.2.1) but it is not installed
 libots0 : Depends: libc6 (>= 2.4) but it is not installed
           Depends: libglib2.0-0 (>= 2.12.0) but it is not installed
 libpam-cap : Depends: libc6 (>= 2.4) but it is not installed
              Depends: libcap2 (>= 2.10) but it is not installed
              Depends: libpam-runtime (>= 1.1.3-2~) but it is not installed
 libpam-modules : PreDepends: libc6 (>= 2.8) but it is not installed
                  PreDepends: libdb5.1 but it is not installed
                  PreDepends: libselinux1 (>= 2.0.85) but it is not installed
                  PreDepends: libpam-modules-bin (= 1.1.3-7ubuntu2) but it is not installed
 libpam0g : Depends: libc6 (>= 2.8) but it is not installed
            PreDepends: multiarch-support but it is not installed
 libpango-perl : Depends: libc6 (>= 2.4) but it is not installed
                 Depends: libglib2.0-0 (>= 2.16.0) but it is not installed
                 Depends: libpango1.0-0 (>= 1.22.0) but it is not installed
                 Depends: perl (>= 5.14.2-3) but it is not installed
                 Depends: libcairo-perl but it is not installed
                 Depends: libglib-perl (>= 1.220) but it is not installed
 libparted0debian1 : Depends: libblkid1 (>= 2.17.2) but it is not installed
                     Depends: libc6 (>= 2.8) but it is not installed
                     Depends: libdevmapper1.02.1 (>= 2:1.02.36) but it is not installed
                     PreDepends: multiarch-support but it is not installed
 libpci3 : Depends: libc6 (>= 2.7) but it is not installed
           Depends: zlib1g (>= 1:1.1.4) but it is not installed
           PreDepends: multiarch-support but it is not installed
 libperl5.14 : Depends: libc6 (>= 2.11) but it is not installed
 libpolkit-gobject-1-0 : Depends: libc6 (>= 2.7) but it is not installed
                         Depends: libglib2.0-0 (>= 2.31.8) but it is not installed
                         PreDepends: multiarch-support but it is not installed
 libpopt0 : Depends: libc6 (>= 2.8) but it is not installed
            PreDepends: multiarch-support but it is not installed
 libpulse-mainloop-glib0 : Depends: libc6 (>= 2.3.6-6~) but it is not installed
                           Depends: libglib2.0-0 (>= 2.16.0) but it is not installed
                           Depends: libpulse0 (>= 1:1.1-0ubuntu15) but it is not installed
                           PreDepends: multiarch-support but it is not installed
 libpython2.7 : Depends: python2.7 (= 2.7.3-0ubuntu3) but it is not installed
                Depends: libc6 (>= 2.15) but it is not installed
                Depends: libgcc1 (>= 1:4.1.1) but it is not installed
                Depends: zlib1g (>= 1:1.2.0) but it is not installed
 libquadmath0 : Depends: gcc-4.6-base (= 4.6.3-1ubuntu5) but it is not installed
                Depends: libc6 (>= 2.10) but it is not installed
                PreDepends: multiarch-support but it is not installed
 libquicktime2 : Depends: libc6 (>= 2.11) but it is not installed
                 Depends: libdv4 but it is not installed
                 Depends: libfaad2 but it is not installed
                 Depends: libjpeg8 (>= 8c) but it is not installed
                 Depends: libmp3lame0 but it is not installed
                 Depends: libpng12-0 (>= 1.2.13-4) but it is not installed
                 Depends: libschroedinger-1.0-0 (>= 1.0.0) but it is not installed
                 Depends: libswscale2 (>= 4:0.8~beta2-2) but it is not installed or
                          libswscale-extra-2 (>= 4:0.8~beta2-2) but it is not installed
                 Depends: libvorbis0a (>= 1.1.2) but it is not installed
                 Depends: libvorbisenc2 (>= 1.1.2) but it is not installed
                 Depends: libx264-120 but it is not installed
                 Depends: zlib1g (>= 1:1.1.4) but it is not installed
 libraw1394-11 : Depends: libc6 (>= 2.4) but it is not installed
                 PreDepends: multiarch-support but it is not installed
 librdf0 : Depends: libc6 (>= 2.4) but it is not installed
           Depends: libdb5.1 but it is not installed
           Depends: libltdl7 (>= 2.4.2) but it is not installed
           Depends: libraptor2-0 (>= 2.0.4) but it is not installed
           Depends: librasqal3 (>= 0.9.27) but it is not installed
 libsamplerate0 : Depends: libc6 (>= 2.1.3) but it is not installed
                  PreDepends: multiarch-support but it is not installed
 libsane : Depends: adduser (>= 3.47) but it is not installed
           Depends: libsane-common (= 1.0.22-7ubuntu1) but it is not installed
           Depends: udev (>= 0.88-1) but it is not installed
           Depends: acl (>= 2.2.49-4) but it is not installed
           Depends: libavahi-client3 (>= 0.6.16) but it is not installed
           Depends: libavahi-common3 (>= 0.6.16) but it is not installed
           Depends: libc6 (>= 2.11) but it is not installed
           Depends: libgphoto2-2 (>= 2.4.10.1) but it is not installed
           Depends: libgphoto2-port0 (>= 2.4.10.1) but it is not installed
           Depends: libieee1284-3 but it is not installed
           Depends: libjpeg8 (>= 8c) but it is not installed
           Depends: libtiff4 but it is not installed
           PreDepends: multiarch-support but it is not installed
 libsane-hpaio : Depends: libc6 (>= 2.7) but it is not installed
                 Depends: libcups2 (>= 1.4.0) but it is not installed
                 Depends: libhpmud0 but it is not installed
                 Recommends: hplip (= 3.12.2-1ubuntu3) but it is not installed
 libsdl1.2debian : Depends: libasound2 (> 1.0.24.1)
                   Depends: libc6 (>= 2.4) but it is not installed
                   Depends: libcaca0 (>= 0.99.beta17-1) but it is not installed
                   Depends: libpulse0 (>= 1:0.99.1) but it is not installed
                   Depends: libx11-6 (>= 2:1.4.99.1) but it is not installed
                   PreDepends: multiarch-support but it is not installed
 libsocket6-perl : Depends: perl (>= 5.14.2-3) but it is not installed
                   Depends: libc6 (>= 2.4) but it is not installed
 libsoup-gnome2.4-1 : Depends: libc6 (>= 2.1.3) but it is not installed
                      Depends: libglib2.0-0 (>= 2.31.7) but it is not installed
                      Depends: libgnome-keyring0 (>= 2.20.3) but it is not installed
                      Depends: libsqlite3-0 (>= 3.5.9) but it is not installed
                      PreDepends: multiarch-support but it is not installed
 libsoup2.4-1 : Depends: libc6 (>= 2.4) but it is not installed
                Depends: libglib2.0-0 (>= 2.31.8) but it is not installed
                PreDepends: multiarch-support but it is not installed
 libspandsp2 : Depends: libc6 (>= 2.4) but it is not installed
               Depends: libtiff4 but it is not installed
 libspeex1 : Depends: libc6 (>= 2.4) but it is not installed
             PreDepends: multiarch-support but it is not installed
 libssl1.0.0 : Depends: libc6 (>= 2.7) but it is not installed
               Depends: zlib1g (>= 1:1.1.4) but it is not installed
               PreDepends: multiarch-support but it is not installed
 libswitch-perl : Depends: perl but it is not installed
 libsysfs2 : Depends: libc6 (>= 2.4) but it is not installed
 libt1-5 : Depends: libc6 (>= 2.11) but it is not installed
           Depends: libx11-6 but it is not installed
 libtasn1-3 : Depends: libc6 (>= 2.4) but it is not installed
              PreDepends: multiarch-support but it is not installed
 libtelepathy-glib0 : Depends: libc6 (>= 2.4) but it is not installed
                      Depends: libglib2.0-0 (>= 2.30.0) but it is not installed
 libtext-wrapi18n-perl : Depends: libtext-charwidth-perl but it is not installed
 libtie-ixhash-perl : Depends: perl (>= 5.6.0-16) but it is not installed
 libtimedate-perl : Depends: perl but it is not installed
 libts-0.0-0 : Depends: libc6 (>= 2.7) but it is not installed
               Depends: tsconf but it is not installed
               PreDepends: multiarch-support but it is not installed
 libudev0 : Depends: libc6 (>= 2.8) but it is not installed
            PreDepends: multiarch-support but it is not installed
 libusb-0.1-4 : Depends: libc6 (>= 2.4) but it is not installed
                PreDepends: multiarch-support but it is not installed
 libusb-1.0-0 : Depends: libc6 (>= 2.8) but it is not installed
                PreDepends: multiarch-support but it is not installed
 libusbmuxd1 : Depends: libc6 (>= 2.4) but it is not installed
               Depends: libplist1 (>= 0.16) but it is not installed
 libutempter0 : Depends: libc6 (>= 2.4) but it is not installed
                Depends: adduser but it is not installed
 libutouch-evemu1 : Depends: libc6 (>= 2.7) but it is not installed
                    PreDepends: multiarch-support but it is not installed
 libuuid1 : Depends: passwd but it is not installed
            Depends: libc6 (>= 2.4) but it is not installed
            PreDepends: multiarch-support but it is not installed
            Recommends: uuid-runtime but it is not installed
 libv4l-0 : Depends: libv4lconvert0 (= 0.8.6-1ubuntu2) but it is not installed
            Depends: libc6 (>= 2.4) but it is not installed
            PreDepends: multiarch-support but it is not installed
 libvorbisfile3 : Depends: libc6 (>= 2.4) but it is not installed
                  Depends: libvorbis0a (= 1.3.2-1ubuntu3) but it is not installed
                  PreDepends: multiarch-support but it is not installed
 libwavpack1 : Depends: libc6 (>= 2.4) but it is not installed
               PreDepends: multiarch-support but it is not installed
 libwbclient0 : Depends: libc6 (>= 2.8) but it is not installed
                PreDepends: multiarch-support but it is not installed
 libwebkitgtk-1.0-0 : Depends: libatk1.0-0 (>= 1.12.4) but it is not installed
                      Depends: libc6 (>= 2.11) but it is not installed
                      Depends: libenchant1c2a (>= 1.6) but it is not installed
                      Depends: libgail18 (>= 1.18.0) but it is not installed
                      Depends: libgcc1 (>= 1:4.1.1) but it is not installed
                      Depends: libgeoclue0 (>= 0.11.1) but it is not installed
                      Depends: libglib2.0-0 (>= 2.31.2) but it is not installed
                      Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.31) but it is not installed
                      Depends: libgstreamer0.10-0 (>= 0.10.31) but it is not installed
                      Depends: libgtk2.0-0 (>= 2.24.3) but it is not installed
                      Depends: libicu48 (>= 4.8-1) but it is not installed
                      Depends: libjpeg8 (>= 8c) but it is not installed
                      Depends: libpango1.0-0 (>= 1.22.0) but it is not installed
                      Depends: libpng12-0 (>= 1.2.13-4) but it is not installed
                      Depends: libsqlite3-0 (>= 3.5.9) but it is not installed
                      Depends: libstdc++6 (>= 4.1.1) but it is not installed
                      Depends: libx11-6 but it is not installed
                      Depends: libxrender1 but it is not installed
                      Depends: libxt6 but it is not installed
                      Depends: zlib1g (>= 1:1.1.4) but it is not installed
                      Depends: libwebkitgtk-1.0-common (>= 1.8.0) but it is not installed
 libwebkitgtk-3.0-0 : Depends: libatk1.0-0 (>= 1.12.4) but it is not installed
                      Depends: libc6 (>= 2.11) but it is not installed
                      Depends: libenchant1c2a (>= 1.6) but it is not installed
                      Depends: libgcc1 (>= 1:4.1.1) but it is not installed
                      Depends: libgeoclue0 (>= 0.11.1) but it is not installed
                      Depends: libglib2.0-0 (>= 2.31.2) but it is not installed
                      Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.31) but it is not installed
                      Depends: libgstreamer0.10-0 (>= 0.10.31) but it is not installed
                      Depends: libgtk-3-0 (>= 3.3.6) but it is not installed
                      Depends: libicu48 (>= 4.8-1) but it is not installed
                      Depends: libjpeg8 (>= 8c) but it is not installed
                      Depends: libpango1.0-0 (>= 1.22.0) but it is not installed
                      Depends: libpng12-0 (>= 1.2.13-4) but it is not installed
                      Depends: libsqlite3-0 (>= 3.5.9) but it is not installed
                      Depends: libstdc++6 (>= 4.1.1) but it is not installed
                      Depends: libx11-6 but it is not installed
                      Depends: libxrender1 but it is not installed
                      Depends: libxt6 but it is not installed
                      Depends: zlib1g (>= 1:1.1.4) but it is not installed
 libwildmidi1 : Depends: libc6 (>= 2.4) but it is not installed
                PreDepends: multiarch-support but it is not installed
 libwpd-0.9-9 : Depends: libc6 (>= 2.4) but it is not installed
                Depends: libgcc1 (>= 1:4.1.1) but it is not installed
                Depends: libstdc++6 (>= 4.6) but it is not installed
 libxapian22 : Depends: libc6 (>= 2.4) but it is not installed
               Depends: libgcc1 (>= 1:4.1.1) but it is not installed
               Depends: libstdc++6 (>= 4.6) but it is not installed
               Depends: zlib1g (>= 1:1.1.4) but it is not installed
 libxcb-shm0 : Depends: libc6 (>= 2.1.3) but it is not installed
               Depends: libxcb1 but it is not installed
               PreDepends: multiarch-support but it is not installed
 libxcb-util0 : Depends: libc6 (>= 2.8) but it is not installed
                Depends: libxcb1 but it is not installed
                PreDepends: multiarch-support but it is not installed
 libxdmcp6 : Depends: libc6 (>= 2.4) but it is not installed
             PreDepends: multiarch-support but it is not installed
 libxext6 : Depends: libc6 (>= 2.4) but it is not installed
            Depends: libx11-6 (>= 2:1.4.99.1) but it is not installed
            PreDepends: multiarch-support but it is not installed
 libxinerama1 : Depends: libc6 (>= 2.1.3) but it is not installed
                Depends: libx11-6 (>= 2:1.4.99.1) but it is not installed
                PreDepends: multiarch-support but it is not installed
 libxkbfile1 : Depends: libc6 (>= 2.7) but it is not installed
               Depends: libx11-6 but it is not installed
 libxml-parser-perl : Depends: perl (>= 5.14.2-3build1) but it is not installed
                      Depends: liburi-perl but it is not installed
                      Depends: libwww-perl but it is not installed
                      Depends: libc6 (>= 2.4) but it is not installed
                      Depends: libexpat1 (>= 1.95.8) but it is not installed
 libxml-xpath-perl : Depends: perl but it is not installed
 libxml2 : Depends: libc6 (>= 2.15) but it is not installed
           Depends: zlib1g (>= 1:1.2.3.3.dfsg) but it is not installed
           PreDepends: multiarch-support but it is not installed
           Recommends: xml-core but it is not installed
 libxmuu1 : Depends: libc6 (>= 2.4) but it is not installed
            Depends: libx11-6 but it is not installed
            PreDepends: multiarch-support but it is not installed
 libxres1 : Depends: libc6 (>= 2.1.3) but it is not installed
            Depends: libx11-6 but it is not installed
            Depends: x11-common but it is not installed
 libxslt1.1 : Depends: libc6 (>= 2.4) but it is not installed
              PreDepends: multiarch-support but it is not installed
 libxss1 : Depends: libc6 (>= 2.1.3) but it is not installed
           Depends: libx11-6 but it is not installed
           Depends: x11-common but it is not installed
           PreDepends: multiarch-support but it is not installed
 libxxf86dga1 : Depends: libc6 (>= 2.3.4) but it is not installed
                Depends: libx11-6 but it is not installed
                Depends: x11-common but it is not installed
 login : PreDepends: libc6 (>= 2.7) but it is not installed
         PreDepends: libpam-runtime but it is not installed
 lsb-base : Depends: sed but it is not installed
 lsb-release : Depends: python2.7 but it is not installed
 makedev : Depends: base-passwd (>= 3.0.4) but it is not installed
 man-db : Depends: groff-base (>= 1.18.1.1-15) but it is not installed
          Depends: bsdmainutils but it is not installed
          Depends: dpkg (>= 1.9.0) but it is not installed
          Depends: libc6 (>= 2.8) but it is not installed
          Depends: libpipeline1 (>= 1.1.0) but it is not installed
          Depends: zlib1g (>= 1:1.1.4) but it is not installed
 manpages-dev : Depends: manpages but it is not installed
 modemmanager : Depends: libc6 (>= 2.8) but it is not installed
                Depends: libglib2.0-0 (>= 2.31.2) but it is not installed
                Depends: upstart-job
                Recommends: usb-modeswitch but it is not installed
 module-init-tools : Depends: libc6 (>= 2.8) but it is not installed
                     Depends: upstart-job
                     PreDepends: dpkg (>= 1.15.7.2) but it is not installed
 mpg321 : Depends: libao4 (>= 1.1.0) but it is not installed
          Depends: libc6 (>= 2.7) but it is not installed
          Depends: libid3tag0 (>= 0.15.1b) but it is not installed
          Depends: libmad0 (>= 0.15.1b-3) but it is not installed
          Recommends: libaudio-scrobbler-perl but it is not installed
 mscompress : Depends: libc6 (>= 2.4) but it is not installed
 mtools : Depends: libc6 (>= 2.7) but it is not installed
 mtr-tiny : Depends: libc6 (>= 2.4) but it is not installed
            Depends: libncurses5 (>= 5.5-5~) but it is not installed
 ncurses-bin : PreDepends: libc6 (>= 2.4) but it is not installed
               PreDepends: libtinfo5 (>= 5.9-3~) but it is not installed
 netbase : Depends: initscripts but it is not installed
           Depends: upstart-job
 ntfs-3g : Depends: libc6 (>= 2.7) but it is not installed
           Depends: libgnutls26 (>= 2.12.6.1-0) but it is not installed
           Depends: initscripts (>= 2.88dsf-13.3) but it is not installed
           PreDepends: multiarch-support but it is not installed
           PreDepends: fuse but it is not installed
 obex-data-server : Depends: libbluetooth3 (>= 4.66) but it is not installed
                    Depends: libc6 (>= 2.7) but it is not installed
                    Depends: libglib2.0-0 (>= 2.16.0) but it is not installed
                    Depends: libopenobex1 but it is not installed
                    Recommends: python-gobject but it is not installed
 openprinting-ppds : Depends: xz-utils but it is not installed
                     Recommends: foomatic-filters but it is not installed
                     Recommends: cups but it is not installed
 openssl : Depends: libc6 (>= 2.15) but it is not installed
 pciutils : Depends: libc6 (>= 2.7) but it is not installed
 perl-base : PreDepends: libc6 (>= 2.11) but it is not installed
             PreDepends: dpkg (>= 1.14.20) but it is not installed
 perl-modules : Depends: perl (>= 5.14.2-1) but it is not installed
                Depends: libclass-isa-perl but it is not installed
 plymouth-theme-xubuntu-logo : Depends: plymouth but it is not installed
                               Depends: plymouth-label but it is not installed
 printer-driver-hpcups : Depends: libc6 (>= 2.15) but it is not installed
                         Depends: libcups2 (>= 1.4.0) but it is not installed
                         Depends: libcupsimage2 (>= 1.4.0) but it is not installed
                         Depends: libgcc1 (>= 1:4.1.1) but it is not installed
                         Depends: libhpmud0 but it is not installed
                         Depends: libjpeg8 (>= 8c) but it is not installed
                         Depends: libstdc++6 (>= 4.1.1) but it is not installed
                         Depends: ghostscript-cups but it is not installed
                         Depends: cups but it is not installed
 printer-driver-hpijs : Depends: libc6 (>= 2.4) but it is not installed
                        Depends: libgcc1 (>= 1:4.1.1) but it is not installed
                        Depends: libhpmud0 (= 3.12.2-1ubuntu3) but it is not installed
                        Depends: libjpeg8 (>= 8c) but it is not installed
                        Depends: libstdc++6 (>= 4.1.1) but it is not installed
                        Recommends: ghostscript but it is not installed
                        Recommends: foomatic-filters but it is not installed
 printer-driver-pxljr : Depends: libc6 (>= 2.4) but it is not installed
                        Depends: libijs-0.35 (>= 0.35) but it is not installed
                        Depends: libjpeg8 (>= 8c) but it is not installed
                        Depends: xz-utils but it is not installed
                        Depends: foomatic-filters (>= 4.0.0~bzr156) but it is not installed
 procps : Depends: libc6 (>= 2.4) but it is not installed
          Depends: libncurses5 (>= 5.5-5~) but it is not installed
          Depends: libncursesw5 (>= 5.6+20070908) but it is not installed
          Depends: libtinfo5 but it is not installed
          Depends: upstart-job
          Depends: initscripts but it is not installed
 psmisc : Depends: libc6 (>= 2.8) but it is not installed
          Depends: libtinfo5 but it is not installed
 pulseaudio-module-x11 : Depends: libc6 (>= 2.4) but it is not installed
                         Depends: libice6 (>= 1:1.0.0) but it is not installed
                         Depends: libpulse0 (>= 1:1.1-0ubuntu15) but it is not installed
                         Depends: libsm6 but it is not installed
                         Depends: libx11-6 but it is not installed
                         Depends: libxcb1 but it is not installed
                         Depends: libxtst6 but it is not installed
                         Depends: pulseaudio but it is not installed
 pulseaudio-utils : Depends: libc6 (>= 2.4) but it is not installed
                    Depends: libice6 (>= 1:1.0.0) but it is not installed
                    Depends: libpulse0 (>= 1:1.1-0ubuntu15) but it is not installed
                    Depends: libsm6 but it is not installed
                    Depends: libsndfile1 (>= 1.0.20) but it is not installed
                    Depends: libx11-6 but it is not installed
                    Depends: libx11-xcb1 but it is not installed
                    Depends: libxcb1 but it is not installed
                    Depends: libxtst6 but it is not installed
                    Depends: libpulsedsp but it is not installed
 python : Depends: python2.7 (>= 2.7.3) but it is not installed
 python-apport : Depends: python2.7 but it is not installed
                 Depends: python-apt (>= 0.7.9) but it is not installed
                 Depends: python-problem-report (>= 0.94) but it is not installed
                 Depends: python-launchpadlib (>= 1.5.7) but it is not installed
 python-aptdaemon : Depends: python2.7 but it is not installed
                    Depends: python-apt (>= 0.7.96.1ubuntu9) but it is not installed
                    Depends: python-debian but it is not installed
                    Depends: gir1.2-glib-2.0 but it is not installed
                    Depends: policykit-1 but it is not installed
                    Recommends: aptdaemon but it is not installed
 python-configobj : Depends: python2.7 but it is not installed
 python-dbus : Depends: python2.7 but it is not installed
               Depends: libc6 (>= 2.4) but it is not installed
               Depends: libglib2.0-0 (>= 2.12.0) but it is not installed
               Depends: python-dbus-dev but it is not installed
 python-defer : Depends: python2.7 but it is not installed
 python-gi : Depends: python2.7 but it is not installed
             Depends: libc6 (>= 2.4) but it is not installed
             Depends: libgirepository-1.0-1 (>= 1.29.0) but it is not installed
             Depends: libglib2.0-0 (>= 2.31.8) but it is not installed
             Depends: gir1.2-glib-2.0 (>= 1.31.0) but it is not installed
 python-gnupginterface : Depends: python2.7 but it is not installed
                         Depends: gnupg (>= 1.2.1) but it is not installed or
                                  gnupg2 but it is not installed
 python-ibus : Depends: python2.7 but it is not installed
               Depends: python-gtk2 but it is not installed
               Depends: iso-codes but it is not installed
 python-minimal : Depends: python2.7-minimal (>= 2.7.3) but it is not installed
                  Depends: dpkg (>= 1.13.20) but it is not installed
 python-reportlab : Depends: python2.7 but it is not installed
                    Recommends: python-reportlab-accel but it is not installed
                    Recommends: python-renderpm but it is not installed
                    Recommends: python-imaging (>= 1.1.6) but it is not installed
 python-software-properties : Depends: python2.7 but it is not installed
                              Depends: python-apt (>= 0.6.20ubuntu16) but it is not installed
                              Depends: unattended-upgrades but it is not installed
                              Depends: iso-codes but it is not installed
                              Depends: python-pycurl but it is not installed
 python-twisted-bin : Depends: python2.7 but it is not installed
                      Depends: libc6 (>= 2.3.6-6~) but it is not installed
 python-twisted-web : Depends: python2.7 but it is not installed
                      Depends: python-twisted-core (>= 11.1) but it is not installed
 python-zope.interface : Depends: python2.7 but it is not installed
                         Depends: libc6 (>= 2.3.6-6~) but it is not installed
 rfkill : Depends: libc6 (>= 2.4) but it is not installed
          Depends: upstart-job
 sane-utils : Depends: adduser (>= 3.47) but it is not installed
              Depends: libavahi-client3 (>= 0.6.16) but it is not installed
              Depends: libavahi-common3 (>= 0.6.16) but it is not installed
              Depends: libc6 (>= 2.4) but it is not installed
              Depends: libieee1284-3 but it is not installed
 shared-mime-info : Depends: libc6 (>= 2.3) but it is not installed
                    Depends: libglib2.0-0 (>= 2.24.0) but it is not installed
 shimmer-themes : Depends: gtk3-engines-unico (>= 1.0.1) but it is not installed
 ssl-cert : Depends: adduser but it is not installed
 sudo : Depends: libc6 (>= 2.15) but it is not installed
 syslinux-legacy : Depends: libc6 (>= 2.4) but it is not installed
 system-config-printer-gnome : Depends: system-config-printer-common but it is not installed
                               Depends: python-gtk2 but it is not installed
                               Depends: python-notify but it is not installed
                               Depends: python-gobject but it is not installed
                               Depends: gnome-icon-theme but it is not installed
                               Depends: python-libxml2 but it is not installed
                               Depends: python-gnomekeyring but it is not installed
 sysv-rc : Depends: sysvinit-utils (>= 2.86.ds1-62) but it is not installed
           Depends: insserv (> 1.12.0-10) but it is not installed
 tcl8.5 : Depends: libc6 (>= 2.7) but it is not installed
 tcpd : Depends: libc6 (>= 2.4) but it is not installed
        Depends: libwrap0 (>= 7.6-4~) but it is not installed
 telnet : Depends: libc6 (>= 2.11) but it is not installed
          Depends: libgcc1 (>= 1:4.1.1) but it is not installed
          Depends: libncurses5 (>= 5.6+20071006-3) but it is not installed
          Depends: libstdc++6 (>= 4.1.1) but it is not installed
 thunar : Depends: libatk1.0-0 (>= 1.12.4) but it is not installed
          Depends: libc6 (>= 2.4) but it is not installed
          Depends: libexo-1-0 (>= 0.5.0) but it is not installed
          Depends: libglib2.0-0 (>= 2.31.8) but it is not installed
          Depends: libgtk2.0-0 (>= 2.24.0) but it is not installed
          Depends: libice6 (>= 1:1.0.0) but it is not installed
          Depends: libpango1.0-0 (>= 1.14.0) but it is not installed
          Depends: libsm6 but it is not installed
          Depends: libthunarx-2-0 (>= 1.1.0) but it is not installed
          Depends: libxfce4ui-1-0 but it is not installed
          Depends: libxfce4util4 (>= 4.3.99.2) but it is not installed
          Depends: thunar-data (= 1.2.3-3ubuntu2) but it is not installed
          Depends: exo-utils but it is not installed
          Recommends: dbus-x11 but it is not installed
          Recommends: thunar-volman but it is not installed
          Recommends: tumbler but it is not installed
          Recommends: xdg-user-dirs but it is not installed
          Recommends: gvfs but it is not installed
 thunderbird-globalmenu : Depends: libc6 (>= 2.4) but it is not installed
                          Depends: libdbusmenu-gtk4 (>= 0.4.2) but it is not installed
                          Depends: libglib2.0-0 (>= 2.26.0) but it is not installed
                          Depends: libgtk2.0-0 (>= 2.24.0) but it is not installed
                          Depends: libstdc++6 (>= 4.1.1) but it is not installed
                          Depends: thunderbird (= 12.0.1+build1-0ubuntu0.12.04.1) but it is not installed
 thunderbird-locale-en : Depends: thunderbird but it is not installed
 ubuntu-extras-keyring : Depends: gnupg but it is not installed
 ubuntu-sso-client-gtk : Depends: python2.7 but it is not installed
                         Depends: gir1.2-glib-2.0 but it is not installed
                         Depends: gir1.2-gtk-3.0 but it is not installed
                         Depends: gir1.2-webkit-3.0 but it is not installed
                         Depends: python-ubuntu-sso-client (= 3.0.0-0ubuntu2) but it is not installed
                         Depends: ubuntu-sso-client (= 3.0.0-0ubuntu2) but it is not installed
 ubuntu-standard : Depends: at but it is not installed
                   Depends: busybox-static but it is not installed
                   Depends: cpio but it is not installed
                   Depends: cron
                   Depends: dosfstools but it is not installed
                   Depends: ed but it is not installed
                   Depends: file but it is not installed
                   Depends: ftp
                   Depends: hdparm but it is not installed
                   Depends: info but it is not installed
                   Depends: iptables but it is not installed
                   Depends: language-selector-common but it is not installed
                   Depends: logrotate but it is not installed
                   Depends: lshw but it is not installed
                   Depends: lsof but it is not installed
                   Depends: ltrace but it is not installed
                   Depends: mime-support but it is not installed
                   Depends: parted but it is not installed
                   Depends: popularity-contest but it is not installed
                   Depends: rsync but it is not installed
                   Depends: strace but it is not installed
                   Depends: time but it is not installed
                   Depends: usbutils but it is not installed
                   Depends: wget but it is not installed
                   Recommends: apparmor but it is not installed
                   Recommends: bash-completion but it is not installed
                   Recommends: command-not-found but it is not installed
                   Recommends: friendly-recovery but it is not installed
                   Recommends: iputils-tracepath but it is not installed
                   Recommends: irqbalance but it is not installed
                   Recommends: manpages but it is not installed
                   Recommends: mlocate but it is not installed
                   Recommends: nano but it is not installed
                   Recommends: openssh-client but it is not installed
                   Recommends: plymouth but it is not installed
                   Recommends: plymouth-theme-ubuntu-text but it is not installed
                   Recommends: ppp but it is not installed
                   Recommends: pppconfig but it is not installed
                   Recommends: pppoeconf but it is not installed
                   Recommends: tcpdump but it is not installed
                   Recommends: ufw but it is not installed
                   Recommends: update-manager-core but it is not installed
                   Recommends: uuid-runtime but it is not installed
 update-inetd : Depends: libfile-copy-recursive-perl but it is not installed
 usb-creator-common : Depends: python2.7 but it is not installed
                      Depends: syslinux but it is not installed
                      Depends: udisks (>= 1.0~) but it is not installed
                      Depends: udisks (< 1.1) but it is not installed
                      Depends: genisoimage but it is not installed
                      Depends: parted but it is not installed
                      Depends: python-debian but it is not installed
 vim-common : Depends: libc6 (>= 2.3.4) but it is not installed
              Recommends: vim or
                          vim-gnome but it is not installed or
                          vim-gtk but it is not installed or
                          vim-athena but it is not installed or
                          vim-nox but it is not installed or
                          vim-tiny but it is not installed
 vorbis-tools : Depends: libao4 (>= 1.1.0) but it is not installed
                Depends: libc6 (>= 2.15) but it is not installed
                Depends: libvorbis0a (>= 1.1.2) but it is not installed
                Depends: libvorbisenc2 (>= 1.1.2) but it is not installed
 whiptail : Depends: libc6 (>= 2.4) but it is not installed
            Depends: libnewt0.52 (>= 0.52.11) but it is not installed
            Depends: libslang2 (>= 2.0.7-1) but it is not installed
 wpasupplicant : Depends: libc6 (>= 2.15) but it is not installed
                 Depends: libnl-genl-3-200 (>= 3.2.3) but it is not installed
                 Depends: libpcsclite1 but it is not installed
                 Depends: libreadline6 (>= 6.0) but it is not installed
                 Depends: adduser but it is not installed
                 Depends: initscripts (>= 2.88dsf-13.3) but it is not installed
 x11-xkb-utils : Depends: libc6 (>= 2.7) but it is not installed
                 Depends: libx11-6 but it is not installed
                 Depends: libxaw7 but it is not installed
                 Depends: libxt6 but it is not installed
 xdg-user-dirs-gtk : Depends: libc6 (>= 2.2) but it is not installed
                     Depends: libglib2.0-0 (>= 2.12.0) but it is not installed
                     Depends: libgtk-3-0 (>= 3.0.0) but it is not installed
                     Depends: xdg-user-dirs but it is not installed
 xfburn : Depends: libburn4 (>= 1.1.6) but it is not installed
          Depends: libc6 (>= 2.4) but it is not installed
          Depends: libexo-1-0 (>= 0.5.0) but it is not installed
          Depends: libglib2.0-0 (>= 2.24.0) but it is not installed
          Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.12) but it is not installed
          Depends: libgstreamer0.10-0 (>= 0.10.0) but it is not installed
          Depends: libgtk2.0-0 (>= 2.14.0) but it is not installed
          Depends: libisofs6 (>= 1.1.6) but it is not installed
          Depends: libxfce4ui-1-0 but it is not installed
          Depends: libxfce4util4 (>= 4.3.99.2) but it is not installed
 xfce4-cpugraph-plugin : Depends: libc6 (>= 2.4) but it is not installed
                         Depends: libglib2.0-0 (>= 2.18.0) but it is not installed
                         Depends: libgtk2.0-0 (>= 2.14.0) but it is not installed
                         Depends: libxfce4util4 (>= 4.3.99.2) but it is not installed
                         Depends: libxfcegui4-4 (>= 4.7.0) but it is not installed
 xfce4-datetime-plugin : Depends: libc6 (>= 2.4) but it is not installed
                         Depends: libglib2.0-0 (>= 2.18.0) but it is not installed
                         Depends: libgtk2.0-0 (>= 2.8.0) but it is not installed
                         Depends: libpango1.0-0 (>= 1.14.0) but it is not installed
                         Depends: libxfce4util4 (>= 4.3.99.2) but it is not installed
                         Depends: libxfcegui4-4 (>= 4.7.0) but it is not installed
 xfce4-indicator-plugin : Depends: libc6 (>= 2.4) but it is not installed
                          Depends: libglib2.0-0 (>= 2.18.0) but it is not installed
                          Depends: libgtk2.0-0 (>= 2.24.0) but it is not installed
                          Depends: libindicator7 (>= 0.4.90) but it is not installed
                          Depends: libxfce4util4 (>= 4.3.99.2) but it is not installed
                          Recommends: indicator-messages-gtk2 but it is not installed
 xfce4-panel : Depends: libatk1.0-0 (>= 1.12.4) but it is not installed
               Depends: libc6 (>= 2.4) but it is not installed
               Depends: libexo-1-0 (>= 0.5.0) but it is not installed
               Depends: libgarcon-1-0 (>= 0.1.2) but it is not installed
               Depends: libglib2.0-0 (>= 2.24.0) but it is not installed
               Depends: libgtk2.0-0 (>= 2.24.0) but it is not installed
               Depends: libpango1.0-0 (>= 1.14.0) but it is not installed
               Depends: libwnck22 (>= 1:2.22) but it is not installed
               Depends: libx11-6 but it is not installed
               Depends: libxfce4ui-1-0 but it is not installed
               Depends: libxfce4util4 (>= 4.3.99.2) but it is not installed
               Depends: libxfconf-0-2 (>= 4.6.0) but it is not installed
               Depends: exo-utils but it is not installed
               PreDepends: dpkg (>= 1.15.7.2) but it is not installed
               PreDepends: multiarch-support but it is not installed
 xfce4-power-manager : Depends: libc6 (>= 2.4) but it is not installed
                       Depends: libglib2.0-0 (>= 2.24.0) but it is not installed
                       Depends: libgtk2.0-0 (>= 2.24.0) but it is not installed
                       Depends: libx11-6 but it is not installed
                       Depends: libxfce4ui-1-0 but it is not installed
                       Depends: libxfce4util4 (>= 4.6.0) but it is not installed
                       Depends: libxfconf-0-2 (>= 4.6.0) but it is not installed
                       Depends: libxrandr2 (>= 2:1.2.99.2) but it is not installed
                       Depends: upower but it is not installed
                       Depends: xfce4-power-manager-data (= 1.0.11-0ubuntu2) but it is not installed
                       Recommends: consolekit but it is not installed
 xfce4-verve-plugin : Depends: libc6 (>= 2.4) but it is not installed
                      Depends: libglib2.0-0 (>= 2.18.0) but it is not installed
                      Depends: libgtk2.0-0 (>= 2.14.0) but it is not installed
                      Depends: libpcre3 (>= 8.10) but it is not installed
                      Depends: libxfce4util4 (>= 4.3.99.2) but it is not installed
                      Depends: libxfcegui4-4 (>= 4.7.0) but it is not installed
                      Depends: exo-utils but it is not installed
 xfce4-weather-plugin : Depends: libc6 (>= 2.11) but it is not installed
                        Depends: libglib2.0-0 (>= 2.18.0) but it is not installed
                        Depends: libgtk2.0-0 (>= 2.14.0) but it is not installed
                        Depends: libpango1.0-0 (>= 1.14.0) but it is not installed
                        Depends: libxfce4util4 (>= 4.3.99.2) but it is not installed
                        Depends: libxfcegui4-4 (>= 4.7.0) but it is not installed
 xfdesktop4 : Depends: libc6 (>= 2.4) but it is not installed
              Depends: libexo-1-0 (>= 0.5.0) but it is not installed
              Depends: libgarcon-1-0 (>= 0.1.2) but it is not installed
              Depends: libglib2.0-0 (>= 2.31.8) but it is not installed
              Depends: libgtk2.0-0 (>= 2.24.0) but it is not installed
              Depends: libpango1.0-0 (>= 1.14.0) but it is not installed
              Depends: libthunarx-2-0 (>= 1.1.0) but it is not installed
              Depends: libwnck22 (>= 1:2.22) but it is not installed
              Depends: libx11-6 but it is not installed
              Depends: libxfce4ui-1-0 but it is not installed
              Depends: libxfce4util4 (>= 4.6.0) but it is not installed
              Depends: libxfconf-0-2 (>= 4.6.0) but it is not installed
              Depends: xfdesktop4-data (= 4.8.3-2ubuntu7) but it is not installed
              Depends: exo-utils but it is not installed
              Recommends: dbus-x11 but it is not installed
              Recommends: librsvg2-common but it is not installed
              Recommends: xdg-user-dirs but it is not installed
              Recommends: xfce4-utils but it is not installed
              Recommends: tumbler but it is not installed
 xorg : Depends: xserver-xorg (>= 1:7.6+12ubuntu1) but it is not installed
        Depends: libgl1-mesa-glx but it is not installed or
                 libgl1
        Depends: libglu1-mesa but it is not installed
        Depends: xfonts-base (>= 1:1.0.0-1) but it is not installed
        Depends: x11-apps but it is not installed
        Depends: x11-session-utils but it is not installed
        Depends: x11-utils but it is not installed
        Depends: x11-xfs-utils but it is not installed
        Depends: x11-xserver-utils but it is not installed
        Depends: xauth but it is not installed
        Depends: xinit but it is not installed
        Depends: xfonts-utils but it is not installed
        Depends: xkb-data but it is not installed
        Depends: xorg-docs-core but it is not installed
        Depends: x11-common but it is not installed
        Depends: xinput but it is not installed
        Recommends: xfonts-scalable (>= 1:1.0.0-1) but it is not installed
 xscreensaver-data : Depends: libc6 (>= 2.7) but it is not installed
                     Depends: libglib2.0-0 (>= 2.12.0) but it is not installed
                     Depends: libx11-6 but it is not installed
                     Depends: libxmu6 but it is not installed
                     Depends: libxt6 but it is not installed
 xserver-common : Depends: x11-common but it is not installed
                  Depends: xkb-data but it is not installed
                  Recommends: xfonts-base but it is not installed
                  Recommends: xauth but it is not installed
 xserver-xorg-core : Depends: keyboard-configuration but it is not installed
                     Depends: udev (>= 149) but it is not installed
                     Depends: libc6 (>= 2.15) but it is not installed
                     Depends: libpciaccess0 (>= 0.10.7) but it is not installed
                     Depends: libpixman-1-0 (>= 0.21.6) but it is not installed
                     Depends: libxau6 but it is not installed
                     Depends: libxfont1 (>= 1:1.4.2) but it is not installed
 xserver-xorg-input-vmmouse : Depends: libc6 (>= 2.7) but it is not installed
                              Depends: xserver-xorg-input-mouse but it is not installed
                              Depends: udev but it is not installed
 xserver-xorg-input-wacom : Depends: libc6 (>= 2.4) but it is not installed
                            Depends: libx11-6 but it is not installed
                            Depends: libxi6 (>= 2:1.2.0) but it is not installed
                            Depends: libxrandr2 (>= 2:1.2.0) but it is not installed
 xserver-xorg-video-openchrome : Depends: libc6 (>= 2.4) but it is not installed
                                 Depends: libx11-6 (>= 2:1.4.99.1) but it is not installed
                                 Depends: libxv1 but it is not installed
                                 Depends: libxvmc1 but it is not installed
 xserver-xorg-video-radeon : Depends: libc6 (>= 2.7) but it is not installed
                             Depends: libdrm-radeon1 (>= 2.4.17) but it is not installed
                             Depends: libpciaccess0 (>= 0.10.2) but it is not installed
                             Depends: libpixman-1-0 but it is not installed
 xserver-xorg-video-sis : Depends: libc6 (>= 2.7) but it is not installed
 xserver-xorg-video-vmware : Depends: libc6 (>= 2.4) but it is not installed
                             Depends: libx11-6 (>= 2:1.4.99.1) but it is not installed
                             Depends: libxatracker1 but it is not installed
 xterm : Depends: xbitmaps but it is not installed
         Depends: libc6 (>= 2.11) but it is not installed
         Depends: libice6 (>= 1:1.0.0) but it is not installed
         Depends: libncurses5 (>= 5.5-5~) but it is not installed
         Depends: libx11-6 but it is not installed
         Depends: libxaw7 but it is not installed
         Depends: libxft2 (> 2.1.1) but it is not installed
         Depends: libxmu6 but it is not installed
         Depends: libxt6 but it is not installed
         Recommends: x11-utils but it is not installed
E: Unmet dependencies. Try using -f.
```


heres the code I got when i tried that and you were right when i ran from a boot disk and did a hard drive check up on my system I found that my main partition is going bad it said "FAILURE IMMINENT"

---

### Post by Shadius on 2012-06-25
If you have bad sectors on the hard disk drive those files in those bad sectors might not be accessible so that's why using the Update Manager isn't working. Your hard disk drive is about to die so I suggest you back up your data and use another hard disk drive.

---

