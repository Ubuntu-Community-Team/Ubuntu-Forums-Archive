---
title: "Problems with manual fglrx install"
date: 2010-08-13
forum: Installation &amp; Upgrades
---

### Post by cletus1jr on 2010-08-13
Hi,

I recently upgraded to Lucid (x86_64) on an HP dv2 laptop, and after doing so, the system will not resume after a suspend (with fglrx installed from the "official" repositories). After reading a lot about the problem, I have seen that updating to the latest ATI driver had fixed this issue for some, so I would like to try that.

I am following the guide at at [cchtml]("http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide").

First, I tried installing the Ubuntu-X team's drivers. However, after (successfully) adding their repository, an update does not fetch their packages:

```

...
Hit http://ppa.launchpad.net lucid Release.gpg                                   
Ign http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ lucid/main Translation-en_US
Hit http://security.ubuntu.com lucid-security/main Packages          
Get:1 http://ppa.launchpad.net lucid Release.gpg [307B]              
Ign http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release                           
...
Hit http://ppa.launchpad.net lucid/main Packages 
Get:3 http://ppa.launchpad.net lucid/main Packages [52.6kB]
Fetched 110kB in 0s (266kB/s)     
Reading package lists... Done

```It looks like both the xorg-edgers and ubuntu-x-swat repositories are being ignored? (If I'm reading that correctly.) If I open the window System->Administration->Software Sources, I can see that the ubuntu-x-swat repository is checked, so I'm confused why it's being ignored.

If I try to demand the fglrx-installer package, I get an error that it cannot find this package.

```

[cjreed@cjreed-laptop Desktop]$ sudo apt-get install fglrx-installer 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package fglrx-installer

```I have the same issues for xorg-edgers and ubuntu-x-swat.

Finally, if I try to build the official ATI v10.7 drivers myself, I get an error that Linux is an unrecognized architecture!

```

[cjreed@cjreed-laptop Desktop]$ sh ati-driver-installer-10-7-x86.x86_64.run --buildpkg Ubuntu/lucid
Created directory fglrx-install.fGajKF
Verifying archive integrity... All good.
Uncompressing ATI Catalyst(TM) Proprietary Linux Driver-8.753........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/lucid
Error: unsupported architecture: Linux
Removing temporary directory: fglrx-install.fGajKF

```I have installed all preliminary packages suggested in the guide:

```

[cjreed@cjreed-laptop Desktop]$ sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
cdbs is already the newest version.
fakeroot is already the newest version.
dh-make is already the newest version.
debhelper is already the newest version.
debconf is already the newest version.
libstdc++6 is already the newest version.
dkms is already the newest version.
libqtgui4 is already the newest version.
wget is already the newest version.
ia32-libs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```Any help with these problems would be greatly appreciated! I really can't understand why I'm unable to build the package from ATI myself.

Thanks!

- Corey

---

### Post by cletus1jr on 2010-08-16
Hi,

Just wondering if anyone could point me in the right direction to investigate the "Error: unsupported architecture: Linux" that I get when trying to build the ATI driver 10.7 package.

Thanks!

- Corey

---

### Post by atryus28 on 2010-08-26
I'm having the same problem right now with the 10.8 drivers and those repos.  I hope someone can give some insight as to why the package can not be found.

---

### Post by cletus1jr on 2010-11-07
Just in case anyone finds this thread, I've gotten fglrx to work by:


[LIST=1]
[*]Unchecking both xorg-edgers and ubuntu-x-swat from the software sources
[*]Building the Catalyst driver 10.10 myself following the direction at [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually)
[*]Doing "sudo sh ati-driver-installer-10-10-x86.x86_64.run --buildpkg Ubuntu/lucid" instead of the non-sudo command suggested in the guide. This actually fixed the "Unrecognized architecture:Linux" problem.
[*]Building and installing the fglrx 10.9 hotfix (as suggested in the cchtml guide).
[/LIST]
Now everything works again -- compiz as well as system suspend/restore!

---

