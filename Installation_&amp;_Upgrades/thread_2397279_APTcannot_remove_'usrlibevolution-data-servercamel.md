---
title: "APT:cannot remove '/usr/lib/evolution-data-server/camel-providers': Permission denied"
date: 2018-07-27
forum: Installation &amp; Upgrades
---

### Post by bvargo on 2018-07-27
Somehow Evolution broke.  I don't use/want a local email/calendar/contact client/server, not the least of which is Evolution.  I have no idea if I have previously tried to get rid of it but in any case, it is broken and now so is APT.

I don't know how to get rid of it (I'm very much hoping it isn't integral to the functioning of Ubuntu e.g. some Windows applications like IE) and now I cannot use APT:

```

:~$ ver
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.5 LTS
Release:	16.04
Codename:	xenial


:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 evolution-data-server : Depends: libcamel-1.2-54 (= 3.18.5-1ubuntu1) but 3.18.5-1ubuntu1.1 is to be installed
                         Depends: libedata-cal-1.2-28 (>= 3.17) but it is not going to be installed
                         Depends: evolution-data-server-common (= 3.18.5-1ubuntu1) but 3.18.5-1ubuntu1.1 is to be installed
E: Broken packages
:~$ sudo apt purge evolution-data-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  evolution-data-server
0 upgraded, 0 newly installed, 1 to remove and 46 not upgraded.
12 not fully installed or removed.
After this operation, 1,860 kB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 280818 files and directories currently installed.)
Removing evolution-data-server (3.18.5-1ubuntu1) ...
dpkg: error processing package evolution-data-server (--remove):
 cannot remove '/usr/lib/evolution-data-server/camel-providers': Permission denied
Errors were encountered while processing:
 evolution-data-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libedata-cal-1.2-28 signon-plugin-password
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  evolution-data-server evolution-data-server-online-accounts
0 upgraded, 0 newly installed, 2 to remove and 46 not upgraded.
14 not fully installed or removed.
After this operation, 2,162 kB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 280800 files and directories currently installed.)
Removing evolution-data-server (3.18.5-1ubuntu1) ...
dpkg: error processing package evolution-data-server (--remove):
 cannot remove '/usr/lib/evolution-data-server/camel-providers': Permission denied
Removing evolution-data-server-online-accounts (3.18.5-1ubuntu1.1) ...
dpkg: error processing package evolution-data-server-online-accounts (--remove):
 cannot remove '/usr/lib/evolution-data-server/credential-modules': Permission denied
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.2) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20180209-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Errors were encountered while processing:
 evolution-data-server
 evolution-data-server-online-accounts
E: Sub-process /usr/bin/dpkg returned an error code (1)

:~$ sudo apt install evolution-data-server-common 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
evolution-data-server-common is already the newest version (3.18.5-1ubuntu1.1).
The following packages were automatically installed and are no longer required:
  bogofilter bogofilter-bdb bogofilter-common libchamplain-0.12-0 libchamplain-gtk-0.12-0 libcryptui0a libedata-cal-1.2-28 libedataserverui-1.2-1 libpst4 libytnef0 seahorse-daemon signon-plugin-password
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  evolution-data-server evolution-data-server-online-accounts
0 upgraded, 0 newly installed, 2 to remove and 46 not upgraded.
24 not fully installed or removed.
After this operation, 2,162 kB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 281041 files and directories currently installed.)
Removing evolution-data-server (3.18.5-1ubuntu1) ...
dpkg: error processing package evolution-data-server (--remove):
 cannot remove '/usr/lib/evolution-data-server/camel-providers': Permission denied
Removing evolution-data-server-online-accounts (3.18.5-1ubuntu1.1) ...
dpkg: error processing package evolution-data-server-online-accounts (--remove):
 cannot remove '/usr/lib/evolution-data-server/credential-modules': Permission denied
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.2) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20180209-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Errors were encountered while processing:
 evolution-data-server
 evolution-data-server-online-accounts
E: Sub-process /usr/bin/dpkg returned an error code (1)

:~$ sudo apt install evolution-data-server
evolution-data-server                  evolution-data-server-common           evolution-data-server-dbg              evolution-data-server-dev              evolution-data-server-doc              evolution-data-server-online-accounts  

:~$ sudo apt install evolution-data-server-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bogofilter bogofilter-bdb bogofilter-common libchamplain-0.12-0 libchamplain-gtk-0.12-0 libcryptui0a libedata-cal-1.2-28 libedataserverui-1.2-1 libpst4 libytnef0 seahorse-daemon signon-plugin-password
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libnspr4-dev libnss3-dev
The following packages will be REMOVED:
  evolution-data-server evolution-data-server-online-accounts
The following NEW packages will be installed:
  evolution-data-server-dev libnspr4-dev libnss3-dev
0 upgraded, 3 newly installed, 2 to remove and 46 not upgraded.
24 not fully installed or removed.
Need to get 556 kB of archives.
After this operation, 676 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libnspr4-dev amd64 2:4.13.1-0ubuntu0.16.04.1 [213 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libnss3-dev amd64 2:3.28.4-0ubuntu0.16.04.3 [230 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 evolution-data-server-dev amd64 3.18.5-1ubuntu1.1 [113 kB]
Fetched 556 kB in 0s (2,764 kB/s)                  
(Reading database ... 281041 files and directories currently installed.)
Removing evolution-data-server (3.18.5-1ubuntu1) ...
dpkg: error processing package evolution-data-server (--remove):
 cannot remove '/usr/lib/evolution-data-server/camel-providers': Permission denied
Removing evolution-data-server-online-accounts (3.18.5-1ubuntu1.1) ...
dpkg: error processing package evolution-data-server-online-accounts (--remove):
 cannot remove '/usr/lib/evolution-data-server/credential-modules': Permission denied
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.2) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20180209-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Errors were encountered while processing:
 evolution-data-server
 evolution-data-server-online-accounts
E: Sub-process /usr/bin/dpkg returned an error code (1)

:~$ sudo apt install evolution
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  evolution-data-server evolution-plugins libevolution
Suggested packages:
  evolution-ews evolution-plugins-experimental evolution-data-server-dbg
The following NEW packages will be installed:
  evolution evolution-plugins libevolution
The following packages will be upgraded:
  evolution-data-server
1 upgraded, 3 newly installed, 0 to remove and 46 not upgraded.
24 not fully installed or removed.
Need to get 0 B/2,958 kB of archives.
After this operation, 9,530 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Selecting previously unselected package evolution-data-server.
(Reading database ... 281043 files and directories currently installed.)
Preparing to unpack .../evolution-data-server_3.18.5-1ubuntu1.1_amd64.deb ...
Unpacking evolution-data-server (3.18.5-1ubuntu1.1) over (3.18.5-1ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/evolution-data-server_3.18.5-1ubuntu1.1_amd64.deb (--unpack):
 unable to create '/usr/lib/evolution/evolution-user-prompter.dpkg-new' (while processing './usr/lib/evolution/evolution-user-prompter'): Permission denied
Preparing to unpack .../libevolution_3.18.5.2-0ubuntu3.2_amd64.deb ...
Unpacking libevolution (3.18.5.2-0ubuntu3.2) ...
dpkg: error processing archive /var/cache/apt/archives/libevolution_3.18.5.2-0ubuntu3.2_amd64.deb (--unpack):
 unable to create '/usr/lib/evolution/evolution-backup.dpkg-new' (while processing './usr/lib/evolution/evolution-backup'): Permission denied
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../evolution_3.18.5.2-0ubuntu3.2_amd64.deb ...
Unpacking evolution (3.18.5.2-0ubuntu3.2) ...
dpkg: error processing archive /var/cache/apt/archives/evolution_3.18.5.2-0ubuntu3.2_amd64.deb (--unpack):
 error creating directory './usr/lib/evolution/plugins': Permission denied
Preparing to unpack .../evolution-plugins_3.18.5.2-0ubuntu3.2_amd64.deb ...
Unpacking evolution-plugins (3.18.5.2-0ubuntu3.2) ...
dpkg: error processing archive /var/cache/apt/archives/evolution-plugins_3.18.5.2-0ubuntu3.2_amd64.deb (--unpack):
 error creating directory './usr/lib/evolution/plugins': Permission denied
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.2) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20180209-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/evolution-data-server_3.18.5-1ubuntu1.1_amd64.deb
 /var/cache/apt/archives/libevolution_3.18.5.2-0ubuntu3.2_amd64.deb
 /var/cache/apt/archives/evolution_3.18.5.2-0ubuntu3.2_amd64.deb
 /var/cache/apt/archives/evolution-plugins_3.18.5.2-0ubuntu3.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)





```

So if someone could, please help me figure out how I may get rid of Evolution, evolution data server, camel, and all the rest so I can use apt again?

---

### Post by samyscoub2 on 2018-07-28
Same thing since today. Surely a bad generated package ...
We have to wait a new one

---

### Post by #&amp;thj^% on 2018-07-28
> **bvargo said:**
> Somehow Evolution broke.  I don't use/want a local email/calendar/contact client/server, not the least of which is Evolution.  I have no idea if I have previously tried to get rid of it but in any case, it is broken and now so is APT.

I don't know how to get rid of it (I'm very much hoping it isn't integral to the functioning of Ubuntu e.g. some Windows applications like IE) and now I cannot use APT:

So if someone could, please help me figure out how I may get rid of Evolution, evolution data server, camel, and all the rest so I can use apt again?
**_This could get real messy see this:_** [https://askubuntu.com/questions/315640/how-do-i-completely-remove-evolution](https://askubuntu.com/questions/315640/how-do-i-completely-remove-evolution)
NOTE:If you are successful you will need to re-install "gnome panel". to install just do:

```
sudo apt install gnome-panel

```

---

### Post by bvargo on 2018-07-28
@samysoub2, do you know if anyone has submitted a bug for this? honestly, evolution was just a PITA that I'd just ignored but this is something I can't...which brings me to...

@1fallen, it looks like the second option (linking the Evolution processes to null) is easier than removing everything. I just looked and on my desktop there aren't any processes named evolution or camel running so that is good I guess. Nothing like the problems described on askubuntu.

Anyway, the problem persists and if it is helpful here's the last 250 lines from /var/log/dpkg.log (i.e., a whole lot of fail):

```

2018-07-28 06:04:26 startup archives unpack
2018-07-28 06:04:26 upgrade evolution-data-server:amd64 3.18.5-1ubuntu1 3.18.5-1ubuntu1.1
2018-07-28 06:04:26 status half-installed evolution-data-server:amd64 3.18.5-1ubuntu1
2018-07-28 06:04:27 status half-installed evolution-data-server:amd64 3.18.5-1ubuntu1
2018-07-28 06:04:27 install libedata-cal-1.2-28:amd64 <none> 3.18.5-1ubuntu1.1
2018-07-28 06:04:27 status triggers-pending libc-bin:amd64 2.23-0ubuntu10
2018-07-28 06:04:27 status half-installed libedata-cal-1.2-28:amd64 3.18.5-1ubuntu1.1
2018-07-28 06:04:27 status unpacked libedata-cal-1.2-28:amd64 3.18.5-1ubuntu1.1
2018-07-28 06:04:27 status unpacked libedata-cal-1.2-28:amd64 3.18.5-1ubuntu1.1
2018-07-28 06:04:27 trigproc libc-bin:amd64 2.23-0ubuntu10 <none>
2018-07-28 06:04:27 status half-configured libc-bin:amd64 2.23-0ubuntu10
2018-07-28 06:04:27 status installed libc-bin:amd64 2.23-0ubuntu10
2018-07-28 06:04:32 startup packages remove
2018-07-28 06:04:32 status half-installed evolution-data-server:amd64 3.18.5-1ubuntu1
2018-07-28 06:04:32 remove evolution-data-server:amd64 3.18.5-1ubuntu1 <none>
2018-07-28 06:04:32 status half-installed evolution-data-server:amd64 3.18.5-1ubuntu1
2018-07-28 06:04:32 status half-installed evolution-data-server-online-accounts:amd64 3.18.5-1ubuntu1.1
2018-07-28 06:04:32 remove evolution-data-server-online-accounts:amd64 3.18.5-1ubuntu1.1 <none>
2018-07-28 06:04:32 status triggers-pending libc-bin:amd64 2.23-0ubuntu10
2018-07-28 06:04:32 status half-installed evolution-data-server-online-accounts:amd64 3.18.5-1ubuntu1.1
2018-07-28 06:04:32 status triggers-pending desktop-file-utils:amd64 0.22-1ubuntu5.2
2018-07-28 06:04:32 status triggers-pending bamfdaemon:amd64 0.5.3~bzr0+16.04.20180209-0ubuntu1
2018-07-28 06:04:32 status triggers-pending gnome-menus:amd64 3.13.3-6ubuntu3.1
2018-07-28 06:04:32 status triggers-pending mime-support:all 3.59ubuntu1
2018-07-28 06:04:32 status unpacked libedata-cal-1.2-28:amd64 3.18.5-1ubuntu1.1
2018-07-28 06:04:32 remove libedata-cal-1.2-28:amd64 3.18.5-1ubuntu1.1 <none>
2018-07-28 06:04:32 status half-installed libedata-cal-1.2-28:amd64 3.18.5-1ubuntu1.1
2018-07-28 06:04:32 status config-files libedata-cal-1.2-28:amd64 3.18.5-1ubuntu1.1
2018-07-28 06:04:32 status config-files libedata-cal-1.2-28:amd64 3.18.5-1ubuntu1.1
2018-07-28 06:04:32 status config-files libedata-cal-1.2-28:amd64 3.18.5-1ubuntu1.1
2018-07-28 06:04:32 status not-installed libedata-cal-1.2-28:amd64 <none>
2018-07-28 06:04:32 trigproc libc-bin:amd64 2.23-0ubuntu10 <none>
2018-07-28 06:04:32 status half-configured libc-bin:amd64 2.23-0ubuntu10
2018-07-28 06:04:32 status installed libc-bin:amd64 2.23-0ubuntu10
2018-07-28 06:04:32 trigproc desktop-file-utils:amd64 0.22-1ubuntu5.2 <none>
2018-07-28 06:04:32 status half-configured desktop-file-utils:amd64 0.22-1ubuntu5.2
2018-07-28 06:04:32 status installed desktop-file-utils:amd64 0.22-1ubuntu5.2
2018-07-28 06:04:32 trigproc bamfdaemon:amd64 0.5.3~bzr0+16.04.20180209-0ubuntu1 <none>
2018-07-28 06:04:32 status half-configured bamfdaemon:amd64 0.5.3~bzr0+16.04.20180209-0ubuntu1
2018-07-28 06:04:33 status installed bamfdaemon:amd64 0.5.3~bzr0+16.04.20180209-0ubuntu1
2018-07-28 06:04:33 trigproc gnome-menus:amd64 3.13.3-6ubuntu3.1 <none>
2018-07-28 06:04:33 status half-configured gnome-menus:amd64 3.13.3-6ubuntu3.1
2018-07-28 06:04:33 status installed gnome-menus:amd64 3.13.3-6ubuntu3.1
2018-07-28 06:04:33 trigproc mime-support:all 3.59ubuntu1 <none>
2018-07-28 06:04:33 status half-configured mime-support:all 3.59ubuntu1
2018-07-28 06:04:33 status installed mime-support:all 3.59ubuntu1
2018-07-28 06:19:51 startup packages remove
2018-07-28 06:19:51 status half-installed evolution-data-server:amd64 3.18.5-1ubuntu1
2018-07-28 06:19:51 remove evolution-data-server:amd64 3.18.5-1ubuntu1 <none>
2018-07-28 06:19:51 status half-installed evolution-data-server:amd64 3.18.5-1ubuntu1
2018-07-28 06:19:51 status unpacked gnome-applets:amd64 3.18.2-1
2018-07-28 06:19:51 remove gnome-applets:amd64 3.18.2-1 <none>
2018-07-28 06:19:51 status half-installed gnome-applets:amd64 3.18.2-1
2018-07-28 06:19:51 status triggers-pending man-db:amd64 2.7.5-1
2018-07-28 06:19:51 status config-files gnome-applets:amd64 3.18.2-1
2018-07-28 06:19:51 status config-files gnome-applets:amd64 3.18.2-1
2018-07-28 06:19:51 status config-files gnome-applets:amd64 3.18.2-1
2018-07-28 06:19:51 status not-installed gnome-applets:amd64 <none>
2018-07-28 06:19:51 status installed gnome-session-flashback:all 1:3.18.2-1ubuntu1
2018-07-28 06:19:51 remove gnome-session-flashback:all 1:3.18.2-1ubuntu1 <none>
2018-07-28 06:19:51 status half-configured gnome-session-flashback:all 1:3.18.2-1ubuntu1
2018-07-28 06:19:51 status half-installed gnome-session-flashback:all 1:3.18.2-1ubuntu1
2018-07-28 06:19:51 status triggers-pending desktop-file-utils:amd64 0.22-1ubuntu5.2
2018-07-28 06:19:51 status triggers-pending bamfdaemon:amd64 0.5.3~bzr0+16.04.20180209-0ubuntu1
2018-07-28 06:19:51 status triggers-pending gnome-menus:amd64 3.13.3-6ubuntu3.1
2018-07-28 06:19:51 status triggers-pending mime-support:all 3.59ubuntu1
2018-07-28 06:19:51 status config-files gnome-session-flashback:all 1:3.18.2-1ubuntu1
2018-07-28 06:19:51 status config-files gnome-session-flashback:all 1:3.18.2-1ubuntu1
2018-07-28 06:19:51 status unpacked gnome-panel:amd64 1:3.18.3-0ubuntu0.1
2018-07-28 06:19:51 remove gnome-panel:amd64 1:3.18.3-0ubuntu0.1 <none>
2018-07-28 06:19:51 status half-installed gnome-panel:amd64 1:3.18.3-0ubuntu0.1
2018-07-28 06:19:51 status config-files gnome-panel:amd64 1:3.18.3-0ubuntu0.1
2018-07-28 06:19:51 status config-files gnome-panel:amd64 1:3.18.3-0ubuntu0.1
2018-07-28 06:19:51 status config-files gnome-panel:amd64 1:3.18.3-0ubuntu0.1
2018-07-28 06:19:51 status not-installed gnome-panel:amd64 <none>
2018-07-28 06:19:51 trigproc man-db:amd64 2.7.5-1 <none>
2018-07-28 06:19:51 status half-configured man-db:amd64 2.7.5-1
2018-07-28 06:19:51 status installed man-db:amd64 2.7.5-1
2018-07-28 06:19:51 trigproc desktop-file-utils:amd64 0.22-1ubuntu5.2 <none>
2018-07-28 06:19:51 status half-configured desktop-file-utils:amd64 0.22-1ubuntu5.2
2018-07-28 06:19:51 status installed desktop-file-utils:amd64 0.22-1ubuntu5.2
2018-07-28 06:19:51 trigproc bamfdaemon:amd64 0.5.3~bzr0+16.04.20180209-0ubuntu1 <none>
2018-07-28 06:19:51 status half-configured bamfdaemon:amd64 0.5.3~bzr0+16.04.20180209-0ubuntu1
2018-07-28 06:19:51 status installed bamfdaemon:amd64 0.5.3~bzr0+16.04.20180209-0ubuntu1
2018-07-28 06:19:51 trigproc gnome-menus:amd64 3.13.3-6ubuntu3.1 <none>
2018-07-28 06:19:51 status half-configured gnome-menus:amd64 3.13.3-6ubuntu3.1
2018-07-28 06:19:51 status installed gnome-menus:amd64 3.13.3-6ubuntu3.1
2018-07-28 06:19:51 trigproc mime-support:all 3.59ubuntu1 <none>
2018-07-28 06:19:51 status half-configured mime-support:all 3.59ubuntu1
2018-07-28 06:19:52 status installed mime-support:all 3.59ubuntu1
2018-07-28 07:58:34 startup archives unpack
2018-07-28 07:58:34 upgrade evolution-data-server:amd64 3.18.5-1ubuntu1 3.18.5-1ubuntu1.1
2018-07-28 07:58:34 status half-installed evolution-data-server:amd64 3.18.5-1ubuntu1
2018-07-28 07:58:34 status half-installed evolution-data-server:amd64 3.18.5-1ubuntu1
2018-07-28 07:58:34 install libedata-cal-1.2-28:amd64 <none> 3.18.5-1ubuntu1.1
2018-07-28 07:58:34 status triggers-pending libc-bin:amd64 2.23-0ubuntu10
2018-07-28 07:58:34 status half-installed libedata-cal-1.2-28:amd64 3.18.5-1ubuntu1.1
2018-07-28 07:58:34 status unpacked libedata-cal-1.2-28:amd64 3.18.5-1ubuntu1.1
2018-07-28 07:58:34 status unpacked libedata-cal-1.2-28:amd64 3.18.5-1ubuntu1.1
2018-07-28 07:58:34 install gnome-panel:amd64 <none> 1:3.18.3-0ubuntu0.1
2018-07-28 07:58:34 status half-installed gnome-panel:amd64 1:3.18.3-0ubuntu0.1
2018-07-28 07:58:35 status triggers-pending desktop-file-utils:amd64 0.22-1ubuntu5.2
2018-07-28 07:58:35 status triggers-pending bamfdaemon:amd64 0.5.3~bzr0+16.04.20180209-0ubuntu1
2018-07-28 07:58:35 status triggers-pending gnome-menus:amd64 3.13.3-6ubuntu3.1
2018-07-28 07:58:35 status triggers-pending mime-support:all 3.59ubuntu1
2018-07-28 07:58:35 status triggers-pending man-db:amd64 2.7.5-1
2018-07-28 07:58:35 status unpacked gnome-panel:amd64 1:3.18.3-0ubuntu0.1
2018-07-28 07:58:35 status unpacked gnome-panel:amd64 1:3.18.3-0ubuntu0.1
2018-07-28 07:58:35 install gnome-applets:amd64 <none> 3.18.2-1
2018-07-28 07:58:35 status half-installed gnome-applets:amd64 3.18.2-1
2018-07-28 07:58:35 status unpacked gnome-applets:amd64 3.18.2-1
2018-07-28 07:58:35 status unpacked gnome-applets:amd64 3.18.2-1
2018-07-28 07:58:35 install gnome-session-flashback:all 1:3.18.2-1ubuntu1 1:3.18.2-1ubuntu1
2018-07-28 07:58:35 status half-installed gnome-session-flashback:all 1:3.18.2-1ubuntu1
2018-07-28 07:58:35 status unpacked gnome-session-flashback:all 1:3.18.2-1ubuntu1
2018-07-28 07:58:35 status unpacked gnome-session-flashback:all 1:3.18.2-1ubuntu1
2018-07-28 07:58:35 trigproc libc-bin:amd64 2.23-0ubuntu10 <none>
2018-07-28 07:58:35 status half-configured libc-bin:amd64 2.23-0ubuntu10
2018-07-28 07:58:35 status installed libc-bin:amd64 2.23-0ubuntu10
2018-07-28 07:58:35 trigproc desktop-file-utils:amd64 0.22-1ubuntu5.2 <none>
2018-07-28 07:58:35 status half-configured desktop-file-utils:amd64 0.22-1ubuntu5.2
2018-07-28 07:58:35 status installed desktop-file-utils:amd64 0.22-1ubuntu5.2
2018-07-28 07:58:35 trigproc bamfdaemon:amd64 0.5.3~bzr0+16.04.20180209-0ubuntu1 <none>
2018-07-28 07:58:35 status half-configured bamfdaemon:amd64 0.5.3~bzr0+16.04.20180209-0ubuntu1
2018-07-28 07:58:35 status installed bamfdaemon:amd64 0.5.3~bzr0+16.04.20180209-0ubuntu1
2018-07-28 07:58:35 trigproc gnome-menus:amd64 3.13.3-6ubuntu3.1 <none>
2018-07-28 07:58:35 status half-configured gnome-menus:amd64 3.13.3-6ubuntu3.1
2018-07-28 07:58:35 status installed gnome-menus:amd64 3.13.3-6ubuntu3.1
2018-07-28 07:58:35 trigproc mime-support:all 3.59ubuntu1 <none>
2018-07-28 07:58:35 status half-configured mime-support:all 3.59ubuntu1
2018-07-28 07:58:35 status installed mime-support:all 3.59ubuntu1
2018-07-28 07:58:35 trigproc man-db:amd64 2.7.5-1 <none>
2018-07-28 07:58:35 status half-configured man-db:amd64 2.7.5-1
2018-07-28 07:58:35 status installed man-db:amd64 2.7.5-1
2018-07-28 08:24:02 startup packages remove
2018-07-28 08:24:02 status half-installed evolution-data-server:amd64 3.18.5-1ubuntu1
2018-07-28 08:24:02 remove evolution-data-server:amd64 3.18.5-1ubuntu1 <none>
2018-07-28 08:24:02 status half-installed evolution-data-server:amd64 3.18.5-1ubuntu1
2018-07-28 08:24:02 status half-installed evolution-data-server-online-accounts:amd64 3.18.5-1ubuntu1.1
2018-07-28 08:24:02 remove evolution-data-server-online-accounts:amd64 3.18.5-1ubuntu1.1 <none>
2018-07-28 08:24:02 status triggers-pending libc-bin:amd64 2.23-0ubuntu10
2018-07-28 08:24:02 status half-installed evolution-data-server-online-accounts:amd64 3.18.5-1ubuntu1.1
2018-07-28 08:24:02 status triggers-pending desktop-file-utils:amd64 0.22-1ubuntu5.2
2018-07-28 08:24:02 status triggers-pending bamfdaemon:amd64 0.5.3~bzr0+16.04.20180209-0ubuntu1
2018-07-28 08:24:02 status triggers-pending gnome-menus:amd64 3.13.3-6ubuntu3.1
2018-07-28 08:24:02 status triggers-pending mime-support:all 3.59ubuntu1
2018-07-28 08:24:02 trigproc libc-bin:amd64 2.23-0ubuntu10 <none>
2018-07-28 08:24:02 status half-configured libc-bin:amd64 2.23-0ubuntu10
2018-07-28 08:24:02 status installed libc-bin:amd64 2.23-0ubuntu10
2018-07-28 08:24:02 trigproc desktop-file-utils:amd64 0.22-1ubuntu5.2 <none>
2018-07-28 08:24:02 status half-configured desktop-file-utils:amd64 0.22-1ubuntu5.2
2018-07-28 08:24:02 status installed desktop-file-utils:amd64 0.22-1ubuntu5.2
2018-07-28 08:24:02 trigproc bamfdaemon:amd64 0.5.3~bzr0+16.04.20180209-0ubuntu1 <none>
2018-07-28 08:24:02 status half-configured bamfdaemon:amd64 0.5.3~bzr0+16.04.20180209-0ubuntu1
2018-07-28 08:24:02 status installed bamfdaemon:amd64 0.5.3~bzr0+16.04.20180209-0ubuntu1
2018-07-28 08:24:02 trigproc gnome-menus:amd64 3.13.3-6ubuntu3.1 <none>
2018-07-28 08:24:02 status half-configured gnome-menus:amd64 3.13.3-6ubuntu3.1
2018-07-28 08:24:02 status installed gnome-menus:amd64 3.13.3-6ubuntu3.1
2018-07-28 08:24:02 trigproc mime-support:all 3.59ubuntu1 <none>
2018-07-28 08:24:02 status half-configured mime-support:all 3.59ubuntu1
2018-07-28 08:24:03 status installed mime-support:all 3.59ubuntu1
2018-07-28 08:24:04 startup packages configure
2018-07-28 08:24:04 configure evolution-common:all 3.18.5.2-0ubuntu3.2 <none>
2018-07-28 08:24:04 status unpacked evolution-common:all 3.18.5.2-0ubuntu3.2
2018-07-28 08:24:04 status half-configured evolution-common:all 3.18.5.2-0ubuntu3.2
2018-07-28 08:24:04 status installed evolution-common:all 3.18.5.2-0ubuntu3.2
2018-07-28 08:24:04 configure evolution-data-server-common:all 3.18.5-1ubuntu1.1 <none>
2018-07-28 08:24:04 status unpacked evolution-data-server-common:all 3.18.5-1ubuntu1.1
2018-07-28 08:24:04 status half-configured evolution-data-server-common:all 3.18.5-1ubuntu1.1
2018-07-28 08:24:04 status installed evolution-data-server-common:all 3.18.5-1ubuntu1.1
2018-07-28 08:24:04 configure libcamel-1.2-54:amd64 3.18.5-1ubuntu1.1 <none>
2018-07-28 08:24:04 status triggers-pending libc-bin:amd64 2.23-0ubuntu10
2018-07-28 08:24:04 status unpacked libcamel-1.2-54:amd64 3.18.5-1ubuntu1.1
2018-07-28 08:24:04 status half-configured libcamel-1.2-54:amd64 3.18.5-1ubuntu1.1
2018-07-28 08:24:04 status installed libcamel-1.2-54:amd64 3.18.5-1ubuntu1.1
2018-07-28 08:24:04 configure libedataserver-1.2-21:amd64 3.18.5-1ubuntu1.1 <none>
2018-07-28 08:24:04 status unpacked libedataserver-1.2-21:amd64 3.18.5-1ubuntu1.1
2018-07-28 08:24:04 status half-configured libedataserver-1.2-21:amd64 3.18.5-1ubuntu1.1
2018-07-28 08:24:04 status installed libedataserver-1.2-21:amd64 3.18.5-1ubuntu1.1
2018-07-28 08:24:04 configure libecal-1.2-19:amd64 3.18.5-1ubuntu1.1 <none>
2018-07-28 08:24:04 status unpacked libecal-1.2-19:amd64 3.18.5-1ubuntu1.1
2018-07-28 08:24:04 status half-configured libecal-1.2-19:amd64 3.18.5-1ubuntu1.1
2018-07-28 08:24:04 status installed libecal-1.2-19:amd64 3.18.5-1ubuntu1.1
2018-07-28 08:24:04 configure gnome-panel:amd64 1:3.18.3-0ubuntu0.1 <none>
2018-07-28 08:24:04 status unpacked gnome-panel:amd64 1:3.18.3-0ubuntu0.1
2018-07-28 08:24:04 status half-configured gnome-panel:amd64 1:3.18.3-0ubuntu0.1
2018-07-28 08:24:04 status installed gnome-panel:amd64 1:3.18.3-0ubuntu0.1
2018-07-28 08:24:04 configure libebackend-1.2-10:amd64 3.18.5-1ubuntu1.1 <none>
2018-07-28 08:24:04 status unpacked libebackend-1.2-10:amd64 3.18.5-1ubuntu1.1
2018-07-28 08:24:04 status half-configured libebackend-1.2-10:amd64 3.18.5-1ubuntu1.1
2018-07-28 08:24:04 status installed libebackend-1.2-10:amd64 3.18.5-1ubuntu1.1
2018-07-28 08:24:04 configure libebook-contacts-1.2-2:amd64 3.18.5-1ubuntu1.1 <none>
2018-07-28 08:24:04 status unpacked libebook-contacts-1.2-2:amd64 3.18.5-1ubuntu1.1
2018-07-28 08:24:04 status half-configured libebook-contacts-1.2-2:amd64 3.18.5-1ubuntu1.1
2018-07-28 08:24:04 status installed libebook-contacts-1.2-2:amd64 3.18.5-1ubuntu1.1
2018-07-28 08:24:04 configure libedata-cal-1.2-28:amd64 3.18.5-1ubuntu1.1 <none>
2018-07-28 08:24:04 status unpacked libedata-cal-1.2-28:amd64 3.18.5-1ubuntu1.1
2018-07-28 08:24:04 status half-configured libedata-cal-1.2-28:amd64 3.18.5-1ubuntu1.1
2018-07-28 08:24:04 status installed libedata-cal-1.2-28:amd64 3.18.5-1ubuntu1.1
2018-07-28 08:24:04 configure libedata-book-1.2-25:amd64 3.18.5-1ubuntu1.1 <none>
2018-07-28 08:24:04 status unpacked libedata-book-1.2-25:amd64 3.18.5-1ubuntu1.1
2018-07-28 08:24:04 status half-configured libedata-book-1.2-25:amd64 3.18.5-1ubuntu1.1
2018-07-28 08:24:04 status installed libedata-book-1.2-25:amd64 3.18.5-1ubuntu1.1
2018-07-28 08:24:04 configure gnome-applets:amd64 3.18.2-1 <none>
2018-07-28 08:24:04 status unpacked gnome-applets:amd64 3.18.2-1
2018-07-28 08:24:04 status half-configured gnome-applets:amd64 3.18.2-1
2018-07-28 08:24:04 status installed gnome-applets:amd64 3.18.2-1
2018-07-28 08:24:04 configure gnome-session-flashback:all 1:3.18.2-1ubuntu1 <none>
2018-07-28 08:24:04 status unpacked gnome-session-flashback:all 1:3.18.2-1ubuntu1
2018-07-28 08:24:04 status unpacked gnome-session-flashback:all 1:3.18.2-1ubuntu1
2018-07-28 08:24:04 status half-configured gnome-session-flashback:all 1:3.18.2-1ubuntu1
2018-07-28 08:24:04 status installed gnome-session-flashback:all 1:3.18.2-1ubuntu1
2018-07-28 08:24:05 configure libebook-1.2-16:amd64 3.18.5-1ubuntu1.1 <none>
2018-07-28 08:24:05 status unpacked libebook-1.2-16:amd64 3.18.5-1ubuntu1.1
2018-07-28 08:24:05 status half-configured libebook-1.2-16:amd64 3.18.5-1ubuntu1.1
2018-07-28 08:24:05 status installed libebook-1.2-16:amd64 3.18.5-1ubuntu1.1
2018-07-28 08:24:05 trigproc libc-bin:amd64 2.23-0ubuntu10 <none>
2018-07-28 08:24:05 status half-configured libc-bin:amd64 2.23-0ubuntu10
2018-07-28 08:24:05 status installed libc-bin:amd64 2.23-0ubuntu10
2018-07-28 08:26:44 startup packages remove
2018-07-28 08:26:44 status half-installed evolution-data-server:amd64 3.18.5-1ubuntu1
2018-07-28 08:26:44 remove evolution-data-server:amd64 3.18.5-1ubuntu1 <none>
2018-07-28 08:26:44 status half-installed evolution-data-server:amd64 3.18.5-1ubuntu1
2018-07-28 08:26:44 status half-installed evolution-data-server-online-accounts:amd64 3.18.5-1ubuntu1.1
2018-07-28 08:26:44 remove evolution-data-server-online-accounts:amd64 3.18.5-1ubuntu1.1 <none>
2018-07-28 08:26:44 status triggers-pending libc-bin:amd64 2.23-0ubuntu10
2018-07-28 08:26:44 status half-installed evolution-data-server-online-accounts:amd64 3.18.5-1ubuntu1.1
2018-07-28 08:26:44 status triggers-pending desktop-file-utils:amd64 0.22-1ubuntu5.2
2018-07-28 08:26:44 status triggers-pending bamfdaemon:amd64 0.5.3~bzr0+16.04.20180209-0ubuntu1
2018-07-28 08:26:44 status triggers-pending gnome-menus:amd64 3.13.3-6ubuntu3.1
2018-07-28 08:26:44 status triggers-pending mime-support:all 3.59ubuntu1
2018-07-28 08:26:44 trigproc libc-bin:amd64 2.23-0ubuntu10 <none>
2018-07-28 08:26:44 status half-configured libc-bin:amd64 2.23-0ubuntu10
2018-07-28 08:26:44 status installed libc-bin:amd64 2.23-0ubuntu10
2018-07-28 08:26:44 trigproc desktop-file-utils:amd64 0.22-1ubuntu5.2 <none>
2018-07-28 08:26:44 status half-configured desktop-file-utils:amd64 0.22-1ubuntu5.2
2018-07-28 08:26:44 status installed desktop-file-utils:amd64 0.22-1ubuntu5.2
2018-07-28 08:26:44 trigproc bamfdaemon:amd64 0.5.3~bzr0+16.04.20180209-0ubuntu1 <none>
2018-07-28 08:26:44 status half-configured bamfdaemon:amd64 0.5.3~bzr0+16.04.20180209-0ubuntu1
2018-07-28 08:26:44 status installed bamfdaemon:amd64 0.5.3~bzr0+16.04.20180209-0ubuntu1
2018-07-28 08:26:44 trigproc gnome-menus:amd64 3.13.3-6ubuntu3.1 <none>
2018-07-28 08:26:44 status half-configured gnome-menus:amd64 3.13.3-6ubuntu3.1
2018-07-28 08:26:44 status installed gnome-menus:amd64 3.13.3-6ubuntu3.1
2018-07-28 08:26:44 trigproc mime-support:all 3.59ubuntu1 <none>
2018-07-28 08:26:44 status half-configured mime-support:all 3.59ubuntu1
2018-07-28 08:26:44 status installed mime-support:all 3.59ubuntu1

```

---

### Post by #&amp;thj^% on 2018-07-28
My point was it would have been better to start with link provided first, :(
Someone else has the same issue here: [https://gist.github.com/Spijkervet/c4853cd389f9d0f966108ae8f23c2a3b](https://gist.github.com/Spijkervet/c4853cd389f9d0f966108ae8f23c2a3b)
And that was 2 months ago.
But your mess is something that I have no solution for ATM.
And I'm not sure this solely pertains to evolution alone.
Also maybe this will shed something useful for others to see.
```
dpkg -l
```

---

### Post by mc4man on 2018-07-28
Have you disabled the Security and or Updates repos in your software sources?

---

### Post by bvargo on 2018-07-28
@1fallen:  not sure what to make of the link you sent but here's the dpkg -l:  [https://paste.ubuntu.com/p/YW8ntBMB6P/](https://paste.ubuntu.com/p/YW8ntBMB6P/)
@mc4man:  No, I don't have any present knowledge of making changes such as you mentioned.  It should be noted that I'm not saying it didn't happen, just that I don't specifically remember doing anything like what you are suggesting.

---

### Post by bvargo on 2018-07-28
Here's my sources.list:  [https://paste.ubuntu.com/p/wjMYKVqzCH/](https://paste.ubuntu.com/p/wjMYKVqzCH/)

---

### Post by #&amp;thj^% on 2018-07-28
I'm not trying to sound like a bad guy here, just the messenger of bad news. (I wish it was the opposite)
This is where things went horribly wrong "purge evolution-data-server" it just has to many things attached to it and a dependency of gnome-panel, which in turn is a dependency of quite a lot of gnome stuff. Removing it will remove half your desktop along with it.
If you still had access to apt you could try to reinstall "ubuntu-desktop" 
Other than that I have nothing else relevant to add >>>except a re-install.
Sorry About that.

---

### Post by bvargo on 2018-07-28
> **1fallen said:**
> I'm not trying to sound like a bad guy here, just the messenger of bad news. (I wish it was the opposite)
This is where things went horribly wrong "purge evolution-data-server" it just has to many things attached to it and a dependency of gnome-panel, which in turn is a dependency of quite a lot of gnome stuff. Removing it will remove half your desktop along with it.
If you still had access to apt you could try to reinstall "ubuntu-desktop" 
Other than that I have nothing else relevant to add >>>except a re-install.
Sorry About that.

I understand...but I don't think it actually purged the evolution-data-server or anything else since I don't think apt was actually doing anything when I was issuing commands.  That may be wishful thinking so if there is some log to check, please let me know.
Also, it seems that evolution-data-server is still installed:

```

**:/etc/apt/sources.list.d# apt show evolution-data-server -a**
Package: evolution-data-server
Version: 3.18.5-1ubuntu1.1
Priority: optional
Section: gnome
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Evolution Maintainers <pkg-evolution-maintainers@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 1,860 kB
Depends: libc6 (>= 2.14), libcamel-1.2-54 (= 3.18.5-1ubuntu1.1), libdb5.3, libebackend-1.2-10 (>= 3.18.0), libebook-1.2-16 (>= 3.17), libebook-contacts-1.2-2 (>= 3.16.2), libecal-1.2-19 (>= 3.17), libedata-book-1.2-25 (>= 3.17), libedata-cal-1.2-28 (>= 3.17), libedataserver-1.2-21 (>= 3.17.90), libgcr-base-3-1 (>= 3.8.0), libgcr-ui-3-1 (>= 3.8.0), libgdata22 (>= 0.15.0), libglib2.0-0 (>= 2.40), libgtk-3-0 (>= 3.0.0), libgweather-3-6 (>= 3.10.0), libical1a (>= 1.0), libldap-2.4-2 (>= 2.4.7), libpango-1.0-0 (>= 1.14.0), libsecret-1-0 (>= 0.7), libsoup2.4-1 (>= 2.42), libxml2 (>= 2.9.0), evolution-data-server-common (= 3.18.5-1ubuntu1.1), gnome-keyring
Recommends: evolution-data-server-online-accounts
Suggests: evolution, evolution-data-server-dbg (= 3.18.5-1ubuntu1.1)
Breaks: libebook-1.2-13 (<< 3.6), libedataserverui-3.0-5
Homepage: https://wiki.gnome.org/Apps/Evolution
Task: ubuntu-desktop, ubuntu-usb, edubuntu-desktop, edubuntu-usb, ubuntu-gnome-desktop, ubuntu-touch, ubuntukylin-desktop
Supported: 5y
Download-Size: 425 kB
APT-Sources: http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
Description: evolution database backend server
 The data server, called "Evolution Data Server" is responsible for managing
 mail, calendar, addressbook, tasks and memo information.


Package: evolution-data-server
Version: 3.18.5-1ubuntu1
Priority: optional
Section: gnome
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Evolution Maintainers <pkg-evolution-maintainers@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 1,860 kB
Depends: libc6 (>= 2.14), libcamel-1.2-54 (= 3.18.5-1ubuntu1), libdb5.3, libebackend-1.2-10 (>= 3.18.0), libebook-1.2-16 (>= 3.17), libebook-contacts-1.2-2 (>= 3.16.2), libecal-1.2-19 (>= 3.17), libedata-book-1.2-25 (>= 3.17), libedata-cal-1.2-28 (>= 3.17), libedataserver-1.2-21 (>= 3.17.90), libgcr-base-3-1 (>= 3.8.0), libgcr-ui-3-1 (>= 3.8.0), libgdata22 (>= 0.15.0), libglib2.0-0 (>= 2.40), libgtk-3-0 (>= 3.0.0), libgweather-3-6 (>= 3.10.0), libical1a (>= 1.0), libldap-2.4-2 (>= 2.4.7), libpango-1.0-0 (>= 1.14.0), libsecret-1-0 (>= 0.7), libsoup2.4-1 (>= 2.42), libxml2 (>= 2.9.0), evolution-data-server-common (= 3.18.5-1ubuntu1), gnome-keyring
Recommends: evolution-data-server-online-accounts
Suggests: evolution, evolution-data-server-dbg (= 3.18.5-1ubuntu1)
Breaks: libebook-1.2-13 (<< 3.6), libedataserverui-3.0-5
Homepage: https://wiki.gnome.org/Apps/Evolution
Task: ubuntu-desktop, ubuntu-usb, edubuntu-desktop, edubuntu-usb, ubuntu-gnome-desktop, ubuntu-touch, ubuntukylin-desktop
Supported: 5y
Download-Size: 427 kB
APT-Manual-Installed: yes
APT-Sources: http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
Description: evolution database backend server
 The data server, called "Evolution Data Server" is responsible for managing
 mail, calendar, addressbook, tasks and memo information.


**# dpkg -l evolution-data-server**
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                                              Version                               Architecture                          Description
+++-=================================================================-=====================================-=====================================-=======================================================================================================================================
iH  evolution-data-server                                             3.18.5-1ubuntu1                       amd64                                 evolution database backend server



```

---

### Post by #&amp;thj^% on 2018-07-28
According to dpkg -l and the errors in /var/log/dpkg.log 
"rH  evolution-data-server && rH  evolution-data-server-online-accounts"
The "r" means removed the "H" means half installed
Also shown IE: 
```
2018-07-28 06:04:32 status half-installed evolution-data-server:amd64 3.18.5-1ubuntu1
2018-07-28 06:04:32 remove evolution-data-server:amd64 3.18.5-1ubuntu1 <none>
2018-07-28 06:04:32 status half-installed evolution-data-server:amd64 3.18.5-1ubuntu1
2018-07-28 06:04:32 status half-installed evolution-data-server-online-accounts:amd64 3.18.5-1ubuntu1.1
```
Also this:
```
# dpkg -l evolution-data-server
Desired=Unknown/Install/Remove/Purge/Hold
[B]| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)[/B]
|
```

It might be wise to not re-boot yet>> in the hopes of solution for you. (Hopefully soon)

---

### Post by bvargo on 2018-07-28
Well, the reboot already happened since my system inexplicably (and for the first time) did a hard reboot when i plugged my headset in...

---

### Post by #&amp;thj^% on 2018-07-28
Well lets hope for some luck here with:
```
sudo apt-get dist-upgrade
```

---

### Post by bvargo on 2018-07-28
Well, I figured out that somehow an immutable flag got set on one of the evolution/components directories...  that seems to have solved it.  I'm still having some issues but at least apt is working, more or less.  It seems like dpkg is still throwing errors.

---

### Post by bvargo on 2018-07-29
So what it came down to was needing to use chattr -R -i on the directories that evolution/camel were in.  No idea how it got that way (chattr and the flags it controls was new to me) but it is working now!

Thank you very much for the help, I just wanted to make sure I closed this out.

---

### Post by #&amp;thj^% on 2018-07-29
I just had to commend you on your efforts and posting back your solution, this is very helpful to the community here.
Nicely done bvargo. :KS
Kind Regards

---

