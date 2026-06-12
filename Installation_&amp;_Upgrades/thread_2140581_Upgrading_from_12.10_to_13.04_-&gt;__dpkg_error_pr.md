---
title: "Upgrading from 12.10 to 13.04 -&gt;  dpkg: error processing sudo (--configure):"
date: 2013-04-30
forum: Installation &amp; Upgrades
---

### Post by desesperado on 2013-04-30
Hi, forum fellows.

Here's the deal and reason I'm asking for your help. Last night I went on upgrading my Xubuntu 12.10 installation to 13.04, so at tty1 I run the command ```
sudo do-release-upgrade
``` and everything seemed to went well except that after rebooting and when I run ```
sudo apt-get update && sudo apt-get upgrade
```, I get this error:
```
sudo apt-get update && sudo apt-get upgrade
Hit http://pt.archive.ubuntu.com raring Release.gpg
Hit http://pt.archive.ubuntu.com raring-updates Release.gpg                    
Hit http://dl.google.com stable Release.gpg                                    
Hit http://pt.archive.ubuntu.com raring-backports Release.gpg                  
Hit http://pt.archive.ubuntu.com raring Release                                
Hit http://archive.canonical.com raring Release.gpg                            
Hit http://ppa.launchpad.net raring Release.gpg                                
Hit http://pt.archive.ubuntu.com raring-updates Release                        
Hit http://extras.ubuntu.com raring Release.gpg                                
Hit http://pt.archive.ubuntu.com raring-backports Release                      
Hit http://dl.google.com stable Release                                        
Hit http://pt.archive.ubuntu.com raring/main Sources                           
Hit http://pt.archive.ubuntu.com raring/restricted Sources                     
Hit http://extras.ubuntu.com raring Release                                    
Hit http://archive.canonical.com raring Release                                
Hit http://ppa.launchpad.net raring Release.gpg                                
Hit http://pt.archive.ubuntu.com raring/universe Sources                       
Hit http://pt.archive.ubuntu.com raring/multiverse Sources                     
Hit http://dl.google.com stable/main i386 Packages                             
Get:1 http://security.ubuntu.com raring-security Release.gpg [933 B]           
Hit http://pt.archive.ubuntu.com raring/main i386 Packages                     
Hit http://extras.ubuntu.com raring/main Sources                               
Hit http://ppa.launchpad.net raring Release                                    
Hit http://archive.canonical.com raring/partner i386 Packages                  
Hit http://pt.archive.ubuntu.com raring/restricted i386 Packages               
Hit http://pt.archive.ubuntu.com raring/universe i386 Packages                 
Hit http://extras.ubuntu.com raring/main i386 Packages                         
Hit http://pt.archive.ubuntu.com raring/multiverse i386 Packages               
Hit http://ppa.launchpad.net raring Release                                    
Hit http://pt.archive.ubuntu.com raring/main Translation-en                    
Hit http://ppa.launchpad.net raring/main Sources                               
Hit http://ppa.launchpad.net raring/main i386 Packages                         
Hit http://pt.archive.ubuntu.com raring/multiverse Translation-en              
Hit http://pt.archive.ubuntu.com raring/restricted Translation-en              
Hit http://pt.archive.ubuntu.com raring/universe Translation-en                
Hit http://pt.archive.ubuntu.com raring-updates/main Sources                   
Hit http://pt.archive.ubuntu.com raring-updates/restricted Sources             
Hit http://ppa.launchpad.net raring/main Sources                               
Hit http://pt.archive.ubuntu.com raring-updates/universe Sources               
Hit http://pt.archive.ubuntu.com raring-updates/multiverse Sources             
Hit http://pt.archive.ubuntu.com raring-updates/main i386 Packages             
Hit http://ppa.launchpad.net raring/main i386 Packages                         
Hit http://pt.archive.ubuntu.com raring-updates/restricted i386 Packages       
Hit http://pt.archive.ubuntu.com raring-updates/universe i386 Packages         
Hit http://pt.archive.ubuntu.com raring-updates/multiverse i386 Packages       
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://pt.archive.ubuntu.com raring-updates/main Translation-en            
Ign http://archive.canonical.com raring/partner Translation-en_US              
Ign http://extras.ubuntu.com raring/main Translation-en_US                     
Ign http://dl.google.com stable/main Translation-en                            
Ign http://archive.canonical.com raring/partner Translation-en                 
Hit http://pt.archive.ubuntu.com raring-updates/multiverse Translation-en      
Ign http://extras.ubuntu.com raring/main Translation-en                        
Hit http://pt.archive.ubuntu.com raring-updates/restricted Translation-en      
Hit http://pt.archive.ubuntu.com raring-updates/universe Translation-en
Hit http://pt.archive.ubuntu.com raring-backports/main Sources
Hit http://pt.archive.ubuntu.com raring-backports/restricted Sources
Hit http://pt.archive.ubuntu.com raring-backports/universe Sources
Hit http://pt.archive.ubuntu.com raring-backports/multiverse Sources
Hit http://pt.archive.ubuntu.com raring-backports/main i386 Packages
Hit http://pt.archive.ubuntu.com raring-backports/restricted i386 Packages
Hit http://pt.archive.ubuntu.com raring-backports/universe i386 Packages
Hit http://pt.archive.ubuntu.com raring-backports/multiverse i386 Packages
Hit http://pt.archive.ubuntu.com raring-backports/main Translation-en
Hit http://pt.archive.ubuntu.com raring-backports/multiverse Translation-en
Get:2 http://security.ubuntu.com raring-security Release [40.8 kB]
Hit http://pt.archive.ubuntu.com raring-backports/restricted Translation-en
Hit http://pt.archive.ubuntu.com raring-backports/universe Translation-en
Ign http://ppa.launchpad.net raring/main Translation-en_US
Ign http://ppa.launchpad.net raring/main Translation-en
Get:3 http://security.ubuntu.com raring-security/main Sources [2,109 B]
Ign http://ppa.launchpad.net raring/main Translation-en_US
Ign http://ppa.launchpad.net raring/main Translation-en               
Get:4 http://security.ubuntu.com raring-security/restricted Sources [14 B]
Get:5 http://security.ubuntu.com raring-security/universe Sources [14 B]
Get:6 http://security.ubuntu.com raring-security/multiverse Sources [14 B]
Get:7 http://security.ubuntu.com raring-security/main i386 Packages [3,670 B]
Get:8 http://security.ubuntu.com raring-security/restricted i386 Packages [14 B]
Get:9 http://security.ubuntu.com raring-security/universe i386 Packages [2,824 B]
Get:10 http://security.ubuntu.com raring-security/multiverse i386 Packages [14 B]
Ign http://pt.archive.ubuntu.com raring/main Translation-en_US
Ign http://pt.archive.ubuntu.com raring/multiverse Translation-en_US
Ign http://pt.archive.ubuntu.com raring/restricted Translation-en_US
Ign http://pt.archive.ubuntu.com raring/universe Translation-en_US
Ign http://pt.archive.ubuntu.com raring-updates/main Translation-en_US
Ign http://pt.archive.ubuntu.com raring-updates/multiverse Translation-en_US
Hit http://security.ubuntu.com raring-security/main Translation-en
Ign http://pt.archive.ubuntu.com raring-updates/restricted Translation-en_US
Ign http://pt.archive.ubuntu.com raring-updates/universe Translation-en_US
Ign http://pt.archive.ubuntu.com raring-backports/main Translation-en_US
Ign http://pt.archive.ubuntu.com raring-backports/multiverse Translation-en_US
Ign http://pt.archive.ubuntu.com raring-backports/restricted Translation-en_US
Hit http://security.ubuntu.com raring-security/multiverse Translation-en
Ign http://pt.archive.ubuntu.com raring-backports/universe Translation-en_US
Hit http://security.ubuntu.com raring-security/restricted Translation-en
Hit http://security.ubuntu.com raring-security/universe Translation-en
Ign http://security.ubuntu.com raring-security/main Translation-en_US          
Ign http://security.ubuntu.com raring-security/multiverse Translation-en_US    
Ign http://security.ubuntu.com raring-security/restricted Translation-en_US    
Ign http://security.ubuntu.com raring-security/universe Translation-en_US      
Fetched 50.4 kB in 6s (7,454 B/s)                                              
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[COLOR=#ff0000]2 not fully installed or removed.
Need to get 0 B/373 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: error processing sudo (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on sudo; however:
  Package sudo is not configured yet.
[/COLOR]
[COLOR=#ff0000]dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 sudo
 ubuntu-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]
```

I've tried everything I thought logical, like ```
sudo dpkg --configure -a
dpkg: error processing sudo (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on sudo; however:
  Package sudo is not configured yet.

dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sudo
 ubuntu-minimal
```, ```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/373 kB of archives.
After this operation, 0 B of additional disk space will be used.
dpkg: error processing sudo (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on sudo; however:
  Package sudo is not configured yet.

dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            Errors were encountered while processing:
 sudo
 ubuntu-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Can someone help me, please.

---

### Post by desesperado on 2013-04-30
Here's some more info that could be of help for anyone. The output of```
 apt-cache policy linux-image-generic-pae linux-generic-pae 
``` is
```
linux-image-generic-pae:
  Installed: (none)
  Candidate: 3.8.0.19.35
  Version table:
     3.8.0.19.35 0
        500 http://pt.archive.ubuntu.com/ubuntu/ raring/main i386 Packages
linux-generic-pae:
  Installed: (none)
  Candidate: 3.8.0.19.35
  Version table:
     3.8.0.19.35 0
        500 http://pt.archive.ubuntu.com/ubuntu/ raring/main i386 Packages
```

---

### Post by slickymaster on 2013-04-30
Try to reinstall sudo. At a terminal window, run the following command:
```
sudo apt-get install --reinstall sudo
```

---

### Post by desesperado on 2013-05-01
I did that and it seems that it solved the problem with sudo, but now I get this list of dpkg warnings about missing files list file for several packages, and the list is bigger but that's the only part I was able to copy/past:

```
dpkg: warning: files list file for package 'gsfonts' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-lazr.uri' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libapt-inst1.5:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libglu1-mesa:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libevdocument3-4' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'os-prober' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcanberra-gtk3-module:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxrandr2:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libburn4' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmailtools-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'pavucontrol' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libapt-pkg-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libespeak1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libunity9:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xserver-xorg' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libindicate-gtk3' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libroken18-heimdal:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gnome-sudoku' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcloog-ppl1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'zlib1g:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libvpx1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcupsfilters1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfribidi0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libwebkitgtk-1.0-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libotr2' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libotr5' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'netcat-openbsd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpython3.3-minimal:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libio-socket-inet6-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'geoclue-ubuntu-geoip' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libhttp-cookies-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'nautilus-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-renderpm' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-aptdaemon.gtk3widgets' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmount1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gir1.2-webkit-3.0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-oauthlib' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xfce4-quicklauncher-plugin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libhx509-5-heimdal:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfont-afm-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdrm-radeon1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcap2-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnet-domain-tld-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblcms2-2:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liburi-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libclass-isa-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gnome-mines' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gcc-4.7' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsigsegv2' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ibus-pinyin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgsf-1-114' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'file' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgettextpo0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libimobiledevice3' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'tar' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtdb1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgnome-keyring-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gnome-keyring' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xchat-indicator' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gir1.2-atk-1.0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkmod2:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-pexpect' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxpm4:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-xdg' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-gi' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libthai-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'resolvconf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libppl-c4:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xfce4-screenshooter' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-libc-dev:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsnmp-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gconf2-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfile-mimeinfo-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libwnck-3-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-3.5.0-23-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgnomevfs2-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xserver-xorg-input-evdev' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtag1-vanilla:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liboil0.3:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpolkit-agent-1-0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libasprintf-dev:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'doc-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libatasmart4:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgtk2.0-0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libwww-robotrules-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgstreamer-plugins-base0.10-0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'indicator-application-gtk2' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxvmc1' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'aspell-en' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'diffutils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libva1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'printer-driver-min12xxw' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ttf-ubuntu-font-family' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'usb-modeswitch' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libthai0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libboost-serialization1.49.0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'zeitgeist' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libenchant1c2a' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'pidgin-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'software-center' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxfont1' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xserver-xorg-video-fbdev' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libapt-pkg4.12:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xserver-xorg-video-savage' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gir1.2-javascriptcoregtk-3.0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xserver-xorg-video-qxl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dbus' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgtop2-7' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libc-dev-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpython3.3:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'transmission-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'kmod' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkpathsea6' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'mountall' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxrender1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblzo2-2:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpurple-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gvfs-backends' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'hunspell-en-us' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpurple0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdpkg-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'x11-session-utils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'geoclue' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xserver-xorg-video-radeon' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libts-0.0-0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libogg0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xterm' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libusb-1.0-0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgconf2-4:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gnome-accessibility-themes' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxext6:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libglade2-0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxxf86dga1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'grub-pc-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'systemd-services' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsemanage1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ifupdown' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gstreamer0.10-gnomevfs:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xserver-xorg-input-wacom' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfontconfig1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gettext' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'obex-data-server' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libudev1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libudev0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libavahi-glib1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'avahi-autoipd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'tzdata' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xserver-xorg-video-vmware' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpam-modules:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libelfg0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'apt-transport-https' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgtkmm-2.4-1c2a:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dmidecode' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libaspell15' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libwebkitgtk-3.0-0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libwpd-0.9-9' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsepol1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpulse-mainloop-glib0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ntfs-3g' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'bzr' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'thunar' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'cups-client' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpam-xdg-support:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xserver-xorg-video-openchrome' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgoa-1.0-0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgsm1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'whiptail' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpython-stdlib:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdrm-nouveau1a:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgcr-3-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdrm2:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmagic1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gir1.2-packagekitglib-1.0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'netbase' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'shimmer-themes' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdirac-encoder0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'glib-networking:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xfce4-power-manager' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-configobj' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'bc' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgupnp-igd-1.0-4:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dnsmasq-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libk5crypto3:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'librdf0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xserver-xorg-core' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libisccfg82' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'mtr-tiny' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'accountsservice' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgrail5' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgrail6' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-oneconf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'mtools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'grub-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxres1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ubuntu-standard' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'manpages-dev' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnatpmp1' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdbus-glib-1-2:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libunistring0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'rfkill' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libprocps0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'pciutils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libopenal-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libisc83' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdigest-hmac-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libswitch-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxfce4util-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxslt1.1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'sgml-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'policykit-desktop-privileges' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdconf1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'bluez' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmtp9:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gstreamer1.0-plugins-base:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libexo-helpers' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libusbmuxd2' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'zeitgeist-core' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'apt' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'language-pack-gnome-en-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtimedate-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpython3-stdlib:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gnome-time-admin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libutempter0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'sysv-rc' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgrip0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'perl-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtelepathy-glib0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ncurses-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fonts-lklug-sinhala' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xorg' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libical0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libquadmath0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnet-ip-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgdk-pixbuf2.0-0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libglib2.0-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-gi' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'geany' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'printer-driver-hpcups' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'modemmanager' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'openssl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'language-selector-gnome' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libhttp-negotiate-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gir1.2-soup-2.4' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libwavpack1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'vim-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'bzip2' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'oneconf-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liba52-0.7.4' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnotify4:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libc6-dev:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnm-util2' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsamplerate0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxml-xpath-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'apport-gtk' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ssl-cert' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcrack2' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgudev-1.0-0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xdg-user-dirs-gtk' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fonts-tlwg-umpush' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'update-inetd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-twisted-web' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgail-3-0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'lsb-release' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xfce4-panel' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxkbfile1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblwres90' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libwacom2:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfile-basedir-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'apport-symptoms' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxss1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libflite1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libloudmouth1-0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'geany-plugin-macro' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xfce4-weather-plugin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'install-info' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gigolo' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fonts-tlwg-loma' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libwbclient0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'indicator-sound-gtk2' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgstreamer-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'aptdaemon-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgcc-4.7-dev:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'geany-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'system-config-printer-gnome' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xfce4-verve-plugin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'hicolor-icon-theme' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgdome2-cpp-smart0c2a' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcdaudio1' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-defer' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxapian22' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'colord' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'iw' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'catfish' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'sensible-utils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libwebkitgtk-3.0-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'tumbler-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-apt' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcolorhug1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'bsdutils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'perl-modules' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gir1.2-atspi-2.0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'avahi-utils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ucf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdbusmenu-glib4:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'psmisc' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgpg-error0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libavc1394-0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpython2.7:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libusb-0.1-4:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xfburn' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpci3:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'hpijs' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpam0g:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'geany-plugin-vc' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpopt0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-reportlab' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'wamerican' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ncurses-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'tcl8.5' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-zope.interface' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ubuntu-extras-keyring' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libv4l-0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'apt-xapian-index' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfuse2:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libwildmidi1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdvdread4' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-ibus' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-minimal' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'mscompress' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'scrollkeeper' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxcb-util0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgssapi-krb5-2:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libspeex1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'geany-plugin-tableconvert' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libllvm3.1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libllvm3.2:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgles2-mesa:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ibus-gtk:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-aptdaemon' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xbrlapi' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgconf-2-4:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'geany-plugin-lipsum' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dnsutils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgeoip1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'language-pack-en' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'wpasupplicant' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gstreamer0.10-nice:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'procps' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'cpp-4.7' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libjavascriptcoregtk-3.0-0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libp11-kit-gnome-keyring:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'printer-driver-hpijs' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libparted0debian1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsoup-gnome2.4-1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fontconfig' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gnome-settings-daemon' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcurl3-gnutls:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'lsb-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsoup2.4-1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtasn1-3:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgd2-xpm:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libspandsp2' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgcr-3-1' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgtop2-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libuuid1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'screensaver-default-images' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxinerama1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsdl1.2debian:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libwebkitgtk-1.0-0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'locate' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'isc-dhcp-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libwildmidi-config' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libbind9-80' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnet-http-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xserver-xorg-video-sis' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-3.5.0-24-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-dbus' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xcursor-themes' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libframe6:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libjs-jquery' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgcrypt11:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtie-ixhash-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libavcodec53:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libexif12:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgdbm3:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'pulseaudio-utils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libhtml-format-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xfce4-indicator-plugin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fonts-liberation' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcairo2:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'sound-theme-freedesktop' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-image-3.5.0-25-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'geany-plugin-webhelper' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'man-db' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libffi6:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpango-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libenca0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'module-init-tools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libflac8:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gettext-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libvorbisfile3:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'geany-plugin-gproject' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libperl5.14' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gnome-user-guide' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdbus-1-3:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libzvbi-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'cups-ppdc' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xscreensaver-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libssl1.0.0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'desktop-file-utils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-dbus' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gpgv' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'login' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'telnet' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'x11-xkb-utils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfarstream-0.1-0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gstreamer0.10-plugins-base-apps' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxml2:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'laptop-detect' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'makedev' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'initramfs-tools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'plymouth-theme-xubuntu-logo' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-twisted-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'menu' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gdb' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxmuu1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libclass-accessor-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgtk2-trayicon-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxml-parser-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxcb-shm0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'pulseaudio-module-x11' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'openprinting-ppds' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fonts-tlwg-typo' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsysfs2:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'printer-driver-pxljr' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'debianutils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfreetype6:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-aptdaemon.gtk3widgets' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsane:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmtp-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'coreutils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xfce4-cpugraph-plugin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsane-hpaio' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnl-3-200:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libevview3-3' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gvfs-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgl1-mesa-dri:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libjavascriptcoregtk-1.0-0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpoppler28:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxdmcp6:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libt1-5' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'shared-mime-info' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libots0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libraw1394-11:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'link-grammar-dictionaries-en' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpam-cap:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpolkit-gobject-1-0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-six' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgtk-3-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ibus-gtk3:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libart-2.0-2:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libatspi2.0-0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsocket6-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dash' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'memtest86+' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libelf1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libasprintf0c2:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gtk2-engines-murrine:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-aptdaemon' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xserver-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpth20' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'debconf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgnomekbd8' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libhttp-date-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libjson-glib-1.0-0:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgssdp-1.0-3' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fonts-tlwg-waree' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fonts-kacst' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ubuntu-restricted-addons' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgmpxx4ldbl:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xfdesktop4' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-lxml' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-imaging-compat' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libustr-1.0-1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fonts-freefont-ttf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'sane-utils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtext-wrapi18n-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfftw3-3:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnotify-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-aptdaemon.pkcompat' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'tcpd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-pkg-resources' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgtkspell0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ubuntu-release-upgrader-gtk' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xserver-xorg-input-vmmouse' missing; assuming package has no files currently installed
(Reading database ... 121 files and directories currently installed.)
Preparing to replace sudo 1.8.6p3-0ubuntu3 (using .../sudo_1.8.6p3-0ubuntu3_i386.deb) ...
Unpacking replacement sudo ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up sudo (1.8.6p3-0ubuntu3) ...
```

I think that all this missing information is crucial for smooth operating of package installation and updates. Is it possible to solve this and recover my system?

---

### Post by desesperado on 2013-05-02
Please help!!!!!! :frown: ](*,)

---

### Post by alan9800 on 2013-05-02
as explained [here](https://sites.google.com/site/easylinuxtipsproject/upgrade#TOC-Avoid-the-upgrade-button-), it is preferable to do a clean installation instead of using the upgrade button or the equivalent command in the terminal.

---

### Post by desesperado on 2013-05-02
Yeah, but now the damage is done.

Thing is, does this problem with the dozens of [COLOR=#000000]dpkg warnings about missing files list file for several packages[/COLOR] be fixed?

---

### Post by alan9800 on 2013-05-02
does that list of errors have appeared after that you have again run```
sudo apt-get install -f
```after to have reinstalled sudo? Or after what else?

---

### Post by desesperado on 2013-05-02
It appeared after running ```
sudo apt-get install --reinstall sudo
```. When I reinstalled sudo, the problem I initially had with it and with ubuntu-minimal disappeared.
But then, I run ```
sudo apt-get autoremove
``` and that was when that huge list appeared. I know that it shows that I lost the contents of some files used by the package management system (in the directory /var/lib/dpkg and its subdirectories).What I don't know is if it's fixable without having to reinstall.

---

### Post by alan9800 on 2013-05-02
now that you've reinstalled sudo, what happens if you try to run again```
sudo apt-get install -f
```:?:

---

### Post by desesperado on 2013-05-02
Nothing happens:

```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded
```

The same if I run ```
sudo dpkg --configure -a
```

And stuck at this.

---

