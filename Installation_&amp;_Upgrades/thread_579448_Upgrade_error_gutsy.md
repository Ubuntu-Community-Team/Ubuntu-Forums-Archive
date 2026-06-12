---
title: "Upgrade error gutsy"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by ericrosenfield on 2007-10-18
Every time I try to upgrade to Gutsy I get the following error:
> 
Failed to fetch [http://hendrik.kaju.pri.ee/ubuntu/dists/feisty/Release](http://hendrik.kaju.pri.ee/ubuntu/dists/feisty/Release) Unable to find expected entry  all/binary-i386/Packages in Meta-index file (malformed Release file?)


Is this just because the servers are slammed or do I need to point some repositories to a different place or what?

Thank you,
Eric

---

### Post by bapoumba on 2007-10-18
The page you liked to is tagged feisty.

---

### Post by ericrosenfield on 2007-10-18
Yes. But that's the error I get when I go to System > Administration > Update Manager and click "Upgrade" next to "New distribution release '7.10' is available." Why it's Feisty I donno. I'm running Feisty now.

---

### Post by Sef on 2007-10-18
> Failed to fetch [http://hendrik.kaju.pri.ee/ubuntu/dists/feisty/Release](http://hendrik.kaju.pri.ee/ubuntu/dists/feisty/Release) Unable to find expected entry all/binary-i386/Packages in Meta-index file (malformed Release file?)

Your upgrading to Gutsy, but those packages are for Feisty.  I would comment that line out.  To comment out a line put a # before it:

```
 #http://hendrik.kaju.pri.ee/ubuntu/dists/feisty/Release Unable to find expected entry all/binary-i386/Packages
```

To go to comment out the line, follow these instructions:

Applications > Accessories > Terminal

then type in or copy and paste this command:

```
gksudo gedit /etc/apt/sources.list
```

Then find that line and comment it out.

---

### Post by ericrosenfield on 2007-10-18
That seems to have solved the problem, thanks!

---

