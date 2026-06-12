---
title: "Can I get old packages from somewhere?"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by paulm on 2007-06-19
Is it possible to get packages from older (no longer supported) distributions from anywhere?


I have a system that has been upgraded to Dapper at some point (from Hoary/Breezy).
On the system are some documents stored under subversion that I want to get but it seems like the upgrade has changed the version of Berkeley DB used by subversion and left me unable to access these old repositories, I see messages like:

> Berkeley DB error for filesystem /opt/repos/db while opening environment:\nDB_VERSION_MISMATCH: Database environment version mismatch

Googling suggests that this is due to a Berkely DB upgrade and the [solution]("http://subversion.tigris.org/faq.html#bdb43-upgrade")  involves getting an older svnadmin binary which was linked to the older version of Berkley DB

But the unsupported distros seem to have gone from archive.ubuntu.com so I don't know where I'm going to find such a binary.....

Any suggestions?

---

### Post by PaulFr on 2007-06-19
[http://packages.debian.org/oldstable/devel/subversion](http://packages.debian.org/oldstable/devel/subversion) ? It seems to be a DB 4.2 based svn package.

---

### Post by raul_ on 2007-06-19
[http://packages.ubuntu.com]("http://packages.ubuntu.com")

---

### Post by paulm on 2007-06-19
I ended up just getting the source and building a copy of svn against the old bdb and installing it temporarily in my home dir to do the svn recovery process.

---

