---
title: "Subversion: Connection reset by peer (Gutsy, 7.10)"
date: 2008-02-27
forum: Installation &amp; Upgrades
---

### Post by Jeremy.M on 2008-02-27
Recently ran an apt-get update, apt-get upgrade and subversion commits from command line (svn commit) to locally hosted repository were returning:
[INDENT]
Transmitting file data .svn: Commit failed (details follow):
svn: Can't read from connection: Connection reset by peer[/INDENT]

Source of this bug is documented here: [INDENT][https://bugs.launchpad.net/ubuntu/+source/db4.4/+bug/153996](https://bugs.launchpad.net/ubuntu/+source/db4.4/+bug/153996)[/INDENT]


To fix this temporarily, you have to downgrade your Berkeley DB (libdb4.4) version from 4.4.20-8.1ubuntu3.1 to 4.4.20-8.1ubuntu3 with the command:
[INDENT]```

apt-get install libdb4.4=4.4.20-8.1ubuntu3
```[/INDENT]

The SVN server I had the problem w/ was svnserve from the subversion package (version 1.4.4dfsg1-1ubuntu3), but looks like it might mess w/ mod_svn on apache too.

Hopefully this helps anyone having the same problem.

---

