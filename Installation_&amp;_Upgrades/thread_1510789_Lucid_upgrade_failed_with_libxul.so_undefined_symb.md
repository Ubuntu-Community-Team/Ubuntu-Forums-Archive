---
title: "Lucid upgrade failed with libxul.so: undefined symbol: sqlite3_initialize"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by R2-Bert on 2010-06-16
I upgraded from 9.10 Karmic Koala to 10.04 Lucid Lynx (Desktop, 32-bit) and got this error during the upgrade:

```
Setting up xulrunner-1.9.2 (1.9.2.3+nobinonly-0ubuntu2) ...
/usr/lib/xulrunner-1.9.2.3/xulrunner-bin: symbol lookup error: /usr/lib/xulrunner-1.9.2.3/libxul.so: undefined symbol: sqlite3_initialize
dpkg: error processing xulrunner-1.9.2 (--configure):
 subprocess installed post-installation script returned error exit status 127
```

This is followed by a series of dependency problems, halting the configuration of several other packages that depend on xulrunner, including ubuntu-desktop (gulp!).

I've tried installing sqlite3 and libsqlite3-dev packages, but they made no difference. I can't find any reference to the undefined symbol sqlite3_initialize anywhere in the forums, so this must be because of something weird about my machine. I'm at a loss as to where to look next.

Any suggestions are appreciated. Thank you!

-Keith

---

### Post by dino99 on 2010-06-16
check your sources.list: be sure you only use genuine lucid repo (no third party or ppa: look at synaptic repo tab)

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f

sudo dpkg --configure -a

you can clean the system too with gconf-cleaner (yes to all) and bleachbit

---

### Post by R2-Bert on 2010-06-16
Thank you for the suggestions, but nothing seemed to make a difference.

> **dino99 said:**
> check your sources.list: be sure you only use genuine lucid repo (no third party or ppa: look at synaptic repo tab)

These are the only lines in my /etc/apt/sources.list that are not commented out (there were other 3rd party sources, but the upgrade process commented them out of course):

```
deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu lucid-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted universe multiverse
```


> **dino99 said:**
> sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f

sudo dpkg --configure -a

I did this, and it made no difference. It did uninstall some packages, but I still get the same problem.

> **dino99 said:**
> you can clean the system too with gconf-cleaner (yes to all) and bleachbit

I ran both of these tools (on bleachbit I omitted clearing my bash history, Firefox history, free disk space, and memory) and it made no difference.

Any other ideas?

---

### Post by R2-Bert on 2010-06-17
Nevermind. I've formatted the drive and re-installed Lucid, which works fine now. I have no idea what the problem was, I just got impatient.

Thank you for the help, though.

---

### Post by crimson on 2010-07-03
Although the OP is no longer interested, I ran into the same problem, and for me it turned out to be an installation of sqlite3 in /usr/local that was getting in the way. I must have built sqlite from source and installed in so I could use something else that depended on a newer version than was in the Ubuntu repository. The version in Lucid is newer than the one I had installed. Once I removed the libsqlite3 libs from /usr/local/lib, everything worked fine.

Thanks to this bug report (and subsequent retraction, with the solution) that led me to the answer so quickly:

[libapache2-svn broken on karmic]("https://bugs.launchpad.net/ubuntu/+source/subversion/+bug/500859")

---

### Post by R2-Bert on 2010-07-03
> **crimson said:**
> Although the OP is no longer interested, I ran into the same problem, and for me it turned out to be an installation of sqlite3 in /usr/local that was getting in the way. I must have built sqlite from source and installed in so I could use something else that depended on a newer version than was in the Ubuntu repository.

I bet this was the same problem I had. I'd definitely built a few things from source over the years, and while I don't specifically remember building sqlite, it is very possible.

My apologies for not tracking it down, but I had limited time to get things working again.

Thanks for the information!

---

### Post by lazy74 on 2010-08-25
Confirming crimson's solution. Got the same issue while upgrading to Lucid. Thanks for the answer!


> **crimson said:**
> 
... Once I removed the libsqlite3 libs from /usr/local/lib, everything worked fine.



---

