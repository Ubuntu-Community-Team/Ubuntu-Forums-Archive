---
title: "dpkg error at line 11111"
date: 2012-09-02
forum: Installation &amp; Upgrades
---

### Post by williamwhite on 2012-09-02
dpkg: error: parsing file '/var/lib/dpkg/status' near line 11111 package 'libkio5':
Is the error I get and it happens no matter what I am installing or updating or if I'm using command line, Update manager, gdebi 
package installer all of them return the same error


dpkg: error: parsing file '/var/lib/dpkg/status' near line 11111 package 'libkio5':
 `Recommends' field, reference to `kdelibs5-plugins': version contains ` '

---

### Post by plucky on 2012-09-02
> **williamwhite said:**
> dpkg: error: parsing file '/var/lib/dpkg/status' near line 11111 package 'libkio5':
Is the error I get and it happens no matter what I am installing or updating or if I'm using command line, Update manager, gdebi 
package installer all of them return the same error


dpkg: error: parsing file '/var/lib/dpkg/status' near line 11111 package 'libkio5':
 `Recommends' field, reference to `kdelibs5-plugins': version contains ` '

Open a terminal and ```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-broken
```

Then run ```
sudo mv /var/lib/dpkg/status-old /var/lib/dpkg/status
```

Then run ```
sudo apt-get update && sudo apt-get upgrade
``` and post output if any errors.

The first command renames the file status to status-broken and the second command renames the file status-old to status and hopefully this will fix the problem with your status file.

Good Luck

---

