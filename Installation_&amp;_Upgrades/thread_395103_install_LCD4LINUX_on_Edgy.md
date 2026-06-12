---
title: "install LCD4LINUX on Edgy"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by xelapond on 2007-03-27
I have tried several different ways of getting lcd4linux installed on my AMD64 box running edgy.  I tried the following:

sudo aptitude install lcd4linux and i get this output:

alex@alex-desktop:~$ sudo aptitide install lcd4linux
Password:
sudo: aptitide: command not found
alex@alex-desktop:~$ sudo aptitude install lcd4linux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  linux-image-generic linux-restricted-modules-2.6.17-10-generic 
  linux-restricted-modules-common linux-restricted-modules-generic 
The following packages have been kept back:
  app-install-data-commercial avahi-daemon bind9-host capplets-data dbus 
  dbus-1-utils dnsutils ekiga evolution evolution-data-server 
  evolution-data-server-common evolution-plugins file firefox 
  firefox-gnome-support gnome-applets gnome-applets-data 
  gnome-control-center gnome-netstatus-applet gnome-panel gnome-panel-data 
  gnome-system-tools gnupg language-pack-en language-pack-gnome-en 
  libavahi-client3 libavahi-common-data libavahi-common3 libavahi-core4 
  libavahi-glib1 libbind9-0 libcamel1.2-8 libdbus-1-3 libdns21 
  libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 
  libedataserver1.2-7 libedataserverui1.2-8 libegroupwise1.2-12 
  libexchange-storage1.2-2 libgnome-window-settings1 libgnomevfs2-0 
  libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgtk2.0-0 
  libgtk2.0-bin libgtk2.0-common libgtop2-7 libgtop2-common libisc11 
  libisccc0 libisccfg1 libkrb53 liblwres9 libmagic1 libmagick9 
  libnautilus-extension1 libnspr4 libnss3 libpanel-applet2-0 libpoppler1 
  libpoppler1-glib libsmbclient libsoup2.2-8 libtotem-plparser1 
  libvolumeid0 libwpd8c2a linux-generic linux-headers-generic nautilus 
  nautilus-data openoffice.org openoffice.org-base openoffice.org-calc 
  openoffice.org-common openoffice.org-core openoffice.org-draw 
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress 
  openoffice.org-java-common openoffice.org-math 
  openoffice.org-style-default openoffice.org-style-industrial 
  openoffice.org-writer poppler-utils popularity-contest python-uno 
  samba-common slocate smbclient system-tools-backends tcpdump totem 
  totem-gstreamer totem-mozilla ttf-opensymbol tzdata ubuntu-docs udev 
  update-manager update-notifier vino volumeid w3m xserver-xorg-core 
The following packages will be upgraded:
  lcd4linux 
1 packages upgraded, 0 newly installed, 0 to remove and 113 not upgraded.
Need to get 0B/162kB of archives. After unpacking 45.1kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 104856 files and directories currently installed.)
Preparing to replace lcd4linux 0.10.0+cvs20051015-2ubuntu2 (using .../lcd4linux_0.10.0+cvs20060825-1_amd64.deb) ...
Stopping lcd4linux: invoke-rc.d: initscript lcd4linux, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Stopping lcd4linux: invoke-rc.d: initscript lcd4linux, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/lcd4linux_0.10.0+cvs20060825-1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Starting lcd4linux: lcd4linux.
Errors were encountered while processing:
 /var/cache/apt/archives/lcd4linux_0.10.0+cvs20060825-1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
alex@alex-desktop:~$ 



Could someone please help me?  I am kinda new to linux but completely new to ubuntu.  This is for a robotics project i am working on.

And help would be appriciated

Alex

---

### Post by dyous87 on 2007-03-27
well your main problem is you spelt aptitude wrong. you wrote it as aptitide :lolflag: 

No biggie just try again sudo **aptitude**

edit: my mistake lol.

did you try simply sudo apt-get install?

---

### Post by xelapond on 2007-03-27
ok, i tried that and here is what i get:

alex@alex-desktop:~$ sudo apt-get install lcd4linux
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libwxbase2.6-0 libopenal0a libmodplug0c2 libsdl-mixer1.2 kdesvn-kio-plugins
  libapr0 libiso9660-4 libdvbpsi4 vmware-player-kernel-modules libxosd2
  libsvn0 libalut0 libvlc0 libsdl-image1.2 libwxgtk2.6-0 libpostproc0d
  libdvdnav4 libdvdread3 libavformat0d libsdl-net1.2 libsvnqt2 libssl0.9.7
  libboost-regex1.33.1 libtar libadns1 vmware-player-kernel-modules-2.6.17-11
  plib1.8.4c2 libvcdinfo0 libmpcdec3 libmpeg2-4 libsmpeg0
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  lcd4linux
1 upgraded, 0 newly installed, 0 to remove and 113 not upgraded.
Need to get 0B/162kB of archives.
After unpacking 45.1kB of additional disk space will be used.
(Reading database ... 104883 files and directories currently installed.)
Preparing to replace lcd4linux 0.10.0+cvs20051015-2ubuntu2 (using .../lcd4linux_0.10.0+cvs20060825-1_amd64.deb) ...
Stopping lcd4linux: invoke-rc.d: initscript lcd4linux, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Stopping lcd4linux: invoke-rc.d: initscript lcd4linux, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/lcd4linux_0.10.0+cvs20060825-1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Starting lcd4linux: lcd4linux.
Errors were encountered while processing:
 /var/cache/apt/archives/lcd4linux_0.10.0+cvs20060825-1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Thanks for the help

Alex

---

### Post by dyous87 on 2007-03-27
ok so then do:

```
apt-get autoremove
```

then,

```
apt-get update
```

then, 

```
apt-get upgrade
```

then try it again

---

### Post by xelapond on 2007-03-28
Thanks again for you help, when i ran the last one, the output sauid something about an error:

alex@alex-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-headers-generic linux-image-generic linux-restricted-modules-generic
The following packages will be upgraded:
  app-install-data-commercial avahi-daemon bind9-host capplets-data dbus
  dbus-1-utils dnsutils ekiga evolution evolution-data-server
  evolution-data-server-common evolution-plugins file firefox
  firefox-gnome-support gnome-applets gnome-applets-data gnome-control-center
  gnome-netstatus-applet gnome-panel gnome-panel-data gnome-system-tools gnupg
  language-pack-en language-pack-gnome-en lcd4linux libaudio2 libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-core4 libavahi-glib1
  libbind9-0 libcamel1.2-8 libdbus-1-3 libdns21 libebook1.2-9 libecal1.2-7
  libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-7
  libedataserverui1.2-8 libegroupwise1.2-12 libexchange-storage1.2-2
  libgnome-window-settings1 libgnomevfs2-0 libgnomevfs2-bin
  libgnomevfs2-common libgnomevfs2-extra libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libgtop2-7 libgtop2-common libisc11 libisccc0 libisccfg1
  libkrb53 liblwres9 libmagic1 libmagick9 libnautilus-extension1 libnspr4
  libnss3 libpanel-applet2-0 libpoppler1 libpoppler1-glib libsmbclient
  libsoup2.2-8 libtotem-plparser1 libvolumeid0 libwpd8c2a linux-generic
  linux-restricted-modules-2.6.17-10-generic linux-restricted-modules-common
  nautilus nautilus-data openoffice.org openoffice.org-base
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-gnome openoffice.org-gtk
  openoffice.org-impress openoffice.org-java-common openoffice.org-math
  openoffice.org-style-default openoffice.org-style-industrial
  openoffice.org-writer poppler-utils popularity-contest python-uno
  samba-common slocate smbclient system-tools-backends tcpdump totem
  totem-gstreamer totem-mozilla ttf-opensymbol tzdata ubuntu-docs udev
  update-manager update-notifier vino volumeid w3m xserver-xorg-core
112 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 123MB/156MB of archives.
After unpacking 1188kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main language-pack-en 1:6.10+20070311 [436kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main openoffice.org-style-industrial 2.0.4-0ubuntu5 [3637kB]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main language-pack-en 1:6.10+20070311
  Error reading from server - read (104 Connection reset by peer)
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main libgnomevfs2-extra 2.16.1-0ubuntu7 [306kB]
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main libgnomevfs2-0 2.16.1-0ubuntu7 [657kB]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main openoffice.org-style-default 2.0.4-0ubuntu5 [3147kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main openoffice.org-calc 2.0.4-0ubuntu5 [5215kB]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main libgnomevfs2-0 2.16.1-0ubuntu7
  Error reading from server - read (104 Connection reset by peer)
Get:7 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main libvolumeid0 093-0ubuntu18.0edgy2 [67.8kB]
Get:8 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main udev 093-0ubuntu18.0edgy2 [248kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main python-uno 2.0.4-0ubuntu5 [225kB]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main openoffice.org-writer 2.0.4-0ubuntu5 [6052kB]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main udev 093-0ubuntu18.0edgy2   
  Error reading from server - read (104 Connection reset by peer)
Get:11 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main volumeid 093-0ubuntu18.0edgy2 [62.4kB]
Get:12 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main tzdata 2007b-0ubuntu0.6.10 [313kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main openoffice.org-impress 2.0.4-0ubuntu5 [644kB]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main openoffice.org-draw 2.0.4-0ubuntu5 [2332kB]
Get:15 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main popularity-contest 1.33ubuntu2.3 [49.9kB]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main openoffice.org-java-common 2.0.4-0ubuntu5 [2696kB]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main popularity-contest 1.33ubuntu2.3
  Error reading from server - read (104 Connection reset by peer)
Get:17 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main app-install-data-commercial 6.3 [13.2kB]
Get:18 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main libedataserver1.2-7 1.8.1-0ubuntu5 [127kB]
Get:19 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main libcamel1.2-8 1.8.1-0ubuntu5 [360kB]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main openoffice.org-base 2.0.4-0ubuntu5 [3597kB]
Get:21 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main libebook1.2-9 1.8.1-0ubuntu5 [143kB]
Get:22 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main libnautilus-extension1 2.16.1-0ubuntu3.2 [93.6kB]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libgtk2.0-common 2.10.6-0ubuntu3.1 [4454kB]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main libnautilus-extension1 2.16.1-0ubuntu3.2
  Error reading from server - read (104 Connection reset by peer)
Get:24 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main gnome-control-center 1:2.16.1-0ubuntu4.2 [686kB]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main openoffice.org-gtk 2.0.4-0ubuntu5 [216kB]
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main openoffice.org-gnome 2.0.4-0ubuntu5 [57.4kB]
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main openoffice.org-math 2.0.4-0ubuntu5 [321kB]
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main openoffice.org 2.0.4-0ubuntu5 [3102B]
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main ttf-opensymbol 2.0.4-0ubuntu5 [149kB]
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libaudio2 1.8-2ubuntu0.1 [76.4kB]
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main openoffice.org-core 2.0.4-0ubuntu5 [35.4MB]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main gnome-control-center 1:2.16.1-0ubuntu4.2
  Error reading from server - read (104 Connection reset by peer)
Get:32 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main libgnome-window-settings1 1:2.16.1-0ubuntu4.2 [85.5kB]
Get:33 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main capplets-data 1:2.16.1-0ubuntu4.2 [443kB]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main capplets-data 1:2.16.1-0ubuntu4.2
  Error reading from server - read (104 Connection reset by peer)
Get:34 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main libecal1.2-7 1.8.1-0ubuntu5 [317kB]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main libecal1.2-7 1.8.1-0ubuntu5 
  Error reading from server - read (104 Connection reset by peer)
Get:35 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main libedata-book1.2-2 1.8.1-0ubuntu5 [105kB]
Get:36 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main libedata-cal1.2-6 1.8.1-0ubuntu5 [117kB]
Get:37 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main libegroupwise1.2-12 1.8.1-0ubuntu5 [114kB]
Get:38 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main evolution-data-server 1.8.1-0ubuntu5 [486kB]
Get:39 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main evolution-data-server-common 1.8.1-0ubuntu5 [114kB]
Get:40 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main libedataserverui1.2-8 1.8.1-0ubuntu5 [126kB]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main libedataserverui1.2-8 1.8.1-0ubuntu5
  Error reading from server - read (104 Connection reset by peer)
Get:41 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main libexchange-storage1.2-2 1.8.1-0ubuntu5 [184kB]
Get:42 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main libpanel-applet2-0 2.16.1-0ubuntu4 [101kB]
Get:43 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main gnome-applets 2.16.1-0ubuntu4 [430kB]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main gnome-applets 2.16.1-0ubuntu4
  Error reading from server - read (104 Connection reset by peer)
Get:44 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main gnome-applets-data 2.16.1-0ubuntu4 [6122kB]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main gnome-applets-data 2.16.1-0ubuntu4
  Error reading from server - read (104 Connection reset by peer)
Get:45 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main gnome-panel 2.16.1-0ubuntu4 [531kB]
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main openoffice.org-core 2.0.4-0ubuntu5
  Connection timed out
Get:46 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main openoffice.org-common 2.0.4-0ubuntu5 [11.4MB]
Get:47 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main gnome-panel-data 2.16.1-0ubuntu4 [1243kB]
Get:48 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main gnome-netstatus-applet 2.12.0-5ubuntu7 [122kB]
Get:49 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main libgnomevfs2-bin 2.16.1-0ubuntu7 [313kB]
Get:50 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main libtotem-plparser1 2.16.2-0ubuntu3 [33.3kB]
Get:51 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libnss3 2:1.firefox2.0.0.3+0dfsg-0ubuntu0.6.10 [862kB]
Get:52 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libnspr4 2:1.firefox2.0.0.3+0dfsg-0ubuntu0.6.10 [168kB]
Get:53 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main evolution 2.8.1-0ubuntu4.1 [5341kB]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main libtotem-plparser1 2.16.2-0ubuntu3
  Error reading from server - read (104 Connection reset by peer)
Get:54 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main nautilus 2.16.1-0ubuntu3.2 [646kB]
Get:55 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main evolution-plugins 2.8.1-0ubuntu4.1 [124kB]
Get:56 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main firefox-gnome-support 2.0.0.3+0dfsg-0ubuntu0.6.10 [90.1kB]
Get:57 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main firefox 2.0.0.3+0dfsg-0ubuntu0.6.10 [10.4MB]
Get:58 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main nautilus-data 2.16.1-0ubuntu3.2 [856kB]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main nautilus-data 2.16.1-0ubuntu3.2
  Error reading from server - read (104 Connection reset by peer)
Get:59 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main gnome-system-tools 2.15.5-0ubuntu5 [2432kB]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main gnome-system-tools 2.15.5-0ubuntu5
  Error reading from server - read (104 Connection reset by peer)
Get:60 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main system-tools-backends 1.9.7-0ubuntu5 [156kB]
Get:61 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main totem-gstreamer 2.16.2-0ubuntu3 [1193kB]
Get:62 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main totem 2.16.2-0ubuntu3 [11.2kB]
Get:63 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main totem-mozilla 2.16.2-0ubuntu3 [11.0kB]
Get:64 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main ubuntu-docs 6.10.4.2 [5041kB]
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main ubuntu-docs 6.10.4.2        
  Connection timed out
Get:65 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main update-manager 0.45.2 [794kB]
Get:66 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main update-notifier 0.43.4 [56.2kB]                                                                       
Get:67 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main vino 2.16.0-0ubuntu2.4 [185kB]                                                                        
Fetched 68.6MB in 1h22m39s (13.8kB/s)                                                                                                                       
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_6.10+20070311_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_6.10+20070311_all.deb)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gnome-vfs2/libgnomevfs2-0_2.16.1-0ubuntu7_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gnome-vfs2/libgnomevfs2-0_2.16.1-0ubuntu7_amd64.deb)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_2.0.4-0ubuntu5_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_2.0.4-0ubuntu5_amd64.deb)  Connection timed out
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/u/udev/udev_093-0ubuntu18.0edgy2_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/u/udev/udev_093-0ubuntu18.0edgy2_amd64.deb)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/p/popularity-contest/popularity-contest_1.33ubuntu2.3_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/p/popularity-contest/popularity-contest_1.33ubuntu2.3_all.deb)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/libnautilus-extension1_2.16.1-0ubuntu3.2_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/libnautilus-extension1_2.16.1-0ubuntu3.2_amd64.deb)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/c/control-center/gnome-control-center_2.16.1-0ubuntu4.2_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/c/control-center/gnome-control-center_2.16.1-0ubuntu4.2_amd64.deb)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/c/control-center/capplets-data_2.16.1-0ubuntu4.2_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/c/control-center/capplets-data_2.16.1-0ubuntu4.2_all.deb)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libecal1.2-7_1.8.1-0ubuntu5_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libecal1.2-7_1.8.1-0ubuntu5_amd64.deb)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserverui1.2-8_1.8.1-0ubuntu5_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserverui1.2-8_1.8.1-0ubuntu5_amd64.deb)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gnome-applets/gnome-applets_2.16.1-0ubuntu4_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gnome-applets/gnome-applets_2.16.1-0ubuntu4_amd64.deb)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gnome-applets/gnome-applets-data_2.16.1-0ubuntu4_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gnome-applets/gnome-applets-data_2.16.1-0ubuntu4_all.deb)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/t/totem/libtotem-plparser1_2.16.2-0ubuntu3_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/t/totem/libtotem-plparser1_2.16.2-0ubuntu3_amd64.deb)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus-data_2.16.1-0ubuntu3.2_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus-data_2.16.1-0ubuntu3.2_all.deb)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gnome-system-tools/gnome-system-tools_2.15.5-0ubuntu5_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gnome-system-tools/gnome-system-tools_2.15.5-0ubuntu5_amd64.deb)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-docs/ubuntu-docs_6.10.4.2_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-docs/ubuntu-docs_6.10.4.2_all.deb)  Connection timed out
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


At this point i am completely lost, i have no idea what to do.

Thanks for you patience in helping a newbie to Ubuntu.

Alex

---

### Post by dyous87 on 2007-03-28
see what happens if you try 

```
apt-get dist-upgrade
```

---

### Post by xelapond on 2007-03-28
That command ram fine without error but the sudo aptitude install lcd4linux still does not work, here is what happened:

alex@alex-desktop:~$ sudo aptitude install lcd4linux
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be upgraded:
  lcd4linux 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/162kB of archives. After unpacking 45.1kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 122464 files and directories currently installed.)
Preparing to replace lcd4linux 0.10.0+cvs20051015-2ubuntu2 (using .../lcd4linux_0.10.0+cvs20060825-1_amd64.deb) ...
Stopping lcd4linux: invoke-rc.d: initscript lcd4linux, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Stopping lcd4linux: invoke-rc.d: initscript lcd4linux, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/lcd4linux_0.10.0+cvs20060825-1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Starting lcd4linux: lcd4linux.
Errors were encountered while processing:
 /var/cache/apt/archives/lcd4linux_0.10.0+cvs20060825-1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:


Thanks again for help!

Alex

---

### Post by dyous87 on 2007-03-30
hmm what happens if you try uninstalling  lcd4linux through apt or synaptic?

---

