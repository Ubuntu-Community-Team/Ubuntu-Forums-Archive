---
title: "Error: Failed to fetch"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by smittyfree on 2006-06-02
While trying to update to Ubuntu 6.06, I get to about file 54 of 56 and this error pops up. It says it's some sort of possible network issue.

Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz) 404 Not Found

Any thoughts? All I want to do is just use the new AmaroK.

---

### Post by johnc4510 on 2006-06-02
Those two repositories are left over from automatix I believe. Do this:
Applications>Accessories>Terminal
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
Put # in front on those two lines, or take them out completely
Save the file and exit window
sudo apt-get update
sudo apt-get upgrade
This should fix it.

---

