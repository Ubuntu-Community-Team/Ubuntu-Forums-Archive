---
title: "More repository failures"
date: 2012-06-11
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2012-06-11
In addition to this problem encountered earlier:

[http://ubuntuforums.org/showthread.php?t=2001720](http://ubuntuforums.org/showthread.php?t=2001720)

I'm now encountering new problems:

[http://phil.ipal.org/corrupt-repository-0.png](http://phil.ipal.org/corrupt-repository-0.png)
[http://phil.ipal.org/corrupt-repository-1.png](http://phil.ipal.org/corrupt-repository-1.png)

Anyone know what is going on?  Repository corruption?

Update:

Seems to now be working OK.  Looks like one of the index files was not transferring completely, or may have been truncated on whichever repository server I was getting.  If they are using FTP to upload to the public servers, they need to change over to using RSYNC.

---

