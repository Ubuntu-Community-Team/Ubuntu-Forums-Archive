---
title: "Installation Problem (System Suffed)"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by beamendslrs on 2008-05-27
Hi All,
when installing MySQL (not included in Gusty) for some reason I felt the need to install mysql-connector-odbc This was downloaded but failed to install correctly. Ubuntu Gusty on a 32-bit Dell

I've gone through all the options with apt, including the dodgy ones - nothing ! Surely there must be a way of just saying that I simply don't want this dammed package, please delete it (without it insisting on trying to install it first)?

As this is a work machine, re-installing the OS is a very major task (as in just what would I back up apart from everything), and as this is the second time in three months that packaging has failed I'm pretty pee'd off. The last time I lost everything.......

Is there really no package for mysql-connector-odbc anywhere, other than at MySQL via "alien", which has caused all the trouble in the first place?

Cheers
Richard

---

### Post by dstew on 2008-05-27
This package may help you get connected: [http://packages.ubuntu.com/hardy/libmyodbc](http://packages.ubuntu.com/hardy/libmyodbc)

---

### Post by beamendslrs on 2008-05-27
Thanks - but the problem is I can't install *anything*!


Cheers
Richard

---

### Post by dstew on 2008-05-28
You should be able to install that package with Synaptic. System --> Administration --> Synaptic Package Manager, search for libmyodbc.

---

### Post by beamendslrs on 2008-05-28
> **dstew said:**
> You should be able to install that package with Synaptic. System --> Administration --> Synaptic Package Manager, search for libmyodbc.

The issue is that apt, however called, and with whatever options, always finds that the package mysql-connector-odbc is corrupt, and will not proceed with any installation. mysql-connector-odbc came from the MySQL site as a prm, so I had to "alien" it. The resulting deb failed to install, and since then I can install nothing - synaptic will not even start, saying mysql-connector-odbc must be re-installed first.
I need a method of telling apt that I don't want mysql-connector-odbc installed, uninstalled or anything else, I just want it to go away so I can get on with my work!

Cheers
Richard

---

### Post by rbmorse on 2008-05-28
have you tried sudo apt-get purge *packagename*?

---

### Post by dstew on 2008-05-28
You may be in a bit of trouble. [This article]("http://www.linux.com/articles/48910") seems pretty complete with respect to trying to fix your broken system. There doesn't seem to be an easy solution, such as a single command that will make everything go away.

What is the output of apt-get check? Please post it.

What happens when you try ```
sudo apt-get remove --purge mysql-connector-odbc
```

---

### Post by beamendslrs on 2008-05-28
> **dstew said:**
> You may be in a bit of trouble. [This article]("http://www.linux.com/articles/48910") seems pretty complete with respect to trying to fix your broken system. There doesn't seem to be an easy solution, such as a single command that will make everything go away.

What is the output of apt-get check? Please post it.

What happens when you try ```
sudo apt-get remove --purge mysql-connector-odbc
```

Thanks to both of you. I've seen the article and worked through it. I tried it again but....

beamends@beamends-1:~$ sudo apt-get remove --purge mysql-connector-odbc
[sudo] password for beamends:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package mysql-connector-odbc needs to be reinstalled, but I can't find an archive for it.
beamends@beamends-1:~$

:-(

Cheers
Richard

---

### Post by dstew on 2008-05-28
As a last resort, try```
sudo dpkg --remove --force-remove-reinstreq mysql-connector-odbc
```That may break your system, but it is pretty broken already. The worst outcome will be you have to re-install the operating system, so maybe back-up essential data first.

---

