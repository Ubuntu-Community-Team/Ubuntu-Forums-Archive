---
title: "I can't upgrade through the Update Manager."
date: 2006-09-20
forum: Installation &amp; Upgrades
---

### Post by TailsAndy on 2006-09-20
Every time I try to upgrade, I get the error Message 
```
Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.
```

and the details

```
ailed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/source/Sources.gz Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/source/Sources.gz Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)

```

Any help?

---

### Post by croak77 on 2006-09-20
Are you doing a dist-upgrade to Dapper or just upgrading packages in Breezy? Looks like [http://antesis.freecontrib.org](http://antesis.freecontrib.org) is down. Maybe try a differnet mirror or remove the entry from your /etc/apt/sources.list. If you are dist-upgrading to Dapper, then you have to change all your Breezy repo entries to Dapper.

---

### Post by TailsAndy on 2006-09-20
Dist-upgrade to Dapper.

---

### Post by croak77 on 2006-09-20
Well you should remove that entry anyway since it's for Breezy not 
Dapper. Take a look at the wiki guide. It has a sample /etc/apt/sources.list.

[https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)

---

### Post by TailsAndy on 2006-09-20
So should I replace the sources.list with the one there and try again?

EDIT: Or I could try actually reading the wiki, but i just wanted to make sure i didn't muck something up.

SON OF EDIT: after I fixed it all up, changing all occurances of breezy to dapper, I got the same errors, except they all said dapper instead of breezy.

---

### Post by croak77 on 2006-09-20
Just remove the line that has [http://antesis.freecontrib.org](http://antesis.freecontrib.org) in it. It's not an Ubuntu repo, Its plf. Its not needed. As you can see of you visit, [http://antesis.freecontrib.org](http://antesis.freecontrib.org), there is nothing there.

---

### Post by TailsAndy on 2006-09-21
Hosed. I followed the wiki exactly, but ah well. Already installed Dapper, and am using it now.

---

