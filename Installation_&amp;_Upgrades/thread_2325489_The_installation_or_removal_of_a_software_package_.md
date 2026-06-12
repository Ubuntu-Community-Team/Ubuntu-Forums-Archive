---
title: "The installation or removal of a software package failed"
date: 2016-05-23
forum: Installation &amp; Upgrades
---

### Post by sathu on 2016-05-23
Hi All

I have been struggling to update my ubuntu 14.04 for last one week
My update option shows 

" The installation or removal of a software package failed"
when ever I try to install or upgrade some software

I have seen many threads with same heading and many solutions
Unfortunately when i execute the commands i dont see any results

I tried  
sudo dpkg --configure --pending
sudo apt-get --fix-broken install
sudo dpkg --configure -a

but all messages are executed with no results

Can any one help me on this?

thank you

---

### Post by Impavidus on 2016-05-23
dpkg and apt-get tend to be quite verbose. They should give you some useful diagnostics or error messages. Try```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
```and show us the full output. If that last command tries to uninstall something important, abort it.

---

### Post by sathu on 2016-05-24
Hi

thank your for the reply

please find the command and its results below

```

abc@ubuntu:~$sudo dpkg --configure -a
abc@ubuntu:~$ sudo apt-get update
Ign http://archive.canonical.com trusty InRelease
Ign http://extras.ubuntu.com trusty InRelease 
Hit http://archive.canonical.com trusty Release.gpg
Ign http://in.archive.ubuntu.com trusty InRelease
Hit http://archive.canonical.com trusty Release
Get:1 http://extras.ubuntu.com trusty Release.gpg [71 B]              
Get:2 http://in.archive.ubuntu.com trusty-updates InRelease [65.9 kB]          
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://archive.canonical.com trusty/partner Translation-en                 
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://in.archive.ubuntu.com trusty-backports InRelease                    
Hit http://extras.ubuntu.com trusty/main i386 Packages                   
Get:3 http://in.archive.ubuntu.com trusty-security InRelease [65.9 kB]         
Hit http://in.archive.ubuntu.com trusty Release.gpg                        
Get:4 http://in.archive.ubuntu.com trusty-updates/main Sources [275 kB]
Ign http://extras.ubuntu.com trusty/main Translation-en_IN
Ign http://extras.ubuntu.com trusty/main Translation-en
Get:5 http://in.archive.ubuntu.com trusty-updates/restricted Sources [5,352 B] 
Get:6 http://in.archive.ubuntu.com trusty-updates/universe Sources [155 kB]    
Get:7 http://in.archive.ubuntu.com trusty-updates/multiverse Sources [5,939 B] 
Get:8 http://in.archive.ubuntu.com trusty-updates/main amd64 Packages [768 kB] 
Get:9 http://in.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.9 kB]
Get:10 http://in.archive.ubuntu.com trusty-updates/universe amd64 Packages [360 kB]
Get:11 http://in.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [13.2 kB]
Get:12 http://in.archive.ubuntu.com trusty-updates/main i386 Packages [736 kB] 
Get:13 http://in.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.6 kB]
Get:14 http://in.archive.ubuntu.com trusty-updates/universe i386 Packages [361 kB]
Get:15 http://in.archive.ubuntu.com trusty-updates/multiverse i386 Packages [13.6 kB]
Get:16 http://in.archive.ubuntu.com trusty-updates/main Translation-en [384 kB]
Get:17 http://in.archive.ubuntu.com trusty-updates/multiverse Translation-en [7,227 B]
Get:18 http://in.archive.ubuntu.com trusty-updates/restricted Translation-en [3,699 B]
Get:19 http://in.archive.ubuntu.com trusty-updates/universe Translation-en [188 kB]
Hit http://in.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://in.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://in.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://in.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://in.archive.ubuntu.com trusty-backports/main amd64 Packages          
Hit http://in.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://in.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Hit http://in.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Hit http://in.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://in.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://in.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://in.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://in.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://in.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://in.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://in.archive.ubuntu.com trusty-backports/universe Translation-en      
Get:20 http://in.archive.ubuntu.com trusty-security/main Sources [116 kB]      
Get:21 http://in.archive.ubuntu.com trusty-security/restricted Sources [4,035 B]
Get:22 http://in.archive.ubuntu.com trusty-security/universe Sources [36.5 kB] 
Get:23 http://in.archive.ubuntu.com trusty-security/multiverse Sources [2,760 B]
Get:24 http://in.archive.ubuntu.com trusty-security/main amd64 Packages [480 kB]
Get:25 http://in.archive.ubuntu.com trusty-security/restricted amd64 Packages [13.0 kB]
Get:26 http://in.archive.ubuntu.com trusty-security/universe amd64 Packages [129 kB]
Get:27 http://in.archive.ubuntu.com trusty-security/multiverse amd64 Packages [4,978 B]
Get:28 http://in.archive.ubuntu.com trusty-security/main i386 Packages [454 kB]
Get:29 http://in.archive.ubuntu.com trusty-security/restricted i386 Packages [12.7 kB]
Get:30 http://in.archive.ubuntu.com trusty-security/universe i386 Packages [129 kB]
Get:31 http://in.archive.ubuntu.com trusty-security/multiverse i386 Packages [5,168 B]
Get:32 http://in.archive.ubuntu.com trusty-security/main Translation-en [264 kB]
Get:33 http://in.archive.ubuntu.com trusty-security/multiverse Translation-en [2,570 B]
Get:34 http://in.archive.ubuntu.com trusty-security/restricted Translation-en [3,206 B]
Get:35 http://in.archive.ubuntu.com trusty-security/universe Translation-en [75.8 kB]
Hit http://in.archive.ubuntu.com trusty Release                                
Hit http://in.archive.ubuntu.com trusty/main Sources                           
Hit http://in.archive.ubuntu.com trusty/restricted Sources                     
Hit http://in.archive.ubuntu.com trusty/universe Sources                       
Hit http://in.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://in.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://in.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://in.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://in.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://in.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://in.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://in.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://in.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://in.archive.ubuntu.com trusty/main Translation-en                    
Hit http://in.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://in.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://in.archive.ubuntu.com trusty/universe Translation-en                
Ign http://in.archive.ubuntu.com trusty/main Translation-en_IN                 
Ign http://in.archive.ubuntu.com trusty/multiverse Translation-en_IN           
Ign http://in.archive.ubuntu.com trusty/restricted Translation-en_IN           
Ign http://in.archive.ubuntu.com trusty/universe Translation-en_IN             
Fetched 5,172 kB in 1min 13s (70.0 kB/s)                                       
Reading package lists... Done
abc@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libhdb9-heimdal libkdc2-heimdal libntdb1 python-ntdb
Use 'apt-get autoremove' to remove them.
The following packages have been kept back:
  linux-generic-lts-utopic linux-headers-generic-lts-utopic
  linux-image-generic-lts-utopic
The following packages will be upgraded:
  apport apport-gtk apt apt-transport-https apt-utils base-files
  bash-completion bind9-host binutils ca-certificates coreutils cpio cpp-4.8
  dnsutils dpkg dpkg-dev eog firefox firefox-locale-en fonts-opensymbol
  g++-4.8 gcc-4.8 gcc-4.8-base gcc-4.8-base:i386 gir1.2-gtk-3.0
  gir1.2-gudev-1.0 gir1.2-ibus-1.0 gir1.2-javascriptcoregtk-3.0
  gir1.2-networkmanager-1.0 gir1.2-soup-2.4 gir1.2-webkit-3.0 git git-man
  glib-networking glib-networking-common glib-networking-services ibus
  ibus-gtk ibus-gtk3 ifupdown initramfs-tools initramfs-tools-bin initscripts
  klibc-utils libapache2-mod-php5 libapt-inst1.5 libapt-pkg4.12 libarchive13
  libasan0 libatomic1 libbind9-90 libc-bin libc-dev-bin libc6 libc6:i386
  libc6-dbg libc6-dev libc6-i386 libdns100 libdpkg-perl libdrm-intel1
  libdrm-intel1:i386 libdrm-nouveau2 libdrm-nouveau2:i386 libdrm-radeon1
  libdrm-radeon1:i386 libdrm2 libdrm2:i386 libebml4 libexpat1 libexpat1:i386
  libgail-3-0 libgail-common libgail18 libgcc-4.8-dev libgcrypt11
  libgcrypt11:i386 libgfortran3 libgnutls-openssl27 libgnutls26
  libgnutls26:i386 libgomp1 libgraphite2-3 libgtk-3-0 libgtk-3-bin
  libgtk-3-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgudev-1.0-0
  libhogweed2 libibus-1.0-5 libisc95 libisccc90 libisccfg90 libitm1 libjasper1
  libjavascriptcoregtk-1.0-0 libjavascriptcoregtk-3.0-0 libklibc liblcms2-2
  liblcms2-2:i386 libldb1 liblwres90 libmatroska6 libmm-glib0 libmysqlclient18
  libmysqlclient18:i386 libnautilus-extension1a libnettle4 libnl-3-200
  libnl-genl-3-200 libnl-route-3-200 libnm-glib-vpn1 libnm-glib4 libnm-util2
  libnss-winbind libnss3 libnss3-nssdb libnuma1 liboxideqt-qmlplugin
  liboxideqtcore0 liboxideqtquick0 libpam-modules libpam-modules-bin
  libpam-runtime libpam-systemd libpam-winbind libpam0g libpci3 libpcre3
  libpcre3:i386 libperl5.18 libpixman-1-0 libpoppler-glib8 libpoppler44
  libquadmath0 libreoffice-avmedia-backend-gstreamer libreoffice-base-core
  libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw
  libreoffice-gnome libreoffice-gtk libreoffice-impress libreoffice-math
  libreoffice-ogltrans libreoffice-pdfimport
  libreoffice-presentation-minimizer libreoffice-style-human
  libreoffice-writer libsmbclient libsnmp-base libsnmp30 libsoup-gnome2.4-1
  libsoup2.4-1 libssh-4 libssl-dev libssl-doc libssl1.0.0 libssl1.0.0:i386
  libstdc++-4.8-dev libstdc++6 libstdc++6:i386 libsystemd-daemon0
  libsystemd-journal0 libsystemd-login0 libtalloc2 libtasn1-6 libtasn1-6:i386
  libtdb1 libtevent0 libtiff5 libtiff5:i386 libtsan0 libudev1 libudev1:i386
  libvlc5 libvlccore7 libwbclient0 libwebkitgtk-1.0-0 libwebkitgtk-1.0-common
  libwebkitgtk-3.0-0 libwebkitgtk-3.0-common linux-firmware linux-libc-dev
  login lsb lsb-base lsb-core lsb-cxx lsb-desktop lsb-graphics lsb-invalid-mta
  lsb-languages lsb-multimedia lsb-printing lsb-release lsb-security
  modemmanager multiarch-support mysql-client-5.5 mysql-client-core-5.5
  mysql-common mysql-server mysql-server-5.5 mysql-server-core-5.5 nautilus
  nautilus-data network-manager ntpdate oneconf oneconf-common openjdk-7-jdk
  openjdk-7-jre openjdk-7-jre-headless openssh-client openssh-server
  openssh-sftp-server openssl oxideqt-codecs passwd pciutils perl perl-base
  perl-modules php5 php5-cgi php5-cli php5-common php5-curl php5-gd php5-mysql
  php5-readline pm-utils poppler-utils python-ibus python-ldb python-oneconf
  python-samba python-talloc python-tdb python3-apport python3-oneconf
  python3-problem-report python3-uno samba samba-common samba-common-bin
  samba-dsdb-modules samba-libs samba-vfs-modules simple-scan smbclient ssh
  ssh-askpass-gnome systemd-services sysv-rc sysvinit-utils tdb-tools
  thunderbird thunderbird-gnome-support thunderbird-locale-en
  thunderbird-locale-en-us tzdata tzdata-java udev unity-lens-music
  unity-scope-musicstores uno-libs3 ure usbutils vlc vlc-data vlc-nox
  vlc-plugin-notify vlc-plugin-pulse winbind
279 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0 B/416 MB of archives.
After this operation, 56.3 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Extracting templates from packages: 100%
Preconfiguring packages ...
E: Sub-process /usr/bin/dpkg returned an error code (2)


```

---

### Post by Impavidus on 2016-05-24
That's strange.

Quite a lot of upgrades, it seems it hasn't been properly upgraded in while. No complaints from apt, nothing strange in your repositories, but dpkg fails immediately. Is there a problem with any package?```
dpkg --list | grep -v "^ii \|^rc "
```Or is it a problem with dpkg itself? Maybe you can find something interesting in /var/log/dpkg.log.

---

### Post by sathu on 2016-05-26
Hello

I checked the log - sudo gedit  /var/log/dpkg.log

```

2016-05-24 14:29:04 startup archives unpack2016-05-24 14:29:28 startup packages configure
2016-05-24 14:29:33 startup packages configure
2016-05-24 14:32:22 startup archives unpack

```

I also tried the command - dpkg --list | grep -v "^ii \|^rc " which gave me 

```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                                  Version                                             Architecture Description
+++-=====================================================-===================================================-============-===============================================================================
ri  account-plugin-windows-live                           0.11+14.04.20140409.1-0ubuntu2                      all          GNOME Control Center account plugin for single signon - windows live
ri  phpmyadmin                                            4:4.0.10-1                                          all          MySQL web administration tool



```

---

### Post by vasa1 on 2016-05-26
Does```
sudo dpkg -C
```return anything?

And do you have personal data of importance on your system? I'd suggest backing it all up on another device just in case ...

And then, if nothing else works, do a clean re-install.

---

### Post by sathu on 2016-05-26
Hi 

The command returned nothing

thank you

---

### Post by Impavidus on 2016-05-26
Maybe there's something wrong with the downloaded packages? Try```
sudo apt-get clean
```Next time it should redownload all upgrades. Then try to install upgrades again.

Try running```
echo $?
```after your dpkg or apt-get commands. It will tell us whether there were any errors, even when there's no proper error message. Just in case, I don't expect it will show much.

I've never seen this kind of dpkg error before.

---

### Post by RobGoss on 2016-05-26
Hello and welcome, Have you try changing your servers? Go to **Software & Updates**, choose **Other** from the drop-down menu then choose **Best server**

This will find the best server for your location

---

### Post by JimHiTek on 2016-05-26
Just a thought: I'm getting the same error and failure when I try to upgrade from 14.04 to 15 or higher but I'm pretty sure it's because I'm in a RV park which uses Tengo Internet services. That company throttles usage. You'd think in the US where the internet was invented, we wouldn't have to put up with that kind of garbage. But, it is what it is. This is what they say about it, "[COLOR=#333333][FONT=&amp]this system utilizes bandwidth shaping technology to govern your connection speed".  Whenever I try to download a large file and install it fails. Small apps seem to make it ok.[/FONT][/COLOR]

Are you somewhere where your internet connection is 'monitored' or 'throttled'?

---

### Post by sathu on 2016-05-27
Hi All

thanks for the support and replies

please find the response from the commands

```

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libhdb9-heimdal libkdc2-heimdal libntdb1 python-ntdb
Use 'apt-get autoremove' to remove them.
The following packages have been kept back:
  linux-generic-lts-utopic linux-headers-generic-lts-utopic
  linux-image-generic-lts-utopic
The following packages will be upgraded:
  apport apport-gtk apt apt-transport-https apt-utils base-files
  bash-completion bind9-host binutils ca-certificates compiz compiz-core
  compiz-gnome compiz-plugins-default compizconfig-settings-manager coreutils
  cpio cpp-4.8 dnsutils dpkg dpkg-dev eog firefox firefox-locale-en
  fonts-opensymbol g++-4.8 gcc-4.8 gcc-4.8-base gcc-4.8-base:i386
  gir1.2-gtk-3.0 gir1.2-gudev-1.0 gir1.2-ibus-1.0 gir1.2-javascriptcoregtk-3.0
  gir1.2-networkmanager-1.0 gir1.2-soup-2.4 gir1.2-webkit-3.0 git git-man
  glib-networking glib-networking-common glib-networking-services ibus
  ibus-gtk ibus-gtk3 ifupdown initramfs-tools initramfs-tools-bin initscripts
  klibc-utils libapache2-mod-php5 libapt-inst1.5 libapt-pkg4.12 libarchive13
  libasan0 libatomic1 libbind9-90 libc-bin libc-dev-bin libc6 libc6:i386
  libc6-dbg libc6-dev libc6-i386 libcompizconfig0 libdecoration0 libdns100
  libdpkg-perl libdrm-intel1 libdrm-intel1:i386 libdrm-nouveau2
  libdrm-nouveau2:i386 libdrm-radeon1 libdrm-radeon1:i386 libdrm2 libdrm2:i386
  libebml4 libexpat1 libexpat1:i386 libgail-3-0 libgail-common libgail18
  libgcc-4.8-dev libgcrypt11 libgcrypt11:i386 libgfortran3 libgnutls-openssl27
  libgnutls26 libgnutls26:i386 libgomp1 libgraphite2-3 libgtk-3-0 libgtk-3-bin
  libgtk-3-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgudev-1.0-0
  libhogweed2 libibus-1.0-5 libisc95 libisccc90 libisccfg90 libitm1 libjasper1
  libjavascriptcoregtk-1.0-0 libjavascriptcoregtk-3.0-0 libklibc liblcms2-2
  liblcms2-2:i386 libldb1 liblwres90 libmatroska6 libmm-glib0 libmysqlclient18
  libmysqlclient18:i386 libnautilus-extension1a libnettle4 libnl-3-200
  libnl-genl-3-200 libnl-route-3-200 libnm-glib-vpn1 libnm-glib4 libnm-util2
  libnss-winbind libnss3 libnss3-nssdb libnuma1 liboxideqt-qmlplugin
  liboxideqtcore0 liboxideqtquick0 libpam-modules libpam-modules-bin
  libpam-runtime libpam-systemd libpam-winbind libpam0g libpci3 libpcre3
  libpcre3:i386 libperl5.18 libpixman-1-0 libpoppler-glib8 libpoppler44
  libquadmath0 libreoffice-avmedia-backend-gstreamer libreoffice-base-core
  libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw
  libreoffice-gnome libreoffice-gtk libreoffice-impress libreoffice-math
  libreoffice-ogltrans libreoffice-pdfimport
  libreoffice-presentation-minimizer libreoffice-style-human
  libreoffice-writer libsmbclient libsnmp-base libsnmp30 libsoup-gnome2.4-1
  libsoup2.4-1 libssh-4 libssl-dev libssl-doc libssl1.0.0 libssl1.0.0:i386
  libstdc++-4.8-dev libstdc++6 libstdc++6:i386 libsystemd-daemon0
  libsystemd-journal0 libsystemd-login0 libtalloc2 libtasn1-6 libtasn1-6:i386
  libtdb1 libtevent0 libtiff5 libtiff5:i386 libtsan0 libudev1 libudev1:i386
  libvlc5 libvlccore7 libwbclient0 libwebkitgtk-1.0-0 libwebkitgtk-1.0-common
  libwebkitgtk-3.0-0 libwebkitgtk-3.0-common linux-firmware linux-libc-dev
  login lsb lsb-base lsb-core lsb-cxx lsb-desktop lsb-graphics lsb-invalid-mta
  lsb-languages lsb-multimedia lsb-printing lsb-release lsb-security
  modemmanager multiarch-support mysql-client-5.5 mysql-client-core-5.5
  mysql-common mysql-server mysql-server-5.5 mysql-server-core-5.5 nautilus
  nautilus-data network-manager ntpdate oneconf oneconf-common openjdk-7-jdk
  openjdk-7-jre openjdk-7-jre-headless openssh-client openssh-server
  openssh-sftp-server openssl oxideqt-codecs passwd pciutils perl perl-base
  perl-modules php5 php5-cgi php5-cli php5-common php5-curl php5-gd php5-mysql
  php5-readline pm-utils poppler-utils python-compizconfig python-ibus
  python-ldb python-oneconf python-samba python-talloc python-tdb
  python3-apport python3-oneconf python3-problem-report python3-uno samba
  samba-common samba-common-bin samba-dsdb-modules samba-libs
  samba-vfs-modules simple-scan smbclient ssh ssh-askpass-gnome
  systemd-services sysv-rc sysvinit-utils tdb-tools thunderbird
  thunderbird-gnome-support thunderbird-locale-en thunderbird-locale-en-us
  tzdata tzdata-java udev unity-lens-music unity-scope-musicstores uno-libs3
  ure usbutils vlc vlc-data vlc-nox vlc-plugin-notify vlc-plugin-pulse winbind
287 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0 B/418 MB of archives.
After this operation, 56.3 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Extracting templates from packages: 100%
Preconfiguring packages ...
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

And the next set 
```

echo $?
100

```

@[COLOR=#000000]JimHiTek - Yes there are some restrictions in network, but i think its not affected with linux upgrades

@[/COLOR][COLOR=#000000]RobGoss - Will try that too - thanks![/COLOR][COLOR=#000000]
 [/COLOR]

---

### Post by Impavidus on 2016-05-27
> **vasa1 said:**
> 
And do you have personal data of importance on your system? I'd suggest backing it all up on another device just in case ...

And then, if nothing else works, do a clean re-install.

I begin to agree with that. I've got no idea what might cause this error. For some unknown reason dpkg doesn't work. It doesn't seem to be a network related problem though.

In your output, it seems that all packages are already stored on your computer. Did you run the apt-get clean command? Anyway, that should cause a 418MB download, which is big. It sounds like months of updates waiting for you. For 3 times that download you can get a fresh install of the latest release of Ubuntu. It's worth considering a fresh install now, unless you really want to keep 14.04 for as long as possible.

---

