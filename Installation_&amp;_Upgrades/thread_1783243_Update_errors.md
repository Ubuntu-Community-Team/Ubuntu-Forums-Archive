---
title: "Update errors"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by dodgingspam on 2011-06-15
I have a DELL mini with Ubuntu. When I attempt to run System Update Update Manager says: "Your system is up-to-date. The package information was last updated 304 days ago." So, I run "Check" unfortunately i get an error message box with the following:

> **Could not download all repository indexes**
Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/Release](http://dl.google.com/linux/talkplugin/deb/dists/stable/Release)  Unable to find expected entry  main/binary-lpia/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead. 

How do I clean this and run a good update?

Thanks.

---

### Post by dodgingspam on 2011-06-20
Anybody?... Any suggestions?...

---

### Post by jerrrys on 2011-06-20
open a terminal and enter

sudo apt-get update

sudo apt-get upgrade

and please post any errors you get

---

### Post by Rubi1200 on 2011-06-20
In the terminal:

```
sudo apt-get update
```

Post the error messages.

Also,

```
cat /etc/apt/sources.list
```

and post here too.

Thanks.

---

