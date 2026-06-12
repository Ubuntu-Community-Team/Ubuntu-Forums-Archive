---
title: "Hash Sum Mismatch"
date: 2015-10-13
forum: Installation &amp; Upgrades
---

### Post by Dukenukemx on 2015-10-13
I'm getting these errors when I "suod apt-get udpate" and have no idea how to fix it.  

```

Failed to fetch http://archive.canonical.com/ubuntu/dists/trusty/partner/binary-amd64/Packages  Hash Sum mismatch
Failed to fetch http://archive.canonical.com/ubuntu/dists/trusty/partner/binary-i386/Packages  Hash Sum mismatch
Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by Bashing-om on 2015-10-13
Dukenukemx; Hi !

Generally a corrupted control file.
Most often removing the files and updating the system resolves the issue.
```

sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
sudo apt-get upgrade

```

These removed files will be re-built in the update process.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by QDR06VV9 on 2015-10-13
See post #2 
[http://ubuntuforums.org/showthread.php?t=2252106](http://ubuntuforums.org/showthread.php?t=2252106)
Ninjed again:p

---

### Post by mc4man on 2015-10-13
Maybe see here - 
[http://askubuntu.com/questions/685145/archive-canonical-com-repo-for-trusty-is-broken](http://askubuntu.com/questions/685145/archive-canonical-com-repo-for-trusty-is-broken)

---

### Post by Dukenukemx on 2015-10-13
> **Bashing-om said:**
> Dukenukemx; Hi !

Generally a corrupted control file.
Most often removing the files and updating the system resolves the issue.
```

sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
sudo apt-get upgrade

```

These removed files will be re-built in the update process.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]
Already tried and and doesn't work.

---

### Post by David_Ramsay on 2015-10-13
problem only a few hours old for me:-

Failed to fetch [http://archive.canonical.com/ubuntu/dists/trusty/partner/](http://archive.canonical.com/ubuntu/dists/trusty/partner/)

source/Sources  Hash Sum mismatch
binary-amd64/Packages  Hash Sum mismatch
binary-i386/Packages  Hash Sum mismatch

sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
sudo apt-get upgrade

did not work..

Made software centre be only server from local to where I live.. Hope it works.

[ it did not work] Updates still happen though...

Leave it to linux gods I guess... Or just update to new linux beyond 14.04LTS?

CDrom update from was removed ages ago -

---

### Post by buzzingrobot on 2015-10-13
Here, too. 

And there's a Flash update out there, too, from 521 to 535.  This week's zero day, presumably.

---

### Post by Dukenukemx on 2015-10-13
So this is a server end problem?

---

### Post by QDR06VV9 on 2015-10-13
All I did was change the server location from United States to Main Server and all is good!
```
 apt-cache policy flashplugin-installerflashplugin-installer:
  Installed: 11.2.202.535ubuntu1
  Candidate: 11.2.202.535ubuntu1
  Version table:
 *** 11.2.202.535ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ wily/multiverse amd64 Packages
        100 /var/lib/dpkg/status

```
This was happening in wily also, Again changed Servers from US to Main.
```
 apt-cache policy flashplugin-installer flashplugin-installer:
  Installed: 11.2.202.535ubuntu0.14.04.1
  Candidate: 11.2.202.535ubuntu0.14.04.1
  Version table:
 *** 11.2.202.535ubuntu0.14.04.1 0
        500 http://uk.archive.ubuntu.com/ubuntu/ trusty-security/multiverse amd64 Packages
        500 http://uk.archive.ubuntu.com/ubuntu/ trusty-updates/multiverse amd64 Packages
        500 http://archive.ubuntu.com/ubuntu/ trusty-updates/multiverse amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/multiverse amd64 Packages
        100 /var/lib/dpkg/status
     11.2.202.350ubuntu1 0
        500 http://uk.archive.ubuntu.com/ubuntu/ trusty/multiverse amd64 Packages
        500 http://archive.ubuntu.com/ubuntu/ trusty/multiverse amd64 Packages



```
Regards

---

### Post by Dukenukemx on 2015-10-13
Problem is gone.  Seems the server went down.

---

### Post by nargaroth_reg on 2015-10-14
I also experienced this issue earlier and now it's fine on my machine as well, which is great since coincidentally today I changed priorities of some repositories and thought I had broken apt-get at first u__u .

---

