---
title: "liberror-perl install hangs at Unpacking replacement liberror-perl"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by jeffk on 2010-10-17
On Ubuntu 10.10 meerkat server amd46, I'm having a problem with the git dependency liberror-perl_0.17-1 hanging at with the following step:

Preparing to replace liberror-perl 0.17-1 (using .../liberror-perl_0.17-1_all.deb) ...
Unpacking replacement liberror-perl ...

This never returns, so I kill the aptitude process, remove /var/lib/dpkg/lock, and run sudo dpkg --configure -a.

Unfortunately, this package liberror-perl is now partially installed, and aptitude will try to finish installing it, to no effect. Any attempt to sudo aptitude purge liberror-perl hangs at the same point.

UPDATE: I did apparently remove the liberror-perl package with the following:

/var/lib/dpkg$ sudo dpkg --force-all -r liberror-perl
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 
dpkg: warning: files list file for package `liberror-perl' missing, assuming package has no files currently installed.
(Reading database ... 57080 files and directories currently installed.)
Removing liberror-perl ...

I still would like to get git installed though. This package is a dependency.

Thank you for any suggestions, this is fairly urgent to complete a machine deployment today.

---

### Post by adityabankar on 2010-10-23
Even I am getting same problem on Ubuntu 10.10. I think it can happen if the .deb file is broken, is that possible?

---

### Post by Krishna_stan on 2011-02-16
Have you resolved the issue? Please post if you did so.

---

### Post by sikander3786 on 2011-02-17
> **Krishna_stan said:**
> Have you resolved the issue? Please post if you did so.

In most cases, cleaning apt-get cache helps.

```
sudo apt-get clean
sudo apt-get autoclean
```

If you have got the same issue, please post the complete output from your Terminal.

```
sudo dpkg --configure -a
```

---

### Post by hingo on 2011-03-08
Hi

I was also hit by this exact problem, also for me it was when trying to install git, and the error was in unpacking liberror-perl.

I did sudo kill on the apt-get process, did apt-get [auto]clean, removed the lock file and retried, but it wouldn't work. In fact, now also other installs hanged.

I eventually did "ps aux|grep dpkg" and realized that when killing the apt-get process, in fact the failed dpkg process had been left hanging.

I then restarted the computer, again did apt-get [auto]clean, and after this both apt-get upgrade and apt-get install git worked fine.

Possibly liberror-perl is corrupted on some mirror, and on the second try I got a good one and it worked. But the key is to also restart between. (Or know exactly what processes you have to kill.)

---

