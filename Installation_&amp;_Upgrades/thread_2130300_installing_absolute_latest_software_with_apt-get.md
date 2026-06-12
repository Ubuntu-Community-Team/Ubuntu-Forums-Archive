---
title: "installing absolute latest software with apt-get"
date: 2013-03-29
forum: Installation &amp; Upgrades
---

### Post by DiGiTY on 2013-03-29
I want to install the absolute latest software (e.g., Apache 2.4.4, MySQL 5.6.10 and PHP 5.4.13) and all it's dependencies using apt-get, but I'm pretty sure the Ubuntu repositories will only install older more stable versions by default. Trying to manually find and download all the dependencies for these software packages is driving me insane! How can I get apt-get to download and install the exact version of the software packages I want and their dependencies?

---

### Post by kc1di on 2013-03-29
[COLOR=#ff0000][/COLOR]you can try this it will give you newer but mostly untested packages.

Go to Software Center >edit>Software sources> updates > check the box that says pre-release updates

then go to terminal and type ```
sudo apt-get update
```
and try to install your packages. 
[COLOR="#FF0000"](WARNING: this may break your system)[/COLOR]


good Luck ;)

---

### Post by dino99 on 2013-03-29
[http://launchpad.net/ubuntu/+source/thatpackageyouarelookingforinstallation](http://launchpad.net/ubuntu/+source/thatpackageyouarelookingforinstallation)

---

### Post by DiGiTY on 2013-03-29
> **kc1di said:**
> [COLOR=#ff0000][/COLOR]you can try this it will give you newer but mostly untested packages.

Go to Software Center >edit>Software sources> updates > check the box that says pre-release updates

then go to terminal and type ```
sudo apt-get update
```
and try to install your packages. 
[COLOR="#FF0000"](WARNING: this may break your system)[/COLOR]


good Luck ;)

I'm running server. Any idea how to do this via command line?

---

### Post by DiGiTY on 2013-03-29
> **dino99 said:**
> [http://launchpad.net/ubuntu/+source/thatpackageyouarelookingforinstallation](http://launchpad.net/ubuntu/+source/thatpackageyouarelookingforinstallation)

Thanks, but I know how to find the packages it's just the tedious task of having to keep searching for dependencies of dependencies of dependencies...

---

### Post by dino99 on 2013-03-29
man dpkg

if you run : sudo dpkg -i thatpackage2install

then dpkg takes care of the dependencies (indeed you need first to download them into the same dir as the main deb)

---

### Post by kc1di on 2013-03-29
you can add the following line in  the /etc/apt/sources.list file and do the same thing.

```
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
```

But I'm not sure the packages your looking for are in back-port either.  you may be stuck with searching for them online. 
Good Luck :)

---

### Post by DiGiTY on 2013-03-31
> **dino99 said:**
> man dpkg

if you run : sudo dpkg -i thatpackage2install

then dpkg takes care of the dependencies (indeed you need first to download them into the same dir as the main deb)

Well that works for a package with one or two dependencies, but its still a nightmare if there's a lot of dependencies and some of those dependencies have dependencies and then those have dependencies.... I'm hoping for something where I only have to manually download my desired main .deb file and in combination with apt-get it'll install it and all it dependencies automagically. Is this possible?

---

