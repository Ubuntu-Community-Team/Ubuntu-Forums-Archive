---
title: "dapper server and x-windows-system-core?"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by patricksmith on 2006-06-03
Hi,

I just did a fresh install of the 6.06 LAMP server and would like to install x-windows.

On my 5.10 box, doing 'apt-get install x-windows-system-core' worked like a champ.

But on 6.06, I'm getting the error 'Couldn't find package x-windows-system-core'

I uncommented the universal servers in my /etc/apt/sources.list, along with the other dapper servers, and still get the same message.

Is there another package I should install?

thanks,
Patrick

---

### Post by llamakc on 2006-06-03
ken@vulva:~$ apt-cache show x-window-system-core
Package: x-window-system-core
Priority: optional
Section: x11
Installed-Size: 36
Maintainer: Ubuntu X Maintainers <ubuntu-devel@lists.ubuntu.com>
Architecture: i386
Source: xorg
Version: 7.0.0-0ubuntu45
Depends: xserver-xorg, libgl1-mesa, libgl1-mesa-dri, libglu1-mesa, xfonts-base, xfonts-100dpi, xfonts-75dpi, xfonts-scalable, xbase-clients, xutils, xkeyboard-config
Filename: pool/main/x/xorg/x-window-system-core_7.0.0-0ubuntu45_i386.deb
Size: 9180
MD5sum: 2eb3b7ac5c5e5004d2f19868947e17e4
Description: X Window System core components
 This metapackage provides the essential components for a standalone
 workstation running the X Window System.  It provides the X libraries, an X
 server, a set of fonts, and a group of basic X clients and utilities.
 .
 Higher level metapackages, such as those for desktop environments, can
 depend on this package and simplify their dependencies.
 .
 It should be noted that a package providing x-window-manager and a package
 providing x-terminal-emulator should also be installed to ensure a
 comfortable X experience.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-desktop, kubuntu-desktop, edubuntu-desktop, xubuntu-desktop



I think you just added the "s" to window and that was the problem.

---

### Post by ubuntu_demon on 2006-06-04
You also need to install xserver-xorg and some other packages. I don't know which graphical environment you wish. There are lots of options. An example of a light and easy one is icewm. 

examples :
$sudo apt-get install xserver-xorg x-window-system-core icewm xdm
$sudo apt-get install xserver-xorg x-window-system-core icewm wdm
$sudo apt-get install xserver-xorg x-window-system-core xfce4 xfwm4
this one installs xubuntu which is xfce4 + good looks + a lot of programs :
$sudo apt-get install xserver-xorg x-window-system-core xubuntu-desktop

to find some packages related to icewm :
$apt-cache search icewm

to find some packages related to xfce4 :
$apt-cache search xfce4

---

