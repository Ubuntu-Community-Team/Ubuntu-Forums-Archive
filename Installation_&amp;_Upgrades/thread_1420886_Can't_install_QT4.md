---
title: "Can't install QT4"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by insane2600tt on 2010-03-03
Hi Everybody!

I'm trying to install qt4 to start coding with it (i'm just starting these days) on my machine (Ubuntu 8.04.4 LTS; kernel 2.6.24-27-generic #1 SMP i686 GNU/Linux) but when i try

```
sudo apt-get install libqt4-dev
```

this is what I get:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libqt4-dev: Depends: libqt4-gui (= 4.3.4-0ubuntu3.1) but 4.4.0-1ubuntu5~hardy1 is to be installed
              Depends: libqt4-qt3support (= 4.3.4-0ubuntu3.1) but 4.4.0-1ubuntu5~hardy1 is to be installed
              Depends: libqt4-sql (= 4.3.4-0ubuntu3.1) but 4.4.0-1ubuntu5~hardy1 is to be installed
E: Broken packages

```

I don't really know how to deal with this error message :(

Thanks for your help!!!

---

### Post by yogesh.girikumar on 2010-03-04
Hi,

The sources.list file could have been outdated or the package itself could have some bugs or there could be some conflicting packages installed...

You can try this solution

Type the following in the terminal one after the other:
```
$ sudo apt-get clean 
$ sudo apt-get autoclean
$ sudo apt-get update
$ sudo apt-get install -f libqt4-dev
```
This will try to install it and fix any broken packages. See if that works.

HTH

---

