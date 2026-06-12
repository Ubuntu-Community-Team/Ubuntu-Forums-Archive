---
title: "Cannot upgrade on Ubuntu 15.04"
date: 2015-07-19
forum: Installation &amp; Upgrades
---

### Post by oc666 on 2015-07-19
Hello
I'm trying to make simple upgrade but get a lot of errors on Ubuntu 15.04.
```

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  adobe-flash-properties-gtk adobe-flashplugin gir1.2-totem-1.0 libtotem0 totem totem-common totem-plugins
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
Need to get 10.7 MB of archives.
After this operation, 66.6 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://archive.canonical.com/ vivid/partner adobe-flash-properties-gtk amd64 1:20150716.1-0vivid1 [113 kB]
Get:2 http://il.archive.ubuntu.com/ubuntu/ vivid-updates/main libtotem0 amd64 3.14.3-0ubuntu0.1 [184 kB]
Get:3 http://il.archive.ubuntu.com/ubuntu/ vivid-updates/main totem-plugins amd64 3.14.3-0ubuntu0.1 [118 kB]
Get:4 http://il.archive.ubuntu.com/ubuntu/ vivid-updates/main totem amd64 3.14.3-0ubuntu0.1 [43.0 kB]
Get:5 http://il.archive.ubuntu.com/ubuntu/ vivid-updates/main totem-common all 3.14.3-0ubuntu0.1 [181 kB]
Get:6 http://il.archive.ubuntu.com/ubuntu/ vivid-updates/main gir1.2-totem-1.0 amd64 3.14.3-0ubuntu0.1 [5,222 B]
Get:7 http://archive.canonical.com/ vivid/partner adobe-flashplugin amd64 1:20150716.1-0vivid1 [10.1 MB]
Fetched 10.7 MB in 10s (1,039 kB/s)                                                                                                                                                                                 
(Reading database ... 345201 files and directories currently installed.)
Preparing to unpack .../adobe-flash-properties-gtk_1%3a20150716.1-0vivid1_amd64.deb ...
Unpacking adobe-flash-properties-gtk (1:20150716.1-0vivid1) over (1:20150708.1-0vivid1) ...
Preparing to unpack .../adobe-flashplugin_1%3a20150716.1-0vivid1_amd64.deb ...
Unpacking adobe-flashplugin (1:20150716.1-0vivid1) over (1:20150708.1-0vivid1) ...
Preparing to unpack .../libtotem0_3.14.3-0ubuntu0.1_amd64.deb ...
Unpacking libtotem0 (3.14.3-0ubuntu0.1) over (3.14.2-0ubuntu2) ...
Preparing to unpack .../totem-plugins_3.14.3-0ubuntu0.1_amd64.deb ...
Unpacking totem-plugins (3.14.3-0ubuntu0.1) over (3.14.2-0ubuntu2) ...
Preparing to unpack .../totem_3.14.3-0ubuntu0.1_amd64.deb ...
Unpacking totem (3.14.3-0ubuntu0.1) over (3.14.2-0ubuntu2) ...
Preparing to unpack .../totem-common_3.14.3-0ubuntu0.1_all.deb ...
Unpacking totem-common (3.14.3-0ubuntu0.1) over (3.14.2-0ubuntu2) ...
Preparing to unpack .../gir1.2-totem-1.0_3.14.3-0ubuntu0.1_amd64.deb ...
Unpacking gir1.2-totem-1.0 (3.14.3-0ubuntu0.1) over (3.14.2-0ubuntu2) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu5) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for bamfdaemon (0.5.1+15.04.20150202-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.58ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.14-0ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.44.1-1ubuntu1) ...
Processing triggers for libglib2.0-0:i386 (2.44.1-1ubuntu1) ...
Processing triggers for gconf2 (3.2.6-3ubuntu1) ...
Processing triggers for man-db (2.7.0.2-5) ...
Setting up cups-daemon (2.0.2-1ubuntu3.2) ...
insserv: warning: script 'S85vpnagentd_init' missing LSB tags and overrides
insserv: warning: script 'vpnagentd_init' missing LSB tags and overrides
insserv: warning: script 'mongod' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `mongod'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `mongod'
insserv: There is a loop at service ondemand if started
insserv: There is a loop between service ondemand and urandom if started
insserv:  loop involving service urandom at depth 4
insserv:  loop involving service hwclock at depth 3
insserv: There is a loop between service vpnagentd_init and udev if started
insserv:  loop involving service udev at depth 1
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service cgproxy at depth 1
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service vpnagentd_init if started
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv:  loop involving service mountkernfs at depth 1
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package cups-daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cups-core-drivers:
 cups-core-drivers depends on cups-daemon (>= 2.0.2-1ubuntu3.2); however:
  Package cups-daemon is not configured yet.

dpkg: error processing package cups-core-drivers (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups:
 cups depends on cups-core-drivers (>= 2.0.2-1ubuntu3.2); however:
  Package cups-core-drivers is not configured yet.
 cups depends on cups-daemon (>= 2.0.2-1ubuntu3.2); however:
  Package cups-daemon is not configured yet.

dpkg: error processing package cups (--configure):
 dependency problems - leaving unconfigured
Setting up grub-common (2.02~beta2-22ubuntu1.1) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: warning: script 'S85vpnagentd_init' missing LSB tags and overrides
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                                                                                                    insserv: warning: script 'vpnagentd_init' missing LSB tags and overrides
insserv: warning: script 'mongod' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `mongod'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `mongod'
insserv: There is a loop at service ondemand if started
insserv: There is a loop between service ondemand and urandom if started
insserv:  loop involving service urandom at depth 4
insserv:  loop involving service hwclock at depth 3
insserv: There is a loop between service vpnagentd_init and udev if started
insserv:  loop involving service udev at depth 1
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service cgproxy at depth 1
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service vpnagentd_init if started
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv:  loop involving service mountkernfs at depth 1
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package grub-common (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of grub2-common:
 grub2-common depends on grub-common (= 2.02~beta2-22ubuntu1.1); however:
  Package grub-common is not configured yet.

dpkg: error processing package grub2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-pc-bin:
 grub-pc-bin depends on grub-common (= 2.02~beta2-22ubuntu1.1); however:
  Package grub-common is not configured yet.

dpkg: error processing package grub-pc-bin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            dpkg: dependency problems prevent configuration of grub-pc:
 grub-pc depends on grub-common (= 2.02~beta2-22ubuntu1.1); however:
  Package grub-common is not configured yet.
 grub-pc depends on grub2-common (= 2.02~beta2-22ubuntu1.1); however:
  Package grub2-common is not configured yet.
 grub-pc depends on grub-pc-bin (= 2.02~beta2-22ubuntu1.1); however:
  Package grub-pc-bin is not configured yet.

dpkg: error processing package grub-pc (--configure):
 dependency problems - leaving unconfigured
Setting up php5-fpm (5.6.4+dfsg-4ubuntu6.2) ...
No apport report written because MaxReports is reached already
                                                              insserv: warning: script 'S85vpnagentd_init' missing LSB tags and overrides
insserv: warning: script 'vpnagentd_init' missing LSB tags and overrides
insserv: warning: script 'mongod' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `mongod'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `mongod'
insserv: There is a loop at service ondemand if started
insserv: There is a loop between service ondemand and urandom if started
insserv:  loop involving service urandom at depth 4
insserv:  loop involving service hwclock at depth 3
insserv: There is a loop between service vpnagentd_init and udev if started
insserv:  loop involving service udev at depth 1
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv:  loop involving service cgproxy at depth 1
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service vpnagentd_init if started
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv:  loop involving service mountkernfs at depth 1
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: Starting vpnagentd_init depends on ondemand and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package php5-fpm (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up adobe-flashplugin (1:20150716.1-0vivid1) ...
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/mozilla/plugins/flashplugin-alternative.so (mozilla-flashplugin) in auto mode
Setting up adobe-flash-properties-gtk (1:20150716.1-0vivid1) ...
Setting up libtotem0 (3.14.3-0ubuntu0.1) ...
Setting up totem-common (3.14.3-0ubuntu0.1) ...
Setting up totem (3.14.3-0ubuntu0.1) ...
Setting up gir1.2-totem-1.0 (3.14.3-0ubuntu0.1) ...
Setting up totem-plugins (3.14.3-0ubuntu0.1) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
Errors were encountered while processing:
 cups-daemon
 cups-core-drivers
 cups
 grub-common
 grub2-common
 grub-pc-bin
 grub-pc
 php5-fpm
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

What can I do to get over this issue?

Thanks

---

### Post by howefield on 2015-07-19
Whilst you are waiting for someone to come along, you might want to start here

[http://askubuntu.com/questions/601226/udev-and-systemd-are-broken-any-help-would-be-appreciated](http://askubuntu.com/questions/601226/udev-and-systemd-are-broken-any-help-would-be-appreciated)

Looks similar enough and involves sorting out the third party packages that you have installed.

---

### Post by Bucky Ball on 2015-07-19
Just a point, just in case you didn't, and may have nothing to do with your issue: *_always_* update before upgrading.

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

:)

---

### Post by jason_gibson2 on 2015-07-19
What is the reason for doing ```
apt-get upgrade
``` then doing ```
apt-get dist-upgrade
``` immediately following. Seems somewhat redundant? I always just do the dist-upgrade and haven't had an issue yet.

*EDIT* Yes I know the difference between the 2, just not why you don't just do one or the other rather than both one right after the other.

---

### Post by v3.xx on 2015-07-19
> **jason_gibson2 said:**
> What is the reason for doing ```
apt-get upgrade
``` then doing ```
apt-get dist-upgrade
``` immediately following. Seems somewhat redundant? I always just do the dist-upgrade and haven't had an issue yet.

*EDIT* Yes I know the difference between the 2, just not why you don't just do one or the other rather than both one right after the other.
I like to first upgrade to check that things are good.  Then a dist-upgrade to install the latest kernel.

---

### Post by Bucky Ball on 2015-07-19
> **jason_gibson2 said:**
> What is the reason for doing ```
apt-get upgrade
``` then doing ```
apt-get dist-upgrade
``` immediately following.

Off-topic, but see [here]("http://askubuntu.com/questions/81585/what-is-dist-upgrade-and-why-does-it-upgrade-more-than-upgrade"). 

Back to the OPs issue. :)

---

