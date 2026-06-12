---
title: "GPG Error when using apt-get update"
date: 2012-11-27
forum: Installation &amp; Upgrades
---

### Post by Rokkross on 2012-11-27
I'm running a fresh install of Lubuntu 12.10 (wubi), and I keep encountering this error when trying to update:
```
$ sudo apt-get update
Get:1 http://archive.canonical.com quantal InRelease [3,954 B]                                       
Get:2 http://archive.canonical.com quantal Release.gpg [3,954 B]                                     
Get:3 http://archive.canonical.com quantal Release [3,954 B]                                         
Ign http://archive.canonical.com quantal Release                                                     
E: GPG error: http://archive.canonical.com quantal Release: The following signatures were invalid: NODATA 1 NODATA 2

```
Please bear with me, as I don't exactly know a lot about package management/key signing, but does anyone know what steps I could take to fix this? Any help is appreciated.

---

### Post by monkeybrain2012 on 2012-11-27
Easiest way to fix gpg error is to install and run the script lauchpad-getkeys

[http://www.webupd8.org/2010/05/automatically-import-all-missing.html](http://www.webupd8.org/2010/05/automatically-import-all-missing.html)

---

### Post by Rokkross on 2012-11-27
> **monkeybrain2012 said:**
> Easiest way to fix gpg error is to install and run the script lauchpad-getkeys

[http://www.webupd8.org/2010/05/automatically-import-all-missing.html](http://www.webupd8.org/2010/05/automatically-import-all-missing.html)

Installed the package and ran it; didn't seem to help at all: 
```
$ sudo launchpad-getkeys

Please wait... launchpad-getkeys is running an update so 
it can detect the missing GPG keys

Trying to import all the missing keys
gpg: keyring `/etc/apt/secring.gpg' created

launchpad-getkeys has finished importing all missing GPG keys. 
Try running sudo apt-get update - you shouldn't see any key 
errors anymore
$ sudo apt-get update
Get:1 http://archive.canonical.com quantal InRelease [3,954 B]                         
Get:2 http://archive.canonical.com quantal Release.gpg [3,954 B]                       
Ign http://extras.ubuntu.com quantal InRelease                                         
Get:3 http://archive.canonical.com quantal Release [3,954 B]                           
Ign http://us.archive.ubuntu.com quantal InRelease                                     
Ign http://archive.canonical.com quantal Release                                       
E: GPG error: http://archive.canonical.com quantal Release: The following signatures were invalid: NODATA 1 NODATA 2

```
Thanks for the help though. This script may be useful in the future.

---

### Post by ibjsb4 on 2012-11-27
I like "Ubuntu Geek's" fix

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GPG+error+The+following+signatures+were+invalid&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=GPG+error+The+following+signatures+were+invalid&as_qdr=all&sa=Google+Search&lang=en)

---

