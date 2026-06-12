---
title: "Can't upgrade to Fiesty:"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by jordanm on 2007-04-21
I guess I'm not the only one that can't upgrade to Fiesty from Edgy. I've been trying since this morning and the problem still persists using the official upgrade method (the GUI). I get the error:

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz) Sub-process gzip returned an error code (1)

Any ideas, or is it just an upstream repo error? While I am loyal to debian-based linux, after all the hype of Fiesty I hate to see things like this that can potentially detract users.

Jordan

---

### Post by jdong on 2007-04-21
Sounds like a repo issue... retry after a while, I guess :(

---

### Post by kosnick on 2007-04-21
well maybe i should not post it here but it seems to be the same thing , more or less
i seem to have the same problem during upgrade and i get the message 

"Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.



Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.bz2) Sub-process bzip2 returned an error code (2) "

As for the fact that it may be the repos i've been trying since yesterday . I guess it would be ok after a day wouldn't it? And one more , yesterday there were only two failures (the first two i think) , but today there are four .

---

### Post by jdong on 2007-04-21
Looks like the security repositories are also hit by the influx of traffic. Sorry :( all I can say is keep trying periodically.

---

