---
title: "unable to locate package phpmyadmin"
date: 2011-07-08
forum: Installation &amp; Upgrades
---

### Post by waltenstein on 2011-07-08
I've got 11.04 server installed.  I can't successfully install phpmyadmin.  I've reviewed the documentation here:

[https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin)

... which tells me to do the following, but please note the error result:

```
08:40:35# sudo apt-get install phpmyadmin
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package phpmyadmin
```

I've been googling for an hour or so now, searched these forums and everywhere else.

I've tried doing this, but it doesn't change the above result:
```

08:42:04# sudo apt-get update
Ign http://archive.ubuntu.com natty InRelease
Hit http://archive.ubuntu.com natty Release.gpg
Hit http://archive.ubuntu.com natty Release
Hit http://archive.ubuntu.com natty/main amd64 Packages
Ign http://archive.ubuntu.com natty/main TranslationIndex
Ign http://archive.ubuntu.com natty/main Translation-en_US
Ign http://archive.ubuntu.com natty/main Translation-en
Reading package lists... Done

```

How can I tell apt-get where to find the phpmyadmin package?

Thanks in advance!

---

### Post by dino99 on 2011-07-08
that package is into synaptic repo (universe need to be activated)

[http://packages.ubuntu.com/en/natty/phpmyadmin](http://packages.ubuntu.com/en/natty/phpmyadmin)

---

### Post by waltenstein on 2011-07-08
> **dino99 said:**
> that package is into synaptic repo (universe need to be activated)

[http://packages.ubuntu.com/en/natty/phpmyadmin](http://packages.ubuntu.com/en/natty/phpmyadmin)
Thanks so much dino99.  I've added the universe repository info into my /etc/apt/sources.list file, then did the following:
```
sudo apt-get update
```
I was then able to do ```
sudo apt-get install phpmysqladmin 
```without any problems!

---

### Post by dino99 on 2011-07-08
Thats good :) :)

---

