---
title: "Gutsy Could Not Download all Repository indexes (malformed Release file?)"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by MrKirby on 2007-11-05
All of a sudden upon update:

Could not download all repository indexes
[B]
http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release: Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release: Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release: Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)[/B]

Is this something to worry about?  Fix?  Did not upgrade from Feisty, did a clean install and everything was working fine for awhile.  Not sure what changed.  Thought maybe servers were down for awhile or something, but problem has persisted for a few days now.

Sources.list is attached.

---

### Post by MrKirby on 2007-11-05
Ok, don't know what I did, but after I found this site:
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

I generated a new list, which was drastically different from the previous one posted, and reloaded and everything seems to be loading fine, no missed connections.  don't know why my sources.list had all those entries. 

new one posted

---

