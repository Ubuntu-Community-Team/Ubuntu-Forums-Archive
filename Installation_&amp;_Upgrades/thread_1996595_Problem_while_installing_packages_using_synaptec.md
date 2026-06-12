---
title: "Problem while installing packages using synaptec"
date: 2012-06-04
forum: Installation &amp; Upgrades
---

### Post by ershu on 2012-06-04
Am having problem installing packages using synaptec. Initially i thought it was the problem with the getdeb repository so i removed it from synaptec(using GUI)...but the problem was not solved...so i deleted the source list file from etc/apt/source.list.d..but still the problem is there...i get the following when i try to install a package... 


Selecting previously unselected package gnome-contacts.
(Reading database ... 178350 files and directories currently installed.)
Unpacking gnome-contacts (from .../gnome-contacts_3.4.0-1_i386.deb) ...
Processing triggers for libglib2.0-0 ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up getdeb-repository (0.1-1~getdeb1) ...
--2012-06-04 20:21:15--  [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key)
Resolving archive.getdeb.net (archive.getdeb.net)... 209.105.191.78
Connecting to archive.getdeb.net (archive.getdeb.net)|209.105.191.78|:80... failed: Connection timed out.
Retrying.

--2012-06-04 20:22:20--  (try: 2)  [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key)
Connecting to archive.getdeb.net (archive.getdeb.net)|209.105.191.78|:80... failed: Connection timed out.
Retrying.

--2012-06-04 20:23:25--  (try: 3)  [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key)
Connecting to archive.getdeb.net (archive.getdeb.net)|209.105.191.78|:80... failed: Connection timed out.
Retrying.

--2012-06-04 20:24:31--  (try: 4)  [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key)
Connecting to archive.getdeb.net (archive.getdeb.net)|209.105.191.78|:80... failed: Connection timed out.
Retrying.

--2012-06-04 20:25:38--  (try: 5)  [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key)
Connecting to archive.getdeb.net (archive.getdeb.net)|209.105.191.78|:80... failed: Connection timed out.
Retrying.

--2012-06-04 20:26:46--  (try: 6)  [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key)
Connecting to archive.getdeb.net (archive.getdeb.net)|209.105.191.78|:80... failed: Connection timed out.
Retrying.

---

