---
title: "No Screensfound after update from 9.3 to 10.4 Ubuntu"
date: 2011-06-01
forum: Installation &amp; Upgrades
---

### Post by void_void on 2011-06-01
Hello,

Recently I updated ubuntu from 9.3 to 10.04. and found that xorg's newer version of inter driver is no longer supported. causes `No Screen Found error`

So trying to move back to previous version of driver. 
Downloaded previous version (the one comes with 9.3) from [here][1],

also installed it using 

    sudo aptitude install xserver-xorg-video-intel=2:2.6.3-0ubuntu9.3

but still


    X.Org X Server 1.7.6
    Release Date: 2010-03-17
    X Protocol Version 11, Revision 0
    Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
    Current Operating System: Linux ArguSoft-Apps-Linux 2.6.28-19-server #66-Ubuntu SMP Sat Oct 16 18:41:24 UTC 2010 i686
    Kernel command line: root=UUID=8bf4ec8b-ac33-465c-806e-4c95c38e6d59 ro  single
    Build Date: 08 March 2011  08:22:50AM
    xorg-server 2:1.7.6-2ubuntu7.6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
    Current version of pixman: 0.16.4
            Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
            to make sure that you have the latest version.
    Markers: (--) probed, (**) from config file, (==) default setting,
            (++) from command line, (!!) notice, (II) informational,
            (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
    (==) Log file: "/var/log/Xorg.0.log", Time: Tue May 31 23:29:57 2011
    (==) Using config file: "/etc/X11/xorg.conf"
    (==) Using config directory: "/usr/lib/X11/xorg.conf.d"
    (EE) open /dev/fb0: No such file or directory
    (EE) intel(0): [drm] Failed to open DRM device for pci:0000:00:02.0: No such file or directory
    (EE) intel(0): Failed to become DRM master.
    (EE) intel(0): No valid modes.
    (EE) Screen(s) found, but none have a usable configuration.
    
    Fatal server error:
    no screens found
    
    Please consult the The X.Org Foundation support


downgrading shows:

    Selecting previously deselected package xserver-xorg-video-intel.
    dpkg: regarding 1xserver-xorg-video-intel_2.2.1-1ubuntu12_i386.deb containing xserver-xorg-video-intel:
     xserver-xorg-core conflicts with xserver-xorg-video-2
      xserver-xorg-video-intel provides xserver-xorg-video-2 and is to be installed.
    dpkg: error processing 1xserver-xorg-video-intel_2.2.1-1ubuntu12_i386.deb (--install):
     conflicting packages - not installing xserver-xorg-video-intel
    Errors were encountered while processing:
     1xserver-xorg-video-intel_2.2.1-1ubuntu12_i386.deb


  [1]: [https://launchpad.net/ubuntu/+source/xserver-xorg-video-intel/2:2.6.3-0ubuntu9.3](https://launchpad.net/ubuntu/+source/xserver-xorg-video-intel/2:2.6.3-0ubuntu9.3)

---

