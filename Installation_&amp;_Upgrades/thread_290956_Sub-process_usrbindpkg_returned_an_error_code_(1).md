---
title: "Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by piege on 2006-11-01
I had an error while upgrading from dapper to edgy the official way since then i can't install/remove anything here is what i get when i try to apt-get upgrade

Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  libggi2 mplayer vmware-player
The following packages will be upgraded:
  imagemagick libmagick++9c2a libmagick9 libpq4 libruby1.8 libwv-1.2-1 ruby1.8
  screen
8 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
8 not fully installed or removed.
Need to get 4764kB of archives.
After unpacking, 32.8kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main libmagick9 7:6.2.4.5.dfsg1-0.10ubuntu0.1 [1285kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main libmagick++9c2a 7:6.2.4.5.dfsg1-0.10ubuntu0.1 [169kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main screen 4.0.2-4.1ubuntu5.6.10 [584kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main imagemagick 7:6.2.4.5.dfsg1-0.10ubuntu0.1 [742kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main libpq4 8.1.4-7ubuntu0.1 [203kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main libruby1.8 1.8.4-5ubuntu1.1 [1451kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main libwv-1.2-1 1.2.1-2ubuntu0.1 [139kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main ruby1.8 1.8.4-5ubuntu1.1 [191kB]
Fetched 4764kB in 22s (207kB/s)                                                
Preconfiguring packages ...
(Reading database ... 237367 files and directories currently installed.)
Preparing to replace libmagick9 7:6.2.4.5.dfsg1-0.10 (using .../libmagick9_7%3a6.2.4.5.dfsg1-0.10ubuntu0.1_i386.deb) ...
Unpacking replacement libmagick9 ...
Preparing to replace libmagick++9c2a 7:6.2.4.5.dfsg1-0.10 (using .../libmagick++9c2a_7%3a6.2.4.5.dfsg1-0.10ubuntu0.1_i386.deb) ...
Unpacking replacement libmagick++9c2a ...
Preparing to replace screen 4.0.2-4.1ubuntu5 (using .../screen_4.0.2-4.1ubuntu5.6.10_i386.deb) ...
Unpacking replacement screen ...
Preparing to replace imagemagick 7:6.2.4.5.dfsg1-0.10 (using .../imagemagick_7%3a6.2.4.5.dfsg1-0.10ubuntu0.1_i386.deb) ...
Unpacking replacement imagemagick ...
Preparing to replace libpq4 8.1.4-7 (using .../libpq4_8.1.4-7ubuntu0.1_i386.deb) ...
Unpacking replacement libpq4 ...
Preparing to replace libruby1.8 1.8.4-5ubuntu1 (using .../libruby1.8_1.8.4-5ubuntu1.1_i386.deb) ...
Unpacking replacement libruby1.8 ...
Preparing to replace libwv-1.2-1 1.2.1-2 (using .../libwv-1.2-1_1.2.1-2ubuntu0.1_i386.deb) ...
Unpacking replacement libwv-1.2-1 ...
Preparing to replace ruby1.8 1.8.4-5ubuntu1 (using .../ruby1.8_1.8.4-5ubuntu1.1_i386.deb) ...
Unpacking replacement ruby1.8 ...
Setting up acpid (1.0.4-5ubuntu4) ...
 * Loading ACPI modules...                                               [ ok ] 
 * Starting ACPI services...                                                    acpid: can't open /proc/acpi/event: Device or resource busy
invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of powermanagement-interface:
 powermanagement-interface depends on acpi-support (>= 0.17); however:
  Package acpi-support is not configured yet.
dpkg: error processing powermanagement-interface (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-power-manager:
 gnome-power-manager depends on powermanagement-interface; however:
  Package powermanagement-interface is not configured yet.
dpkg: error processing gnome-power-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on gnome-power-manager; however:
  Package gnome-power-manager is not configured yet.
dpkg: error processing gnome-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-core:
 gnome-core depends on gnome-session (>= 2.14.2); however:
  Package gnome-session is not configured yet.
dpkg: error processing gnome-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-office:
 gnome-office depends on gnome-core (= 1:2.14.2.1ubuntu1); however:
  Package gnome-core is not configured yet.
dpkg: error processing gnome-office (--configure):
 dependency problems - leaving unconfigured
Setting up libmagick9 (6.2.4.5.dfsg1-0.10ubuntu0.1) ...

Setting up libmagick++9c2a (6.2.4.5.dfsg1-0.10ubuntu0.1) ...

Setting up k3d (0.5.12.0-1ubuntu2) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 865, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 535, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error processing k3d (--configure):
 subprocess post-installation script returned error exit status 1
Setting up screen (4.0.2-4.1ubuntu5.6.10) ...
 Removing any system startup links for /etc/init.d/screen-cleanup ...

Setting up imagemagick (6.2.4.5.dfsg1-0.10ubuntu0.1) ...

Setting up libpq4 (8.1.4-7ubuntu0.1) ...

Setting up libruby1.8 (1.8.4-5ubuntu1.1) ...

Setting up libwv-1.2-1 (1.2.1-2ubuntu0.1) ...

Setting up ruby1.8 (1.8.4-5ubuntu1.1) ...
Errors were encountered while processing:
 acpid
 acpi-support
 powermanagement-interface
 gnome-power-manager
 gnome-session
 gnome-core
 gnome-office
 k3d
E: Sub-process /usr/bin/dpkg returned an error code (1)

Can someone please help me figure how what is happening?!

---

### Post by deepwave on 2006-11-01
Technical Explanation:
apt-get acts an intelligent wrapper for dpkg.  And dpkg in your case, crapped out (hence the Python tracecall) when it tried setting up k3d.

How to Fix it?
Try running sudo dpkg --configure -a

---

