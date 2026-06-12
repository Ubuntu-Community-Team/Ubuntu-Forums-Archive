---
title: "Ubuntu Edgy Upgrade"
date: 2012-03-28
forum: Installation &amp; Upgrades
---

### Post by dotku on 2012-03-28
I'm using upgrade manager to upgrade the system.
I got the error message below

[HTML]http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.92.166 80]
http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.92.166 80]
http://archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.92.181 80]
http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.92.181 80]
http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.92.181 80]
http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.92.181 80]
http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.92.181 80]
http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.92.181 80]
http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.92.181 80]
http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.92.181 80]
http://archive.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.92.181 80]
http://archive.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.92.181 80]
http://archive.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.92.181 80]
http://archive.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.92.181 80]
http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.92.181 80]
http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.92.181 80]
http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.92.181 80]
http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.92.181 80]
[/HTML]

---

### Post by mörgæs on 2012-03-28
There is a similar question here:
[http://ubuntuforums.org/showthread.php?t=1948603](http://ubuntuforums.org/showthread.php?t=1948603)

---

### Post by dotku on 2012-03-28
I'm upgrade from 6.10 to 7.04, which should be the correct path by the offical EOLUpgrade Document ([https://help.ubuntu.com/community/EOLUpgrades/Edgy](https://help.ubuntu.com/community/EOLUpgrades/Edgy))

However, the source seems wrong over here.

> Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)

I have already edit /etc/apt/sources.list

> ## EOL upgrade sources.list
# Required
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) edgy-security main restricted universe multiverse

# Optional
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse


Whatelse I can do?

---

### Post by plucky on 2012-03-29
Put a # in front of this line ```
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe main multiverse restricted
``` as it doesn't have the edgy Repositories. See [http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/)

Good Luck

---

