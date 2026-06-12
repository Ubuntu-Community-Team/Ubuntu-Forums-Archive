---
title: "&quot;you installed local builds which are taking over the ubuntu versions&quot;"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by JasonSpradlin82 on 2008-09-10
I can't run certain gnome applications, including the gnomes games package and gnome-system-monitor.  They begin loading, and then leave the following error in terminal:

   /usr/games/mahjongg: symbol lookup error: /usr/games/mahjongg: undefined symbol: rsvg_handle_new_from_file

   /usr/games/gnobots2: symbol lookup error: /usr/games/gnobots2: undefined symbol: rsvg_handle_new_from_file


Also, while using gnome-system-monitor, if I select the resources tabs, its crashes with the following error (last line only):

    $ gnome-system-monitor   

    ** (gnome-system-monitor:7011): WARNING **: SELinux was found but is not enabled. 

    gnome-system-monitor: symbol lookup error: gnome-system-monitor: undefined symbol: rsvg_handle_new_from_file

----------------------------
$ uname -a
Linux jason-desktop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
---------------------------
Ubuntu 8.04 - the Hardy Heron - released in April 2008.

$ apt-cache policy gnome-system-monitor
gnome-system-monitor:
  Installed: 2.22.3-0ubuntu2
  Candidate: 2.22.3-0ubuntu2
  Version table:
 *** 2.22.3-0ubuntu2 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
        100 /var/lib/dpkg/status
     2.22.0-1ubuntu3 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages

$ apt-cache policy gnome-games
gnome-games:
  Installed: 1:2.22.3-0ubuntu2
  Candidate: 1:2.22.3-0ubuntu2
  Version table:
 *** 1:2.22.3-0ubuntu2 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
        100 /var/lib/dpkg/status
     1:2.22.1.1-0ubuntu3 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages

$ apt-cache policy libpcre3
libpcre3:
  Installed: 7.4-1ubuntu2.1
  Candidate: 7.4-1ubuntu2.1
  Version table:
 *** 7.4-1ubuntu2.1 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
        500 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
        100 /var/lib/dpkg/status
     7.4-1ubuntu2 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages

$ apt-cache policy libpcrecpp0
libpcrecpp0:
  Installed: (none)
  Candidate: 7.4-1ubuntu2.1
  Version table:
     7.4-1ubuntu2.1 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
        500 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
     7.4-1ubuntu2 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages

------------------------

I was asked in another forum to run "ldd /usr/games/mahjongg" and the results are attached.

After posting the attached file on the other forum, I got the following response, but no information as to one goes about correcting this:

[INDENT]> libgtk-x11-2.0.so.0 => /usr/local/lib/libgtk-x11-2.0.so.0 (0xb7b5a000)

you installed local builds which are taking over the ubuntu versions, that's not an ubuntu bug[/INDENT]

I've since re-installed all of the libgtk packages that were installed and re-installed gnome-games, but neither made any difference.

Jason Spradlin

---

