---
title: "Samba not installing"
date: 2013-02-09
forum: Installation &amp; Upgrades
---

### Post by ivotkl on 2013-02-09
Ok guys, reviving [this](http://ubuntuforums.org/showthread.php?t=1983830) old thread.

```
$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-gtkclutter-1.0 gir1.2-champlain-0.12 libchamplain-0.12-0
  libchamplain-gtk-0.12-0 gir1.2-gtkchamplain-0.12
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up samba4 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
/var/lib/dpkg/info/samba4.postinst: 14: /var/lib/dpkg/info/samba4.postinst: /usr/share/samba/setoption.pl: Permission denied
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 126
Errors were encountered while processing:
 samba4
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any ideas? Thanks.

---

### Post by ivotkl on 2013-02-11
Shameless bump. Anyone?

Update:

donaldfarkas from linuxforums suggested me to install samba again. Below you can find my whole "battle" against it.

```
$ sudo apt-get install samba
[sudo] password for ivan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 samba : Depends: samba-common (= 2:3.6.3-2ubuntu2) but 2:3.6.3-2ubuntu2.3 is to be installed
         Depends: libwbclient0 (= 2:3.6.3-2ubuntu2) but 2:3.6.3-2ubuntu2.3 is to be installed
E: Unable to correct problems, you have held broken packages.
```

Then I've tried to fix it, without any luck:
```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ivan@ivan-desktop:~$ sudo apt-get autoclean 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ivan@ivan-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

So, as it had problem with samba-common, I just removed it.
```
$ sudo apt-get purge samba-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libdcerpc-server0* libdcerpc0* libgensec0* libregistry0* libsamba-policy0*
  libsmbclient-raw0* nautilus-share* python-samba* samba-common*
  samba-common-bin* samba-dsdb-modules* samba4-common-bin* smbclient*
0 upgraded, 0 newly installed, 13 to remove and 0 not upgraded.
After this operation, 76.0 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 200317 files and directories currently installed.)
Removing libdcerpc-server0 ...
Purging configuration files for libdcerpc-server0 ...
Removing samba-dsdb-modules ...
Removing samba4-common-bin ...
Removing python-samba ...
Removing libsamba-policy0 ...
Purging configuration files for libsamba-policy0 ...
Removing libregistry0 ...
Purging configuration files for libregistry0 ...
Removing libdcerpc0 ...
Purging configuration files for libdcerpc0 ...
Removing libsmbclient-raw0 ...
Purging configuration files for libsmbclient-raw0 ...
Removing libgensec0 ...
Purging configuration files for libgensec0 ...
Removing nautilus-share ...
Removing samba-common-bin ...
Removing smbclient ...
Removing samba-common ...
Purging configuration files for samba-common ...
dpkg: warning: while removing samba-common, directory '/etc/dhcp3/dhclient-enter-hooks.d' not empty so not removed.
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
```

And:
```
$ sudo apt-get purge libwbclient0 -y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gvfs-backends* libgnomevfs2-extra* libsmbclient* libwbclient0* python-smbc*
  system-config-printer-common* system-config-printer-gnome* ubuntu-desktop*
  vlc* vlc-nox* vlc-plugin-notify* vlc-plugin-pulse*
0 upgraded, 0 newly installed, 12 to remove and 0 not upgraded.
After this operation, 25.0 MB disk space will be freed.
(Reading database ... 199797 files and directories currently installed.)
Removing gvfs-backends ...
Removing libgnomevfs2-extra ...
Purging configuration files for libgnomevfs2-extra ...
Removing vlc-plugin-notify ...
Removing vlc ...
Purging configuration files for vlc ...
Removing vlc-plugin-pulse ...
Removing vlc-nox ...
Removing ubuntu-desktop ...
Removing system-config-printer-gnome ...
Purging configuration files for system-config-printer-gnome ...
Removing system-config-printer-common ...
Purging configuration files for system-config-printer-common ...
Removing python-smbc ...
Removing libsmbclient ...
Purging configuration files for libsmbclient ...
Removing libwbclient0 ...
Purging configuration files for libwbclient0 ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```

Then:
```
$ sudo apt-get install samba -y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmodplug1 libva-x11-1 libdc1394-22 libxcb-keysyms1 libbluray1
  libresid-builder0c2a libzvbi0 libxcb-xv0 libtar0 libdca0 libcddb2 libass4
  libdvbpsi7 avahi-utils libdirectfb-1.2-9 libvlc5 libenca0 libcdio-cdda1
  libupnp3 libaacs0 libzvbi-common libcrystalhd3 libxcb-randr0
  libxcb-composite0 libiso9660-8 libkate1 libcdio-paranoia1 libsidplay2
  vlc-data libdirac-encoder0 libvlccore5 libvcdinfo0 libebml3 libmpcdec6
  libmatroska5 libsdl-image1.2 libfaad2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libwbclient0 samba-common samba-common-bin
Suggested packages:
  openbsd-inetd inet-superserver smbldap-tools ctdb
The following NEW packages will be installed:
  libwbclient0 samba samba-common samba-common-bin
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.5 MB of archives.
After this operation, 42.1 MB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/main libwbclient0 i386 2:3.6.3-2ubuntu2 [30.6 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/main samba-common all 2:3.6.3-2ubuntu2 [326 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise/main samba-common-bin i386 2:3.6.3-2ubuntu2 [6,147 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise/main samba i386 2:3.6.3-2ubuntu2 [8,000 kB]
Fetched 14.5 MB in 44s (326 kB/s)                                              
Preconfiguring packages ...
Selecting previously unselected package libwbclient0.
(Reading database ... 199157 files and directories currently installed.)
Unpacking libwbclient0 (from .../libwbclient0_2%3a3.6.3-2ubuntu2_i386.deb) ...
Selecting previously unselected package samba-common.
Unpacking samba-common (from .../samba-common_2%3a3.6.3-2ubuntu2_all.deb) ...
Selecting previously unselected package samba-common-bin.
Unpacking samba-common-bin (from .../samba-common-bin_2%3a3.6.3-2ubuntu2_i386.deb) ...
Selecting previously unselected package samba.
Unpacking samba (from .../samba_2%3a3.6.3-2ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up libwbclient0 (2:3.6.3-2ubuntu2) ...
Setting up samba-common (2:3.6.3-2ubuntu2) ...

Creating config file /etc/samba/smb.conf with new version
Setting up samba-common-bin (2:3.6.3-2ubuntu2) ...
update-alternatives: using /usr/bin/nmblookup.samba3 to provide /usr/bin/nmblookup (nmblookup) in auto mode.
update-alternatives: using /usr/bin/net.samba3 to provide /usr/bin/net (net) in auto mode.
update-alternatives: using /usr/bin/testparm.samba3 to provide /usr/bin/testparm (testparm) in auto mode.
Setting up samba (2:3.6.3-2ubuntu2) ...
Generating /etc/default/samba...
Importing account for nobody...ok
Importing account for ivan...ok
update-alternatives: using /usr/bin/smbstatus.samba3 to provide /usr/bin/smbstatus (smbstatus) in auto mode.
smbd start/running, process 5475
nmbd start/running, process 5508
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```

However:
```
$ samba
The program 'samba' is currently not installed.  You can install it by typing:
sudo apt-get install samba4
```

So:
```
$ sudo apt-get install samba4 -y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmodplug1 libva-x11-1 libdc1394-22 libxcb-keysyms1 libbluray1
  libresid-builder0c2a libzvbi0 libxcb-xv0 libtar0 libdca0 libcddb2 libass4
  libdvbpsi7 avahi-utils libdirectfb-1.2-9 libvlc5 libenca0 libcdio-cdda1
  libupnp3 libaacs0 libzvbi-common libcrystalhd3 libxcb-randr0
  libxcb-composite0 libiso9660-8 libkate1 libcdio-paranoia1 libsidplay2
  vlc-data libdirac-encoder0 libvlccore5 libvcdinfo0 libebml3 libmpcdec6
  libmatroska5 libsdl-image1.2 libfaad2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libdcerpc-server0 libdcerpc0 libgensec0 libregistry0 libsamba-policy0
  libsmbclient-raw0 python-samba samba-dsdb-modules samba4-common-bin
Suggested packages:
  phpldapadmin samba-gtk swat2
Recommended packages:
  bind9
The following NEW packages will be installed:
  libdcerpc-server0 libdcerpc0 libgensec0 libregistry0 libsamba-policy0
  libsmbclient-raw0 python-samba samba-dsdb-modules samba4 samba4-common-bin
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 5,258 kB of archives.
After this operation, 25.5 MB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe libgensec0 i386 4.0.0~alpha18.dfsg1-4ubuntu2 [251 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe libsmbclient-raw0 i386 4.0.0~alpha18.dfsg1-4ubuntu2 [556 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe libdcerpc0 i386 4.0.0~alpha18.dfsg1-4ubuntu2 [557 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe libregistry0 i386 4.0.0~alpha18.dfsg1-4ubuntu2 [53.6 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe libdcerpc-server0 i386 4.0.0~alpha18.dfsg1-4ubuntu2 [336 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe libsamba-policy0 i386 4.0.0~alpha18.dfsg1-4ubuntu2 [23.2 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe python-samba i386 4.0.0~alpha18.dfsg1-4ubuntu2 [1,545 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe samba-dsdb-modules i386 4.0.0~alpha18.dfsg1-4ubuntu2 [261 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe samba4-common-bin i386 4.0.0~alpha18.dfsg1-4ubuntu2 [25.4 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe samba4 i386 4.0.0~alpha18.dfsg1-4ubuntu2 [1,649 kB]
Fetched 5,258 kB in 12s (405 kB/s)                                             
Preconfiguring packages ...
/tmp/samba4.config.55771: 1: /tmp/samba4.config.55771: samba-tool: not found
/tmp/samba4.config.55771: 1: /tmp/samba4.config.55771: samba-tool: not found
Selecting previously unselected package libgensec0.
(Reading database ... 199286 files and directories currently installed.)
Unpacking libgensec0 (from .../libgensec0_4.0.0~alpha18.dfsg1-4ubuntu2_i386.deb) ...
Selecting previously unselected package libsmbclient-raw0.
Unpacking libsmbclient-raw0 (from .../libsmbclient-raw0_4.0.0~alpha18.dfsg1-4ubuntu2_i386.deb) ...
Selecting previously unselected package libdcerpc0.
Unpacking libdcerpc0 (from .../libdcerpc0_4.0.0~alpha18.dfsg1-4ubuntu2_i386.deb) ...
Selecting previously unselected package libregistry0.
Unpacking libregistry0 (from .../libregistry0_4.0.0~alpha18.dfsg1-4ubuntu2_i386.deb) ...
Selecting previously unselected package libdcerpc-server0.
Unpacking libdcerpc-server0 (from .../libdcerpc-server0_4.0.0~alpha18.dfsg1-4ubuntu2_i386.deb) ...
Selecting previously unselected package libsamba-policy0.
Unpacking libsamba-policy0 (from .../libsamba-policy0_4.0.0~alpha18.dfsg1-4ubuntu2_i386.deb) ...
Selecting previously unselected package python-samba.
Unpacking python-samba (from .../python-samba_4.0.0~alpha18.dfsg1-4ubuntu2_i386.deb) ...
Selecting previously unselected package samba-dsdb-modules.
Unpacking samba-dsdb-modules (from .../samba-dsdb-modules_4.0.0~alpha18.dfsg1-4ubuntu2_i386.deb) ...
Selecting previously unselected package samba4-common-bin.
Unpacking samba4-common-bin (from .../samba4-common-bin_4.0.0~alpha18.dfsg1-4ubuntu2_i386.deb) ...
Selecting previously unselected package samba4.
Unpacking samba4 (from .../samba4_4.0.0~alpha18.dfsg1-4ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up libgensec0 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Setting up libsmbclient-raw0 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Setting up libdcerpc0 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Setting up libregistry0 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Setting up libdcerpc-server0 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Setting up libsamba-policy0 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Setting up python-samba (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Setting up samba-dsdb-modules (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Setting up samba4-common-bin (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Setting up samba4 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
ERROR: Invalid smb.conf
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
ERROR: Invalid smb.conf
/var/lib/dpkg/info/samba4.postinst: 14: /var/lib/dpkg/info/samba4.postinst: /usr/share/samba/setoption.pl: Permission denied
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 126
No apport report written because MaxReports is reached already
                                                              Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 samba4
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I'm back on square one regarding error code on last line.

Nevertheless:
```
$ samba
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
[2013/02/11 08:45:40,  0] ../lib/util/debug.c:578(reopen_logs_internal)
  Unable to open new log file '/var/log/samba/log.%m': Permission denied
[2013/02/11 08:45:40,  0] ../source4/smbd/server.c:366(binary_smbd_main)
  samba version 4.0.0alpha18 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2012
```

So, I'm assuming this problem was solved. Kindly confirm as I do not currently have 2 PCs to test it.

---

### Post by darkod on 2013-02-11
Why does it say
```
Setting up samba4 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
```

Is this an alpha package not yet released? If that is the case it might not work correctly and that might be the issue.

Or that's how they named the package?

Is it already in the main repositories or you tried other repositories with unreleased software or a .deb of an alpha version?

It looks like it can't finish installing it, but why...

---

### Post by ivotkl on 2013-02-25
Thank you darkod for the help provided and sorry for this late reply. I was without a box and bought one a few days ago.

I wouldn't know if release is alpha, beta or stable. I believe back then terminal itself "suggested" that I should install samba4. Otherwise, might have been a user here, at linuxforums or at IRC channel #ubuntu or some other similar.

Now, I am trying to install samba from Ubuntu Software Center (second option, used 'samba' as search term).

Details of error are as follow:
```
The following packages have unmet dependencies:

system-config-samba:
```

Attachment with error can be found as well.

---

### Post by darkod on 2013-02-25
I'm not sure what software centre will install, there might be more options with the word 'samba' in them. Have you tried in terminal:
sudo apt-get install samba4

or
sudo apt-get install samba

---

