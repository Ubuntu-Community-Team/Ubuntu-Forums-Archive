---
title: "Firefox and update bugs."
date: 2006-12-13
forum: Installation &amp; Upgrades
---

### Post by Refined Power on 2006-12-13
Hi, I am having problems trying to install plugins for firefox 2.0 I have tried using automatix2 and synaptec, but Firefox does not recognize the plugins i.e. when I type about;plugins nothing is shown. I have tried following several tutorials and have searched the net with no success. 

Also there seems to be problems with update manager since I get this when I try and update:

W: Failed to fetch [http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/libdivxdecore0_1:5.0.1-1_i386.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/libdivxdecore0_1:5.0.1-1_i386.deb)
  The HTTP server sent an invalid reply header


W: Failed to fetch [http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/libdivxencore0_1:5.0.1-1_i386.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/libdivxencore0_1:5.0.1-1_i386.deb)
  Bad header line


W: Failed to fetch [http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/mplayer_0.99+1.0-pre8-0ubuntu4_i386.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/mplayer_0.99+1.0-pre8-0ubuntu4_i386.deb)
  The HTTP server sent an invalid reply header


W: Failed to fetch [http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/mozilla-mplayer_3.31-3v1ubuntu2_i386.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/mozilla-mplayer_3.31-3v1ubuntu2_i386.deb)
  Bad header line


W: Failed to fetch [http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/xserver-xorg-input-synaptics_0.14.6-3v1ubuntu0_i386.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/xserver-xorg-input-synaptics_0.14.6-3v1ubuntu0_i386.deb)
  The HTTP server sent an invalid reply header


W: Failed to fetch [http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/mencoder_0.99+1.0-pre8-0ubuntu4_i386.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/mencoder_0.99+1.0-pre8-0ubuntu4_i386.deb)
  Bad header line

Any suggestions? I really do not know what to do. I get this when I put "sudo apt-get dist-upgrade" in the terminal

sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  libdivxdecore0 libdivxencore0
The following packages have been kept back:
  wpasupplicant
The following packages will be upgraded:
  mencoder mozilla-mplayer mplayer xserver-xorg-input-synaptics
4 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 12.2MB of archives.
After unpacking 16.1MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper/3v1n0 libdivxdecore0 1:5.0.1-1
  The HTTP server sent an invalid reply header
Err [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper/3v1n0 libdivxencore0 1:5.0.1-1
  Bad header line
Err [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper/3v1n0 mplayer 2:0.99+1.0-pre8-0ubuntu4
  The HTTP server sent an invalid reply header
Err [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper/3v1n0 mozilla-mplayer 3.31-3v1ubuntu2
  Bad header line
Err [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper/3v1n0 xserver-xorg-input-synaptics 0.14.6-3v1ubuntu0
  The HTTP server sent an invalid reply header
Err [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper/3v1n0 mencoder 2:0.99+1.0-pre8-0ubuntu4
  Bad header line
Failed to fetch [http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/libdivxdecore0_1:5.0.1-1_i386.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/libdivxdecore0_1:5.0.1-1_i386.deb)  The HTTP server sent an invalid reply header
Failed to fetch [http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/libdivxencore0_1:5.0.1-1_i386.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/libdivxencore0_1:5.0.1-1_i386.deb)  Bad header line
Failed to fetch [http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/mplayer_0.99+1.0-pre8-0ubuntu4_i386.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/mplayer_0.99+1.0-pre8-0ubuntu4_i386.deb)  The HTTP server sent an invalid reply header
Failed to fetch [http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/mozilla-mplayer_3.31-3v1ubuntu2_i386.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/mozilla-mplayer_3.31-3v1ubuntu2_i386.deb)  Bad header line
Failed to fetch [http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/xserver-xorg-input-synaptics_0.14.6-3v1ubuntu0_i386.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/xserver-xorg-input-synaptics_0.14.6-3v1ubuntu0_i386.deb)  The HTTP server sent an invalid reply header
Failed to fetch [http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/mencoder_0.99+1.0-pre8-0ubuntu4_i386.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/mencoder_0.99+1.0-pre8-0ubuntu4_i386.deb)  Bad header line
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
mansfield@mansfield-laptop:~$

---

### Post by DJ_Peng on 2006-12-13
The easiest way to fix plugin problems for Firefox is often to get Firefox directly from Mozilla and run it form there. You can make links wherever you want them, and you can even edit your current links to point to the version you have installed yourself.

There's another benefit to getting Firefox from Mozilla yourself. They're getting ready to release Firefox 2.0.0.1 (possibly this coming Tuesday) and if you get Firefox from Mozilla you won't have to wait for Ubuntu to get the update packaged for you. Also, as a Mozilla tester I can tell you that there are features that are intended in Mozilla, some in the program itself, some via extensions) that simply don't work in Ubuntu's version. Getting it from Mozilla will get you the program as the developers intended it to be.

---

