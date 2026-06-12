---
title: "Unable to update Dell with factory installed Ubuntu"
date: 2016-07-04
forum: Installation &amp; Upgrades
---

### Post by Raymond H. on 2016-07-04
I have a Dell Inspiron 14 3000 with Ubuntu 14.04 LTS factory installed.  Every time that I try to update Ubuntu, the computer crashes :( and I have to reinstall from the hard disk backup.  Help this is a cool computer with serious flaw.

---

### Post by grahammechanical on 2016-07-04
Describe the crash. What happens? We have no clues as to what is happening. How are you trying to update? Though Software Updater? Through terminal commands? The term "crashes" can mean anything or nothing unless you explain what is happening.

Can you not shut down and restart? Updating is a very CPU intensive activity. That generates heat. If the laptop is overheating then it may shutdown. Is there enough ventilation? Are the fans working? Shooting in the dark is all we can do.

Regards.

---

### Post by Raymond H. on 2016-07-05
I am using the Software Updated.  The program downloaded the updates and unpackage them.  That is when the problem started on the installs.  I was not able to record the problem but it said something about the installed packages have dependency problems and the installer shut down early.  I was unable to restart on the computer.   Had to use the power switch.  Now the computer start in a blue screen and will not respond.  I'll try Synaptic package manger after I rebuild the system.

---

### Post by Geoffrey_Arndt on 2016-07-07
Also include a copy of your sources file - - is this a standard Ubuntu Unity DE (version 14.04).    If you're installing and re-installing all the time, why not just install 16.04 - - the latest Ubuntu released.   Might get a better result because the software sources should be clean (no PPA's, etc.)

---

### Post by kansasnoob on 2016-07-07
Most vendors use full disk encryption for OEM installs. It might be helpful if you'd post the output of these commands once you've restored the OS **before trying to update**:

```
sudo parted -l
```

```
df -H
```

What I specifically want to rule out is a lack of space in /boot.

---

### Post by Raymond H. on 2016-07-07
This is after I re-installed from the hard drive partition.

sudo parted -l
[sudo] password for test: 
Model: ATA TOSHIBA MQ01ABF0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  525MB   524MB   fat32           EFI system partition  boot
 2      525MB   567MB   41.9MB  fat32           Basic data partition  hidden
 3      567MB   3789MB  3221MB  fat32           Basic data partition  msftdata
 4      3789MB  492GB   488GB   ext4
 5      492GB   500GB   8344MB  linux-swap(v1)

 df -H
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda4       481G  4.8G  451G   2% /
none            4.1k     0  4.1k   0% /sys/fs/cgroup
udev            2.0G  4.1k  2.0G   1% /dev
tmpfs           403M  1.1M  402M   1% /run
none            5.3M     0  5.3M   0% /run/lock
none            2.1G   15M  2.0G   1% /run/shm
none            105M   41k  105M   1% /run/user
/dev/sda1       521M   20M  501M   4% /boot/efi

---

### Post by kansasnoob on 2016-07-08
> **Raymond H. said:**
> This is after I re-installed from the hard drive partition.

sudo parted -l
[sudo] password for test: 
Model: ATA TOSHIBA MQ01ABF0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  525MB   524MB   fat32           EFI system partition  boot
 2      525MB   567MB   41.9MB  fat32           Basic data partition  hidden
 3      567MB   3789MB  3221MB  fat32           Basic data partition  msftdata
 4      3789MB  492GB   488GB   ext4
 5      492GB   500GB   8344MB  linux-swap(v1)

 df -H
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda4       481G  4.8G  451G   2% /
none            4.1k     0  4.1k   0% /sys/fs/cgroup
udev            2.0G  4.1k  2.0G   1% /dev
tmpfs           403M  1.1M  402M   1% /run
none            5.3M     0  5.3M   0% /run/lock
none            2.1G   15M  2.0G   1% /run/shm
none            105M   41k  105M   1% /run/user
/dev/sda1       521M   20M  501M   4% /boot/efi

That all looks fine to me. Please post the full output of these two commands [using code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168"):

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade -s
```

The -s at the end of that last command stands for simulate so no upgrades will actually be applied, but hopefully the output of those two commands will give us an idea what's going wrong.

---

### Post by Raymond H. on 2016-07-10
Here is the first command.

```

sudo apt-get update
[sudo] password for test: 
Ign http://dl.google.com stable InRelease
Get:1 http://dl.google.com stable Release.gpg [916 B]                          
Get:2 http://dl.google.com stable Release [1,189 B]                            
Get:3 http://dl.google.com stable/main amd64 Packages [1,349 B]                
Get:4 http://security.ubuntu.com trusty-security InRelease [65.9 kB]           
Ign http://archive.ubuntu.com trusty InRelease                                 
Ign http://archive.canonical.com trusty InRelease                              
Get:5 http://archive.ubuntu.com trusty-updates InRelease [65.9 kB]             
Get:6 http://archive.canonical.com trusty Release.gpg [933 B]                  
Ign http://dell.archive.canonical.com trusty-dell InRelease                    
Ign http://oem.archive.canonical.com trusty-oem InRelease                      
Get:7 http://archive.canonical.com trusty Release [9,359 B]                    
Get:8 http://dell.archive.canonical.com trusty-dell Release.gpg [287 B]        
Get:9 http://oem.archive.canonical.com trusty-oem Release.gpg [287 B]          
Get:10 http://security.ubuntu.com trusty-security/main Sources [118 kB]        
Get:11 http://dell.archive.canonical.com trusty-dell Release [4,839 B]         
Get:12 http://archive.canonical.com trusty/partner Sources [10.0 kB]           
Get:13 http://archive.ubuntu.com trusty-backports InRelease [65.9 kB]          
Get:14 http://oem.archive.canonical.com trusty-oem Release [4,234 B]           
Get:15 http://archive.canonical.com trusty/partner amd64 Packages [5,614 B]    
Get:16 http://dell.archive.canonical.com trusty-dell/public Sources [2,719 B]  
Get:17 http://archive.ubuntu.com trusty Release.gpg [933 B]                    
Get:18 http://oem.archive.canonical.com trusty-oem/public Sources [1,671 B]    
Get:19 http://archive.canonical.com trusty/partner i386 Packages [6,281 B]     
Get:20 http://security.ubuntu.com trusty-security/restricted Sources [4,035 B] 
Get:21 http://dell.archive.canonical.com trusty-dell/public amd64 Packages [3,132 B]
Get:22 http://archive.ubuntu.com trusty-updates/main Sources [278 kB]          
Get:23 http://oem.archive.canonical.com trusty-oem/public amd64 Packages [1,845 B]
Get:24 http://archive.canonical.com trusty/partner Translation-en [4,593 B]    
Get:25 http://security.ubuntu.com trusty-security/universe Sources [38.0 kB]   
Get:26 http://dell.archive.canonical.com trusty-dell/public i386 Packages [3,140 B]
Get:27 http://oem.archive.canonical.com trusty-oem/public i386 Packages [1,859 B]
Get:28 http://security.ubuntu.com trusty-security/multiverse Sources [2,757 B] 
Get:29 http://archive.ubuntu.com trusty-updates/restricted Sources [5,352 B]   
Get:30 http://security.ubuntu.com trusty-security/main amd64 Packages [502 kB] 
Get:31 http://archive.ubuntu.com trusty-updates/universe Sources [158 kB]      
Get:32 http://archive.ubuntu.com trusty-updates/multiverse Sources [5,936 B]   
Get:33 http://archive.ubuntu.com trusty-updates/main amd64 Packages [791 kB]   
Get:34 http://security.ubuntu.com trusty-security/restricted amd64 Packages [13.0 kB]
Get:35 http://security.ubuntu.com trusty-security/universe amd64 Packages [130 kB]
Get:36 http://archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.9 kB]
Get:37 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [4,989 B]
Get:38 http://archive.ubuntu.com trusty-updates/universe amd64 Packages [363 kB]
Get:39 http://security.ubuntu.com trusty-security/main i386 Packages [469 kB]  
Ign http://oem.archive.canonical.com trusty-oem/public Translation-en_US       
Get:40 http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages [13.2 kB]
Ign http://dell.archive.canonical.com trusty-dell/public Translation-en_US     
Ign http://oem.archive.canonical.com trusty-oem/public Translation-en          
Get:41 http://archive.ubuntu.com trusty-updates/main i386 Packages [757 kB]    
Ign http://dell.archive.canonical.com trusty-dell/public Translation-en        
Get:42 http://security.ubuntu.com trusty-security/restricted i386 Packages [12.7 kB]
Get:43 http://security.ubuntu.com trusty-security/universe i386 Packages [130 kB]
Get:44 http://security.ubuntu.com trusty-security/multiverse i386 Packages [5,170 B]
Get:45 http://archive.ubuntu.com trusty-updates/restricted i386 Packages [15.6 kB]
Get:46 http://security.ubuntu.com trusty-security/main Translation-en [277 kB] 
Get:47 http://archive.ubuntu.com trusty-updates/universe i386 Packages [365 kB]
Get:48 http://archive.ubuntu.com trusty-updates/multiverse i386 Packages [13.6 kB]
Get:49 http://archive.ubuntu.com trusty-updates/main Translation-en [396 kB]   
Get:50 http://security.ubuntu.com trusty-security/multiverse Translation-en [2,570 B]
Get:51 http://security.ubuntu.com trusty-security/restricted Translation-en [3,206 B]
Get:52 http://archive.ubuntu.com trusty-updates/multiverse Translation-en [7,227 B]
Get:53 http://security.ubuntu.com trusty-security/universe Translation-en [77.2 kB]
Get:54 http://archive.ubuntu.com trusty-updates/restricted Translation-en [3,699 B]
Get:55 http://archive.ubuntu.com trusty-updates/universe Translation-en [191 kB]
Get:56 http://archive.ubuntu.com trusty-backports/main Sources [9,561 B]
Get:57 http://archive.ubuntu.com trusty-backports/restricted Sources [28 B]
Get:58 http://archive.ubuntu.com trusty-backports/universe Sources [35.2 kB]
Get:59 http://archive.ubuntu.com trusty-backports/multiverse Sources [1,898 B]
Get:60 http://archive.ubuntu.com trusty-backports/main amd64 Packages [13.3 kB]
Get:61 http://archive.ubuntu.com trusty-backports/restricted amd64 Packages [28 B]
Get:62 http://archive.ubuntu.com trusty-backports/universe amd64 Packages [43.2 kB]
Get:63 http://archive.ubuntu.com trusty-backports/multiverse amd64 Packages [1,571 B]
Get:64 http://archive.ubuntu.com trusty-backports/main i386 Packages [13.3 kB]
Get:65 http://archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Get:66 http://archive.ubuntu.com trusty-backports/universe i386 Packages [43.2 kB]
Get:67 http://archive.ubuntu.com trusty-backports/multiverse i386 Packages [1,552 B]
Get:68 http://archive.ubuntu.com trusty-backports/main Translation-en [7,493 B]
Get:69 http://archive.ubuntu.com trusty-backports/multiverse Translation-en [1,215 B]
Get:70 http://archive.ubuntu.com trusty-backports/restricted Translation-en [28 B]
Get:71 http://archive.ubuntu.com trusty-backports/universe Translation-en [36.8 kB]
Get:72 http://archive.ubuntu.com trusty Release [58.5 kB]                      
Get:73 http://archive.ubuntu.com trusty/main Sources [1,064 kB]                
Get:74 http://archive.ubuntu.com trusty/restricted Sources [5,433 B]           
Get:75 http://archive.ubuntu.com trusty/universe Sources [6,399 kB]            
Get:76 http://archive.ubuntu.com trusty/multiverse Sources [174 kB]            
Get:77 http://archive.ubuntu.com trusty/main amd64 Packages [1,350 kB]         
Get:78 http://archive.ubuntu.com trusty/restricted amd64 Packages [13.0 kB]    
Get:79 http://archive.ubuntu.com trusty/universe amd64 Packages [5,859 kB]     
Get:80 http://archive.ubuntu.com trusty/multiverse amd64 Packages [132 kB]     
Get:81 http://archive.ubuntu.com trusty/main i386 Packages [1,348 kB]          
Get:82 http://archive.ubuntu.com trusty/restricted i386 Packages [13.4 kB]     
Get:83 http://archive.ubuntu.com trusty/universe i386 Packages [5,866 kB]      
Get:84 http://archive.ubuntu.com trusty/multiverse i386 Packages [134 kB]      
Get:85 http://archive.ubuntu.com trusty/main Translation-en [762 kB]           
Get:86 http://archive.ubuntu.com trusty/multiverse Translation-en [102 kB]     
Get:87 http://archive.ubuntu.com trusty/restricted Translation-en [3,457 B]    
Get:88 http://archive.ubuntu.com trusty/universe Translation-en [4,089 kB]     
Ign http://archive.ubuntu.com trusty/main Translation-en_US                    
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US              
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US              
Ign http://archive.ubuntu.com trusty/universe Translation-en_US                
Fetched 33.0 MB in 26s (1,242 kB/s)                                            
W: There is no public key available for the following key IDs:
1397BC53640DB551
W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

I have seen this problem with Google repositories.

Here is the second command.

```

sudo apt-get dist-upgrade -s>output.txt
[sudo] password for test: 
Reading package lists...
Building dependency tree...
Reading state information...
The following packages were automatically installed and are no longer required:
  apt-clone archdetect-deb autogen binutils-mingw-w64-i686
  binutils-mingw-w64-x86-64 dmraid g++-mingw-w64 g++-mingw-w64-i686
  g++-mingw-w64-x86-64 gcc-mingw-w64 gcc-mingw-w64-base gcc-mingw-w64-i686
  gcc-mingw-w64-x86-64 gfortran-mingw-w64 gfortran-mingw-w64-i686
  gfortran-mingw-w64-x86-64 gir1.2-json-1.0 gir1.2-timezonemap-1.0
  gir1.2-xkl-1.0 gnat-mingw-w64 gnat-mingw-w64-base gnat-mingw-w64-i686
  gnat-mingw-w64-x86-64 javascript-common kpartx kpartx-boot
  libdebian-installer4 libdevmapper-event1.02.1 libdmraid1.0.0.rc16
  libjs-jquery libjs-jquery-ui libopts25 libopts25-dev lvm2 mingw-w64
  mingw-w64-common mingw-w64-i686-dev mingw-w64-x86-64-dev python3-icu
  python3-pam quilt rdate watershed
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  libandroid-properties1 liboxideqtquick0 libxcb-keysyms1 libxkbcommon-x11-0
  linux-headers-3.13.0-91 linux-headers-3.13.0-91-generic
  linux-image-3.13.0-91-generic linux-image-extra-3.13.0-91-generic
  python-requests python-urllib3
The following packages will be upgraded:
  account-plugin-aim account-plugin-facebook account-plugin-flickr
  account-plugin-google account-plugin-jabber account-plugin-salut
  account-plugin-twitter account-plugin-windows-live account-plugin-yahoo
  accountsservice activity-log-manager activity-log-manager-control-center
  apparmor apport apport-gtk apt apt-clone apt-transport-https apt-utils
  aptdaemon aptdaemon-data archdetect-deb base-files bash bash-completion
  bind9-host binutils bluez bluez-alsa bluez-cups bsdutils btrfs-tools
  ca-certificates casper compiz compiz-core compiz-gnome compiz-plugins
  compiz-plugins-default coreutils cpio cpp-4.8 cups cups-browsed cups-bsd
  cups-client cups-common cups-core-drivers cups-daemon cups-filters
  cups-filters-core-drivers cups-ppdc cups-server-common dbus dbus-x11
  dell-recovery dh-python dkms dnsmasq-base dnsutils dosfstools dpkg dpkg-dev
  duplicity e2fslibs e2fsprogs ecryptfs-utils efibootmgr empathy
  empathy-common eog evince evince-common evolution-data-server
  evolution-data-server-common evolution-data-server-online-accounts file
  file-roller fontconfig fontconfig-config fonts-droid fonts-opensymbol fuse
  g++-4.8 gcc-4.8 gcc-4.8-base gcc-4.9-base gdb gdisk ghostscript
  ghostscript-x gir1.2-appindicator3-0.1 gir1.2-dbusmenu-glib-0.4
  gir1.2-ebook-1.2 gir1.2-ebookcontacts-1.2 gir1.2-edataserver-1.2
  gir1.2-freedesktop gir1.2-gdkpixbuf-2.0 gir1.2-glib-2.0
  gir1.2-gnomebluetooth-1.0 gir1.2-gst-plugins-base-1.0 gir1.2-gstreamer-1.0
  gir1.2-gtk-3.0 gir1.2-gudev-1.0 gir1.2-ibus-1.0 gir1.2-javascriptcoregtk-3.0
  gir1.2-networkmanager-1.0 gir1.2-pango-1.0 gir1.2-soup-2.4 gir1.2-udisks-2.0
  gir1.2-vte-2.90 gir1.2-webkit-3.0 gir1.2-wnck-3.0 glib-networking
  glib-networking-common glib-networking-services gnome-bluetooth
  gnome-calculator gnome-control-center-shared-data gnome-desktop3-data
  gnome-keyring gnome-session-bin gnome-session-common
  gnome-settings-daemon-schemas gnome-sudoku gnupg google-chrome-stable gpgv
  grub-common grub-efi-amd64 grub-efi-amd64-bin grub-efi-amd64-signed
  grub2-common gstreamer1.0-alsa gstreamer1.0-plugins-base
  gstreamer1.0-plugins-base-apps gstreamer1.0-plugins-good
  gstreamer1.0-pulseaudio gstreamer1.0-tools gstreamer1.0-x gvfs gvfs-backends
  gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs hardening-includes
  heirloom-mailx hplip hplip-data hud ibus ibus-gtk ibus-gtk3
  icedtea-6-jre-cacao icedtea-6-jre-jamvm icedtea-6-plugin icedtea-netx
  icedtea-netx-common ifupdown im-config indicator-printers indicator-session
  initramfs-tools initramfs-tools-bin initscripts intel-gpu-tools iproute
  iproute2 iputils-arping iputils-ping iputils-tracepath irqbalance
  isc-dhcp-client isc-dhcp-common klibc-utils kpartx kpartx-boot krb5-locales
  landscape-client-ui-install language-pack-en language-pack-en-base
  language-pack-gnome-en language-pack-gnome-en-base language-selector-common
  language-selector-gnome lib32gcc1 libaccount-plugin-generic-oauth
  libaccount-plugin-google libaccountsservice0 libapparmor-perl libapparmor1
  libappindicator3-1 libapt-inst1.5 libapt-pkg4.12 libarchive13 libasan0
  libasn1-8-heimdal libatomic1 libbind9-90 libblkid1 libbluetooth3
  libboost-date-time1.54.0 libboost-iostreams1.54.0 libboost-system1.54.0
  libc-bin libc-dev-bin libc6 libc6-dbg libc6-dev libc6-i386 libcairo-gobject2
  libcairo2 libcamel-1.2-45 libcgmanager0 libclick-0.4-0 libclutter-gtk-1.0-0
  libcomerr2 libcompizconfig0 libcups2 libcupscgi1 libcupsfilters1
  libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3 libcurl3-gnutls libdbus-1-3
  libdbusmenu-glib4 libdbusmenu-gtk3-4 libdbusmenu-gtk4 libdebian-installer4
  libdecoration0 libdns100 libdpkg-perl libdrm-intel1 libdrm-nouveau2
  libdrm-radeon1 libdrm2 libebackend-1.2-7 libebook-1.2-14
  libebook-contacts-1.2-0 libecal-1.2-16 libecryptfs0 libedata-book-1.2-20
  libedata-cal-1.2-23 libedataserver-1.2-18 libegl1-mesa libegl1-mesa-drivers
  libelf1 libevdocument3-4 libevent-2.0-5 libevview3-3 libexpat1 libffi6
  libflac8 libfontconfig1 libfontembed1 libfreetype6 libfuse2 libgail-3-0
  libgail-common libgail18 libgbm1 libgcc-4.8-dev libgcc1 libgcrypt11 libgd3
  libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common libgirepository-1.0-1
  libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libgles2-mesa libglib2.0-0
  libglib2.0-bin libglib2.0-data libgnome-bluetooth11 libgnome-control-center1
  libgnome-desktop-3-7 libgnutls-openssl27 libgnutls26 libgomp1 libgpgme11
  libgphoto2-6 libgphoto2-l10n libgphoto2-port10 libgraphite2-3 libgs9
  libgs9-common libgssapi-krb5-2 libgssapi3-heimdal
  libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0
  libgstreamer1.0-0 libgtk-3-0 libgtk-3-bin libgtk-3-common libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libgudev-1.0-0 libgweather-3-6
  libgweather-common libharfbuzz-icu0 libharfbuzz0b libhcrypto4-heimdal
  libheimbase1-heimdal libheimntlm0-heimdal libhpmud0 libhud2
  libhunspell-1.3-0 libhx509-5-heimdal libibus-1.0-5 libicu52 libido3-0.1-0
  libimobiledevice4 libindicator3-7 libisc95 libisccc90 libisccfg90 libitm1
  libjasper1 libjavascriptcoregtk-3.0-0 libjson-c2 libjson0 libk5crypto3
  libklibc libkrb5-26-heimdal libkrb5-3 libkrb5support0 liblcms2-2
  libldap-2.4-2 libldb1 liblightdm-gobject-1-0 liblwp-protocol-https-perl
  liblwres90 liblzo2-2 libmagic1 libmbim-glib0 libmetacity-private0a
  libminiupnpc8 libmm-glib0 libmms0 libmono-cairo4.0-cil libmono-corlib4.0-cil
  libmono-corlib4.5-cil libmono-i18n-west4.0-cil libmono-i18n4.0-cil
  libmono-security4.0-cil libmono-system-configuration4.0-cil
  libmono-system-drawing4.0-cil libmono-system-security4.0-cil
  libmono-system-xml4.0-cil libmono-system4.0-cil libmount1 libmtp-common
  libmtp-runtime libmtp9 libnautilus-extension1a libnettle4 libnl-3-200
  libnl-genl-3-200 libnl-route-3-200 libnm-glib-vpn1 libnm-glib4
  libnm-gtk-common libnm-gtk0 libnm-util2 libnspr4 libnss3 libnss3-1d
  libnss3-nssdb libnuma1 libnux-4.0-0 libnux-4.0-common libopenvg1-mesa
  liboxideqt-qmlplugin liboxideqtcore0 libp11-kit-gnome-keyring
  libpam-gnome-keyring libpam-modules libpam-modules-bin libpam-runtime
  libpam-systemd libpam0g libpango-1.0-0 libpango1.0-0 libpangocairo-1.0-0
  libpangoft2-1.0-0 libpangoxft-1.0-0 libparted0debian1 libpci3 libpcre3
  libperl5.18 libpixman-1-0 libplymouth2 libpng12-0 libpolkit-agent-1-0
  libpolkit-backend-1-0 libpolkit-gobject-1-0 libpoppler-glib8 libpoppler44
  libprocps3 libpulse-mainloop-glib0 libpulse0 libpulsedsp libpurple-bin
  libpurple0 libpwquality-common libpwquality1 libpython2.7
  libpython2.7-minimal libpython2.7-stdlib libpython3.4 libpython3.4-minimal
  libpython3.4-stdlib libqt4-dbus libqt4-declarative libqt4-designer
  libqt4-help libqt4-network libqt4-opengl libqt4-script libqt4-scripttools
  libqt4-sql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml
  libqt4-xmlpatterns libqt5core5a libqt5dbus5 libqt5gui5 libqt5network5
  libqt5opengl5 libqt5printsupport5 libqt5qml5 libqt5quick5 libqt5sql5
  libqt5sql5-sqlite libqt5test5 libqt5widgets5 libqt5xml5 libqtcore4
  libqtdbus4 libqtgui4 libquadmath0 libreoffice-avmedia-backend-gstreamer
  libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core
  libreoffice-draw libreoffice-gnome libreoffice-gtk libreoffice-impress
  libreoffice-math libreoffice-ogltrans libreoffice-pdfimport
  libreoffice-presentation-minimizer libreoffice-style-human
  libreoffice-writer libroken18-heimdal libsane libsane-common libsane-hpaio
  libsepol1 libsmbclient libsndfile1 libsnmp-base libsnmp30 libsoup-gnome2.4-1
  libsoup2.4-1 libspectre1 libspice-server1 libsqlite3-0 libss2 libssh-4
  libssl1.0.0 libstdc++-4.8-dev libstdc++6 libsystemd-daemon0
  libsystemd-journal0 libsystemd-login0 libtalloc2 libtasn1-6 libtdb1
  libtevent0 libthumbnailer0 libtiff5 libtsan0 libudev1 libudisks2-0
  libufe-xidgetter0 libunity-control-center1 libunity-core-6.0-9
  libunity-gtk2-parser0 libunity-gtk3-parser0 libupstart1 libuuid1
  libvncserver0 libvte-2.90-9 libvte-2.90-common libwayland-egl1-mesa
  libwbclient0 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libwhoopsie0
  libwind0-heimdal libwmf0.2-7 libwmf0.2-7-gtk libwnck-3-0 libwnck-3-common
  libxatracker2 libxext6 libxfixes3 libxfont1 libxi6 libxml2 libxrender1
  libzeitgeist-2.0-0 lightdm linux-firmware linux-generic
  linux-headers-generic linux-image-generic linux-libc-dev locales login
  lsb-base lsb-release lshw ltrace man-db mcp-account-manager-uoa metacity
  metacity-common mime-support modemmanager mono-4.0-gac mono-gac mono-runtime
  mono-runtime-common mono-runtime-sgen mount multiarch-support myspell-en-gb
  myspell-en-za mythes-en-us nautilus nautilus-data nautilus-sendto-empathy
  net-tools network-manager network-manager-gnome notify-osd-icons ntpdate
  nux-tools onboard onboard-data oneconf oneconf-common openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib openoffice.org-hyphenation
  openssh-client openssl os-prober oxideqt-codecs parted passwd patch pciutils
  perl perl-base perl-modules plymouth plymouth-label
  plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text pm-utils policykit-1
  poppler-utils ppp printer-driver-hpcups printer-driver-postscript-hp procps
  pulseaudio pulseaudio-module-bluetooth pulseaudio-module-x11
  pulseaudio-utils python-apt python-apt-common python-aptdaemon
  python-aptdaemon.gtk3widgets python-cupshelpers python-gi python-gi-cairo
  python-gobject python-ibus python-ldb python-libxml2 python-lxml
  python-oneconf python-pexpect python-pkg-resources python-samba python-six
  python-talloc python-tdb python-zeitgeist python2.7 python2.7-minimal
  python3-apport python3-apt python3-aptdaemon python3-aptdaemon.gtk3widgets
  python3-aptdaemon.pkcompat python3-chardet python3-distupgrade python3-gdbm
  python3-gi python3-gi-cairo python3-lxml python3-oneconf
  python3-pkg-resources python3-problem-report python3-requests python3-six
  python3-software-properties python3-uno python3-update-manager
  python3-urllib3 python3.4 python3.4-minimal qdbus qtcore4-l10n
  qtdeclarative5-dialogs-plugin qtdeclarative5-localstorage-plugin
  qtdeclarative5-privatewidgets-plugin qtdeclarative5-qtquick2-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets
  qtdeclarative5-window-plugin resolvconf rsync rsyslog samba-common
  samba-common-bin samba-libs sane-utils sbsigntool shim shim-signed shotwell
  shotwell-common simple-scan smbclient software-properties-common
  software-properties-gtk sqlite3 ssh-askpass-gnome sudo
  system-config-printer-common system-config-printer-gnome
  system-config-printer-udev systemd-services sysv-rc sysvinit-utils t1utils
  tcpdump telepathy-gabble thunderbird thunderbird-gnome-support
  thunderbird-locale-en thunderbird-locale-en-us transmission-common
  transmission-gtk tzdata tzdata-java ubuntu-docs ubuntu-drivers-common
  ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk ubuntu-session udev
  udisks2 unattended-upgrades unity unity-control-center unity-greeter
  unity-gtk-module-common unity-gtk2-module unity-gtk3-module unity-lens-music
  unity-scope-musicstores unity-services unity-settings-daemon uno-libs3 unzip
  update-manager update-manager-core update-notifier update-notifier-common
  upstart ure usb-creator-common usb-creator-gtk usbutils util-linux
  uuid-runtime webaccounts-extension-common webapp-container webbrowser-app
  wget whoopsie wpasupplicant x11-common xdg-utils xorg xserver-common
  xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-video-all
  xserver-xorg-video-ati xserver-xorg-video-intel
  xserver-xorg-video-openchrome xserver-xorg-video-radeon
  xul-ext-websites-integration zeitgeist zeitgeist-core zeitgeist-datahub
737 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Inst base-files [7.2ubuntu5] (7.2ubuntu5.4 Ubuntu:14.04/trusty-updates [amd64])
Conf base-files (7.2ubuntu5.4 Ubuntu:14.04/trusty-updates [amd64])
Inst bash [4.3-7ubuntu1] (4.3-7ubuntu1.5 Ubuntu:14.04/trusty-updates [amd64])
Conf bash (4.3-7ubuntu1.5 Ubuntu:14.04/trusty-updates [amd64])
Inst coreutils [8.21-1ubuntu5] (8.21-1ubuntu5.4 Ubuntu:14.04/trusty-updates [amd64])
Conf coreutils (8.21-1ubuntu5.4 Ubuntu:14.04/trusty-updates [amd64])
Inst dpkg [1.17.5ubuntu5.2] (1.17.5ubuntu5.7 Ubuntu:14.04/trusty-updates [amd64])
Conf dpkg (1.17.5ubuntu5.7 Ubuntu:14.04/trusty-updates [amd64])
Inst sysv-rc [2.88dsf-41ubuntu6] (2.88dsf-41ubuntu6.3 Ubuntu:14.04/trusty-updates [all])
Inst sysvinit-utils [2.88dsf-41ubuntu6] (2.88dsf-41ubuntu6.3 Ubuntu:14.04/trusty-updates [amd64])
Inst libc6 [2.19-0ubuntu6] (2.19-0ubuntu6.9 Ubuntu:14.04/trusty-updates [amd64]) [libc6-i386:amd64 libc6-dbg:amd64 libc6-dev:amd64 ]
Inst libgcc1 [1:4.9-20140406-0ubuntu1] (1:4.9.3-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-i386:amd64 libc6-dbg:amd64 libc6-dev:amd64 ]
Inst gcc-4.9-base [4.9-20140406-0ubuntu1] (4.9.3-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64]) [lib32gcc1:amd64 libc6-i386:amd64 libc6-dbg:amd64 libc6-dev:amd64 ]
Conf gcc-4.9-base (4.9.3-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64]) [lib32gcc1:amd64 libc6-i386:amd64 libc6-dbg:amd64 libc6-dev:amd64 ]
Conf libgcc1 (1:4.9.3-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64]) [lib32gcc1:amd64 libc6-i386:amd64 libc6-dbg:amd64 libc6-dev:amd64 ]
Conf libc6 (2.19-0ubuntu6.9 Ubuntu:14.04/trusty-updates [amd64]) [lib32gcc1:amd64 libc6-i386:amd64 libc6-dbg:amd64 libc6-dev:amd64 ]
Conf sysvinit-utils (2.88dsf-41ubuntu6.3 Ubuntu:14.04/trusty-updates [amd64]) [lib32gcc1:amd64 libc6-i386:amd64 libc6-dbg:amd64 libc6-dev:amd64 ]
Conf sysv-rc (2.88dsf-41ubuntu6.3 Ubuntu:14.04/trusty-updates [all]) [lib32gcc1:amd64 libc6-i386:amd64 libc6-dbg:amd64 libc6-dev:amd64 ]
Inst mount [2.20.1-5.1ubuntu20] (2.20.1-5.1ubuntu20.7 Ubuntu:14.04/trusty-updates [amd64]) [lib32gcc1:amd64 libc6-i386:amd64 libc6-dbg:amd64 libc6-dev:amd64 ]
Conf mount (2.20.1-5.1ubuntu20.7 Ubuntu:14.04/trusty-updates [amd64]) [lib32gcc1:amd64 libc6-i386:amd64 libc6-dbg:amd64 libc6-dev:amd64 ]
Inst lsb-base [4.1+Debian11ubuntu6] (4.1+Debian11ubuntu6.1 Ubuntu:14.04/trusty-updates [all]) [lib32gcc1:amd64 libc6-i386:amd64 libc6-dbg:amd64 libc6-dev:amd64 ]
Conf lsb-base (4.1+Debian11ubuntu6.1 Ubuntu:14.04/trusty-updates [all]) [lib32gcc1:amd64 libc6-i386:amd64 libc6-dbg:amd64 libc6-dev:amd64 ]
Inst libpam0g [1.1.8-1ubuntu2] (1.1.8-1ubuntu2.2 Ubuntu:14.04/trusty-updates [amd64]) [lib32gcc1:amd64 libc6-i386:amd64 libc6-dbg:amd64 libc6-dev:amd64 ]
Conf libpam0g (1.1.8-1ubuntu2.2 Ubuntu:14.04/trusty-updates [amd64]) [lib32gcc1:amd64 libc6-i386:amd64 libc6-dbg:amd64 libc6-dev:amd64 ]
Inst libpam-modules-bin [1.1.8-1ubuntu2] (1.1.8-1ubuntu2.2 Ubuntu:14.04/trusty-updates [amd64]) [libpam-modules:amd64 on libpam-modules-bin:amd64] [lib32gcc1:amd64 libpam-modules:amd64 libc6-i386:amd64 libc6-dbg:amd64 libc6-dev:amd64 ]
Conf libpam-modules-bin (1.1.8-1ubuntu2.2 Ubuntu:14.04/trusty-updates [amd64]) [lib32gcc1:amd64 libpam-modules:amd64 libc6-i386:amd64 libc6-dbg:amd64 libc6-dev:amd64 ]
Inst libpam-modules [1.1.8-1ubuntu2] (1.1.8-1ubuntu2.2 Ubuntu:14.04/trusty-updates [amd64]) [lib32gcc1:amd64 libc6-i386:amd64 libc6-dbg:amd64 libc6-dev:amd64 ]
Conf libpam-modules (1.1.8-1ubuntu2.2 Ubuntu:14.04/trusty-updates [amd64]) [lib32gcc1:amd64 libc6-i386:amd64 libc6-dbg:amd64 libc6-dev:amd64 ]
Inst passwd [1:4.1.5.1-1ubuntu9] (1:4.1.5.1-1ubuntu9.2 Ubuntu:14.04/trusty-updates [amd64]) [lib32gcc1:amd64 libc6-i386:amd64 libc6-dbg:amd64 libc6-dev:amd64 ]
Conf passwd (1:4.1.5.1-1ubuntu9.2 Ubuntu:14.04/trusty-updates [amd64]) [lib32gcc1:amd64 libc6-i386:amd64 libc6-dbg:amd64 libc6-dev:amd64 ]
Inst initscripts [2.88dsf-41ubuntu6] (2.88dsf-41ubuntu6.3 Ubuntu:14.04/trusty-updates [amd64]) [lib32gcc1:amd64 libc6-i386:amd64 libc6-dbg:amd64 libc6-dev:amd64 ]
Inst libdbus-1-3 [1.6.18-0ubuntu4] (1.6.18-0ubuntu4.3 Ubuntu:14.04/trusty-updates [amd64]) [lib32gcc1:amd64 libc6-i386:amd64 libc6-dbg:amd64 libc6-dev:amd64 ]
Inst libjson-c2 [0.11-3ubuntu1] (0.11-3ubuntu1.2 Ubuntu:14.04/trusty-updates [amd64]) [lib32gcc1:amd64 libc6-i386:amd64 libc6-dbg:amd64 libc6-dev:amd64 ]
Inst libapparmor1 [2.8.95~2430-0ubuntu5] (2.8.95~2430-0ubuntu5.3 Ubuntu:14.04/trusty-updates [amd64]) [lib32gcc1:amd64 libc6-i386:amd64 libc6-dbg:amd64 libc6-dev:amd64 ]
Inst libexpat1 [2.1.0-4ubuntu1] (2.1.0-4ubuntu1.3 Ubuntu:14.04/trusty-updates [amd64]) [lib32gcc1:amd64 libc6-i386:amd64 libc6-dbg:amd64 libc6-dev:amd64 ]
Inst libcgmanager0 [0.24-0ubuntu5] (0.24-0ubuntu7.5 Ubuntu:14.04/trusty-updates [amd64]) [lib32gcc1:amd64 libc6-i386:amd64 libc6-dbg:amd64 libc6-dev:amd64 ]
Inst libsystemd-login0 [204-5ubuntu20kittyhawk1] (204-5ubuntu20.19 Ubuntu:14.04/trusty-updates [amd64]) [lib32gcc1:amd64 libc6-i386:amd64 libc6-dbg:amd64 libc6-dev:amd64 ]
Inst dbus [1.6.18-0ubuntu4] (1.6.18-0ubuntu4.3 Ubuntu:14.04/trusty-updates [amd64]) [lib32gcc1:amd64 libc6-i386:amd64 libc6-dbg:amd64 libc6-dev:amd64 ]
Inst libpolkit-gobject-1-0 [0.105-4ubuntu2] (0.105-4ubuntu3.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) [lib32gcc1:amd64 libc6-i386:amd64 libc6-dbg:amd64 libc6-dev:amd64 ]
Inst libaccountsservice0 [0.6.35-0ubuntu7] (0.6.35-0ubuntu7.2 Ubuntu:14.04/trusty-updates [amd64]) [accountsservice:amd64 lib32gcc1:amd64 libc6-i386:amd64 libc6-dbg:amd64 libc6-dev:amd64 ]
Inst accountsservice [0.6.35-0ubuntu7] (0.6.35-0ubuntu7.2 Ubuntu:14.04/trusty-updates [amd64]) [lib32gcc1:amd64 libc6-i386:amd64 libc6-dbg:amd64 libc6-dev:amd64 ]
Inst libc6-i386 [2.19-0ubuntu6] (2.19-0ubuntu6.9 Ubuntu:14.04/trusty-updates [amd64]) [lib32gcc1:amd64 libc6-dbg:amd64 libc6-dev:amd64 ]
Inst lib32gcc1 [1:4.9-20140406-0ubuntu1] (1:4.9.3-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 libc6-dev:amd64 ]
Inst libfontconfig1 [2.11.0-0ubuntu4] (2.11.0-0ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 libc6-dev:amd64 ]
Inst fontconfig-config [2.11.0-0ubuntu4] (2.11.0-0ubuntu4.1 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 libc6-dev:amd64 ]
Inst libpng12-0 [1.2.50-1ubuntu2] (1.2.50-1ubuntu2.14.04.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 libc6-dev:amd64 ]
Inst libfreetype6 [2.5.2-1ubuntu2] (2.5.2-1ubuntu2.5 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 libc6-dev:amd64 ]
Inst liblcms2-2 [2.5-0ubuntu4] (2.5-0ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 libc6-dev:amd64 ]
Inst libtsan0 [4.8.2-19ubuntu1] (4.8.4-2ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 libc6-dev:amd64 ]
Inst libgomp1 [4.8.2-19ubuntu1] (4.8.4-2ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 libc6-dev:amd64 ]
Inst libitm1 [4.8.2-19ubuntu1] (4.8.4-2ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 libc6-dev:amd64 ]
Inst libatomic1 [4.8.2-19ubuntu1] (4.8.4-2ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 libc6-dev:amd64 ]
Inst libasan0 [4.8.2-19ubuntu1] (4.8.4-2ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 libc6-dev:amd64 ]
Inst libquadmath0 [4.8.2-19ubuntu1] (4.8.4-2ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 libc6-dev:amd64 ]
Inst g++-4.8 [4.8.2-19ubuntu1] (4.8.4-2ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 libc6-dev:amd64 ]
Inst gcc-4.8 [4.8.2-19ubuntu1] (4.8.4-2ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 libc6-dev:amd64 ]
Inst cpp-4.8 [4.8.2-19ubuntu1] (4.8.4-2ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 libc6-dev:amd64 ]
Inst libc6-dev [2.19-0ubuntu6] (2.19-0ubuntu6.9 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libc-dev-bin [2.19-0ubuntu6] (2.19-0ubuntu6.9 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst linux-libc-dev [3.13.0-38.65somerville1] (3.13.0-91.138 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst binutils [2.24-5ubuntu3] (2.24-5ubuntu14.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libstdc++-4.8-dev [4.8.2-19ubuntu1] (4.8.4-2ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libgcc-4.8-dev [4.8.2-19ubuntu1] (4.8.4-2ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst gcc-4.8-base [4.8.2-19ubuntu1] (4.8.4-2ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 libstdc++6:amd64 ]
Conf gcc-4.8-base (4.8.4-2ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 libstdc++6:amd64 ]
Inst libstdc++6 [4.8.2-19ubuntu1] (4.8.4-2ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Conf libstdc++6 (4.8.4-2ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libtiff5 [4.0.3-7ubuntu0.1] (4.0.3-7ubuntu0.4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libpoppler44 [0.24.5-2ubuntu4] (0.24.5-2ubuntu4.4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libreoffice-calc [1:4.2.3~rc3-0ubuntu2] (1:4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libreoffice-gnome [1:4.2.3~rc3-0ubuntu2] (1:4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libreoffice-gtk [1:4.2.3~rc3-0ubuntu2] (1:4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libreoffice-writer [1:4.2.3~rc3-0ubuntu2] (1:4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst uno-libs3 [4.2.3~rc3-0ubuntu2] (4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64]) [ure:amd64 libc6-dbg:amd64 ]
Inst libreoffice-ogltrans [1:4.2.3~rc3-0ubuntu2] (1:4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64]) [ure:amd64 libc6-dbg:amd64 ]
Inst ure [4.2.3~rc3-0ubuntu2] (4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst python3-uno [1:4.2.3~rc3-0ubuntu2] (1:4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libreoffice-common [1:4.2.3~rc3-0ubuntu2] (1:4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst libreoffice-pdfimport [1:4.2.3~rc3-0ubuntu2] (1:4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libreoffice-math [1:4.2.3~rc3-0ubuntu2] (1:4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libreoffice-base-core [1:4.2.3~rc3-0ubuntu2] (1:4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libreoffice-draw [1:4.2.3~rc3-0ubuntu2] (1:4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64]) [libreoffice-impress:amd64 libc6-dbg:amd64 ]
Inst libreoffice-impress [1:4.2.3~rc3-0ubuntu2] (1:4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libreoffice-core [1:4.2.3~rc3-0ubuntu2] (1:4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libxml2 [2.9.1+dfsg1-3ubuntu4] (2.9.1+dfsg1-3ubuntu4.8 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libgles2-mesa [10.1.0-4ubuntu5] (10.1.3-0ubuntu0.6 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libegl1-mesa-drivers [10.1.0-4ubuntu5] (10.1.3-0ubuntu0.6 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libwayland-egl1-mesa [10.1.0-4ubuntu5] (10.1.3-0ubuntu0.6 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libdrm2 [2.4.52-1] (2.4.64-1~ubuntu14.04.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst dbus-x11 [1.6.18-0ubuntu4] (1.6.18-0ubuntu4.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst x11-common [1:7.7+1ubuntu8] (1:7.7+1ubuntu8.1 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst xserver-common [2:1.15.1-0ubuntu2] (2:1.15.1-0ubuntu2.7 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst libxext6 [2:1.3.2-1] (2:1.3.2-1ubuntu0.0.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libxfixes3 [1:5.0.1-1ubuntu1] (1:5.0.1-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libgl1-mesa-dri [10.1.0-4ubuntu5] (10.1.3-0ubuntu0.6 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst xserver-xorg-core [2:1.15.1-0ubuntu2] (2:1.15.1-0ubuntu2.7 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libxi6 [2:1.7.1.901-1ubuntu1] (2:1.7.1.901-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libgcrypt11 [1.5.3-2ubuntu4] (1.5.3-2ubuntu4.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libpixman-1-0 [0.30.2-2ubuntu1] (0.30.2-2ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libxfont1 [1:1.4.7-1] (1:1.4.7-1ubuntu0.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libdrm-intel1 [2.4.52-1] (2.4.64-1~ubuntu14.04.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libdrm-nouveau2 [2.4.52-1] (2.4.64-1~ubuntu14.04.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libdrm-radeon1 [2.4.52-1] (2.4.64-1~ubuntu14.04.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libelf1 [0.158-0ubuntu5.1] (0.158-0ubuntu5.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libgbm1 [10.1.0-4ubuntu5] (10.1.3-0ubuntu0.6 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libegl1-mesa [10.1.0-4ubuntu5] (10.1.3-0ubuntu0.6 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libopenvg1-mesa [10.1.0-4ubuntu5] (10.1.3-0ubuntu0.6 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libgl1-mesa-glx [10.1.0-4ubuntu5] (10.1.3-0ubuntu0.6 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libglapi-mesa [10.1.0-4ubuntu5] (10.1.3-0ubuntu0.6 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libreoffice-style-human [1:4.2.3~rc3-0ubuntu2] (1:4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst libicu52 [52.1-3] (52.1-3ubuntu0.4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libgdk-pixbuf2.0-0 [2.30.7-0ubuntu1] (2.30.7-0ubuntu1.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libgdk-pixbuf2.0-common [2.30.7-0ubuntu1] (2.30.7-0ubuntu1.2 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst libjasper1 [1.900.1-14ubuntu3] (1.900.1-14ubuntu3.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libgtk2.0-common [2.24.23-0ubuntu1] (2.24.23-0ubuntu1.4 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst libgtk2.0-bin [2.24.23-0ubuntu1] (2.24.23-0ubuntu1.4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libgraphite2-3 [1.2.4-1ubuntu1] (1.3.6-1ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libharfbuzz0b [0.9.27-1] (0.9.27-1ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libpangoxft-1.0-0 [1.36.3-1ubuntu1] (1.36.3-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) [libpango1.0-0:amd64 libc6-dbg:amd64 ]
Inst libpangocairo-1.0-0 [1.36.3-1ubuntu1] (1.36.3-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) [libpango1.0-0:amd64 libc6-dbg:amd64 ]
Inst libpango-1.0-0 [1.36.3-1ubuntu1] (1.36.3-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) [libpango1.0-0:amd64 libc6-dbg:amd64 ]
Inst libpango1.0-0 [1.36.3-1ubuntu1] (1.36.3-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libpangoft2-1.0-0 [1.36.3-1ubuntu1] (1.36.3-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libxrender1 [1:0.9.8-1] (1:0.9.8-1build0.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst fontconfig [2.11.0-0ubuntu4] (2.11.0-0ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libgail-common [2.24.23-0ubuntu1] (2.24.23-0ubuntu1.4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libgail18 [2.24.23-0ubuntu1] (2.24.23-0ubuntu1.4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libcupsppdc1 [1.7.2-0ubuntu1] (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libcupsmime1 [1.7.2-0ubuntu1] (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libcupsfilters1 [1.0.52-0ubuntu1] (1.0.52-0ubuntu1.7 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libcupsimage2 [1.7.2-0ubuntu1] (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libcupscgi1 [1.7.2-0ubuntu1] (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst cups-browsed [1.0.52-0ubuntu1] (1.0.52-0ubuntu1.7 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libgnutls-openssl27 [2.12.23-12ubuntu2] (2.12.23-12ubuntu2.5 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libtasn1-6 [3.4-3] (3.4-3ubuntu0.4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libgnutls26 [2.12.23-12ubuntu2] (2.12.23-12ubuntu2.5 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libk5crypto3 [1.12+dfsg-2ubuntu4] (1.12+dfsg-2ubuntu5.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libgssapi-krb5-2 [1.12+dfsg-2ubuntu4] (1.12+dfsg-2ubuntu5.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libkrb5-3 [1.12+dfsg-2ubuntu4] (1.12+dfsg-2ubuntu5.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libkrb5support0 [1.12+dfsg-2ubuntu4] (1.12+dfsg-2ubuntu5.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libcomerr2 [1.42.9-3ubuntu1] (1.42.9-3ubuntu1.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Conf libcomerr2 (1.42.9-3ubuntu1.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libprocps3 [1:3.3.9-1ubuntu2] (1:3.3.9-1ubuntu2.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst procps [1:3.3.9-1ubuntu2] (1:3.3.9-1ubuntu2.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst cups-daemon [1.7.2-0ubuntu1] (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst poppler-utils [0.24.5-2ubuntu4] (0.24.5-2ubuntu4.4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst cups-filters-core-drivers [1.0.52-0ubuntu1] (1.0.52-0ubuntu1.7 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst cups-core-drivers [1.7.2-0ubuntu1] (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst cups-server-common [1.7.2-0ubuntu1] (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst perl [5.18.2-2ubuntu1] (5.18.2-2ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libperl5.18 [5.18.2-2ubuntu1] (5.18.2-2ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst perl-base [5.18.2-2ubuntu1] (5.18.2-2ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Conf perl-base (5.18.2-2ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst perl-modules [5.18.2-2ubuntu1] (5.18.2-2ubuntu1.1 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst libssl1.0.0 [1.0.1f-1ubuntu2.1] (1.0.1f-1ubuntu2.19 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libsnmp-base [5.7.2~dfsg-8.1ubuntu3] (5.7.2~dfsg-8.1ubuntu3.2 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst libsnmp30 [5.7.2~dfsg-8.1ubuntu3] (5.7.2~dfsg-8.1ubuntu3.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst printer-driver-postscript-hp [3.14.3-0ubuntu3] (3.14.3-0ubuntu3.4 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst libsane-hpaio [3.14.3-0ubuntu3] (3.14.3-0ubuntu3.4 Ubuntu:14.04/trusty-updates [amd64]) [hplip:amd64 libc6-dbg:amd64 ]
Inst hplip [3.14.3-0ubuntu3] (3.14.3-0ubuntu3.4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libhpmud0 [3.14.3-0ubuntu3] (3.14.3-0ubuntu3.4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst hplip-data [3.14.3-0ubuntu3] (3.14.3-0ubuntu3.4 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst printer-driver-hpcups [3.14.3-0ubuntu3] (3.14.3-0ubuntu3.4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libsane [1.0.23-3ubuntu3] (1.0.23-3ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libsane-common [1.0.23-3ubuntu3] (1.0.23-3ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libgd3 [2.1.0-3] (2.1.0-3ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libgphoto2-port10 [2.5.3.1-1ubuntu2] (2.5.3.1-1ubuntu2.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libgphoto2-6 [2.5.3.1-1ubuntu2] (2.5.3.1-1ubuntu2.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst python-pexpect [3.1-1] (3.1-1ubuntu0.1 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst libpolkit-backend-1-0 [0.105-4ubuntu2] (0.105-4ubuntu3.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libpolkit-agent-1-0 [0.105-4ubuntu2] (0.105-4ubuntu3.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libpam-systemd [204-5ubuntu20kittyhawk1] (204-5ubuntu20.19 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst systemd-services [204-5ubuntu20kittyhawk1] (204-5ubuntu20.19 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libsystemd-daemon0 [204-5ubuntu20kittyhawk1] (204-5ubuntu20.19 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libpam-runtime [1.1.8-1ubuntu2] (1.1.8-1ubuntu2.2 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Conf libpam-runtime (1.1.8-1ubuntu2.2 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst policykit-1 [0.105-4ubuntu2] (0.105-4ubuntu3.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libuuid1 [2.20.1-5.1ubuntu20] (2.20.1-5.1ubuntu20.7 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Conf libuuid1 (2.20.1-5.1ubuntu20.7 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst wget [1.15-1ubuntu1] (1.15-1ubuntu1.14.04.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libc-bin [2.19-0ubuntu6] (2.19-0ubuntu6.9 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Conf libc-bin (2.19-0ubuntu6.9 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libgs9-common [9.10~dfsg-0ubuntu10] (9.10~dfsg-0ubuntu10.4 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst ghostscript-x [9.10~dfsg-0ubuntu10] (9.10~dfsg-0ubuntu10.4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst ghostscript [9.10~dfsg-0ubuntu10] (9.10~dfsg-0ubuntu10.4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libgs9 [9.10~dfsg-0ubuntu10] (9.10~dfsg-0ubuntu10.4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst cups-bsd [1.7.2-0ubuntu1] (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst cups-client [1.7.2-0ubuntu1] (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libcups2 [1.7.2-0ubuntu1] (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [amd64]) [cups:amd64 libc6-dbg:amd64 ]
Inst cups [1.7.2-0ubuntu1] (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst cups-filters [1.0.52-0ubuntu1] (1.0.52-0ubuntu1.7 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst cups-ppdc [1.7.2-0ubuntu1] (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libfontembed1 [1.0.52-0ubuntu1] (1.0.52-0ubuntu1.7 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst cups-common [1.7.2-0ubuntu1] (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst libgtk2.0-0 [2.24.23-0ubuntu1] (2.24.23-0ubuntu1.4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst python3-six [1.5.2-1] (1.5.2-1ubuntu1 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst python3-urllib3 [1.7.1-1build1] (1.7.1-1ubuntu4 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst mime-support [3.54ubuntu1] (3.54ubuntu1.1 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst python3.4 [3.4.0-2ubuntu1] (3.4.3-1ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst python3.4-minimal [3.4.0-2ubuntu1] (3.4.3-1ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libpython3.4 [3.4.0-2ubuntu1] (3.4.3-1ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libpython3.4-stdlib [3.4.0-2ubuntu1] (3.4.3-1ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libpython3.4-minimal [3.4.0-2ubuntu1] (3.4.3-1ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libffi6 [3.1~rc1+r3.0.13-12] (3.1~rc1+r3.0.13-12ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst sqlite3 [3.8.2-1ubuntu2] (3.8.2-1ubuntu2.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libsqlite3-0 [3.8.2-1ubuntu2] (3.8.2-1ubuntu2.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst fonts-opensymbol [2:102.6+LibO4.2.3~rc3-0ubuntu2] (2:102.6+LibO4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst libboost-date-time1.54.0 [1.54.0-4ubuntu3] (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libroken18-heimdal [1.6~git20131207+dfsg-1ubuntu1] (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libasn1-8-heimdal [1.6~git20131207+dfsg-1ubuntu1] (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libhcrypto4-heimdal [1.6~git20131207+dfsg-1ubuntu1] (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libheimbase1-heimdal [1.6~git20131207+dfsg-1ubuntu1] (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libwind0-heimdal [1.6~git20131207+dfsg-1ubuntu1] (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libhx509-5-heimdal [1.6~git20131207+dfsg-1ubuntu1] (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libkrb5-26-heimdal [1.6~git20131207+dfsg-1ubuntu1] (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libheimntlm0-heimdal [1.6~git20131207+dfsg-1ubuntu1] (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libgssapi3-heimdal [1.6~git20131207+dfsg-1ubuntu1] (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libldap-2.4-2 [2.4.31-1+nmu2ubuntu8] (2.4.31-1+nmu2ubuntu8.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libcurl3-gnutls [7.35.0-1ubuntu2] (7.35.0-1ubuntu2.6 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libharfbuzz-icu0 [0.9.27-1] (0.9.27-1ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libhunspell-1.3-0 [1.3.2-6ubuntu2] (1.3.2-6ubuntu2.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libnspr4 [2:4.10.2-1ubuntu1] (2:4.10.10-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libnss3-1d [2:3.17.4-0ubuntu0.14.04.1] (2:3.21-0ubuntu0.14.04.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libnss3-nssdb [2:3.17.4-0ubuntu0.14.04.1] (2:3.21-0ubuntu0.14.04.2 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst libnss3 [2:3.17.4-0ubuntu0.14.04.1] (2:3.21-0ubuntu0.14.04.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libcairo2 [1.13.0~20140204-0ubuntu1] (1.13.0~20140204-0ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libgtk-3-common [3.10.8-0ubuntu1] (3.10.8-0ubuntu1.6 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst libgail-3-0 [3.10.8-0ubuntu1] (3.10.8-0ubuntu1.6 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libcairo-gobject2 [1.13.0~20140204-0ubuntu1] (1.13.0~20140204-0ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libgtk-3-0 [3.10.8-0ubuntu1] (3.10.8-0ubuntu1.6 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libgnome-bluetooth11 [3.8.2.1-0ubuntu4] (3.8.2.1-0ubuntu4.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst gnome-desktop3-data [3.8.4-0ubuntu3] (3.8.4-0ubuntu3.2 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst libgnome-desktop-3-7 [3.8.4-0ubuntu3] (3.8.4-0ubuntu3.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libibus-1.0-5 [1.5.5-1ubuntu3] (1.5.5-1ubuntu3.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libgudev-1.0-0 [1:204-5ubuntu20kittyhawk1] (1:204-5ubuntu20.19 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libnm-util2 [0.9.8.8-0ubuntu7] (0.9.8.8-0ubuntu7.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libnm-glib4 [0.9.8.8-0ubuntu7] (0.9.8.8-0ubuntu7.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst ppp [2.4.5-5.1ubuntu2] (2.4.5-5.1ubuntu2.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst modemmanager [1.0.0-2ubuntu1] (1.0.0-2ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst network-manager [0.9.8.8-0ubuntu7] (0.9.8.8-0ubuntu7.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libnautilus-extension1a [1:3.10.1-0ubuntu9] (1:3.10.1-0ubuntu9.11 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst nautilus [1:3.10.1-0ubuntu9] (1:3.10.1-0ubuntu9.11 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst unity-control-center [14.04.3+14.04.20140410-0ubuntu1] (14.04.3+14.04.20150916-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst gir1.2-gnomebluetooth-1.0 [3.8.2.1-0ubuntu4] (3.8.2.1-0ubuntu4.2 Ubuntu:14.04/trusty-updates [amd64]) [gnome-bluetooth:amd64 libc6-dbg:amd64 ]
Inst gnome-bluetooth [3.8.2.1-0ubuntu4] (3.8.2.1-0ubuntu4.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst network-manager-gnome [0.9.8.8-0ubuntu4] (0.9.8.8-0ubuntu4.4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libnm-gtk0 [0.9.8.8-0ubuntu4] (0.9.8.8-0ubuntu4.4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libnm-gtk-common [0.9.8.8-0ubuntu4] (0.9.8.8-0ubuntu4.4 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst libmbim-glib0 [1.6.0-2] (1.6.0-2ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libmm-glib0 [1.0.0-2ubuntu1] (1.0.0-2ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libnl-route-3-200 [3.2.21-1] (3.2.21-1ubuntu3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libnl-genl-3-200 [3.2.21-1] (3.2.21-1ubuntu3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libnl-3-200 [3.2.21-1] (3.2.21-1ubuntu3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst glib-networking-services [2.40.0-1] (2.40.0-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libglib2.0-bin [2.40.0-2] (2.40.2-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst gvfs-backends [1.20.1-1ubuntu1] (1.20.3-0ubuntu1.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst gvfs-libs [1.20.1-1ubuntu1] (1.20.3-0ubuntu1.2 Ubuntu:14.04/trusty-updates [amd64]) [gvfs-daemons:amd64 gvfs:amd64 libc6-dbg:amd64 ]
Inst gvfs-fuse [1.20.1-1ubuntu1] (1.20.3-0ubuntu1.2 Ubuntu:14.04/trusty-updates [amd64]) [gvfs-daemons:amd64 gvfs:amd64 libc6-dbg:amd64 ]
Inst gvfs-bin [1.20.1-1ubuntu1] (1.20.3-0ubuntu1.2 Ubuntu:14.04/trusty-updates [amd64]) [gvfs-daemons:amd64 gvfs:amd64 libc6-dbg:amd64 ]
Inst gvfs-common [1.20.1-1ubuntu1] (1.20.3-0ubuntu1.2 Ubuntu:14.04/trusty-updates [all]) [gvfs-daemons:amd64 gvfs:amd64 libc6-dbg:amd64 ]
Inst gvfs [1.20.1-1ubuntu1] (1.20.3-0ubuntu1.2 Ubuntu:14.04/trusty-updates [amd64]) [gvfs-daemons:amd64 libc6-dbg:amd64 ]
Inst gvfs-daemons [1.20.1-1ubuntu1] (1.20.3-0ubuntu1.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libglib2.0-0 [2.40.0-2] (2.40.2-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst glib-networking [2.40.0-1] (2.40.0-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst glib-networking-common [2.40.0-1] (2.40.0-1ubuntu0.1 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst libsoup2.4-1 [2.44.2-1ubuntu2] (2.44.2-1ubuntu2.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst wpasupplicant [2.1-0ubuntu1] (2.1-0ubuntu1.4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Conf initscripts (2.88dsf-41ubuntu6.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst resolvconf [1.69ubuntu1] (1.69ubuntu1.1 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst ntpdate [1:4.2.6.p5+dfsg-3ubuntu2] (1:4.2.6.p5+dfsg-3ubuntu2.14.04.8 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst ifupdown [0.7.47.2ubuntu4] (0.7.47.2ubuntu4.4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst isc-dhcp-client [4.2.4-7ubuntu12] (4.2.4-7ubuntu12.4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst isc-dhcp-common [4.2.4-7ubuntu12] (4.2.4-7ubuntu12.4 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst iproute2 [3.12.0-2] (3.12.0-2ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst dnsmasq-base [2.68-1] (2.68-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst iputils-arping [3:20121221-4ubuntu1] (3:20121221-4ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libgirepository-1.0-1 [1.40.0-1] (1.40.0-1ubuntu0.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst gir1.2-freedesktop [1.40.0-1] (1.40.0-1ubuntu0.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst gir1.2-glib-2.0 [1.40.0-1] (1.40.0-1ubuntu0.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst gir1.2-gdkpixbuf-2.0 [2.30.7-0ubuntu1] (2.30.7-0ubuntu1.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst gir1.2-pango-1.0 [1.36.3-1ubuntu1] (1.36.3-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst gir1.2-gtk-3.0 [3.10.8-0ubuntu1] (3.10.8-0ubuntu1.6 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst gir1.2-dbusmenu-glib-0.4 [12.10.3+14.04.20140319-0ubuntu1] (12.10.3+14.04.20140612-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libdbusmenu-glib4 [12.10.3+14.04.20140319-0ubuntu1] (12.10.3+14.04.20140612-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst nautilus-data [1:3.10.1-0ubuntu9] (1:3.10.1-0ubuntu9.11 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst liblzo2-2 [2.06-1.2ubuntu1] (2.06-1.2ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libnettle4 [2.7.1-1] (2.7.1-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libarchive13 [3.1.2-7ubuntu2] (3.1.2-7ubuntu2.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libbluetooth3 [4.101-0ubuntu13] (4.101-0ubuntu13.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libimobiledevice4 [1.1.5+git20140313.bafe6a9e-0ubuntu1] (1.1.5+git20140313.bafe6a9e-0ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libmtp-common [1.1.6-20-g1b9f164-1ubuntu2] (1.1.6-20-g1b9f164-1ubuntu2.1 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst libmtp-runtime [1.1.6-20-g1b9f164-1ubuntu2] (1.1.6-20-g1b9f164-1ubuntu2.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libmtp9 [1.1.6-20-g1b9f164-1ubuntu2] (1.1.6-20-g1b9f164-1ubuntu2.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst python2.7 [2.7.6-8] (2.7.6-8ubuntu0.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libpython2.7 [2.7.6-8] (2.7.6-8ubuntu0.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libpython2.7-stdlib [2.7.6-8] (2.7.6-8ubuntu0.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libpython2.7-minimal [2.7.6-8] (2.7.6-8ubuntu0.2 Ubuntu:14.04/trusty-updates [amd64]) [python2.7-minimal:amd64 libc6-dbg:amd64 ]
Inst python2.7-minimal [2.7.6-8] (2.7.6-8ubuntu0.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libtalloc2 [2.1.0-1] (2.1.5-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst python-ldb [1:1.1.16-1] (1:1.1.24-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst python-tdb [1.2.12-1] (1.3.8-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libtdb1 [1.2.12-1] (1.3.8-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libtevent0 [0.9.19-1] (0.9.28-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libwbclient0 [2:4.1.6+dfsg-1ubuntu2] (2:4.3.9+dfsg-0ubuntu0.14.04.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst smbclient [2:4.1.6+dfsg-1ubuntu2] (2:4.3.9+dfsg-0ubuntu0.14.04.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst samba-common-bin [2:4.1.6+dfsg-1ubuntu2] (2:4.3.9+dfsg-0ubuntu0.14.04.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst python-samba [2:4.1.6+dfsg-1ubuntu2] (2:4.3.9+dfsg-0ubuntu0.14.04.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libsmbclient [2:4.1.6+dfsg-1ubuntu2] (2:4.3.9+dfsg-0ubuntu0.14.04.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst samba-libs [2:4.1.6+dfsg-1ubuntu2] (2:4.3.9+dfsg-0ubuntu0.14.04.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libldb1 [1:1.1.16-1] (1:1.1.24-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst python-talloc [2.1.0-1] (2.1.5-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst samba-common [2:4.1.6+dfsg-1ubuntu2] (2:4.3.9+dfsg-0ubuntu0.14.04.3 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst libudisks2-0 [2.1.3-1] (2.1.3-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libblkid1 [2.20.1-5.1ubuntu20] (2.20.1-5.1ubuntu20.7 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Conf libblkid1 (2.20.1-5.1ubuntu20.7 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libparted0debian1 [2.3-19ubuntu1] (2.3-19ubuntu1.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst parted [2.3-19ubuntu1] (2.3-19ubuntu1.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst udisks2 [2.1.3-1] (2.1.3-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst fuse [2.9.2-4ubuntu4] (2.9.2-4ubuntu4.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libfuse2 [2.9.2-4ubuntu4] (2.9.2-4ubuntu4.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libglib2.0-data [2.40.0-2] (2.40.2-0ubuntu1 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst libdbusmenu-gtk3-4 [12.10.3+14.04.20140319-0ubuntu1] (12.10.3+14.04.20140612-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libindicator3-7 [12.10.2+14.04.20140402-0ubuntu1] (12.10.2+14.04.20141007.1-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libappindicator3-1 [12.10.1+13.10.20130920-0ubuntu4] (12.10.1+13.10.20130920-0ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libnm-glib-vpn1 [0.9.8.8-0ubuntu7] (0.9.8.8-0ubuntu7.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libflac8 [1.3.0-2] (1.3.0-2ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libsndfile1 [1.0.25-7ubuntu2] (1.0.25-7ubuntu2.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst pulseaudio [1:4.0-0ubuntu11] (1:4.0-0ubuntu11.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libpulse0 [1:4.0-0ubuntu11] (1:4.0-0ubuntu11.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libpulse-mainloop-glib0 [1:4.0-0ubuntu11] (1:4.0-0ubuntu11.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libpwquality-common [1.2.3-1ubuntu1] (1.2.3-1ubuntu1.1 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst libpwquality1 [1.2.3-1ubuntu1] (1.2.3-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libunity-control-center1 [14.04.3+14.04.20140410-0ubuntu1] (14.04.3+14.04.20150916-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libwebkitgtk-3.0-0 [2.4.0-1ubuntu2] (2.4.10-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libjavascriptcoregtk-3.0-0 [2.4.0-1ubuntu2] (2.4.10-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libwebkitgtk-3.0-common [2.4.0-1ubuntu2] (2.4.10-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst libgstreamer1.0-0 [1.2.3-1] (1.2.4-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libgstreamer-plugins-base1.0-0 [1.2.3-1] (1.2.4-1~ubuntu2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst gnome-settings-daemon-schemas [3.8.6.1-0ubuntu11] (3.8.6.1-0ubuntu11.2 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst unity-settings-daemon [14.04.0+14.04.20140414-0ubuntu1] (14.04.0+14.04.20151012-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst ibus [1.5.5-1ubuntu3] (1.5.5-1ubuntu3.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst gir1.2-ibus-1.0 [1.5.5-1ubuntu3] (1.5.5-1ubuntu3.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst python-gi-cairo [3.12.0-1] (3.12.0-1ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst python-gi [3.12.0-1] (3.12.0-1ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libpcre3 [1:8.31-2ubuntu2] (1:8.31-2ubuntu2.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Conf libpcre3 (1:8.31-2ubuntu2.3 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst bluez [4.101-0ubuntu13] (4.101-0ubuntu13.1 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst tzdata-java [2014b-1] (2016f-0ubuntu0.14.04 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst tzdata [2014b-1] (2016f-0ubuntu0.14.04 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Conf tzdata (2016f-0ubuntu0.14.04 Ubuntu:14.04/trusty-updates [all]) [libc6-dbg:amd64 ]
Inst util-linux [2.20.1-5.1ubuntu20] (2.20.1-5.1ubuntu20.7 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Conf util-linux (2.20.1-5.1ubuntu20.7 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst udev [204-5ubuntu20kittyhawk1] (204-5ubuntu20.19 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libudev1 [204-5ubuntu20kittyhawk1] (204-5ubuntu20.19 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libjson0 [0.11-3ubuntu1] (0.11-3ubuntu1.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst upstart [1.12.1-0ubuntu4] (1.12.1-0ubuntu4.2 Ubuntu:14.04/trusty-updates [amd64]) [libc6-dbg:amd64 ]
Inst libc6-dbg [2.19-0ubuntu6] (2.19-0ubuntu6.9 Ubuntu:14.04/trusty-updates [amd64])
Inst e2fslibs [1.42.9-3ubuntu1] (1.42.9-3ubuntu1.3 Ubuntu:14.04/trusty-updates [amd64]) [e2fsprogs:amd64 on e2fslibs:amd64] [e2fsprogs:amd64 ]
Conf e2fslibs (1.42.9-3ubuntu1.3 Ubuntu:14.04/trusty-updates [amd64]) [e2fsprogs:amd64 ]
Inst e2fsprogs [1.42.9-3ubuntu1] (1.42.9-3ubuntu1.3 Ubuntu:14.04/trusty-updates [amd64])
Conf e2fsprogs (1.42.9-3ubuntu1.3 Ubuntu:14.04/trusty-updates [amd64])
Inst login [1:4.1.5.1-1ubuntu9] (1:4.1.5.1-1ubuntu9.2 Ubuntu:14.04/trusty-updates [amd64])
Conf login (1:4.1.5.1-1ubuntu9.2 Ubuntu:14.04/trusty-updates [amd64])
Inst libapt-pkg4.12 [1.0.1ubuntu2] (1.0.1ubuntu2.14 Ubuntu:14.04/trusty-updates [amd64])
Conf libapt-pkg4.12 (1.0.1ubuntu2.14 Ubuntu:14.04/trusty-updates [amd64])
Inst gpgv [1.4.16-1ubuntu2] (1.4.16-1ubuntu2.3 Ubuntu:14.04/trusty-updates [amd64])
Conf gpgv (1.4.16-1ubuntu2.3 Ubuntu:14.04/trusty-updates [amd64])
Inst gnupg [1.4.16-1ubuntu2] (1.4.16-1ubuntu2.3 Ubuntu:14.04/trusty-updates [amd64])
Conf gnupg (1.4.16-1ubuntu2.3 Ubuntu:14.04/trusty-updates [amd64])
Inst apt [1.0.1ubuntu2] (1.0.1ubuntu2.14 Ubuntu:14.04/trusty-updates [amd64])
Conf apt (1.0.1ubuntu2.14 Ubuntu:14.04/trusty-updates [amd64])
Inst bsdutils [1:2.20.1-5.1ubuntu20] (1:2.20.1-5.1ubuntu20.7 Ubuntu:14.04/trusty-updates [amd64])
Conf bsdutils (1:2.20.1-5.1ubuntu20.7 Ubuntu:14.04/trusty-updates [amd64])
Inst libmount1 [2.20.1-5.1ubuntu20] (2.20.1-5.1ubuntu20.7 Ubuntu:14.04/trusty-updates [amd64])
Conf libmount1 (2.20.1-5.1ubuntu20.7 Ubuntu:14.04/trusty-updates [amd64])
Inst libsepol1 [2.2-1] (2.2-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libsepol1 (2.2-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Inst libss2 [1.42.9-3ubuntu1] (1.42.9-3ubuntu1.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libss2 (1.42.9-3ubuntu1.3 Ubuntu:14.04/trusty-updates [amd64])
Inst libapt-inst1.5 [1.0.1ubuntu2] (1.0.1ubuntu2.14 Ubuntu:14.04/trusty-updates [amd64])
Inst file [1:5.14-2ubuntu3] (1:5.14-2ubuntu3.3 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libmagic1 [1:5.14-2ubuntu3] (1:5.14-2ubuntu3.3 Ubuntu:14.04/trusty-updates [amd64])
Inst klibc-utils [2.0.3-0ubuntu1] (2.0.3-0ubuntu1.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libklibc [2.0.3-0ubuntu1] (2.0.3-0ubuntu1.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Inst initramfs-tools [0.103ubuntu4] (0.103ubuntu4.3 Ubuntu:14.04/trusty-updates [all]) []
Inst initramfs-tools-bin [0.103ubuntu4] (0.103ubuntu4.3 Ubuntu:14.04/trusty-updates [amd64])
Inst cpio [2.11+dfsg-1ubuntu1] (2.11+dfsg-1ubuntu1.2 Ubuntu:14.04/trusty-updates [amd64])
Inst plymouth-label [0.8.8-0ubuntu17] (0.8.8-0ubuntu17.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst plymouth [0.8.8-0ubuntu17] (0.8.8-0ubuntu17.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libplymouth2 [0.8.8-0ubuntu17] (0.8.8-0ubuntu17.1 Ubuntu:14.04/trusty-updates [amd64])
Inst bash-completion [1:2.1-4] (1:2.1-4ubuntu0.2 Ubuntu:14.04/trusty-updates [all])
Inst python3-gi-cairo [3.12.0-1] (3.12.0-1ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst python3-gi [3.12.0-1] (3.12.0-1ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst libvte-2.90-9 [1:0.34.9-1ubuntu1] (1:0.34.9-1ubuntu2 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libvte-2.90-common [1:0.34.9-1ubuntu1] (1:0.34.9-1ubuntu2 Ubuntu:14.04/trusty-updates [all])
Inst gir1.2-vte-2.90 [1:0.34.9-1ubuntu1] (1:0.34.9-1ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Inst python-apt-common [0.9.3.5] (0.9.3.5ubuntu2 Ubuntu:14.04/trusty-updates [all])
Inst python3-apt [0.9.3.5] (0.9.3.5ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Inst python-apt [0.9.3.5] (0.9.3.5ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Inst python3-aptdaemon.pkcompat [1.1.1-1ubuntu5] (1.1.1-1ubuntu5.2 Ubuntu:14.04/trusty-updates [all]) []
Inst aptdaemon-data [1.1.1-1ubuntu5] (1.1.1-1ubuntu5.2 Ubuntu:14.04/trusty-updates [all]) []
Inst python3-aptdaemon.gtk3widgets [1.1.1-1ubuntu5] (1.1.1-1ubuntu5.2 Ubuntu:14.04/trusty-updates [all]) []
Inst python3-pkg-resources [3.3-1ubuntu1] (3.3-1ubuntu2 Ubuntu:14.04/trusty-updates [all]) []
Inst aptdaemon [1.1.1-1ubuntu5] (1.1.1-1ubuntu5.2 Ubuntu:14.04/trusty-updates [all]) []
Inst python3-aptdaemon [1.1.1-1ubuntu5] (1.1.1-1ubuntu5.2 Ubuntu:14.04/trusty-updates [all])
Inst im-config [0.24-1ubuntu4] (0.24-1ubuntu4.2 Ubuntu:14.04/trusty-updates [all])
Inst language-selector-gnome [0.129] (0.129.3 Ubuntu:14.04/trusty-updates [all]) []
Inst language-selector-common [0.129] (0.129.3 Ubuntu:14.04/trusty-updates [all])
Inst libnuma1 [2.0.9~rc5-1ubuntu2] (2.0.9~rc5-1ubuntu3.14.04.2 Ubuntu:14.04/trusty-updates [amd64])
Inst pciutils [1:3.2.1-1ubuntu5] (1:3.2.1-1ubuntu5.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libpci3 [1:3.2.1-1ubuntu5] (1:3.2.1-1ubuntu5.1 Ubuntu:14.04/trusty-updates [amd64])
Inst man-db [2.6.7.1-1] (2.6.7.1-1ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst fonts-droid [1:4.3-3ubuntu1] (1:4.3-3ubuntu1.2 Ubuntu:14.04/trusty-updates [all])
Inst libp11-kit-gnome-keyring [3.10.1-1ubuntu4] (3.10.1-1ubuntu4.2 Ubuntu:14.04/trusty-updates [amd64])
Inst gnome-keyring [3.10.1-1ubuntu4] (3.10.1-1ubuntu4.2 Ubuntu:14.04/trusty-updates [amd64])
Inst openssl [1.0.1f-1ubuntu2.1] (1.0.1f-1ubuntu2.19 Ubuntu:14.04/trusty-updates [amd64])
Inst ca-certificates [20130906ubuntu2] (20160104ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [all])
Inst libcurl3 [7.35.0-1ubuntu2] (7.35.0-1ubuntu2.6 Ubuntu:14.04/trusty-updates [amd64])
Inst xdg-utils [1.1.0~rc1-2ubuntu7] (1.1.0~rc1-2ubuntu7.1 Ubuntu:14.04/trusty-updates [all])
Inst google-chrome-stable [41.0.2272.101-1] (51.0.2704.106-1 Google:1.0/stable [amd64])
Inst locales [2.13+git20120306-12] (2.13+git20120306-12.1 Ubuntu:14.04/trusty-updates [all])
Inst language-pack-en [1:14.04+20140410] (1:14.04+20150219 Ubuntu:14.04/trusty-updates [all]) []
Inst language-pack-en-base [1:14.04+20140410] (1:14.04+20150219 Ubuntu:14.04/trusty-updates [all])
Inst language-pack-gnome-en [1:14.04+20140410] (1:14.04+20150219 Ubuntu:14.04/trusty-updates [all]) []
Inst language-pack-gnome-en-base [1:14.04+20140410] (1:14.04+20150219 Ubuntu:14.04/trusty-updates [all])
Inst libboost-iostreams1.54.0 [1.54.0-4ubuntu3] (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Inst libboost-system1.54.0 [1.54.0-4ubuntu3] (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Inst libclick-0.4-0 [0.4.21.1] (0.4.21.1ubuntu0.2 Ubuntu:14.04/trusty-updates [amd64])
Inst libclutter-gtk-1.0-0 [1.4.4-3ubuntu2] (1.4.4-3ubuntu2.2 Ubuntu:14.04/trusty-updates [amd64])
Inst libdbusmenu-gtk4 [12.10.3+14.04.20140319-0ubuntu1] (12.10.3+14.04.20140612-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst libdebian-installer4 [0.88ubuntu4] (0.88ubuntu5.2 Ubuntu:14.04/trusty-updates [amd64])
Inst libevent-2.0-5 [2.0.21-stable-1ubuntu1] (2.0.21-stable-1ubuntu1.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Inst libgpgme11 [1.4.3-0.1ubuntu5] (1.4.3-0.1ubuntu5.1 Ubuntu:14.04/trusty-updates [amd64])
Inst libhud2 [13.10.1+14.04.20140402-0ubuntu1] (14.04+14.04.20140604-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst libido3-0.1-0 [13.10.0+14.04.20140423-0ubuntu1] (13.10.0+14.04.20151021-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst libmms0 [0.6.2-3ubuntu2] (0.6.2-3ubuntu2.1 Ubuntu:14.04/trusty-updates [amd64])
Inst libnux-4.0-0 [4.0.6+14.04.20140409-0ubuntu1] (4.0.6+14.04.20141107-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libnux-4.0-common [4.0.6+14.04.20140409-0ubuntu1] (4.0.6+14.04.20141107-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst libpam-gnome-keyring [3.10.1-1ubuntu4] (3.10.1-1ubuntu4.2 Ubuntu:14.04/trusty-updates [amd64])
Inst libpoppler-glib8 [0.24.5-2ubuntu4] (0.24.5-2ubuntu4.4 Ubuntu:14.04/trusty-updates [amd64])
Inst libpulsedsp [1:4.0-0ubuntu11] (1:4.0-0ubuntu11.1 Ubuntu:14.04/trusty-updates [amd64])
Inst qtcore4-l10n [4:4.8.5+git192-g085f851+dfsg-2ubuntu4] (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [all])
Inst libqt4-scripttools [4:4.8.5+git192-g085f851+dfsg-2ubuntu4] (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libqt4-designer [4:4.8.5+git192-g085f851+dfsg-2ubuntu4] (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libqt4-svg [4:4.8.5+git192-g085f851+dfsg-2ubuntu4] (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libqt4-opengl [4:4.8.5+git192-g085f851+dfsg-2ubuntu4] (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libqt4-help [4:4.8.5+git192-g085f851+dfsg-2ubuntu4] (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libqtgui4 [4:4.8.5+git192-g085f851+dfsg-2ubuntu4] (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64]) [libqt4-declarative:amd64 ]
Inst libqt4-declarative [4:4.8.5+git192-g085f851+dfsg-2ubuntu4] (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libqt4-script [4:4.8.5+git192-g085f851+dfsg-2ubuntu4] (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libqt4-xmlpatterns [4:4.8.5+git192-g085f851+dfsg-2ubuntu4] (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libqt4-network [4:4.8.5+git192-g085f851+dfsg-2ubuntu4] (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libqtdbus4 [4:4.8.5+git192-g085f851+dfsg-2ubuntu4] (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64]) [qdbus:amd64 libqt4-dbus:amd64 ]
Inst libqt4-dbus [4:4.8.5+git192-g085f851+dfsg-2ubuntu4] (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64]) [qdbus:amd64 ]
Inst qdbus [4:4.8.5+git192-g085f851+dfsg-2ubuntu4] (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libqt4-xml [4:4.8.5+git192-g085f851+dfsg-2ubuntu4] (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libqt4-sql-sqlite [4:4.8.5+git192-g085f851+dfsg-2ubuntu4] (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libqt4-sql [4:4.8.5+git192-g085f851+dfsg-2ubuntu4] (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libqt4-test [4:4.8.5+git192-g085f851+dfsg-2ubuntu4] (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libqtcore4 [4:4.8.5+git192-g085f851+dfsg-2ubuntu4] (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Inst libqt5core5a [5.2.1+dfsg-1ubuntu14] (5.2.1+dfsg-1ubuntu14.3 Ubuntu:14.04/trusty-updates [amd64])
Inst libqt5dbus5 [5.2.1+dfsg-1ubuntu14] (5.2.1+dfsg-1ubuntu14.3 Ubuntu:14.04/trusty-updates [amd64])
Inst libxcb-keysyms1 (0.3.9-1ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libxkbcommon-x11-0 (0.4.1-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst libqt5gui5 [5.2.1+dfsg-1ubuntu14] (5.2.1+dfsg-1ubuntu14.3 Ubuntu:14.04/trusty-updates [amd64])
Inst libqt5network5 [5.2.1+dfsg-1ubuntu14] (5.2.1+dfsg-1ubuntu14.3 Ubuntu:14.04/trusty-updates [amd64])
Inst libqt5widgets5 [5.2.1+dfsg-1ubuntu14] (5.2.1+dfsg-1ubuntu14.3 Ubuntu:14.04/trusty-updates [amd64])
Inst libqt5opengl5 [5.2.1+dfsg-1ubuntu14] (5.2.1+dfsg-1ubuntu14.3 Ubuntu:14.04/trusty-updates [amd64])
Inst libqt5printsupport5 [5.2.1+dfsg-1ubuntu14] (5.2.1+dfsg-1ubuntu14.3 Ubuntu:14.04/trusty-updates [amd64])
Inst libqt5qml5 [5.2.1-3ubuntu15] (5.2.1-3ubuntu15.1 Ubuntu:14.04/trusty-updates [amd64])
Inst libqt5quick5 [5.2.1-3ubuntu15] (5.2.1-3ubuntu15.1 Ubuntu:14.04/trusty-updates [amd64])
Inst libqt5sql5 [5.2.1+dfsg-1ubuntu14] (5.2.1+dfsg-1ubuntu14.3 Ubuntu:14.04/trusty-updates [amd64])
Inst libqt5sql5-sqlite [5.2.1+dfsg-1ubuntu14] (5.2.1+dfsg-1ubuntu14.3 Ubuntu:14.04/trusty-updates [amd64])
Inst libqt5test5 [5.2.1+dfsg-1ubuntu14] (5.2.1+dfsg-1ubuntu14.3 Ubuntu:14.04/trusty-updates [amd64])
Inst libqt5xml5 [5.2.1+dfsg-1ubuntu14] (5.2.1+dfsg-1ubuntu14.3 Ubuntu:14.04/trusty-updates [amd64])
Inst libsoup-gnome2.4-1 [2.44.2-1ubuntu2] (2.44.2-1ubuntu2.1 Ubuntu:14.04/trusty-updates [amd64])
Inst libspectre1 [0.2.7-2ubuntu1] (0.2.7-2ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Inst libspice-server1 [0.12.4-0nocelt2] (0.12.4-0nocelt2ubuntu1.3 Ubuntu:14.04/trusty-updates [amd64])
Inst libssh-4 [0.6.1-0ubuntu3] (0.6.1-0ubuntu3.3 Ubuntu:14.04/trusty-updates [amd64])
Inst libthumbnailer0 [1.1+14.04.20140401.1-0ubuntu1] (1.1+14.04.20150205-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst libunity-gtk2-parser0 [0.0.0+14.04.20140403-0ubuntu1] (0.0.0+14.04.20141212-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst libunity-gtk3-parser0 [0.0.0+14.04.20140403-0ubuntu1] (0.0.0+14.04.20141212-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst libupstart1 [1.12.1-0ubuntu4] (1.12.1-0ubuntu4.2 Ubuntu:14.04/trusty-updates [amd64])
Inst libvncserver0 [0.9.9+dfsg-1ubuntu1] (0.9.9+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Inst libwmf0.2-7-gtk [0.2.8.4-10.3ubuntu1] (0.2.8.4-10.3ubuntu1.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libwmf0.2-7 [0.2.8.4-10.3ubuntu1] (0.2.8.4-10.3ubuntu1.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Inst libwnck-3-common [3.4.7-0ubuntu3] (3.4.7-0ubuntu3.1 Ubuntu:14.04/trusty-updates [all])
Inst libwnck-3-0 [3.4.7-0ubuntu3] (3.4.7-0ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Inst libxatracker2 [10.1.0-4ubuntu5] (10.1.3-0ubuntu0.6 Ubuntu:14.04/trusty-updates [amd64])
Inst libapparmor-perl [2.8.95~2430-0ubuntu5] (2.8.95~2430-0ubuntu5.3 Ubuntu:14.04/trusty-updates [amd64])
Inst apparmor [2.8.95~2430-0ubuntu5] (2.8.95~2430-0ubuntu5.3 Ubuntu:14.04/trusty-updates [amd64])
Inst lightdm [1.10.0-0ubuntu3] (1.10.6-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst linux-image-3.13.0-91-generic (3.13.0-91.138 Ubuntu:14.04/trusty-updates [amd64])
Inst qtdeclarative5-privatewidgets-plugin [5.2.1-3ubuntu15] (5.2.1-3ubuntu15.1 Ubuntu:14.04/trusty-updates [amd64])
Inst qtdeclarative5-dialogs-plugin [5.2.1-3ubuntu15] (5.2.1-3ubuntu15.1 Ubuntu:14.04/trusty-updates [amd64])
Inst qtdeclarative5-localstorage-plugin [5.2.1-3ubuntu15] (5.2.1-3ubuntu15.1 Ubuntu:14.04/trusty-updates [amd64])
Inst qtdeclarative5-qtquick2-plugin [5.2.1-3ubuntu15] (5.2.1-3ubuntu15.1 Ubuntu:14.04/trusty-updates [amd64])
Inst qtdeclarative5-window-plugin [5.2.1-3ubuntu15] (5.2.1-3ubuntu15.1 Ubuntu:14.04/trusty-updates [amd64])
Inst usbutils [1:007-2ubuntu1] (1:007-2ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Inst ubuntu-drivers-common [1:0.2.91.7] (1:0.2.91.11 Ubuntu:14.04/trusty-updates [amd64])
Inst unity-gtk-module-common [0.0.0+14.04.20140403-0ubuntu1] (0.0.0+14.04.20141212-0ubuntu1 Ubuntu:14.04/trusty-updates [all])
Inst unity-gtk2-module [0.0.0+14.04.20140403-0ubuntu1] (0.0.0+14.04.20141212-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst unity-gtk3-module [0.0.0+14.04.20140403-0ubuntu1] (0.0.0+14.04.20141212-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst ubuntu-release-upgrader-gtk [1:0.220.2] (1:0.220.8 Ubuntu:14.04/trusty-updates [all]) []
Inst ubuntu-release-upgrader-core [1:0.220.2] (1:0.220.8 Ubuntu:14.04/trusty-updates [all]) []
Inst gir1.2-webkit-3.0 [2.4.0-1ubuntu2] (2.4.10-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst gir1.2-javascriptcoregtk-3.0 [2.4.0-1ubuntu2] (2.4.10-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst gir1.2-soup-2.4 [2.44.2-1ubuntu2] (2.44.2-1ubuntu2.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst lsb-release [4.1+Debian11ubuntu6] (4.1+Debian11ubuntu6.1 Ubuntu:14.04/trusty-updates [all]) []
Inst python3-distupgrade [1:0.220.2] (1:0.220.8 Ubuntu:14.04/trusty-updates [all])
Inst update-manager [1:0.196.12] (1:0.196.14 Ubuntu:14.04/trusty-updates [all]) []
Inst update-manager-core [1:0.196.12] (1:0.196.14 Ubuntu:14.04/trusty-updates [all]) []
Inst python3-update-manager [1:0.196.12] (1:0.196.14 Ubuntu:14.04/trusty-updates [all])
Inst update-notifier [0.154.1] (0.154.1ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst patch [2.7.1-4] (2.7.1-4ubuntu2.3 Ubuntu:14.04/trusty-updates [amd64]) []
Inst update-notifier-common [0.154.1] (0.154.1ubuntu1 Ubuntu:14.04/trusty-updates [all])
Inst gstreamer1.0-plugins-base [1.2.3-1] (1.2.4-1~ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Inst gstreamer1.0-plugins-good [1.2.3-1ubuntu2] (1.2.4-1~ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libgstreamer-plugins-good1.0-0 [1.2.3-1ubuntu2] (1.2.4-1~ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst libsystemd-journal0 [204-5ubuntu20kittyhawk1] (204-5ubuntu20.19 Ubuntu:14.04/trusty-updates [amd64])
Inst openjdk-6-jre-lib [6b31-1.13.3-1ubuntu1] (6b39-1.13.11-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [all])
Inst icedtea-6-jre-jamvm [6b31-1.13.3-1ubuntu1] (6b39-1.13.11-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst icedtea-6-jre-cacao [6b31-1.13.3-1ubuntu1] (6b39-1.13.11-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst openjdk-6-jre-headless [6b31-1.13.3-1ubuntu1] (6b39-1.13.11-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Inst multiarch-support [2.19-0ubuntu6] (2.19-0ubuntu6.9 Ubuntu:14.04/trusty-updates [amd64])
Conf multiarch-support (2.19-0ubuntu6.9 Ubuntu:14.04/trusty-updates [amd64])
Inst apt-utils [1.0.1ubuntu2] (1.0.1ubuntu2.14 Ubuntu:14.04/trusty-updates [amd64])
Inst dh-python [1.20140128-1ubuntu8] (1.20140128-1ubuntu8.2 Ubuntu:14.04/trusty-updates [all])
Inst iputils-ping [3:20121221-4ubuntu1] (3:20121221-4ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Inst net-tools [1.60-25ubuntu2] (1.60-25ubuntu2.1 Ubuntu:14.04/trusty-updates [amd64])
Inst rsyslog [7.4.4-1ubuntu2] (7.4.4-1ubuntu2.6 Ubuntu:14.04/trusty-updates [amd64])
Inst sudo [1.8.9p5-1ubuntu1] (1.8.9p5-1ubuntu1.2 Ubuntu:14.04/trusty-updates [amd64])
Inst apt-transport-https [1.0.1ubuntu2] (1.0.1ubuntu2.14 Ubuntu:14.04/trusty-updates [amd64])
Inst dnsutils [1:9.9.5.dfsg-3] (1:9.9.5.dfsg-3ubuntu0.8 Ubuntu:14.04/trusty-updates [amd64]) []
Inst bind9-host [1:9.9.5.dfsg-3] (1:9.9.5.dfsg-3ubuntu0.8 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libisc95 [1:9.9.5.dfsg-3] (1:9.9.5.dfsg-3ubuntu0.8 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libdns100 [1:9.9.5.dfsg-3] (1:9.9.5.dfsg-3ubuntu0.8 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libisccc90 [1:9.9.5.dfsg-3] (1:9.9.5.dfsg-3ubuntu0.8 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libisccfg90 [1:9.9.5.dfsg-3] (1:9.9.5.dfsg-3ubuntu0.8 Ubuntu:14.04/trusty-updates [amd64]) []
Inst liblwres90 [1:9.9.5.dfsg-3] (1:9.9.5.dfsg-3ubuntu0.8 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libbind9-90 [1:9.9.5.dfsg-3] (1:9.9.5.dfsg-3ubuntu0.8 Ubuntu:14.04/trusty-updates [amd64])
Inst dosfstools [3.0.26-1] (3.0.26-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Inst iputils-tracepath [3:20121221-4ubuntu1] (3:20121221-4ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Inst irqbalance [1.0.6-2] (1.0.6-2ubuntu0.14.04.4 Ubuntu:14.04/trusty-updates [amd64])
Inst krb5-locales [1.12+dfsg-2ubuntu4] (1.12+dfsg-2ubuntu5.2 Ubuntu:14.04/trusty-updates [all])
Inst lshw [02.16-2ubuntu1] (02.16-2ubuntu1.3 Ubuntu:14.04/trusty-updates [amd64])
Inst ltrace [0.7.3-4ubuntu5] (0.7.3-4ubuntu5.1 Ubuntu:14.04/trusty-updates [amd64])
Inst openssh-client [1:6.6p1-2ubuntu1] (1:6.6p1-2ubuntu2.7 Ubuntu:14.04/trusty-updates [amd64])
Inst plymouth-theme-ubuntu-text [0.8.8-0ubuntu17] (0.8.8-0ubuntu17.1 Ubuntu:14.04/trusty-updates [amd64])
Inst python3-gdbm [3.4.0-0ubuntu1] (3.4.3-1~14.04.2 Ubuntu:14.04/trusty-updates [amd64])
Inst rsync [3.1.0-2ubuntu0.1] (3.1.0-2ubuntu0.2 Ubuntu:14.04/trusty-updates [amd64])
Inst tcpdump [4.5.1-2ubuntu1] (4.5.1-2ubuntu1.2 Ubuntu:14.04/trusty-updates [amd64])
Inst uuid-runtime [2.20.1-5.1ubuntu20] (2.20.1-5.1ubuntu20.7 Ubuntu:14.04/trusty-updates [amd64])
Inst nautilus-sendto-empathy [3.8.6-0ubuntu9] (3.8.6-0ubuntu9.2 Ubuntu:14.04/trusty-updates [amd64]) []
Inst mcp-account-manager-uoa [3.8.6-0ubuntu9] (3.8.6-0ubuntu9.2 Ubuntu:14.04/trusty-updates [amd64]) []
Inst account-plugin-yahoo [3.8.6-0ubuntu9] (3.8.6-0ubuntu9.2 Ubuntu:14.04/trusty-updates [amd64]) []
Inst account-plugin-salut [3.8.6-0ubuntu9] (3.8.6-0ubuntu9.2 Ubuntu:14.04/trusty-updates [amd64]) []
Inst account-plugin-jabber [3.8.6-0ubuntu9] (3.8.6-0ubuntu9.2 Ubuntu:14.04/trusty-updates [amd64]) []
Inst account-plugin-aim [3.8.6-0ubuntu9] (3.8.6-0ubuntu9.2 Ubuntu:14.04/trusty-updates [amd64]) []
Inst empathy [3.8.6-0ubuntu9] (3.8.6-0ubuntu9.2 Ubuntu:14.04/trusty-updates [amd64]) []
Inst empathy-common [3.8.6-0ubuntu9] (3.8.6-0ubuntu9.2 Ubuntu:14.04/trusty-updates [all])
Inst telepathy-gabble [0.18.2-1] (0.18.3-0ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Inst gstreamer1.0-pulseaudio [1.2.3-1ubuntu2] (1.2.4-1~ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst libaccount-plugin-generic-oauth [0.11+14.04.20140409.1-0ubuntu1] (0.11+14.04.20140409.1-0ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Inst account-plugin-facebook [0.11+14.04.20140409.1-0ubuntu1] (0.11+14.04.20140409.1-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Inst account-plugin-flickr [0.11+14.04.20140409.1-0ubuntu1] (0.11+14.04.20140409.1-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Inst libaccount-plugin-google [0.11+14.04.20140409.1-0ubuntu1] (0.11+14.04.20140409.1-0ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Inst account-plugin-google [0.11+14.04.20140409.1-0ubuntu1] (0.11+14.04.20140409.1-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Inst account-plugin-twitter [0.11+14.04.20140409.1-0ubuntu1] (0.11+14.04.20140409.1-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Inst account-plugin-windows-live [0.11+14.04.20140409.1-0ubuntu1] (0.11+14.04.20140409.1-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Inst libzeitgeist-2.0-0 [0.9.14-0ubuntu4] (0.9.14-0ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Inst python-zeitgeist [0.9.14-0ubuntu4] (0.9.14-0ubuntu4.1 Ubuntu:14.04/trusty-updates [all])
Inst zeitgeist-core [0.9.14-0ubuntu4] (0.9.14-0ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Inst zeitgeist-datahub [0.9.14-0ubuntu4] (0.9.14-0ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Inst zeitgeist [0.9.14-0ubuntu4] (0.9.14-0ubuntu4.1 Ubuntu:14.04/trusty-updates [all])
Inst activity-log-manager [0.9.7-0ubuntu14] (0.9.7-0ubuntu14.1 Ubuntu:14.04/trusty-updates [amd64])
Inst activity-log-manager-control-center [0.9.7-0ubuntu14] (0.9.7-0ubuntu14.1 Ubuntu:14.04/trusty-updates [all])
Inst grub-efi-amd64-signed [1.34+2.02~beta2-9] (1.34.9+2.02~beta2-9ubuntu1.8 Ubuntu:14.04/trusty-updates [amd64]) []
Inst efibootmgr [0.5.4-7ubuntu1] (0.5.4-7ubuntu1.2 Ubuntu:14.04/trusty-updates [amd64]) []
Inst grub-efi-amd64 [2.02~beta2-9] (2.02~beta2-9ubuntu1.8 Ubuntu:14.04/trusty-updates [amd64]) []
Inst grub-efi-amd64-bin [2.02~beta2-9] (2.02~beta2-9ubuntu1.8 Ubuntu:14.04/trusty-updates [amd64]) []
Inst grub2-common [2.02~beta2-9] (2.02~beta2-9ubuntu1.8 Ubuntu:14.04/trusty-updates [amd64]) []
Inst grub-common [2.02~beta2-9] (2.02~beta2-9ubuntu1.8 Ubuntu:14.04/trusty-updates [amd64])
Inst python3-problem-report [2.14.1-0ubuntu3] (2.14.1-0ubuntu3.21 Ubuntu:14.04/trusty-updates [all])
Inst python3-apport [2.14.1-0ubuntu3] (2.14.1-0ubuntu3.21 Ubuntu:14.04/trusty-updates [all])
Inst apport [2.14.1-0ubuntu3] (2.14.1-0ubuntu3.21 Ubuntu:14.04/trusty-updates [all])
Inst gir1.2-wnck-3.0 [3.4.7-0ubuntu3] (3.4.7-0ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Inst apport-gtk [2.14.1-0ubuntu3] (2.14.1-0ubuntu3.21 Ubuntu:14.04/trusty-updates [all])
Inst archdetect-deb [1.95ubuntu2] (1.95ubuntu2.1 Ubuntu:14.04/trusty-updates [amd64])
Inst bluez-alsa [4.101-0ubuntu13] (4.101-0ubuntu13.1 Ubuntu:14.04/trusty-updates [amd64])
Inst bluez-cups [4.101-0ubuntu13] (4.101-0ubuntu13.1 Ubuntu:14.04/trusty-updates [amd64])
Inst btrfs-tools [3.12-1] (3.12-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Inst libcompizconfig0 [1:0.9.11+14.04.20140423-0ubuntu1] (1:0.9.11.3+14.04.20160425-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst compiz-gnome [1:0.9.11+14.04.20140423-0ubuntu1] (1:0.9.11.3+14.04.20160425-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst compiz-core [1:0.9.11+14.04.20140423-0ubuntu1] (1:0.9.11.3+14.04.20160425-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) [compiz-plugins:amd64 compiz-plugins-default:amd64 ]
Inst compiz-plugins [1:0.9.11+14.04.20140423-0ubuntu1] (1:0.9.11.3+14.04.20160425-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) [compiz-plugins-default:amd64 ]
Inst compiz-plugins-default [1:0.9.11+14.04.20140423-0ubuntu1] (1:0.9.11.3+14.04.20160425-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libdecoration0 [1:0.9.11+14.04.20140423-0ubuntu1] (1:0.9.11.3+14.04.20160425-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst metacity [1:2.34.13-0ubuntu4] (1:2.34.13-0ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libmetacity-private0a [1:2.34.13-0ubuntu4] (1:2.34.13-0ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst metacity-common [1:2.34.13-0ubuntu4] (1:2.34.13-0ubuntu4.1 Ubuntu:14.04/trusty-updates [all])
Inst compiz [1:0.9.11+14.04.20140423-0ubuntu1] (1:0.9.11.3+14.04.20160425-0ubuntu1 Ubuntu:14.04/trusty-updates [all])
Inst python-gobject [3.12.0-1] (3.12.0-1ubuntu1 Ubuntu:14.04/trusty-updates [all])
Inst dell-recovery [1.32~somerville6] (1.33~somerville1 dell.archive.canonical.com [all])
Inst dpkg-dev [1.17.5ubuntu5.2] (1.17.5ubuntu5.7 Ubuntu:14.04/trusty-updates [all]) []
Inst libdpkg-perl [1.17.5ubuntu5.2] (1.17.5ubuntu5.7 Ubuntu:14.04/trusty-updates [all])
Inst dkms [2.2.0.3-1.1ubuntu5] (2.2.0.3-1.1ubuntu5.14.04.5 Ubuntu:14.04/trusty-updates [all])
Inst duplicity [0.6.23-1ubuntu4] (0.6.23-1ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Inst libecryptfs0 [104-0ubuntu1] (104-0ubuntu1.14.04.4 Ubuntu:14.04/trusty-updates [amd64])
Inst ecryptfs-utils [104-0ubuntu1] (104-0ubuntu1.14.04.4 Ubuntu:14.04/trusty-updates [amd64])
Inst eog [3.10.2-0ubuntu5] (3.10.2-0ubuntu5.1 Ubuntu:14.04/trusty-updates [amd64])
Inst evince [3.10.3-0ubuntu10] (3.10.3-0ubuntu10.2 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libevdocument3-4 [3.10.3-0ubuntu10] (3.10.3-0ubuntu10.2 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libevview3-3 [3.10.3-0ubuntu10] (3.10.3-0ubuntu10.2 Ubuntu:14.04/trusty-updates [amd64])
Inst evince-common [3.10.3-0ubuntu10] (3.10.3-0ubuntu10.2 Ubuntu:14.04/trusty-updates [all])
Inst evolution-data-server-online-accounts [3.10.4-0ubuntu1] (3.10.4-0ubuntu1.5 Ubuntu:14.04/trusty-updates [amd64]) []
Inst evolution-data-server [3.10.4-0ubuntu1] (3.10.4-0ubuntu1.5 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libcamel-1.2-45 [3.10.4-0ubuntu1] (3.10.4-0ubuntu1.5 Ubuntu:14.04/trusty-updates [amd64]) []
Inst evolution-data-server-common [3.10.4-0ubuntu1] (3.10.4-0ubuntu1.5 Ubuntu:14.04/trusty-updates [all])
Inst libedataserver-1.2-18 [3.10.4-0ubuntu1] (3.10.4-0ubuntu1.5 Ubuntu:14.04/trusty-updates [amd64])
Inst libebackend-1.2-7 [3.10.4-0ubuntu1] (3.10.4-0ubuntu1.5 Ubuntu:14.04/trusty-updates [amd64])
Inst libebook-contacts-1.2-0 [3.10.4-0ubuntu1] (3.10.4-0ubuntu1.5 Ubuntu:14.04/trusty-updates [amd64])
Inst libedata-book-1.2-20 [3.10.4-0ubuntu1] (3.10.4-0ubuntu1.5 Ubuntu:14.04/trusty-updates [amd64])
Inst libebook-1.2-14 [3.10.4-0ubuntu1] (3.10.4-0ubuntu1.5 Ubuntu:14.04/trusty-updates [amd64])
Inst libecal-1.2-16 [3.10.4-0ubuntu1] (3.10.4-0ubuntu1.5 Ubuntu:14.04/trusty-updates [amd64])
Inst libedata-cal-1.2-23 [3.10.4-0ubuntu1] (3.10.4-0ubuntu1.5 Ubuntu:14.04/trusty-updates [amd64])
Inst libgweather-common [3.10.2-0ubuntu1] (3.10.2-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Inst libgweather-3-6 [3.10.2-0ubuntu1] (3.10.2-0ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Inst unzip [6.0-9ubuntu1] (6.0-9ubuntu1.5 Ubuntu:14.04/trusty-updates [amd64])
Inst file-roller [3.10.2.1-0ubuntu4] (3.10.2.1-0ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Inst gdb [7.7-0ubuntu3] (7.7.1-0ubuntu5~14.04.2 Ubuntu:14.04/trusty-updates [amd64])
Inst gir1.2-appindicator3-0.1 [12.10.1+13.10.20130920-0ubuntu4] (12.10.1+13.10.20130920-0ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Inst gir1.2-ebook-1.2 [3.10.4-0ubuntu1] (3.10.4-0ubuntu1.5 Ubuntu:14.04/trusty-updates [amd64]) []
Inst gir1.2-ebookcontacts-1.2 [3.10.4-0ubuntu1] (3.10.4-0ubuntu1.5 Ubuntu:14.04/trusty-updates [amd64]) []
Inst gir1.2-edataserver-1.2 [3.10.4-0ubuntu1] (3.10.4-0ubuntu1.5 Ubuntu:14.04/trusty-updates [amd64])
Inst gir1.2-gstreamer-1.0 [1.2.3-1] (1.2.4-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst gir1.2-gst-plugins-base-1.0 [1.2.3-1] (1.2.4-1~ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Inst gir1.2-gudev-1.0 [1:204-5ubuntu20kittyhawk1] (1:204-5ubuntu20.19 Ubuntu:14.04/trusty-updates [amd64])
Inst gir1.2-networkmanager-1.0 [0.9.8.8-0ubuntu7] (0.9.8.8-0ubuntu7.3 Ubuntu:14.04/trusty-updates [amd64])
Inst gir1.2-udisks-2.0 [2.1.3-1] (2.1.3-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Inst gnome-calculator [1:3.10.2-0ubuntu1] (1:3.10.3-0ubuntu0.1.1 Ubuntu:14.04/trusty-updates [amd64])
Inst gnome-control-center-shared-data [1:3.6.3-0ubuntu56] (1:3.6.3-0ubuntu56.1 Ubuntu:14.04/trusty-updates [all])
Inst gnome-session-bin [3.9.90-0ubuntu12] (3.9.90-0ubuntu12.1 Ubuntu:14.04/trusty-updates [amd64])
Inst ubuntu-session [3.9.90-0ubuntu12] (3.9.90-0ubuntu12.1 Ubuntu:14.04/trusty-updates [all]) []
Inst gnome-session-common [3.9.90-0ubuntu12] (3.9.90-0ubuntu12.1 Ubuntu:14.04/trusty-updates [all])
Inst gnome-sudoku [1:3.10.2-0ubuntu2] (1:3.10.2-0ubuntu3.1 Ubuntu:14.04/trusty-updates [all])
Inst gstreamer1.0-alsa [1.2.3-1] (1.2.4-1~ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Inst gstreamer1.0-tools [1.2.3-1] (1.2.4-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst gstreamer1.0-plugins-base-apps [1.2.3-1] (1.2.4-1~ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Inst gstreamer1.0-x [1.2.3-1] (1.2.4-1~ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Inst heirloom-mailx [12.5-2] (12.5-2+deb7u1build0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Inst hud [13.10.1+14.04.20140402-0ubuntu1] (14.04+14.04.20140604-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst ibus-gtk [1.5.5-1ubuntu3] (1.5.5-1ubuntu3.2 Ubuntu:14.04/trusty-updates [amd64])
Inst ibus-gtk3 [1.5.5-1ubuntu3] (1.5.5-1ubuntu3.2 Ubuntu:14.04/trusty-updates [amd64])
Inst indicator-session [12.10.5+14.04.20140410-0ubuntu1] (12.10.5+14.04.20151021.1-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst intel-gpu-tools [1.3-0ubuntu2] (1.3-0ubuntu2.1 Ubuntu:14.04/trusty-updates [amd64])
Inst iproute [1:3.12.0-2] (1:3.12.0-2ubuntu1 Ubuntu:14.04/trusty-updates [all])
Inst python-pkg-resources [3.3-1ubuntu1] (3.3-1ubuntu2 Ubuntu:14.04/trusty-updates [all])
Inst python-aptdaemon.gtk3widgets [1.1.1-1ubuntu5] (1.1.1-1ubuntu5.2 Ubuntu:14.04/trusty-updates [all]) []
Inst python-aptdaemon [1.1.1-1ubuntu5] (1.1.1-1ubuntu5.2 Ubuntu:14.04/trusty-updates [all])
Inst landscape-client-ui-install [14.01-0ubuntu3] (14.12-0ubuntu0.14.04 Ubuntu:14.04/trusty-updates [amd64])
Inst libgnome-control-center1 [1:3.6.3-0ubuntu56] (1:3.6.3-0ubuntu56.1 Ubuntu:14.04/trusty-updates [amd64])
Inst libgphoto2-l10n [2.5.3.1-1ubuntu2] (2.5.3.1-1ubuntu2.2 Ubuntu:14.04/trusty-updates [all])
Inst libgtk-3-bin [3.10.8-0ubuntu1] (3.10.8-0ubuntu1.6 Ubuntu:14.04/trusty-updates [amd64])
Inst liblightdm-gobject-1-0 [1.10.0-0ubuntu3] (1.10.6-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst liblwp-protocol-https-perl [6.04-2] (6.04-2ubuntu0.1 Ubuntu:14.04/trusty-updates [all])
Inst libminiupnpc8 [1.6-3ubuntu2] (1.6-3ubuntu2.14.04.2 Ubuntu:14.04/trusty-updates [amd64])
Inst libmono-system-xml4.0-cil [3.2.8+dfsg-4ubuntu1] (3.2.8+dfsg-4ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Inst libmono-system-security4.0-cil [3.2.8+dfsg-4ubuntu1] (3.2.8+dfsg-4ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Inst libmono-system-configuration4.0-cil [3.2.8+dfsg-4ubuntu1] (3.2.8+dfsg-4ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Inst libmono-system4.0-cil [3.2.8+dfsg-4ubuntu1] (3.2.8+dfsg-4ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Inst libmono-security4.0-cil [3.2.8+dfsg-4ubuntu1] (3.2.8+dfsg-4ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Inst mono-runtime [3.2.8+dfsg-4ubuntu1] (3.2.8+dfsg-4ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst mono-runtime-sgen [3.2.8+dfsg-4ubuntu1] (3.2.8+dfsg-4ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst mono-runtime-common [3.2.8+dfsg-4ubuntu1] (3.2.8+dfsg-4ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst mono-gac [3.2.8+dfsg-4ubuntu1] (3.2.8+dfsg-4ubuntu1.1 Ubuntu:14.04/trusty-updates [all]) []
Inst mono-4.0-gac [3.2.8+dfsg-4ubuntu1] (3.2.8+dfsg-4ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Inst libmono-corlib4.5-cil [3.2.8+dfsg-4ubuntu1] (3.2.8+dfsg-4ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Inst libmono-cairo4.0-cil [3.2.8+dfsg-4ubuntu1] (3.2.8+dfsg-4ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Inst libmono-corlib4.0-cil [3.2.8+dfsg-4ubuntu1] (3.2.8+dfsg-4ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Inst libmono-i18n4.0-cil [3.2.8+dfsg-4ubuntu1] (3.2.8+dfsg-4ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Inst libmono-i18n-west4.0-cil [3.2.8+dfsg-4ubuntu1] (3.2.8+dfsg-4ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Inst libmono-system-drawing4.0-cil [3.2.8+dfsg-4ubuntu1] (3.2.8+dfsg-4ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Inst libpurple-bin [1:2.10.9-0ubuntu3] (1:2.10.9-0ubuntu3.2 Ubuntu:14.04/trusty-updates [all])
Inst libpurple0 [1:2.10.9-0ubuntu3] (1:2.10.9-0ubuntu3.2 Ubuntu:14.04/trusty-updates [amd64])
Inst libreoffice-avmedia-backend-gstreamer [1:4.2.3~rc3-0ubuntu2] (1:4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64])
Inst libreoffice-presentation-minimizer [1:4.2.3~rc3-0ubuntu2] (1:4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [all])
Inst libufe-xidgetter0 [3.0.0+14.04.20140416-0ubuntu1] (3.0.0+14.04.20140416-0ubuntu1.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Inst unity [7.2.0+14.04.20140423-0ubuntu1.2] (7.2.6+14.04.20160408-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst unity-lens-music [6.9.0+13.10.20131011-0ubuntu1] (6.9.0+14.04.20151120.2-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst nux-tools [4.0.6+14.04.20140409-0ubuntu1] (4.0.6+14.04.20141107-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst unity-greeter [14.04.9-0ubuntu1] (14.04.11-0ubuntu1somerville1 dell.archive.canonical.com [amd64]) []
Inst libunity-core-6.0-9 [7.2.0+14.04.20140423-0ubuntu1.2] (7.2.6+14.04.20160408-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst unity-services [7.2.0+14.04.20140423-0ubuntu1.2] (7.2.6+14.04.20160408-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst whoopsie [0.2.24.5] (0.2.24.6ubuntu2 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libwhoopsie0 [0.2.24.5] (0.2.24.6ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Inst linux-firmware [1.127.8] (1.127.22 Ubuntu:14.04/trusty-updates [all])
Inst linux-image-extra-3.13.0-91-generic (3.13.0-91.138 Ubuntu:14.04/trusty-updates [amd64])
Inst linux-generic [3.13.0.38.45] (3.13.0.91.97 Ubuntu:14.04/trusty-updates [amd64]) []
Inst linux-image-generic [3.13.0.38.45] (3.13.0.91.97 Ubuntu:14.04/trusty-updates [amd64]) []
Inst linux-headers-3.13.0-91 (3.13.0-91.138 Ubuntu:14.04/trusty-updates [all]) []
Inst linux-headers-3.13.0-91-generic (3.13.0-91.138 Ubuntu:14.04/trusty-updates [amd64]) []
Inst linux-headers-generic [3.13.0.38.45] (3.13.0.91.97 Ubuntu:14.04/trusty-updates [amd64])
Inst myspell-en-gb [1:4.2.1-0ubuntu1] (1:4.2.1-0ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Inst myspell-en-za [1:4.2.1-0ubuntu1] (1:4.2.1-0ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Inst mythes-en-us [1:4.2.1-0ubuntu1] (1:4.2.1-0ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Inst notify-osd-icons [0.8+14.04.20131204-0ubuntu1] (0.8+14.04.20151016-0ubuntu1 Ubuntu:14.04/trusty-updates [all])
Inst onboard [1.0.0-0ubuntu4] (1.0.1-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst onboard-data [1.0.0-0ubuntu4] (1.0.1-0ubuntu1 Ubuntu:14.04/trusty-updates [all])
Inst openoffice.org-hyphenation [0.7] (0.7.1 Ubuntu:14.04/trusty-updates [all])
Inst os-prober [1.63ubuntu1] (1.63ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Inst plymouth-theme-ubuntu-logo [0.8.8-0ubuntu17] (0.8.8-0ubuntu17.1 Ubuntu:14.04/trusty-updates [amd64])
Inst pm-utils [1.4.1-13] (1.4.1-13ubuntu0.2 Ubuntu:14.04/trusty-updates [all])
Inst pulseaudio-utils [1:4.0-0ubuntu11] (1:4.0-0ubuntu11.1 Ubuntu:14.04/trusty-updates [amd64])
Inst pulseaudio-module-x11 [1:4.0-0ubuntu11] (1:4.0-0ubuntu11.1 Ubuntu:14.04/trusty-updates [amd64])
Inst python-six [1.5.2-1] (1.5.2-1ubuntu1 Ubuntu:14.04/trusty-updates [all])
Inst python-urllib3 (1.7.1-1ubuntu4 Ubuntu:14.04/trusty-updates [all])
Inst python-requests (2.2.1-1ubuntu0.3 Ubuntu:14.04/trusty-updates [all])
Inst python-cupshelpers [1.4.3+20140219-0ubuntu2] (1.4.3+20140219-0ubuntu2.6 Ubuntu:14.04/trusty-updates [all])
Inst python-ibus [1.5.5-1ubuntu3] (1.5.5-1ubuntu3.2 Ubuntu:14.04/trusty-updates [all])
Inst python-libxml2 [2.9.1+dfsg1-3ubuntu4] (2.9.1+dfsg1-3ubuntu4.8 Ubuntu:14.04/trusty-updates [amd64])
Inst python-lxml [3.3.3-1] (3.3.3-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Inst python3-chardet [2.0.1-1] (2.2.1-2~ubuntu1 Ubuntu:14.04/trusty-updates [all])
Inst python3-lxml [3.3.3-1] (3.3.3-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Inst python3-requests [2.2.1-1] (2.2.1-1ubuntu0.3 Ubuntu:14.04/trusty-updates [all])
Inst software-properties-common [0.92.37] (0.92.37.7 Ubuntu:14.04/trusty-updates [all]) []
Inst software-properties-gtk [0.92.37] (0.92.37.7 Ubuntu:14.04/trusty-updates [all]) []
Inst unattended-upgrades [0.82.1ubuntu2] (0.82.1ubuntu2.4 Ubuntu:14.04/trusty-updates [all]) []
Inst python3-software-properties [0.92.37] (0.92.37.7 Ubuntu:14.04/trusty-updates [all])
Inst webapp-container [0.23+14.04.20140422-0ubuntu1] (0.23+14.04.20140428-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst liboxideqtcore0 [1.0.0~bzr501-0ubuntu2] (1.15.8-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst oxideqt-codecs [1.0.0~bzr501-0ubuntu2] (1.15.8-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libandroid-properties1 (0.1.0+git20131207+e452e83-0ubuntu12 Ubuntu:14.04/trusty [amd64]) []
Inst liboxideqtquick0 (1.15.8-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst liboxideqt-qmlplugin [1.0.0~bzr501-0ubuntu2] (1.15.8-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst qtdeclarative5-ubuntu-ui-extras-browser-plugin [0.23+14.04.20140422-0ubuntu1] (0.23+14.04.20140428-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) [webbrowser-app:amd64 ]
Inst webbrowser-app [0.23+14.04.20140422-0ubuntu1] (0.23+14.04.20140428-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets [0.23+14.04.20140422-0ubuntu1] (0.23+14.04.20140428-0ubuntu1 Ubuntu:14.04/trusty-updates [all])
Inst sane-utils [1.0.23-3ubuntu3] (1.0.23-3ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Inst sbsigntool [0.6-0ubuntu7] (0.6-0ubuntu7.1 Ubuntu:14.04/trusty-updates [amd64])
Inst shim-signed [1.6+0.4-0ubuntu4] (1.9+0.8-0ubuntu2 Ubuntu:14.04/trusty-updates [amd64]) []
Inst shim [0.4-0ubuntu4] (0.8-0ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Inst shotwell-common [0.18.0-0ubuntu4] (0.18.0-0ubuntu4.4 Ubuntu:14.04/trusty-updates [all]) [shotwell:amd64 ]
Inst shotwell [0.18.0-0ubuntu4] (0.18.0-0ubuntu4.4 Ubuntu:14.04/trusty-updates [amd64])
Inst simple-scan [3.12.0-0ubuntu1] (3.12.3-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst ssh-askpass-gnome [1:6.6p1-2ubuntu1] (1:6.6p1-2ubuntu2.7 Ubuntu:14.04/trusty-updates [amd64])
Inst system-config-printer-common [1.4.3+20140219-0ubuntu2] (1.4.3+20140219-0ubuntu2.6 Ubuntu:14.04/trusty-updates [all])
Inst system-config-printer-gnome [1.4.3+20140219-0ubuntu2] (1.4.3+20140219-0ubuntu2.6 Ubuntu:14.04/trusty-updates [all])
Inst system-config-printer-udev [1.4.3+20140219-0ubuntu2] (1.4.3+20140219-0ubuntu2.6 Ubuntu:14.04/trusty-updates [amd64])
Inst t1utils [1.37-2ubuntu1] (1.37-2ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Inst thunderbird-locale-en [1:24.5.0+build1-0ubuntu0.14.04.1] (1:38.8.0+build1-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst thunderbird [1:24.5.0+build1-0ubuntu0.14.04.1] (1:38.8.0+build1-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) [thunderbird-gnome-support:amd64 ]
Inst thunderbird-gnome-support [1:24.5.0+build1-0ubuntu0.14.04.1] (1:38.8.0+build1-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Inst thunderbird-locale-en-us [1:24.5.0+build1-0ubuntu0.14.04.1] (1:38.8.0+build1-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [all])
Inst transmission-common [2.82-1.1ubuntu3] (2.82-1.1ubuntu3.1 Ubuntu:14.04/trusty-updates [all]) [transmission-gtk:amd64 ]
Inst transmission-gtk [2.82-1.1ubuntu3] (2.82-1.1ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Inst ubuntu-docs [14.04.3] (14.04.5 Ubuntu:14.04/trusty-updates [all])
Inst unity-scope-musicstores [6.9.0+13.10.20131011-0ubuntu1] (6.9.0+14.04.20151120.2-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst usb-creator-gtk [0.2.56] (0.2.56.3ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst usb-creator-common [0.2.56] (0.2.56.3ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Inst webaccounts-extension-common [0.5-0ubuntu2] (0.5-0ubuntu2.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-video-radeon [1:7.3.0-1ubuntu3] (1:7.3.0-1ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-video-ati [1:7.3.0-1ubuntu3] (1:7.3.0-1ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-video-intel [2:2.99.910-0ubuntu1] (2:2.99.910-0ubuntu1.6 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-video-openchrome [1:0.3.3-1build1] (1:0.3.3-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-video-all [1:7.7+1ubuntu8] (1:7.7+1ubuntu8.1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg-input-all [1:7.7+1ubuntu8] (1:7.7+1ubuntu8.1 Ubuntu:14.04/trusty-updates [amd64])
Inst xserver-xorg [1:7.7+1ubuntu8] (1:7.7+1ubuntu8.1 Ubuntu:14.04/trusty-updates [amd64])
Inst xorg [1:7.7+1ubuntu8] (1:7.7+1ubuntu8.1 Ubuntu:14.04/trusty-updates [amd64])
Inst apt-clone [0.3.1~ubuntu11] (0.3.1~ubuntu11.1 Ubuntu:14.04/trusty-updates [all])
Inst casper [1.340] (1.340.2 Ubuntu:14.04/trusty-updates [amd64])
Inst gdisk [0.8.8-1build1] (0.8.8-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Inst hardening-includes [2.5ubuntu2] (2.5ubuntu2.1 Ubuntu:14.04/trusty-updates [all])
Inst openjdk-6-jre [6b31-1.13.3-1ubuntu1] (6b39-1.13.11-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Inst icedtea-netx-common [1.5-1ubuntu1] (1.5.3-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [all])
Inst icedtea-6-plugin [1.5-1ubuntu1] (1.5.3-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst icedtea-netx [1.5-1ubuntu1] (1.5.3-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Inst indicator-printers [0.1.7+14.04.20140313-0ubuntu1] (0.1.7+14.04.20140527-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst kpartx-boot [0.4.9-3ubuntu7] (0.4.9-3ubuntu7.13 Ubuntu:14.04/trusty-updates [all]) []
Inst kpartx [0.4.9-3ubuntu7] (0.4.9-3ubuntu7.13 Ubuntu:14.04/trusty-updates [amd64])
Inst oneconf-common [0.3.7] (0.3.7.14.04.1 Ubuntu:14.04/trusty-updates [all])
Inst python3-oneconf [0.3.7] (0.3.7.14.04.1 Ubuntu:14.04/trusty-updates [all])
Inst oneconf [0.3.7] (0.3.7.14.04.1 Ubuntu:14.04/trusty-updates [all])
Inst pulseaudio-module-bluetooth [1:4.0-0ubuntu11] (1:4.0-0ubuntu11.1 Ubuntu:14.04/trusty-updates [amd64])
Inst python-oneconf [0.3.7] (0.3.7.14.04.1 Ubuntu:14.04/trusty-updates [all])
Inst xul-ext-websites-integration [2.3.6+13.10.20130920.1-0ubuntu1] (2.3.6+13.10.20130920.1-0ubuntu1.2 Ubuntu:14.04/trusty-updates [all])
Conf libdbus-1-3 (1.6.18-0ubuntu4.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libjson-c2 (0.11-3ubuntu1.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libapparmor1 (2.8.95~2430-0ubuntu5.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libexpat1 (2.1.0-4ubuntu1.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libcgmanager0 (0.24-0ubuntu7.5 Ubuntu:14.04/trusty-updates [amd64])
Conf libsystemd-login0 (204-5ubuntu20.19 Ubuntu:14.04/trusty-updates [amd64])
Conf libudev1 (204-5ubuntu20.19 Ubuntu:14.04/trusty-updates [amd64])
Conf iproute2 (3.12.0-2ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf ifupdown (0.7.47.2ubuntu4.4 Ubuntu:14.04/trusty-updates [amd64])
Conf libjson0 (0.11-3ubuntu1.2 Ubuntu:14.04/trusty-updates [amd64])
Conf upstart (1.12.1-0ubuntu4.2 Ubuntu:14.04/trusty-updates [amd64])
Conf dbus (1.6.18-0ubuntu4.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libffi6 (3.1~rc1+r3.0.13-12ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libglib2.0-0 (2.40.2-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf libpolkit-gobject-1-0 (0.105-4ubuntu3.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libaccountsservice0 (0.6.35-0ubuntu7.2 Ubuntu:14.04/trusty-updates [amd64])
Conf accountsservice (0.6.35-0ubuntu7.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libc6-i386 (2.19-0ubuntu6.9 Ubuntu:14.04/trusty-updates [amd64])
Conf lib32gcc1 (1:4.9.3-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64])
Conf fontconfig-config (2.11.0-0ubuntu4.1 Ubuntu:14.04/trusty-updates [all])
Conf libpng12-0 (1.2.50-1ubuntu2.14.04.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libfreetype6 (2.5.2-1ubuntu2.5 Ubuntu:14.04/trusty-updates [amd64])
Conf libfontconfig1 (2.11.0-0ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Conf liblcms2-2 (2.5-0ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libtsan0 (4.8.4-2ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libgomp1 (4.8.4-2ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libitm1 (4.8.4-2ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libatomic1 (4.8.4-2ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libasan0 (4.8.4-2ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libquadmath0 (4.8.4-2ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64])
Conf cpp-4.8 (4.8.4-2ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64])
Conf binutils (2.24-5ubuntu14.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgcc-4.8-dev (4.8.4-2ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64])
Conf gcc-4.8 (4.8.4-2ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libc-dev-bin (2.19-0ubuntu6.9 Ubuntu:14.04/trusty-updates [amd64])
Conf linux-libc-dev (3.13.0-91.138 Ubuntu:14.04/trusty-updates [amd64])
Conf libc6-dev (2.19-0ubuntu6.9 Ubuntu:14.04/trusty-updates [amd64])
Conf libstdc++-4.8-dev (4.8.4-2ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64])
Conf g++-4.8 (4.8.4-2ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libtiff5 (4.0.3-7ubuntu0.4 Ubuntu:14.04/trusty-updates [amd64])
Conf libpoppler44 (0.24.5-2ubuntu4.4 Ubuntu:14.04/trusty-updates [amd64])
Conf fontconfig (2.11.0-0ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Conf fonts-opensymbol (2:102.6+LibO4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [all])
Conf libreoffice-style-human (1:4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [all])
Conf uno-libs3 (4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64])
Conf libxml2 (2.9.1+dfsg1-3ubuntu4.8 Ubuntu:14.04/trusty-updates [amd64])
Conf ure (4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64])
Conf libreoffice-common (1:4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [all])
Conf libboost-date-time1.54.0 (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libpixman-1-0 (0.30.2-2ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libxext6 (2:1.3.2-1ubuntu0.0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libxrender1 (1:0.9.8-1build0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libcairo2 (1.13.0~20140204-0ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgcrypt11 (1.5.3-2ubuntu4.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libtasn1-6 (3.4-3ubuntu0.4 Ubuntu:14.04/trusty-updates [amd64])
Conf libgnutls26 (2.12.23-12ubuntu2.5 Ubuntu:14.04/trusty-updates [amd64])
Conf libkrb5support0 (1.12+dfsg-2ubuntu5.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libk5crypto3 (1.12+dfsg-2ubuntu5.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libkrb5-3 (1.12+dfsg-2ubuntu5.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libgssapi-krb5-2 (1.12+dfsg-2ubuntu5.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libcups2 (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [amd64])
Conf libroken18-heimdal (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libasn1-8-heimdal (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libhcrypto4-heimdal (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libheimbase1-heimdal (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libwind0-heimdal (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libhx509-5-heimdal (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libsqlite3-0 (3.8.2-1ubuntu2.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libkrb5-26-heimdal (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libheimntlm0-heimdal (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgssapi3-heimdal (1.6~git20131207+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libldap-2.4-2 (2.4.31-1+nmu2ubuntu8.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libcurl3-gnutls (7.35.0-1ubuntu2.6 Ubuntu:14.04/trusty-updates [amd64])
Conf libjasper1 (1.900.1-14ubuntu3.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libgdk-pixbuf2.0-common (2.30.7-0ubuntu1.2 Ubuntu:14.04/trusty-updates [all])
Conf libgdk-pixbuf2.0-0 (2.30.7-0ubuntu1.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libdrm2 (2.4.64-1~ubuntu14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libglapi-mesa (10.1.3-0ubuntu0.6 Ubuntu:14.04/trusty-updates [amd64])
Conf libxfixes3 (1:5.0.1-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgl1-mesa-glx (10.1.3-0ubuntu0.6 Ubuntu:14.04/trusty-updates [amd64])
Conf libgraphite2-3 (1.3.6-1ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgtk2.0-common (2.24.23-0ubuntu1.4 Ubuntu:14.04/trusty-updates [all])
Conf libpango-1.0-0 (1.36.3-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libharfbuzz0b (0.9.27-1ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf libpangoft2-1.0-0 (1.36.3-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libpangocairo-1.0-0 (1.36.3-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libxi6 (2:1.7.1.901-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgtk2.0-0 (2.24.23-0ubuntu1.4 Ubuntu:14.04/trusty-updates [amd64])
Conf libicu52 (52.1-3ubuntu0.4 Ubuntu:14.04/trusty-updates [amd64])
Conf libharfbuzz-icu0 (0.9.27-1ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf libhunspell-1.3-0 (1.3.2-6ubuntu2.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libnspr4 (2:4.10.10-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libnss3 (2:3.21-0ubuntu0.14.04.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libnss3-nssdb (2:3.21-0ubuntu0.14.04.2 Ubuntu:14.04/trusty-updates [all])
Conf libnss3-1d (2:3.21-0ubuntu0.14.04.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libreoffice-core (1:4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64])
Conf libreoffice-base-core (1:4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64])
Conf libreoffice-calc (1:4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64])
Conf libreoffice-gtk (1:4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64])
Conf libreoffice-gnome (1:4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64])
Conf libreoffice-writer (1:4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64])
Conf libreoffice-draw (1:4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64])
Conf libreoffice-impress (1:4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64])
Conf libreoffice-ogltrans (1:4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64])
Conf libssl1.0.0 (1.0.1f-1ubuntu2.19 Ubuntu:14.04/trusty-updates [amd64])
Conf libpython3.4-minimal (3.4.3-1ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64])
Conf mime-support (3.54ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Conf libpython3.4-stdlib (3.4.3-1ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libpython3.4 (3.4.3-1ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64])
Conf python3-uno (1:4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64])
Conf libreoffice-pdfimport (1:4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64])
Conf libreoffice-math (1:4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64])
Conf libgles2-mesa (10.1.3-0ubuntu0.6 Ubuntu:14.04/trusty-updates [amd64])
Conf libdrm-nouveau2 (2.4.64-1~ubuntu14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libdrm-radeon1 (2.4.64-1~ubuntu14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libdrm-intel1 (2.4.64-1~ubuntu14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libelf1 (0.158-0ubuntu5.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libgl1-mesa-dri (10.1.3-0ubuntu0.6 Ubuntu:14.04/trusty-updates [amd64])
Conf libgbm1 (10.1.3-0ubuntu0.6 Ubuntu:14.04/trusty-updates [amd64])
Conf libegl1-mesa (10.1.3-0ubuntu0.6 Ubuntu:14.04/trusty-updates [amd64])
Conf libopenvg1-mesa (10.1.3-0ubuntu0.6 Ubuntu:14.04/trusty-updates [amd64])
Conf libwayland-egl1-mesa (10.1.3-0ubuntu0.6 Ubuntu:14.04/trusty-updates [amd64])
Conf libegl1-mesa-drivers (10.1.3-0ubuntu0.6 Ubuntu:14.04/trusty-updates [amd64])
Conf dbus-x11 (1.6.18-0ubuntu4.3 Ubuntu:14.04/trusty-updates [amd64])
Conf x11-common (1:7.7+1ubuntu8.1 Ubuntu:14.04/trusty-updates [all])
Conf xserver-common (2:1.15.1-0ubuntu2.7 Ubuntu:14.04/trusty-updates [all])
Conf libprocps3 (1:3.3.9-1ubuntu2.2 Ubuntu:14.04/trusty-updates [amd64])
Conf procps (1:3.3.9-1ubuntu2.2 Ubuntu:14.04/trusty-updates [amd64])
Conf udev (204-5ubuntu20.19 Ubuntu:14.04/trusty-updates [amd64])
Conf libxfont1 (1:1.4.7-1ubuntu0.2 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-core (2:1.15.1-0ubuntu2.7 Ubuntu:14.04/trusty-updates [amd64])
Conf libgtk2.0-bin (2.24.23-0ubuntu1.4 Ubuntu:14.04/trusty-updates [amd64])
Conf libpangoxft-1.0-0 (1.36.3-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libpango1.0-0 (1.36.3-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgail18 (2.24.23-0ubuntu1.4 Ubuntu:14.04/trusty-updates [amd64])
Conf libgail-common (2.24.23-0ubuntu1.4 Ubuntu:14.04/trusty-updates [amd64])
Conf libcupsppdc1 (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [amd64])
Conf libcupsmime1 (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [amd64])
Conf libcupsfilters1 (1.0.52-0ubuntu1.7 Ubuntu:14.04/trusty-updates [amd64])
Conf libcupsimage2 (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [amd64])
Conf libcupscgi1 (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [amd64])
Conf cups-browsed (1.0.52-0ubuntu1.7 Ubuntu:14.04/trusty-updates [amd64])
Conf libgnutls-openssl27 (2.12.23-12ubuntu2.5 Ubuntu:14.04/trusty-updates [amd64])
Conf cups-daemon (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [amd64])
Conf poppler-utils (0.24.5-2ubuntu4.4 Ubuntu:14.04/trusty-updates [amd64])
Conf cups-filters-core-drivers (1.0.52-0ubuntu1.7 Ubuntu:14.04/trusty-updates [amd64])
Conf cups-core-drivers (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [amd64])
Conf cups-server-common (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [all])
Conf perl (5.18.2-2ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf perl-modules (5.18.2-2ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Conf libperl5.18 (5.18.2-2ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libsnmp-base (5.7.2~dfsg-8.1ubuntu3.2 Ubuntu:14.04/trusty-updates [all])
Conf libsnmp30 (5.7.2~dfsg-8.1ubuntu3.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libhpmud0 (3.14.3-0ubuntu3.4 Ubuntu:14.04/trusty-updates [amd64])
Conf libsane-common (1.0.23-3ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgd3 (2.1.0-3ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgphoto2-port10 (2.5.3.1-1ubuntu2.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libgphoto2-6 (2.5.3.1-1ubuntu2.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libsane (1.0.23-3ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libsane-hpaio (3.14.3-0ubuntu3.4 Ubuntu:14.04/trusty-updates [amd64])
Conf hplip-data (3.14.3-0ubuntu3.4 Ubuntu:14.04/trusty-updates [all])
Conf libfontembed1 (1.0.52-0ubuntu1.7 Ubuntu:14.04/trusty-updates [amd64])
Conf libgs9-common (9.10~dfsg-0ubuntu10.4 Ubuntu:14.04/trusty-updates [all])
Conf libgs9 (9.10~dfsg-0ubuntu10.4 Ubuntu:14.04/trusty-updates [amd64])
Conf ghostscript (9.10~dfsg-0ubuntu10.4 Ubuntu:14.04/trusty-updates [amd64])
Conf cups-filters (1.0.52-0ubuntu1.7 Ubuntu:14.04/trusty-updates [amd64])
Conf cups-common (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [all])
Conf cups-client (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [amd64])
Conf cups-ppdc (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [amd64])
Conf cups (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [amd64])
Conf printer-driver-hpcups (3.14.3-0ubuntu3.4 Ubuntu:14.04/trusty-updates [amd64])
Conf python-pexpect (3.1-1ubuntu0.1 Ubuntu:14.04/trusty-updates [all])
Conf libpolkit-agent-1-0 (0.105-4ubuntu3.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libpolkit-backend-1-0 (0.105-4ubuntu3.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libsystemd-daemon0 (204-5ubuntu20.19 Ubuntu:14.04/trusty-updates [amd64])
Conf systemd-services (204-5ubuntu20.19 Ubuntu:14.04/trusty-updates [amd64])
Conf libpam-systemd (204-5ubuntu20.19 Ubuntu:14.04/trusty-updates [amd64])
Conf policykit-1 (0.105-4ubuntu3.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf wget (1.15-1ubuntu1.14.04.2 Ubuntu:14.04/trusty-updates [amd64])
Conf hplip (3.14.3-0ubuntu3.4 Ubuntu:14.04/trusty-updates [amd64])
Conf printer-driver-postscript-hp (3.14.3-0ubuntu3.4 Ubuntu:14.04/trusty-updates [all])
Conf ghostscript-x (9.10~dfsg-0ubuntu10.4 Ubuntu:14.04/trusty-updates [amd64])
Conf cups-bsd (1.7.2-0ubuntu1.7 Ubuntu:14.04/trusty-updates [amd64])
Conf python3-six (1.5.2-1ubuntu1 Ubuntu:14.04/trusty-updates [all])
Conf python3-urllib3 (1.7.1-1ubuntu4 Ubuntu:14.04/trusty-updates [all])
Conf python3.4-minimal (3.4.3-1ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64])
Conf python3.4 (3.4.3-1ubuntu1~14.04.3 Ubuntu:14.04/trusty-updates [amd64])
Conf sqlite3 (3.8.2-1ubuntu2.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgtk-3-common (3.10.8-0ubuntu1.6 Ubuntu:14.04/trusty-updates [all])
Conf libcairo-gobject2 (1.13.0~20140204-0ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgtk-3-0 (3.10.8-0ubuntu1.6 Ubuntu:14.04/trusty-updates [amd64])
Conf libgail-3-0 (3.10.8-0ubuntu1.6 Ubuntu:14.04/trusty-updates [amd64])
Conf libgnome-bluetooth11 (3.8.2.1-0ubuntu4.2 Ubuntu:14.04/trusty-updates [amd64])
Conf gnome-desktop3-data (3.8.4-0ubuntu3.2 Ubuntu:14.04/trusty-updates [all])
Conf libgnome-desktop-3-7 (3.8.4-0ubuntu3.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libibus-1.0-5 (1.5.5-1ubuntu3.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libgudev-1.0-0 (1:204-5ubuntu20.19 Ubuntu:14.04/trusty-updates [amd64])
Conf libnm-util2 (0.9.8.8-0ubuntu7.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libnm-glib4 (0.9.8.8-0ubuntu7.3 Ubuntu:14.04/trusty-updates [amd64])
Conf ppp (2.4.5-5.1ubuntu2.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libmbim-glib0 (1.6.0-2ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libmm-glib0 (1.0.0-2ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf modemmanager (1.0.0-2ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libnl-3-200 (3.2.21-1ubuntu3 Ubuntu:14.04/trusty-updates [amd64])
Conf libnl-genl-3-200 (3.2.21-1ubuntu3 Ubuntu:14.04/trusty-updates [amd64])
Conf libnl-route-3-200 (3.2.21-1ubuntu3 Ubuntu:14.04/trusty-updates [amd64])
Conf glib-networking-common (2.40.0-1ubuntu0.1 Ubuntu:14.04/trusty-updates [all])
Conf glib-networking-services (2.40.0-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Conf glib-networking (2.40.0-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libsoup2.4-1 (2.44.2-1ubuntu2.1 Ubuntu:14.04/trusty-updates [amd64])
Conf wpasupplicant (2.1-0ubuntu1.4 Ubuntu:14.04/trusty-updates [amd64])
Conf isc-dhcp-common (4.2.4-7ubuntu12.4 Ubuntu:14.04/trusty-updates [amd64])
Conf isc-dhcp-client (4.2.4-7ubuntu12.4 Ubuntu:14.04/trusty-updates [amd64])
Conf dnsmasq-base (2.68-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Conf iputils-arping (3:20121221-4ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf network-manager (0.9.8.8-0ubuntu7.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libnautilus-extension1a (1:3.10.1-0ubuntu9.11 Ubuntu:14.04/trusty-updates [amd64])
Conf libdbusmenu-glib4 (12.10.3+14.04.20140612-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf nautilus-data (1:3.10.1-0ubuntu9.11 Ubuntu:14.04/trusty-updates [all])
Conf libudisks2-0 (2.1.3-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libparted0debian1 (2.3-19ubuntu1.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf parted (2.3-19ubuntu1.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf udisks2 (2.1.3-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Conf gvfs-common (1.20.3-0ubuntu1.2 Ubuntu:14.04/trusty-updates [all])
Conf gvfs-libs (1.20.3-0ubuntu1.2 Ubuntu:14.04/trusty-updates [amd64])
Conf gvfs-daemons (1.20.3-0ubuntu1.2 Ubuntu:14.04/trusty-updates [amd64])
Conf gvfs (1.20.3-0ubuntu1.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libglib2.0-data (2.40.2-0ubuntu1 Ubuntu:14.04/trusty-updates [all])
Conf nautilus (1:3.10.1-0ubuntu9.11 Ubuntu:14.04/trusty-updates [amd64])
Conf libnm-gtk-common (0.9.8.8-0ubuntu4.4 Ubuntu:14.04/trusty-updates [all])
Conf libnm-gtk0 (0.9.8.8-0ubuntu4.4 Ubuntu:14.04/trusty-updates [amd64])
Conf libflac8 (1.3.0-2ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libsndfile1 (1.0.25-7ubuntu2.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libpulse0 (1:4.0-0ubuntu11.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libpulse-mainloop-glib0 (1:4.0-0ubuntu11.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libpwquality-common (1.2.3-1ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Conf libpwquality1 (1.2.3-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libunity-control-center1 (14.04.3+14.04.20150916-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf libjavascriptcoregtk-3.0-0 (2.4.10-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgstreamer1.0-0 (1.2.4-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgstreamer-plugins-base1.0-0 (1.2.4-1~ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Conf libwebkitgtk-3.0-common (2.4.10-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [all])
Conf libwebkitgtk-3.0-0 (2.4.10-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf gnome-settings-daemon-schemas (3.8.6.1-0ubuntu11.2 Ubuntu:14.04/trusty-updates [all])
Conf unity-settings-daemon (14.04.0+14.04.20151012-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgirepository-1.0-1 (1.40.0-1ubuntu0.2 Ubuntu:14.04/trusty-updates [amd64])
Conf gir1.2-glib-2.0 (1.40.0-1ubuntu0.2 Ubuntu:14.04/trusty-updates [amd64])
Conf gir1.2-freedesktop (1.40.0-1ubuntu0.2 Ubuntu:14.04/trusty-updates [amd64])
Conf gir1.2-gdkpixbuf-2.0 (2.30.7-0ubuntu1.2 Ubuntu:14.04/trusty-updates [amd64])
Conf gir1.2-pango-1.0 (1.36.3-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf gir1.2-gtk-3.0 (3.10.8-0ubuntu1.6 Ubuntu:14.04/trusty-updates [amd64])
Conf gir1.2-ibus-1.0 (1.5.5-1ubuntu3.2 Ubuntu:14.04/trusty-updates [amd64])
Conf python-gi (3.12.0-1ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf ibus (1.5.5-1ubuntu3.2 Ubuntu:14.04/trusty-updates [amd64])
Conf unity-control-center (14.04.3+14.04.20150916-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf gir1.2-gnomebluetooth-1.0 (3.8.2.1-0ubuntu4.2 Ubuntu:14.04/trusty-updates [amd64])
Conf bluez (4.101-0ubuntu13.1 Ubuntu:14.04/trusty-updates [amd64])
Conf gnome-bluetooth (3.8.2.1-0ubuntu4.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libdbusmenu-gtk3-4 (12.10.3+14.04.20140612-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf libindicator3-7 (12.10.2+14.04.20141007.1-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf libappindicator3-1 (12.10.1+13.10.20130920-0ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libnm-glib-vpn1 (0.9.8.8-0ubuntu7.3 Ubuntu:14.04/trusty-updates [amd64])
Conf network-manager-gnome (0.9.8.8-0ubuntu4.4 Ubuntu:14.04/trusty-updates [amd64])
Conf libglib2.0-bin (2.40.2-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf liblzo2-2 (2.06-1.2ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libnettle4 (2.7.1-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libarchive13 (3.1.2-7ubuntu2.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libbluetooth3 (4.101-0ubuntu13.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libimobiledevice4 (1.1.5+git20140313.bafe6a9e-0ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libmtp-common (1.1.6-20-g1b9f164-1ubuntu2.1 Ubuntu:14.04/trusty-updates [all])
Conf libmtp9 (1.1.6-20-g1b9f164-1ubuntu2.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libtalloc2 (2.1.5-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libtevent0 (0.9.28-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libtdb1 (1.3.8-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libldb1 (1:1.1.24-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libpython2.7-minimal (2.7.6-8ubuntu0.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libpython2.7-stdlib (2.7.6-8ubuntu0.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libpython2.7 (2.7.6-8ubuntu0.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libwbclient0 (2:4.3.9+dfsg-0ubuntu0.14.04.3 Ubuntu:14.04/trusty-updates [amd64])
Conf python-talloc (2.1.5-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf samba-libs (2:4.3.9+dfsg-0ubuntu0.14.04.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libsmbclient (2:4.3.9+dfsg-0ubuntu0.14.04.3 Ubuntu:14.04/trusty-updates [amd64])
Conf gvfs-backends (1.20.3-0ubuntu1.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libfuse2 (2.9.2-4ubuntu4.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf fuse (2.9.2-4ubuntu4.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf gvfs-fuse (1.20.3-0ubuntu1.2 Ubuntu:14.04/trusty-updates [amd64])
Conf gvfs-bin (1.20.3-0ubuntu1.2 Ubuntu:14.04/trusty-updates [amd64])
Conf resolvconf (1.69ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Conf ntpdate (1:4.2.6.p5+dfsg-3ubuntu2.14.04.8 Ubuntu:14.04/trusty-updates [amd64])
Conf gir1.2-dbusmenu-glib-0.4 (12.10.3+14.04.20140612-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf libmtp-runtime (1.1.6-20-g1b9f164-1ubuntu2.1 Ubuntu:14.04/trusty-updates [amd64])
Conf python2.7-minimal (2.7.6-8ubuntu0.2 Ubuntu:14.04/trusty-updates [amd64])
Conf python2.7 (2.7.6-8ubuntu0.2 Ubuntu:14.04/trusty-updates [amd64])
Conf python-ldb (1:1.1.24-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf python-tdb (1.3.8-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf samba-common (2:4.3.9+dfsg-0ubuntu0.14.04.3 Ubuntu:14.04/trusty-updates [all])
Conf smbclient (2:4.3.9+dfsg-0ubuntu0.14.04.3 Ubuntu:14.04/trusty-updates [amd64])
Conf python-samba (2:4.3.9+dfsg-0ubuntu0.14.04.3 Ubuntu:14.04/trusty-updates [amd64])
Conf samba-common-bin (2:4.3.9+dfsg-0ubuntu0.14.04.3 Ubuntu:14.04/trusty-updates [amd64])
Conf pulseaudio (1:4.0-0ubuntu11.1 Ubuntu:14.04/trusty-updates [amd64])
Conf python-gi-cairo (3.12.0-1ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf tzdata-java (2016f-0ubuntu0.14.04 Ubuntu:14.04/trusty-updates [all])
Conf libc6-dbg (2.19-0ubuntu6.9 Ubuntu:14.04/trusty-updates [amd64])
Conf libapt-inst1.5 (1.0.1ubuntu2.14 Ubuntu:14.04/trusty-updates [amd64])
Conf libmagic1 (1:5.14-2ubuntu3.3 Ubuntu:14.04/trusty-updates [amd64])
Conf file (1:5.14-2ubuntu3.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libklibc (2.0.3-0ubuntu1.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf klibc-utils (2.0.3-0ubuntu1.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf initramfs-tools-bin (0.103ubuntu4.3 Ubuntu:14.04/trusty-updates [amd64])
Conf cpio (2.11+dfsg-1ubuntu1.2 Ubuntu:14.04/trusty-updates [amd64])
Conf initramfs-tools (0.103ubuntu4.3 Ubuntu:14.04/trusty-updates [all])
Conf libplymouth2 (0.8.8-0ubuntu17.1 Ubuntu:14.04/trusty-updates [amd64])
Conf plymouth (0.8.8-0ubuntu17.1 Ubuntu:14.04/trusty-updates [amd64])
Conf plymouth-label (0.8.8-0ubuntu17.1 Ubuntu:14.04/trusty-updates [amd64])
Conf bash-completion (1:2.1-4ubuntu0.2 Ubuntu:14.04/trusty-updates [all])
Conf python3-gi (3.12.0-1ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf python3-gi-cairo (3.12.0-1ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf libvte-2.90-common (1:0.34.9-1ubuntu2 Ubuntu:14.04/trusty-updates [all])
Conf libvte-2.90-9 (1:0.34.9-1ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Conf gir1.2-vte-2.90 (1:0.34.9-1ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Conf python-apt-common (0.9.3.5ubuntu2 Ubuntu:14.04/trusty-updates [all])
Conf python3-apt (0.9.3.5ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Conf python-apt (0.9.3.5ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Conf python3-pkg-resources (3.3-1ubuntu2 Ubuntu:14.04/trusty-updates [all])
Conf python3-aptdaemon (1.1.1-1ubuntu5.2 Ubuntu:14.04/trusty-updates [all])
Conf python3-aptdaemon.pkcompat (1.1.1-1ubuntu5.2 Ubuntu:14.04/trusty-updates [all])
Conf aptdaemon-data (1.1.1-1ubuntu5.2 Ubuntu:14.04/trusty-updates [all])
Conf python3-aptdaemon.gtk3widgets (1.1.1-1ubuntu5.2 Ubuntu:14.04/trusty-updates [all])
Conf aptdaemon (1.1.1-1ubuntu5.2 Ubuntu:14.04/trusty-updates [all])
Conf im-config (0.24-1ubuntu4.2 Ubuntu:14.04/trusty-updates [all])
Conf language-selector-common (0.129.3 Ubuntu:14.04/trusty-updates [all])
Conf language-selector-gnome (0.129.3 Ubuntu:14.04/trusty-updates [all])
Conf libnuma1 (2.0.9~rc5-1ubuntu3.14.04.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libpci3 (1:3.2.1-1ubuntu5.1 Ubuntu:14.04/trusty-updates [amd64])
Conf pciutils (1:3.2.1-1ubuntu5.1 Ubuntu:14.04/trusty-updates [amd64])
Conf man-db (2.6.7.1-1ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf fonts-droid (1:4.3-3ubuntu1.2 Ubuntu:14.04/trusty-updates [all])
Conf libp11-kit-gnome-keyring (3.10.1-1ubuntu4.2 Ubuntu:14.04/trusty-updates [amd64])
Conf gnome-keyring (3.10.1-1ubuntu4.2 Ubuntu:14.04/trusty-updates [amd64])
Conf openssl (1.0.1f-1ubuntu2.19 Ubuntu:14.04/trusty-updates [amd64])
Conf ca-certificates (20160104ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [all])
Conf libcurl3 (7.35.0-1ubuntu2.6 Ubuntu:14.04/trusty-updates [amd64])
Conf xdg-utils (1.1.0~rc1-2ubuntu7.1 Ubuntu:14.04/trusty-updates [all])
Conf google-chrome-stable (51.0.2704.106-1 Google:1.0/stable [amd64])
Conf locales (2.13+git20120306-12.1 Ubuntu:14.04/trusty-updates [all])
Conf language-pack-en (1:14.04+20150219 Ubuntu:14.04/trusty-updates [all])
Conf language-pack-en-base (1:14.04+20150219 Ubuntu:14.04/trusty-updates [all])
Conf language-pack-gnome-en (1:14.04+20150219 Ubuntu:14.04/trusty-updates [all])
Conf language-pack-gnome-en-base (1:14.04+20150219 Ubuntu:14.04/trusty-updates [all])
Conf libboost-iostreams1.54.0 (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libboost-system1.54.0 (1.54.0-4ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libclick-0.4-0 (0.4.21.1ubuntu0.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libclutter-gtk-1.0-0 (1.4.4-3ubuntu2.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libdbusmenu-gtk4 (12.10.3+14.04.20140612-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf libdebian-installer4 (0.88ubuntu5.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libevent-2.0-5 (2.0.21-stable-1ubuntu1.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgpgme11 (1.4.3-0.1ubuntu5.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libhud2 (14.04+14.04.20140604-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf libido3-0.1-0 (13.10.0+14.04.20151021-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf libmms0 (0.6.2-3ubuntu2.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libnux-4.0-common (4.0.6+14.04.20141107-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf libnux-4.0-0 (4.0.6+14.04.20141107-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf libpam-gnome-keyring (3.10.1-1ubuntu4.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libpoppler-glib8 (0.24.5-2ubuntu4.4 Ubuntu:14.04/trusty-updates [amd64])
Conf libpulsedsp (1:4.0-0ubuntu11.1 Ubuntu:14.04/trusty-updates [amd64])
Conf qtcore4-l10n (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [all])
Conf libqtcore4 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libqt4-xml (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libqtdbus4 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libqt4-script (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libqt4-network (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libqt4-sql (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libqt4-xmlpatterns (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libqtgui4 (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libqt4-declarative (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libqt4-scripttools (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libqt4-designer (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libqt4-svg (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libqt4-opengl (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libqt4-help (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Conf qdbus (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libqt4-dbus (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libqt4-sql-sqlite (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libqt4-test (4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libqt5core5a (5.2.1+dfsg-1ubuntu14.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libqt5dbus5 (5.2.1+dfsg-1ubuntu14.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libxcb-keysyms1 (0.3.9-1ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libxkbcommon-x11-0 (0.4.1-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf libqt5gui5 (5.2.1+dfsg-1ubuntu14.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libqt5network5 (5.2.1+dfsg-1ubuntu14.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libqt5widgets5 (5.2.1+dfsg-1ubuntu14.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libqt5opengl5 (5.2.1+dfsg-1ubuntu14.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libqt5printsupport5 (5.2.1+dfsg-1ubuntu14.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libqt5qml5 (5.2.1-3ubuntu15.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libqt5quick5 (5.2.1-3ubuntu15.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libqt5sql5 (5.2.1+dfsg-1ubuntu14.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libqt5sql5-sqlite (5.2.1+dfsg-1ubuntu14.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libqt5test5 (5.2.1+dfsg-1ubuntu14.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libqt5xml5 (5.2.1+dfsg-1ubuntu14.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libsoup-gnome2.4-1 (2.44.2-1ubuntu2.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libspectre1 (0.2.7-2ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libspice-server1 (0.12.4-0nocelt2ubuntu1.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libssh-4 (0.6.1-0ubuntu3.3 Ubuntu:14.04/trusty-updates [amd64])
Conf libthumbnailer0 (1.1+14.04.20150205-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf libunity-gtk2-parser0 (0.0.0+14.04.20141212-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf libunity-gtk3-parser0 (0.0.0+14.04.20141212-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf libupstart1 (1.12.1-0ubuntu4.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libvncserver0 (0.9.9+dfsg-1ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libwmf0.2-7 (0.2.8.4-10.3ubuntu1.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libwmf0.2-7-gtk (0.2.8.4-10.3ubuntu1.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libwnck-3-common (3.4.7-0ubuntu3.1 Ubuntu:14.04/trusty-updates [all])
Conf libwnck-3-0 (3.4.7-0ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libxatracker2 (10.1.3-0ubuntu0.6 Ubuntu:14.04/trusty-updates [amd64])
Conf libapparmor-perl (2.8.95~2430-0ubuntu5.3 Ubuntu:14.04/trusty-updates [amd64])
Conf apparmor (2.8.95~2430-0ubuntu5.3 Ubuntu:14.04/trusty-updates [amd64])
Conf lightdm (1.10.6-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf linux-image-3.13.0-91-generic (3.13.0-91.138 Ubuntu:14.04/trusty-updates [amd64])
Conf qtdeclarative5-privatewidgets-plugin (5.2.1-3ubuntu15.1 Ubuntu:14.04/trusty-updates [amd64])
Conf qtdeclarative5-dialogs-plugin (5.2.1-3ubuntu15.1 Ubuntu:14.04/trusty-updates [amd64])
Conf qtdeclarative5-localstorage-plugin (5.2.1-3ubuntu15.1 Ubuntu:14.04/trusty-updates [amd64])
Conf qtdeclarative5-qtquick2-plugin (5.2.1-3ubuntu15.1 Ubuntu:14.04/trusty-updates [amd64])
Conf qtdeclarative5-window-plugin (5.2.1-3ubuntu15.1 Ubuntu:14.04/trusty-updates [amd64])
Conf usbutils (1:007-2ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf ubuntu-drivers-common (1:0.2.91.11 Ubuntu:14.04/trusty-updates [amd64])
Conf unity-gtk-module-common (0.0.0+14.04.20141212-0ubuntu1 Ubuntu:14.04/trusty-updates [all])
Conf unity-gtk2-module (0.0.0+14.04.20141212-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf unity-gtk3-module (0.0.0+14.04.20141212-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf lsb-release (4.1+Debian11ubuntu6.1 Ubuntu:14.04/trusty-updates [all])
Conf python3-distupgrade (1:0.220.8 Ubuntu:14.04/trusty-updates [all])
Conf python3-update-manager (1:0.196.14 Ubuntu:14.04/trusty-updates [all])
Conf ubuntu-release-upgrader-core (1:0.220.8 Ubuntu:14.04/trusty-updates [all])
Conf update-manager-core (1:0.196.14 Ubuntu:14.04/trusty-updates [all])
Conf patch (2.7.1-4ubuntu2.3 Ubuntu:14.04/trusty-updates [amd64])
Conf update-notifier-common (0.154.1ubuntu1 Ubuntu:14.04/trusty-updates [all])
Conf gir1.2-javascriptcoregtk-3.0 (2.4.10-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf gir1.2-soup-2.4 (2.44.2-1ubuntu2.1 Ubuntu:14.04/trusty-updates [amd64])
Conf gir1.2-webkit-3.0 (2.4.10-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf ubuntu-release-upgrader-gtk (1:0.220.8 Ubuntu:14.04/trusty-updates [all])
Conf update-manager (1:0.196.14 Ubuntu:14.04/trusty-updates [all])
Conf update-notifier (0.154.1ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf gstreamer1.0-plugins-base (1.2.4-1~ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Conf libgstreamer-plugins-good1.0-0 (1.2.4-1~ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf gstreamer1.0-plugins-good (1.2.4-1~ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf libsystemd-journal0 (204-5ubuntu20.19 Ubuntu:14.04/trusty-updates [amd64])
Conf openjdk-6-jre-lib (6b39-1.13.11-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [all])
Conf openjdk-6-jre-headless (6b39-1.13.11-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf icedtea-6-jre-jamvm (6b39-1.13.11-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf icedtea-6-jre-cacao (6b39-1.13.11-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf apt-utils (1.0.1ubuntu2.14 Ubuntu:14.04/trusty-updates [amd64])
Conf dh-python (1.20140128-1ubuntu8.2 Ubuntu:14.04/trusty-updates [all])
Conf iputils-ping (3:20121221-4ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf net-tools (1.60-25ubuntu2.1 Ubuntu:14.04/trusty-updates [amd64])
Conf rsyslog (7.4.4-1ubuntu2.6 Ubuntu:14.04/trusty-updates [amd64])
Conf sudo (1.8.9p5-1ubuntu1.2 Ubuntu:14.04/trusty-updates [amd64])
Conf apt-transport-https (1.0.1ubuntu2.14 Ubuntu:14.04/trusty-updates [amd64])
Conf libisc95 (1:9.9.5.dfsg-3ubuntu0.8 Ubuntu:14.04/trusty-updates [amd64])
Conf libdns100 (1:9.9.5.dfsg-3ubuntu0.8 Ubuntu:14.04/trusty-updates [amd64])
Conf libisccc90 (1:9.9.5.dfsg-3ubuntu0.8 Ubuntu:14.04/trusty-updates [amd64])
Conf libisccfg90 (1:9.9.5.dfsg-3ubuntu0.8 Ubuntu:14.04/trusty-updates [amd64])
Conf libbind9-90 (1:9.9.5.dfsg-3ubuntu0.8 Ubuntu:14.04/trusty-updates [amd64])
Conf liblwres90 (1:9.9.5.dfsg-3ubuntu0.8 Ubuntu:14.04/trusty-updates [amd64])
Conf bind9-host (1:9.9.5.dfsg-3ubuntu0.8 Ubuntu:14.04/trusty-updates [amd64])
Conf dnsutils (1:9.9.5.dfsg-3ubuntu0.8 Ubuntu:14.04/trusty-updates [amd64])
Conf dosfstools (3.0.26-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Conf iputils-tracepath (3:20121221-4ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf irqbalance (1.0.6-2ubuntu0.14.04.4 Ubuntu:14.04/trusty-updates [amd64])
Conf krb5-locales (1.12+dfsg-2ubuntu5.2 Ubuntu:14.04/trusty-updates [all])
Conf lshw (02.16-2ubuntu1.3 Ubuntu:14.04/trusty-updates [amd64])
Conf ltrace (0.7.3-4ubuntu5.1 Ubuntu:14.04/trusty-updates [amd64])
Conf openssh-client (1:6.6p1-2ubuntu2.7 Ubuntu:14.04/trusty-updates [amd64])
Conf plymouth-theme-ubuntu-text (0.8.8-0ubuntu17.1 Ubuntu:14.04/trusty-updates [amd64])
Conf python3-gdbm (3.4.3-1~14.04.2 Ubuntu:14.04/trusty-updates [amd64])
Conf rsync (3.1.0-2ubuntu0.2 Ubuntu:14.04/trusty-updates [amd64])
Conf tcpdump (4.5.1-2ubuntu1.2 Ubuntu:14.04/trusty-updates [amd64])
Conf uuid-runtime (2.20.1-5.1ubuntu20.7 Ubuntu:14.04/trusty-updates [amd64])
Conf empathy-common (3.8.6-0ubuntu9.2 Ubuntu:14.04/trusty-updates [all])
Conf gstreamer1.0-pulseaudio (1.2.4-1~ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf empathy (3.8.6-0ubuntu9.2 Ubuntu:14.04/trusty-updates [amd64])
Conf nautilus-sendto-empathy (3.8.6-0ubuntu9.2 Ubuntu:14.04/trusty-updates [amd64])
Conf mcp-account-manager-uoa (3.8.6-0ubuntu9.2 Ubuntu:14.04/trusty-updates [amd64])
Conf account-plugin-yahoo (3.8.6-0ubuntu9.2 Ubuntu:14.04/trusty-updates [amd64])
Conf account-plugin-salut (3.8.6-0ubuntu9.2 Ubuntu:14.04/trusty-updates [amd64])
Conf telepathy-gabble (0.18.3-0ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Conf account-plugin-jabber (3.8.6-0ubuntu9.2 Ubuntu:14.04/trusty-updates [amd64])
Conf account-plugin-aim (3.8.6-0ubuntu9.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libaccount-plugin-generic-oauth (0.11+14.04.20140409.1-0ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Conf account-plugin-facebook (0.11+14.04.20140409.1-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Conf account-plugin-flickr (0.11+14.04.20140409.1-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Conf libaccount-plugin-google (0.11+14.04.20140409.1-0ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Conf account-plugin-google (0.11+14.04.20140409.1-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Conf account-plugin-twitter (0.11+14.04.20140409.1-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Conf account-plugin-windows-live (0.11+14.04.20140409.1-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Conf libzeitgeist-2.0-0 (0.9.14-0ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Conf python-zeitgeist (0.9.14-0ubuntu4.1 Ubuntu:14.04/trusty-updates [all])
Conf zeitgeist-core (0.9.14-0ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Conf zeitgeist-datahub (0.9.14-0ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Conf zeitgeist (0.9.14-0ubuntu4.1 Ubuntu:14.04/trusty-updates [all])
Conf activity-log-manager (0.9.7-0ubuntu14.1 Ubuntu:14.04/trusty-updates [amd64])
Conf activity-log-manager-control-center (0.9.7-0ubuntu14.1 Ubuntu:14.04/trusty-updates [all])
Conf grub-common (2.02~beta2-9ubuntu1.8 Ubuntu:14.04/trusty-updates [amd64])
Conf grub2-common (2.02~beta2-9ubuntu1.8 Ubuntu:14.04/trusty-updates [amd64])
Conf efibootmgr (0.5.4-7ubuntu1.2 Ubuntu:14.04/trusty-updates [amd64])
Conf grub-efi-amd64-bin (2.02~beta2-9ubuntu1.8 Ubuntu:14.04/trusty-updates [amd64])
Conf grub-efi-amd64 (2.02~beta2-9ubuntu1.8 Ubuntu:14.04/trusty-updates [amd64])
Conf grub-efi-amd64-signed (1.34.9+2.02~beta2-9ubuntu1.8 Ubuntu:14.04/trusty-updates [amd64])
Conf python3-problem-report (2.14.1-0ubuntu3.21 Ubuntu:14.04/trusty-updates [all])
Conf python3-apport (2.14.1-0ubuntu3.21 Ubuntu:14.04/trusty-updates [all])
Conf apport (2.14.1-0ubuntu3.21 Ubuntu:14.04/trusty-updates [all])
Conf gir1.2-wnck-3.0 (3.4.7-0ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Conf apport-gtk (2.14.1-0ubuntu3.21 Ubuntu:14.04/trusty-updates [all])
Conf archdetect-deb (1.95ubuntu2.1 Ubuntu:14.04/trusty-updates [amd64])
Conf bluez-alsa (4.101-0ubuntu13.1 Ubuntu:14.04/trusty-updates [amd64])
Conf bluez-cups (4.101-0ubuntu13.1 Ubuntu:14.04/trusty-updates [amd64])
Conf btrfs-tools (3.12-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Conf compiz-core (1:0.9.11.3+14.04.20160425-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf libcompizconfig0 (1:0.9.11.3+14.04.20160425-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf libdecoration0 (1:0.9.11.3+14.04.20160425-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf metacity-common (1:2.34.13-0ubuntu4.1 Ubuntu:14.04/trusty-updates [all])
Conf libmetacity-private0a (1:2.34.13-0ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Conf compiz-plugins-default (1:0.9.11.3+14.04.20160425-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf compiz-gnome (1:0.9.11.3+14.04.20160425-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf compiz-plugins (1:0.9.11.3+14.04.20160425-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf metacity (1:2.34.13-0ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Conf compiz (1:0.9.11.3+14.04.20160425-0ubuntu1 Ubuntu:14.04/trusty-updates [all])
Conf python-gobject (3.12.0-1ubuntu1 Ubuntu:14.04/trusty-updates [all])
Conf dell-recovery (1.33~somerville1 dell.archive.canonical.com [all])
Conf libdpkg-perl (1.17.5ubuntu5.7 Ubuntu:14.04/trusty-updates [all])
Conf dpkg-dev (1.17.5ubuntu5.7 Ubuntu:14.04/trusty-updates [all])
Conf dkms (2.2.0.3-1.1ubuntu5.14.04.5 Ubuntu:14.04/trusty-updates [all])
Conf duplicity (0.6.23-1ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libecryptfs0 (104-0ubuntu1.14.04.4 Ubuntu:14.04/trusty-updates [amd64])
Conf ecryptfs-utils (104-0ubuntu1.14.04.4 Ubuntu:14.04/trusty-updates [amd64])
Conf eog (3.10.2-0ubuntu5.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libevdocument3-4 (3.10.3-0ubuntu10.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libevview3-3 (3.10.3-0ubuntu10.2 Ubuntu:14.04/trusty-updates [amd64])
Conf evince-common (3.10.3-0ubuntu10.2 Ubuntu:14.04/trusty-updates [all])
Conf evince (3.10.3-0ubuntu10.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libcamel-1.2-45 (3.10.4-0ubuntu1.5 Ubuntu:14.04/trusty-updates [amd64])
Conf evolution-data-server-common (3.10.4-0ubuntu1.5 Ubuntu:14.04/trusty-updates [all])
Conf libedataserver-1.2-18 (3.10.4-0ubuntu1.5 Ubuntu:14.04/trusty-updates [amd64])
Conf libebackend-1.2-7 (3.10.4-0ubuntu1.5 Ubuntu:14.04/trusty-updates [amd64])
Conf evolution-data-server-online-accounts (3.10.4-0ubuntu1.5 Ubuntu:14.04/trusty-updates [amd64])
Conf libebook-contacts-1.2-0 (3.10.4-0ubuntu1.5 Ubuntu:14.04/trusty-updates [amd64])
Conf libedata-book-1.2-20 (3.10.4-0ubuntu1.5 Ubuntu:14.04/trusty-updates [amd64])
Conf libebook-1.2-14 (3.10.4-0ubuntu1.5 Ubuntu:14.04/trusty-updates [amd64])
Conf libecal-1.2-16 (3.10.4-0ubuntu1.5 Ubuntu:14.04/trusty-updates [amd64])
Conf libedata-cal-1.2-23 (3.10.4-0ubuntu1.5 Ubuntu:14.04/trusty-updates [amd64])
Conf libgweather-common (3.10.2-0ubuntu2 Ubuntu:14.04/trusty-updates [all])
Conf libgweather-3-6 (3.10.2-0ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Conf evolution-data-server (3.10.4-0ubuntu1.5 Ubuntu:14.04/trusty-updates [amd64])
Conf unzip (6.0-9ubuntu1.5 Ubuntu:14.04/trusty-updates [amd64])
Conf file-roller (3.10.2.1-0ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Conf gdb (7.7.1-0ubuntu5~14.04.2 Ubuntu:14.04/trusty-updates [amd64])
Conf gir1.2-appindicator3-0.1 (12.10.1+13.10.20130920-0ubuntu4.1 Ubuntu:14.04/trusty-updates [amd64])
Conf gir1.2-edataserver-1.2 (3.10.4-0ubuntu1.5 Ubuntu:14.04/trusty-updates [amd64])
Conf gir1.2-ebookcontacts-1.2 (3.10.4-0ubuntu1.5 Ubuntu:14.04/trusty-updates [amd64])
Conf gir1.2-ebook-1.2 (3.10.4-0ubuntu1.5 Ubuntu:14.04/trusty-updates [amd64])
Conf gir1.2-gstreamer-1.0 (1.2.4-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf gir1.2-gst-plugins-base-1.0 (1.2.4-1~ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Conf gir1.2-gudev-1.0 (1:204-5ubuntu20.19 Ubuntu:14.04/trusty-updates [amd64])
Conf gir1.2-networkmanager-1.0 (0.9.8.8-0ubuntu7.3 Ubuntu:14.04/trusty-updates [amd64])
Conf gir1.2-udisks-2.0 (2.1.3-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Conf gnome-calculator (1:3.10.3-0ubuntu0.1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf gnome-control-center-shared-data (1:3.6.3-0ubuntu56.1 Ubuntu:14.04/trusty-updates [all])
Conf gnome-session-bin (3.9.90-0ubuntu12.1 Ubuntu:14.04/trusty-updates [amd64])
Conf gnome-session-common (3.9.90-0ubuntu12.1 Ubuntu:14.04/trusty-updates [all])
Conf ubuntu-session (3.9.90-0ubuntu12.1 Ubuntu:14.04/trusty-updates [all])
Conf gnome-sudoku (1:3.10.2-0ubuntu3.1 Ubuntu:14.04/trusty-updates [all])
Conf gstreamer1.0-alsa (1.2.4-1~ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Conf gstreamer1.0-tools (1.2.4-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf gstreamer1.0-plugins-base-apps (1.2.4-1~ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Conf gstreamer1.0-x (1.2.4-1~ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Conf heirloom-mailx (12.5-2+deb7u1build0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf hud (14.04+14.04.20140604-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf ibus-gtk (1.5.5-1ubuntu3.2 Ubuntu:14.04/trusty-updates [amd64])
Conf ibus-gtk3 (1.5.5-1ubuntu3.2 Ubuntu:14.04/trusty-updates [amd64])
Conf indicator-session (12.10.5+14.04.20151021.1-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf intel-gpu-tools (1.3-0ubuntu2.1 Ubuntu:14.04/trusty-updates [amd64])
Conf iproute (1:3.12.0-2ubuntu1 Ubuntu:14.04/trusty-updates [all])
Conf python-pkg-resources (3.3-1ubuntu2 Ubuntu:14.04/trusty-updates [all])
Conf python-aptdaemon (1.1.1-1ubuntu5.2 Ubuntu:14.04/trusty-updates [all])
Conf python-aptdaemon.gtk3widgets (1.1.1-1ubuntu5.2 Ubuntu:14.04/trusty-updates [all])
Conf landscape-client-ui-install (14.12-0ubuntu0.14.04 Ubuntu:14.04/trusty-updates [amd64])
Conf libgnome-control-center1 (1:3.6.3-0ubuntu56.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgphoto2-l10n (2.5.3.1-1ubuntu2.2 Ubuntu:14.04/trusty-updates [all])
Conf libgtk-3-bin (3.10.8-0ubuntu1.6 Ubuntu:14.04/trusty-updates [amd64])
Conf liblightdm-gobject-1-0 (1.10.6-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf liblwp-protocol-https-perl (6.04-2ubuntu0.1 Ubuntu:14.04/trusty-updates [all])
Conf libminiupnpc8 (1.6-3ubuntu2.14.04.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libmono-system-xml4.0-cil (3.2.8+dfsg-4ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Conf libmono-system-configuration4.0-cil (3.2.8+dfsg-4ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Conf libmono-system4.0-cil (3.2.8+dfsg-4ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Conf libmono-security4.0-cil (3.2.8+dfsg-4ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Conf mono-4.0-gac (3.2.8+dfsg-4ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Conf mono-gac (3.2.8+dfsg-4ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Conf mono-runtime-common (3.2.8+dfsg-4ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf mono-runtime-sgen (3.2.8+dfsg-4ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf mono-runtime (3.2.8+dfsg-4ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libmono-corlib4.5-cil (3.2.8+dfsg-4ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Conf libmono-system-security4.0-cil (3.2.8+dfsg-4ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Conf libmono-cairo4.0-cil (3.2.8+dfsg-4ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Conf libmono-corlib4.0-cil (3.2.8+dfsg-4ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Conf libmono-i18n4.0-cil (3.2.8+dfsg-4ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Conf libmono-i18n-west4.0-cil (3.2.8+dfsg-4ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Conf libmono-system-drawing4.0-cil (3.2.8+dfsg-4ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Conf libpurple-bin (1:2.10.9-0ubuntu3.2 Ubuntu:14.04/trusty-updates [all])
Conf libpurple0 (1:2.10.9-0ubuntu3.2 Ubuntu:14.04/trusty-updates [amd64])
Conf libreoffice-avmedia-backend-gstreamer (1:4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [amd64])
Conf libreoffice-presentation-minimizer (1:4.2.8-0ubuntu4 Ubuntu:14.04/trusty-updates [all])
Conf libufe-xidgetter0 (3.0.0+14.04.20140416-0ubuntu1.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf unity-services (7.2.6+14.04.20160408-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf libunity-core-6.0-9 (7.2.6+14.04.20160408-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf nux-tools (4.0.6+14.04.20141107-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf unity-greeter (14.04.11-0ubuntu1somerville1 dell.archive.canonical.com [amd64])
Conf unity (7.2.6+14.04.20160408-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf unity-lens-music (6.9.0+14.04.20151120.2-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf libwhoopsie0 (0.2.24.6ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Conf whoopsie (0.2.24.6ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Conf linux-firmware (1.127.22 Ubuntu:14.04/trusty-updates [all])
Conf linux-image-extra-3.13.0-91-generic (3.13.0-91.138 Ubuntu:14.04/trusty-updates [amd64])
Conf linux-image-generic (3.13.0.91.97 Ubuntu:14.04/trusty-updates [amd64])
Conf linux-headers-3.13.0-91 (3.13.0-91.138 Ubuntu:14.04/trusty-updates [all])
Conf linux-headers-3.13.0-91-generic (3.13.0-91.138 Ubuntu:14.04/trusty-updates [amd64])
Conf linux-headers-generic (3.13.0.91.97 Ubuntu:14.04/trusty-updates [amd64])
Conf linux-generic (3.13.0.91.97 Ubuntu:14.04/trusty-updates [amd64])
Conf myspell-en-gb (1:4.2.1-0ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Conf myspell-en-za (1:4.2.1-0ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Conf mythes-en-us (1:4.2.1-0ubuntu1.1 Ubuntu:14.04/trusty-updates [all])
Conf notify-osd-icons (0.8+14.04.20151016-0ubuntu1 Ubuntu:14.04/trusty-updates [all])
Conf onboard (1.0.1-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf onboard-data (1.0.1-0ubuntu1 Ubuntu:14.04/trusty-updates [all])
Conf openoffice.org-hyphenation (0.7.1 Ubuntu:14.04/trusty-updates [all])
Conf os-prober (1.63ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf plymouth-theme-ubuntu-logo (0.8.8-0ubuntu17.1 Ubuntu:14.04/trusty-updates [amd64])
Conf pm-utils (1.4.1-13ubuntu0.2 Ubuntu:14.04/trusty-updates [all])
Conf pulseaudio-utils (1:4.0-0ubuntu11.1 Ubuntu:14.04/trusty-updates [amd64])
Conf pulseaudio-module-x11 (1:4.0-0ubuntu11.1 Ubuntu:14.04/trusty-updates [amd64])
Conf python-six (1.5.2-1ubuntu1 Ubuntu:14.04/trusty-updates [all])
Conf python-urllib3 (1.7.1-1ubuntu4 Ubuntu:14.04/trusty-updates [all])
Conf python-requests (2.2.1-1ubuntu0.3 Ubuntu:14.04/trusty-updates [all])
Conf python-cupshelpers (1.4.3+20140219-0ubuntu2.6 Ubuntu:14.04/trusty-updates [all])
Conf python-ibus (1.5.5-1ubuntu3.2 Ubuntu:14.04/trusty-updates [all])
Conf python-libxml2 (2.9.1+dfsg1-3ubuntu4.8 Ubuntu:14.04/trusty-updates [amd64])
Conf python-lxml (3.3.3-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Conf python3-chardet (2.2.1-2~ubuntu1 Ubuntu:14.04/trusty-updates [all])
Conf python3-lxml (3.3.3-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Conf python3-requests (2.2.1-1ubuntu0.3 Ubuntu:14.04/trusty-updates [all])
Conf unattended-upgrades (0.82.1ubuntu2.4 Ubuntu:14.04/trusty-updates [all])
Conf python3-software-properties (0.92.37.7 Ubuntu:14.04/trusty-updates [all])
Conf software-properties-common (0.92.37.7 Ubuntu:14.04/trusty-updates [all])
Conf software-properties-gtk (0.92.37.7 Ubuntu:14.04/trusty-updates [all])
Conf libandroid-properties1 (0.1.0+git20131207+e452e83-0ubuntu12 Ubuntu:14.04/trusty [amd64])
Conf oxideqt-codecs (1.15.8-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf liboxideqtcore0 (1.15.8-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf liboxideqtquick0 (1.15.8-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf liboxideqt-qmlplugin (1.15.8-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets (0.23+14.04.20140428-0ubuntu1 Ubuntu:14.04/trusty-updates [all])
Conf qtdeclarative5-ubuntu-ui-extras-browser-plugin (0.23+14.04.20140428-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf webbrowser-app (0.23+14.04.20140428-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf webapp-container (0.23+14.04.20140428-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf sane-utils (1.0.23-3ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Conf sbsigntool (0.6-0ubuntu7.1 Ubuntu:14.04/trusty-updates [amd64])
Conf shim (0.8-0ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Conf shim-signed (1.9+0.8-0ubuntu2 Ubuntu:14.04/trusty-updates [amd64])
Conf shotwell-common (0.18.0-0ubuntu4.4 Ubuntu:14.04/trusty-updates [all])
Conf shotwell (0.18.0-0ubuntu4.4 Ubuntu:14.04/trusty-updates [amd64])
Conf simple-scan (3.12.3-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf ssh-askpass-gnome (1:6.6p1-2ubuntu2.7 Ubuntu:14.04/trusty-updates [amd64])
Conf system-config-printer-common (1.4.3+20140219-0ubuntu2.6 Ubuntu:14.04/trusty-updates [all])
Conf system-config-printer-gnome (1.4.3+20140219-0ubuntu2.6 Ubuntu:14.04/trusty-updates [all])
Conf system-config-printer-udev (1.4.3+20140219-0ubuntu2.6 Ubuntu:14.04/trusty-updates [amd64])
Conf t1utils (1.37-2ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf thunderbird (1:38.8.0+build1-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf thunderbird-locale-en (1:38.8.0+build1-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf thunderbird-gnome-support (1:38.8.0+build1-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf thunderbird-locale-en-us (1:38.8.0+build1-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [all])
Conf transmission-common (2.82-1.1ubuntu3.1 Ubuntu:14.04/trusty-updates [all])
Conf transmission-gtk (2.82-1.1ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Conf ubuntu-docs (14.04.5 Ubuntu:14.04/trusty-updates [all])
Conf unity-scope-musicstores (6.9.0+14.04.20151120.2-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf usb-creator-common (0.2.56.3ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Conf usb-creator-gtk (0.2.56.3ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Conf webaccounts-extension-common (0.5-0ubuntu2.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-radeon (1:7.3.0-1ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-ati (1:7.3.0-1ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-intel (2:2.99.910-0ubuntu1.6 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-openchrome (1:0.3.3-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-all (1:7.7+1ubuntu8.1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-input-all (1:7.7+1ubuntu8.1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg (1:7.7+1ubuntu8.1 Ubuntu:14.04/trusty-updates [amd64])
Conf xorg (1:7.7+1ubuntu8.1 Ubuntu:14.04/trusty-updates [amd64])
Conf apt-clone (0.3.1~ubuntu11.1 Ubuntu:14.04/trusty-updates [all])
Conf casper (1.340.2 Ubuntu:14.04/trusty-updates [amd64])
Conf gdisk (0.8.8-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Conf hardening-includes (2.5ubuntu2.1 Ubuntu:14.04/trusty-updates [all])
Conf openjdk-6-jre (6b39-1.13.11-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf icedtea-netx-common (1.5.3-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [all])
Conf icedtea-netx (1.5.3-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf icedtea-6-plugin (1.5.3-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf indicator-printers (0.1.7+14.04.20140527-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf kpartx (0.4.9-3ubuntu7.13 Ubuntu:14.04/trusty-updates [amd64])
Conf kpartx-boot (0.4.9-3ubuntu7.13 Ubuntu:14.04/trusty-updates [all])
Conf oneconf-common (0.3.7.14.04.1 Ubuntu:14.04/trusty-updates [all])
Conf python3-oneconf (0.3.7.14.04.1 Ubuntu:14.04/trusty-updates [all])
Conf oneconf (0.3.7.14.04.1 Ubuntu:14.04/trusty-updates [all])
Conf pulseaudio-module-bluetooth (1:4.0-0ubuntu11.1 Ubuntu:14.04/trusty-updates [amd64])
Conf python-oneconf (0.3.7.14.04.1 Ubuntu:14.04/trusty-updates [all])
Conf xul-ext-websites-integration (2.3.6+13.10.20130920.1-0ubuntu1.2 Ubuntu:14.04/trusty-updates [all])

```

---

