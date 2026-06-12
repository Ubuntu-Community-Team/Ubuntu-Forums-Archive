---
title: "Problem upgrading to 14"
date: 2014-04-27
forum: Installation &amp; Upgrades
---

### Post by srharri9 on 2014-04-27
I upgraded my system as soon as I could a couple days ago.  After nearly an hour of progress on the install, it stopped and I got a message saying something along the lines of the upgrade was not successful.  I regret that I did not take a screenshot or write the entire thing down.  When I go to "details", it shows that I'm running 14.04.  

I haven't seen a single difference, there aren't any new wallpapers (which I always look forward to seeing in new versions lol), and when I turn my computer on, I get two or three "system error detected" pop ups.  

I'd really like to not have to completely start over, but I don't see any other options.  Ideas?

---

### Post by Bashing-om on 2014-04-27
srharri9; Hello,

Unhappy system is an unhappy user !

Try this sequence to stabilize the packages and the manager:
```

sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a

``` Hopefully all runs clean, if errors are reported, post them back here and we will see what is to be done.

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by srharri9 on 2014-04-27
Thanks for the suggestion.

Ok, so I did all the steps.  On 3 or 4 of them, i received errors. 

I'm going to apologize in advance.  I don't know what you're looking for here, so I just copied and pasted the entire thing.  

```
Building dependency tree       
Reading state information... Done
Del libcurl3 7.32.0-1ubuntu1.4 [198 kB]
Del libssl1.0.0 1.0.1e-3ubuntu1.2 [993 kB]
Del ssh-askpass-gnome 1:6.2p2-6ubuntu0.3 [14.4 kB]
Del libcurl3-gnutls 7.32.0-1ubuntu1.4 [189 kB]
Del python-imaging 1.1.7+2.0.0-1ubuntu1.1 [347 kB]
Del libapt-pkg4.12 0.9.9.1~ubuntu3.1 [825 kB]
Del curl 7.32.0-1ubuntu1.4 [128 kB]
Del apt 0.9.9.1~ubuntu3.1 [1,239 kB]
Del flashplugin-installer 11.2.202.350ubuntu0.13.10.1 [6,932 B]
Del libsnmp30 5.7.2~dfsg-8ubuntu1.1 [1,322 kB]
Del apt-utils 0.9.9.1~ubuntu3.1 [196 kB]
Del openssh-client 1:6.2p2-6ubuntu0.3 [489 kB]
Del python-imaging-compat 1.1.7+2.0.0-1ubuntu1.1 [5,410 B]
Del file 5.11-2ubuntu4.2 [18.4 kB]
Del libmagic1 5.11-2ubuntu4.2 [170 kB]
Del python-imaging-tk 1.1.7+2.0.0-1ubuntu1.1 [8,156 B]
Del libsnmp-base 5.7.2~dfsg-8ubuntu1.1 [235 kB]
Del libapt-inst1.5 0.9.9.1~ubuntu3.1 [72.2 kB]
Del libyaml-0-2 0.1.4-2ubuntu0.13.10.3 [56.6 kB]
Del apt-transport-https 0.9.9.1~ubuntu3.1 [16.6 kB]
Del xserver-xorg-video-openchrome 1:0.3.1-0ubuntu2.2 [176 kB]
Del openssl 1.0.1e-3ubuntu1.2 [525 kB]
Del libssl1.0.0 1.0.1e-3ubuntu1.2 [1,050 kB]
Del libcurl3-nss 7.32.0-1ubuntu1.4 [195 kB]
seth@Seth:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  blt libamd2.2.0 libboost-date-time1.53.0 libboost-filesystem1.53.0
  libboost-iostreams1.53.0 libboost-program-options1.53.0
  libboost-random1.53.0 libboost-regex1.53.0 libboost-system1.53.0
  libboost-thread1.53.0 libcmis-0.3-3 libcolamd2.7.1 libdb5.1:i386
  libdee-qt5-3 libdns99 libebackend-1.2-6 libebml3 libedata-book-1.2-17
  libedata-cal-1.2-20 libfftw3-3 libfftw3-long3 libfm-gtk-bin libfm-gtk3
  libfm3 libgweather-3-3 libhud-client2 libjpeg-progs libjpeg-turbo-progs
  liblcms1:i386 libllvm3.3 libllvm3.3:i386 libmatroska5 libmjpegutils-2.0-0
  libmpeg2encpp-2.0-0 libmplex2-2.0-0 libpoppler43 libppl12 libpthread-stubs0
  libpython3.3 libpython3.3-minimal libpython3.3-stdlib libqpdf10 libqt53d5
  libqt5location5 libqt5v8-5 librhythmbox-core7 libtasn1-3:i386 libtcl8.4
  libtcl8.5 libtk8.4 libtk8.5 libumfpack5.4.0 libwebp4 libxcb-sync0
  linux-image-3.11.0-12-generic linux-image-extra-3.11.0-12-generic
  nvidia-common openbox-themes openjdk-7-jre-lib python-imaging-compat
  python-xkit python3.3 python3.3-minimal tcl8.4 tcl8.5 tk8.4 tk8.5
  wine-gecko1.4 wine-gecko1.4:i386 wine1.4-amd64 wine1.4-i386:i386
  xscreensaver-data
0 upgraded, 0 newly installed, 72 to remove and 1 not upgraded.
2 not fully installed or removed.
After this operation, 331 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 269049 files and directories currently installed.)
Removing blt (2.4z-7ubuntu2) ...
Removing libumfpack5.4.0 (1:3.4.0-3ubuntu1) ...
Removing libamd2.2.0 (1:3.4.0-3ubuntu1) ...
Removing libcmis-0.3-3 (0.3.1-3ubuntu1) ...
Removing libboost-date-time1.53.0:amd64 (1.53.0-6+exp3ubuntu8) ...
Removing libboost-filesystem1.53.0:amd64 (1.53.0-6+exp3ubuntu8) ...
Removing libboost-iostreams1.53.0:amd64 (1.53.0-6+exp3ubuntu8) ...
Removing libboost-program-options1.53.0:amd64 (1.53.0-6+exp3ubuntu8) ...
Removing libboost-random1.53.0:amd64 (1.53.0-6+exp3ubuntu8) ...
Removing libboost-regex1.53.0:amd64 (1.53.0-6+exp3ubuntu8) ...
Removing libboost-thread1.53.0:amd64 (1.53.0-6+exp3ubuntu8) ...
Removing libboost-system1.53.0:amd64 (1.53.0-6+exp3ubuntu8) ...
Removing libcolamd2.7.1 (1:3.4.0-3ubuntu1) ...
Removing libdb5.1:i386 (5.1.29-7ubuntu1) ...
Removing libhud-client2:amd64 (13.10.1+14.04.20140402-0ubuntu1) ...
Removing libdee-qt5-3:amd64 (3.3+14.04.20140317-0ubuntu1) ...
Removing libdns99 (1:9.9.3.dfsg.P2-4ubuntu1.1) ...
Removing libedata-book-1.2-17 (3.8.5-1ubuntu3) ...
Removing libedata-cal-1.2-20 (3.8.5-1ubuntu3) ...
Removing libebackend-1.2-6 (3.8.5-1ubuntu3) ...
Removing libmatroska5:amd64 (1.3.0-2) ...
Removing libebml3:amd64 (1.2.2-2) ...
Removing libfftw3-3:amd64 (3.3.3-7ubuntu3) ...
Removing libfftw3-long3:amd64 (3.3.3-7ubuntu3) ...
Removing libfm-gtk-bin (1.1.2-0ubuntu1) ...
Removing libfm-gtk3 (1.1.2-0ubuntu1) ...
Removing libfm3 (1.1.2-0ubuntu1) ...
Removing libgweather-3-3 (3.8.2-0ubuntu1) ...
Removing libjpeg-progs (8c-2ubuntu8) ...
Removing libjpeg-turbo-progs (1.3.0-0ubuntu2) ...
Removing liblcms1:i386 (1.19.dfsg-1.2ubuntu5) ...
Removing libllvm3.3:amd64 (1:3.3-16ubuntu1) ...
Removing libllvm3.3:i386 (1:3.3-16ubuntu1) ...
Removing libmplex2-2.0-0 (1:2.0.0+debian-2ubuntu1) ...
Removing libmpeg2encpp-2.0-0 (1:2.0.0+debian-2ubuntu1) ...
Removing libmjpegutils-2.0-0 (1:2.0.0+debian-2ubuntu1) ...
Removing libpoppler43:amd64 (0.24.1-0ubuntu1) ...
Removing libppl12:amd64 (1:1.0-7ubuntu1) ...
Removing libpthread-stubs0:amd64 (0.3-3) ...
Removing libpython3.3:amd64 (3.3.2-7ubuntu3.1) ...
Removing python3.3 (3.3.2-7ubuntu3.1) ...
Removing python3.3-minimal (3.3.2-7ubuntu3.1) ...
Unlinking and removing bytecode for runtime python3.3
Removing libpython3.3-stdlib:amd64 (3.3.2-7ubuntu3.1) ...
dpkg-query: no packages found matching pkgname
Removing libpython3.3-minimal:amd64 (3.3.2-7ubuntu3.1) ...
dpkg-query: no packages found matching pkgname
Removing libqpdf10:amd64 (4.2.0-2) ...
Removing libqt5location5:amd64 (5.2.1-1ubuntu2) ...
Removing libqt53d5:amd64 (5.0~git20130731-0ubuntu5) ...
Removing libqt5v8-5:amd64 (5.0.2-3) ...
Removing librhythmbox-core7 (2.99.1-0ubuntu1) ...
Removing libtasn1-3:i386 (2.14-3) ...
Removing tk8.4 (8.4.20-7) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/bin/wish8.5 because link group wish is broken
Removing tcl8.4 (8.4.20-7) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/bin/tclsh8.5 because link group tclsh is broken
Removing tk8.5 (8.5.15-2ubuntu3) ...
Removing tcl8.5 (8.5.15-2ubuntu1) ...
Removing libtk8.4:amd64 (8.4.20-7) ...
Removing libtk8.5:amd64 (8.5.15-2ubuntu3) ...
Removing libwebp4:amd64 (0.3.0-3) ...
Removing libxcb-sync0:amd64 (1.9.1-3ubuntu1) ...
Removing linux-image-extra-3.11.0-12-generic (3.11.0-12.19) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.11.0-12-generic /boot/vmlinuz-3.11.0-12-generic
update-initramfs: Deleting /boot/initrd.img-3.11.0-12-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.11.0-12-generic /boot/vmlinuz-3.11.0-12-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found linux image: /boot/vmlinuz-3.11.0-19-generic
Found initrd image: /boot/initrd.img-3.11.0-19-generic
Found linux image: /boot/vmlinuz-3.11.0-18-generic
Found initrd image: /boot/initrd.img-3.11.0-18-generic
Found linux image: /boot/vmlinuz-3.11.0-17-generic
Found initrd image: /boot/initrd.img-3.11.0-17-generic
Found linux image: /boot/vmlinuz-3.11.0-15-generic
Found initrd image: /boot/initrd.img-3.11.0-15-generic
Found linux image: /boot/vmlinuz-3.11.0-14-generic
Found initrd image: /boot/initrd.img-3.11.0-14-generic
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
Found linux image: /boot/vmlinuz-3.11.0-12-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.5.0-30-generic
Found initrd image: /boot/initrd.img-3.5.0-30-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Removing linux-image-3.11.0-12-generic (3.11.0-12.19) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.11.0-12-generic /boot/vmlinuz-3.11.0-12-generic
update-initramfs: Deleting /boot/initrd.img-3.11.0-12-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.11.0-12-generic /boot/vmlinuz-3.11.0-12-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found linux image: /boot/vmlinuz-3.11.0-19-generic
Found initrd image: /boot/initrd.img-3.11.0-19-generic
Found linux image: /boot/vmlinuz-3.11.0-18-generic
Found initrd image: /boot/initrd.img-3.11.0-18-generic
Found linux image: /boot/vmlinuz-3.11.0-17-generic
Found initrd image: /boot/initrd.img-3.11.0-17-generic
Found linux image: /boot/vmlinuz-3.11.0-15-generic
Found initrd image: /boot/initrd.img-3.11.0-15-generic
Found linux image: /boot/vmlinuz-3.11.0-14-generic
Found initrd image: /boot/initrd.img-3.11.0-14-generic
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.5.0-30-generic
Found initrd image: /boot/initrd.img-3.5.0-30-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Removing nvidia-common (1:0.2.91.4) ...
Removing openbox-themes (1.0.2) ...
Removing openjdk-7-jre-lib (7u51-2.4.6-1ubuntu4) ...
Removing python-imaging-compat (2.3.0-1ubuntu3) ...
Removing python-xkit (0.5.0ubuntu2) ...
Removing wine-gecko1.4:amd64 (1.4.0-0ubuntu2) ...
Removing wine-gecko1.4:i386 (1.4.0-0ubuntu2) ...
Removing wine1.4-amd64 (1:1.6.2-0ubuntu4) ...
Removing wine1.4-i386 (1:1.6.2-0ubuntu4) ...
Removing xscreensaver-data (5.15-3ubuntu1) ...
Removing libtcl8.4:amd64 (8.4.20-7) ...
Removing libtcl8.5:amd64 (8.5.15-2ubuntu1) ...
Processing triggers for doc-base (0.10.5) ...
Processing 1 removed doc-base file...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for menu (2.1.46ubuntu1) ...
Setting up eternallands-data (1.9.3-0ubuntu1) ...
el_linux_193.zip: FAILED
md5sum: WARNING: 1 computed checksum did NOT match
rm: invalid option -- 'z'
Try 'rm --help' for more information.
[/var/cache/eternallands/el_linux_193.zip]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of /var/cache/eternallands/el_linux_193.zip or
        /var/cache/eternallands/el_linux_193.zip.zip, and cannot find /var/cache/eternallands/el_linux_193.zip.ZIP, period.
dpkg: error processing package eternallands-data (--configure):
 subprocess installed post-installation script returned error exit status 9
dpkg: dependency problems prevent configuration of eternallands-sound:
 eternallands-sound depends on eternallands-data (>= 1.9.2) | eternallands-rc-data (>= 1.9.2); however:
  Package eternallands-data is not configured yet.
  Package eternallands-rc-data is not installed.

```

```
dpkg: error processing package eternallands-sound (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 eternallands-data
 eternallands-sound
E: Sub-process /usr/bin/dpkg returned an error code (1)
seth@Seth:~$ sudo apt-get clean
seth@Seth:~$ sudo apt-get update
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                                              
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease                                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                              
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                                          
Hit [http://dl.google.com](http://dl.google.com) stable Release                                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release                                                
Hit [http://dl.google.com](http://dl.google.com) stable Release                                                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                                                   
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources                                           
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                         
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg [933 B]                      
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg                                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                                                      
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                                               
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                                        
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                                               
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                                        
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release [58.5 kB]                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources                                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release                                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages                       
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages                     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages                                 
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe amd64 Packages                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse amd64 Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US            
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages        
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [6,548 B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [14 B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [1,687 B]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [1,790 B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages [14.0 kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en_US  
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [14 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en_US
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe amd64 Packages [4,133 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en_US
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [6,362 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en_US
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [12.7 kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [14 B]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [4,166 B]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [6,386 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main amd64 Packages                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted amd64 Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe amd64 Packages                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en_US
Fetched 117 kB in 13s (8,471 B/s)
Reading package lists... Done
seth@Seth:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  bash
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 575 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main bash amd64 4.3-7ubuntu1 [575 kB]
Fetched 575 kB in 1s (338 kB/s)
(Reading database ... 261056 files and directories currently installed.)
Preparing to unpack .../bash_4.3-7ubuntu1_amd64.deb ...
Unpacking bash (4.3-7ubuntu1) over (4.3-6ubuntu1) ...
Processing triggers for menu (2.1.46ubuntu1) ...
Processing triggers for install-info (5.2.0.dfsg.1-2) ...
Processing triggers for man-db (2.6.7.1-1) ...
Setting up bash (4.3-7ubuntu1) ...
update-alternatives: using /usr/share/man/man7/bash-builtins.7.gz to provide /usr/share/man/man7/builtins.7.gz (builtins.7.gz) in auto mode
Setting up eternallands-data (1.9.3-0ubuntu1) ...
el_linux_193.zip: FAILED
md5sum: WARNING: 1 computed checksum did NOT match
rm: invalid option -- 'z'
Try 'rm --help' for more information.
[/var/cache/eternallands/el_linux_193.zip]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of /var/cache/eternallands/el_linux_193.zip or
        /var/cache/eternallands/el_linux_193.zip.zip, and cannot find /var/cache/eternallands/el_linux_193.zip.ZIP, period.
dpkg: error processing package eternallands-data (--configure):
 subprocess installed post-installation script returned error exit status 9
dpkg: dependency problems prevent configuration of eternallands-sound:
 eternallands-sound depends on eternallands-data (>= 1.9.2) | eternallands-rc-data (>= 1.9.2); however:
  Package eternallands-data is not configured yet.
  Package eternallands-rc-data is not installed.


```
```
dpkg: error processing package eternallands-sound (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
   Processing triggers for menu (2.1.46ubuntu1) ...
Errors were encountered while processing:
 eternallands-data
 eternallands-sound
E: Sub-process /usr/bin/dpkg returned an error code (1)
seth@Seth:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up eternallands-data (1.9.3-0ubuntu1) ...
el_linux_193.zip: FAILED
md5sum: WARNING: 1 computed checksum did NOT match
rm: invalid option -- 'z'
Try 'rm --help' for more information.
[/var/cache/eternallands/el_linux_193.zip]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of /var/cache/eternallands/el_linux_193.zip or
        /var/cache/eternallands/el_linux_193.zip.zip, and cannot find /var/cache/eternallands/el_linux_193.zip.ZIP, period.
No apport report written because the error message indicates its a followup error from a previous failure.
   dpkg: error processing package eternallands-data (--configure):
 subprocess installed post-installation script returned error exit status 9
dpkg: dependency problems prevent configuration of eternallands-sound:
 eternallands-sound depends on eternallands-data (>= 1.9.2) | eternallands-rc-data (>= 1.9.2); however:
  Package eternallands-data is not configured yet.
  Package eternallands-rc-data is not installed.

```

```
dpkg: error processing package eternallands-sound (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 eternallands-data
 eternallands-sound
E: Sub-process /usr/bin/dpkg returned an error code (1)
seth@Seth:~$ sudo apt-get -f install
[sudo] password for seth: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up eternallands-data (1.9.3-0ubuntu1) ...
el_linux_193.zip: FAILED
md5sum: WARNING: 1 computed checksum did NOT match
rm: invalid option -- 'z'
Try 'rm --help' for more information.
[/var/cache/eternallands/el_linux_193.zip]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of /var/cache/eternallands/el_linux_193.zip or
        /var/cache/eternallands/el_linux_193.zip.zip, and cannot find /var/cache/eternallands/el_linux_193.zip.ZIP, period.
dpkg: error processing package eternallands-data (--configure):
 subprocess installed post-installation script returned error exit status 9
dpkg: dependency problems prevent configuration of eternallands-sound:
 eternallands-sound depends on eternallands-data (>= 1.9.2) | eternallands-rc-data (>= 1.9.2); however:
  Package eternallands-data is not configured yet.
  Package eternallands-rc-data is not installed.


dpkg: error processing package eternallands-sound (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
   Errors were encountered while processing:
 eternallands-data
 eternallands-sound
E: Sub-process /usr/bin/dpkg returned an error code (1)
seth@Seth:~$ sudo dpkg --configure -a
Setting up eternallands-data (1.9.3-0ubuntu1) ...
el_linux_193.zip: FAILED
md5sum: WARNING: 1 computed checksum did NOT match
rm: invalid option -- 'z'
Try 'rm --help' for more information.
[/var/cache/eternallands/el_linux_193.zip]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of /var/cache/eternallands/el_linux_193.zip or
        /var/cache/eternallands/el_linux_193.zip.zip, and cannot find /var/cache/eternallands/el_linux_193.zip.ZIP, period.
dpkg: error processing package eternallands-data (--configure):
 subprocess installed post-installation script returned error exit status 9
dpkg: dependency problems prevent configuration of eternallands-sound:
 eternallands-sound depends on eternallands-data (>= 1.9.2) | eternallands-rc-data (>= 1.9.2); however:
  Package eternallands-data is not configured yet.
  Package eternallands-rc-data is not installed.

```

```
dpkg: error processing package eternallands-sound (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 eternallands-data
 eternallands-sound
seth@Seth:~$ ^C
seth@Seth:~$
```

---

### Post by oldfred on 2014-04-28
Please use code tags on long text output.

I am not familial with this:
 Errors were encountered while processing:
 eternallands-data
 eternallands-sound

Try 'rm --help' for more information. 
[/var/cache/eternallands/el_linux_193.zip] 


But I do not find eterallands in synaptic, so is this from one of the google ppa?

Almost invariably the errors on upgrades are where users do not turn off all ppas and remove proprietary drivers. Then they can add those again after upgrade. But many times the ppa does not exist for the new version and causes an issue.

You may need to manually edit out zip file in /var/cache. Backup if you think you may need it later.


 # Edit Sources
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
gksu gedit /etc/apt/sources.list

Also check /etc/apt/sources.list.d for ppa.

---

