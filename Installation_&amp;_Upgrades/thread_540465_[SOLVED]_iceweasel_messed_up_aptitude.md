---
title: "[SOLVED] iceweasel messed up aptitude"
date: 2007-09-01
forum: Installation &amp; Upgrades
---

### Post by duruttye on 2007-09-01
Hello

After installing iceweasel, and updating the source list, it messed up something, it looks like this:

sudo aptitude update
Get:1 [http://kiwi.startx.ro](http://kiwi.startx.ro) feisty Release.gpg [189B]
Ign [http://kiwi.startx.ro](http://kiwi.startx.ro) feisty/misc Translation-en_US
.
.
.
Hit [http://http.us.debian.org](http://http.us.debian.org) unstable/main Packages
Fetched 79.8kB in 4s (17.3kB/s)
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing sppc (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/http.us.debian.org_debian_dists_unstable_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: Couldn't rebuild package cache
kucko@kucko-mashina:~/Desktop$ 

The last thing I did is: sudo aptitude upgrade iceweasel

Any ideas?

---

### Post by duruttye on 2007-09-01
Removed Iceweasel (from the repos too), problem solved, all by myself :guitar:

---

