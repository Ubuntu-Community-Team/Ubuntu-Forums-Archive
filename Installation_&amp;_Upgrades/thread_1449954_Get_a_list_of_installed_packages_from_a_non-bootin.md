---
title: "Get a list of installed packages from a non-booting ubuntu"
date: 2010-04-08
forum: Installation &amp; Upgrades
---

### Post by Cdwijs on 2010-04-08
Hi All,

I'm reinstalling an ubuntu machine that does not boot anymore. I have a complete backup of all the files that were on the harddrive.

I would like to make a list of all the programs that were installed, so I can re-install them on the fresh install.

I've found the following procedure, but this method requires that the machine still boots. (and my machine does not boot anymore)

"
-- save the list of packages currently installed --
dpkg --get-selections > ~/package-list.log

-- install packages from list on a new installation --
dpkg --set-selections < ~/package-list.log
apt-get dselect-upgrade 

"
Is it possible to get a list of installed packages from the backup of an ubuntu machine?

Best regards,
Cedric

PS, My appologies for my English, I'm dutch

---

### Post by Cdwijs on 2010-04-13
The solution is simple, dpkg has the option --admindir This allows to specify the location of the package database

So the command is as follows (assuming your old installation is located under /backup)

-- save the list of packages currently installed --
dpkg --admindir=/backup/var/lib/dpkg --get-selections > ~/package-list.log

-- install packages from list on a new installation --
dpkg --set-selections < ~/package-list.log
apt-get dselect-upgrade 

Could somebody tell me howto mark this thread as solved?

PS. Did I post this in the wrong location? 

Best regards,
Cedric

---

