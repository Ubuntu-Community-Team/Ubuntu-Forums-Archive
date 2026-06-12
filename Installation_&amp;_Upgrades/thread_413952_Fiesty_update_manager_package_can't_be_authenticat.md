---
title: "Fiesty update manager package can't be authenticated"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by brew1brew on 2007-04-19
I installed fresh fiesty 32bit system, after bringing the system up the first time update manager pops up saying that there are updates. the update is update-manager & update-manager-core, from 1:0.59.19 to 1:0.59.20. when I try to apply it I get the response that the package "can't be authenticated!" sounds like the package signature is bad from the repo. 

Any one else see this? should I go ahead and install?

Les

---

### Post by karnakdk on 2007-05-24
yeah... i'm having the same problem and i don't know what to do. (I upgraded from Dapper.)

---

### Post by miro_dan on 2007-08-03
I have the same problem. It appear two days ago.  Please help.

---

### Post by arijarot on 2007-08-14
try ```
sudo apt-get update
``` then ```
sudo apt-get upgrade
```

---

### Post by arohanui on 2007-10-10
I've just installed Feisty and ran the update manager for the first time.  40 of the 122 available updates were marked as non-authenticated, including the update for the update manager itself! Running apt-get from the command line (as suggested above) made no difference; this was the error reported:
```
W: GPG error: http://nz.archive.ubuntu.com feisty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```

Note the server [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com).  Changing to the main server [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) fixed the problem, but should the bad sig on the New Zealand server be reported?  If so, where?

Thanks

---

