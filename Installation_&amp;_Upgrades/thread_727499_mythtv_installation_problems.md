---
title: "mythtv installation problems"
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by Chbuntu on 2008-03-17
Ok So, I've tried installing mythtv twice to no avail using this awfully lengthy guide: [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

Here's my errors once I get to installing through the terminal:
(the errors are all near the bottom)

```

erik@erik-desktop:~$ sudo apt-get install mythtv mythtv-themes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdbd-mysql-perl libmyth-0.21-0 libmyth-perl libqt3-mt-mysql mysql-client
  mysql-client-5.0 mysql-server mysql-server-5.0 mythtv-backend mythtv-common
  mythtv-database mythtv-frontend mythtv-transcode-utils
Suggested packages:
  mysql-doc-5.0 tinyca mythtv-doc mythweb xmltv-util mythmusic mythweather
  mythgallery mythvideo mythgame mythstream mytharchive
Recommended packages:
  mailx mythtv-theme-gray-osd mythtv-theme-isthmus mythtv-theme-iulius
  mythtv-theme-iulius-osd mythtv-theme-minimalist-wide mythtv-theme-mythcenter
  mythtv-theme-mythcenter-wide mythtv-theme-retro mythtv-theme-retro-osd
  mythtv-theme-titivillus mythtv-theme-titivillus-osd mythtv-theme-blootube
  mythtv-theme-blootubelite-wide mythtv-theme-blootube-osd
  mythtv-theme-blootube-wide mythtv-theme-glass-wide mythtv-theme-neon-wide
  mythtv-theme-projectgrayhem mythtv-theme-projectgrayhem-osd
  mythtv-theme-projectgrayhem-wide mythtv-theme-mythbuntu
The following NEW packages will be installed:
  libdbd-mysql-perl libmyth-0.21-0 libmyth-perl libqt3-mt-mysql mysql-client
  mysql-client-5.0 mysql-server mysql-server-5.0 mythtv mythtv-backend
  mythtv-common mythtv-database mythtv-frontend mythtv-themes
  mythtv-transcode-utils
0 upgraded, 15 newly installed, 0 to remove and 0 not upgraded.
Need to get 136kB/51.5MB of archives.
After unpacking, 142MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ca.archive.ubuntu.com gutsy/main libdbd-mysql-perl 4.004-2 [136kB]
Fetched 136kB in 1s (85.5kB/s)           
Preconfiguring packages ...
Selecting previously deselected package libdbd-mysql-perl.
(Reading database ... 171761 files and directories currently installed.)
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_4.004-2_i386.deb) ...
Selecting previously deselected package mysql-client-5.0.
Unpacking mysql-client-5.0 (from .../mysql-client-5.0_5.0.45-1ubuntu3.1_i386.deb) ...
Selecting previously deselected package mysql-server-5.0.
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.45-1ubuntu3.1_i386.deb) ...
Selecting previously deselected package mysql-client.
Unpacking mysql-client (from .../mysql-client_5.0.45-1ubuntu3.1_all.deb) ...
Selecting previously deselected package mythtv-common.
Unpacking mythtv-common (from .../mythtv-common_0.21.0-0ubuntu2~gutsy1_all.deb) ...
Selecting previously deselected package mythtv-database.
Unpacking mythtv-database (from .../mythtv-database_0.21.0-0ubuntu2~gutsy1_all.deb) ...
Selecting previously deselected package libqt3-mt-mysql.
Unpacking libqt3-mt-mysql (from .../libqt3-mt-mysql_3%3a3.3.8really3.3.7-0ubuntu11.1_i386.deb) ...
Selecting previously deselected package libmyth-0.21-0.
Unpacking libmyth-0.21-0 (from .../libmyth-0.21-0_0.21.0-0ubuntu2~gutsy1_i386.deb) ...
Selecting previously deselected package mythtv-frontend.
Unpacking mythtv-frontend (from .../mythtv-frontend_0.21.0-0ubuntu2~gutsy1_i386.deb) ...
Selecting previously deselected package mythtv-transcode-utils.
Unpacking mythtv-transcode-utils (from .../mythtv-transcode-utils_0.21.0-0ubuntu2~gutsy1_i386.deb) ...
Selecting previously deselected package libmyth-perl.
Unpacking libmyth-perl (from .../libmyth-perl_0.21.0-0ubuntu2~gutsy1_all.deb) ...
Selecting previously deselected package mythtv-backend.
Unpacking mythtv-backend (from .../mythtv-backend_0.21.0-0ubuntu2~gutsy1_i386.deb) ...
Setting up libdbd-mysql-perl (4.004-2) ...
Setting up mysql-client-5.0 (5.0.45-1ubuntu3.1) ...

Setting up mysql-server-5.0 (5.0.45-1ubuntu3.1) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.

Selecting previously deselected package mythtv.
(Reading database ... 174566 files and directories currently installed.)
Unpacking mythtv (from .../mythtv_0.21.0-0ubuntu2~gutsy1_all.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.0.45-1ubuntu3.1_all.deb) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
Selecting previously deselected package mythtv-themes.
Unpacking mythtv-themes (from .../mythtv-themes_0.21.0-0ubuntu1~gutsy1_all.deb) ...
Setting up mysql-client (5.0.45-1ubuntu3.1) ...
Setting up mythtv-common (0.21.0-0ubuntu2~gutsy1) ...
adduser: Warning: that home directory does not belong to the user you are currently creating.

Setting up mythtv-database (0.21.0-0ubuntu2~gutsy1) ...
 * Starting MySQL database server mysqld                                 [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
Failed to execute SQL: GRANT ALL PRIVILEGES ON mythconverg.* TO Gnome Sane@localhost IDENTIFIED BY 'purple'\nYou have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'Sane@localhost IDENTIFIED BY 'purple'' at line 1 at -e line 8, <> line 1.
dpkg: error processing mythtv-database (--configure):
 subprocess post-installation script returned error exit status 255
Setting up libqt3-mt-mysql (3:3.3.8really3.3.7-0ubuntu11.1) ...
Setting up libmyth-0.21-0 (0.21.0-0ubuntu2~gutsy1) ...

Setting up mythtv-frontend (0.21.0-0ubuntu2~gutsy1) ...

Setting up mythtv-transcode-utils (0.21.0-0ubuntu2~gutsy1) ...
Setting up libmyth-perl (0.21.0-0ubuntu2~gutsy1) ...
Setting up mythtv-backend (0.21.0-0ubuntu2~gutsy1) ...
udev active, devices will be created in /dev/.static/dev/
 * Starting MythTV server: mythbackend                                   [ OK ] 

dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-database (= 0.21.0-0ubuntu2~gutsy1); however:
  Package mythtv-database is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
Setting up mysql-server (5.0.45-1ubuntu3.1) ...
Setting up mythtv-themes (0.21.0-0ubuntu1~gutsy1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 mythtv-database
 mythtv
E: Sub-process /usr/bin/dpkg returned an error code (1)
erik@erik-desktop:~$ 

```

What should I do?

---

### Post by viciouslime on 2008-03-23
Try: sudo dpkg --configure  mythtv-database

---

### Post by Chbuntu on 2008-03-25
Thank you for the reply. However, it turns out my tuner card is not supported. I guess its back to windoze until someone has enough free time on their hands to write a driver for my hardware.
(WinTV HVR-1600)

---

