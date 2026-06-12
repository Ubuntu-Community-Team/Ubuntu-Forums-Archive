---
title: "dependency building"
date: 2015-04-04
forum: Installation &amp; Upgrades
---

### Post by Imtiaz_Dipto on 2015-04-04
hey i am a new user on ubuntu.
when i was run this command```
sudo apt-get build-dep build-essential
``` on terminal for building dependency... after 5 min its show me at last 
```
E:  Problem renaming the file /var/cache/apt/pkgcache.bin.sglW15 to  /var/cache/apt/pkgcache.bin - rename (2: No such file or directory) debconf: apt-extracttemplates failed: No such file or directory dpkg: error: dpkg status database is locked by another process E: Sub-process /usr/bin/dpkg returned an error code (2) E: Failed to process build dependencies
```
i don't understand the problem what is says please help me and how can i build dependencies ??

---

### Post by ian-weisser on 2015-04-04
> **Imtiaz_Dipto said:**
> dpkg: error: dpkg status database is locked by another process

Well, you seem to have more than one package manager operating at the same time.
Shut them all down, then try again.

---

### Post by Imtiaz_Dipto on 2015-04-04
i am running ubuntu with windows 7... its showing this for the problem ? or i am running more than one programme on ubuntu thats why its show me that ??

---

### Post by grahammechanical on 2015-04-04
The problem or problems are nothing to do with the fact that the machine has both Windows and Ubuntu installed. This is part of the error message

> dpkg status database is locked by another process

the dpkg program is at the base of the package management system. APT has to access the database when we run the apt-get install command. But APT is not the only program that can access the dpkg database. The Ubuntu software centre does and so does the Update Manager. And there are other applications that we can install and they will also access the dpkg database.

The point is this: whichever method we use to update the system or install software the dpkg database gets locked to prevent another utility from interfering. The apt-get command that you ran cannot access the dpkg database because you have another software installer/updater utility open.

This can also happen if we cancel an install/update before it is finished and then try to install something. In this case we usually need to restart Ubuntu to clear the block on the dpkg database.

[http://en.wikipedia.org/wiki/Dpkg](http://en.wikipedia.org/wiki/Dpkg)

Regards.

---

### Post by ajgreeny on 2015-04-04
> **Imtiaz_Dipto said:**
> hey i am a new user on ubuntu.
when i was run this command```
sudo apt-get build-dep build-essential
``` on terminal for building dependency... after 5 min its show me at last 
```
E:  Problem renaming the file /var/cache/apt/pkgcache.bin.sglW15 to  /var/cache/apt/pkgcache.bin - rename (2: No such file or directory) debconf: apt-extracttemplates failed: No such file or directory dpkg: error: dpkg status database is locked by another process E: Sub-process /usr/bin/dpkg returned an error code (2) E: Failed to process build dependencies
```
i don't understand the problem what is says please help me and how can i build dependencies ??
You also missed the word [COLOR=#ff0000]install[/COLOR] from your first command ie[B] sudo apt-get [COLOR=#ff0000]install[/COLOR] build-dep build-essential
[/B]

---

### Post by mc4man on 2015-04-04
> **Imtiaz_Dipto said:**
> hey i am a new user on ubuntu.
when i was run this command```
sudo apt-get build-dep build-essential
``` on terminal for building dependency... after 5 min its show me at last 
```
E:  Problem renaming the file /var/cache/apt/pkgcache.bin.sglW15 to  /var/cache/apt/pkgcache.bin - rename (2: No such file or directory) debconf: apt-extracttemplates failed: No such file or directory dpkg: error: dpkg status database is locked by another process E: Sub-process /usr/bin/dpkg returned an error code (2) E: Failed to process build dependencies
```
i don't understand the problem what is says please help me and how can i build dependencies ??
It failed to 'do nothing' because as mentioned something was open or preventing the use of apt-get. A log out or restart would solve if you didn't figure out what.

In any event installing the build deps of an info or meta package is generally worthless, in this case by default everything needed to build the build-essential source is already installed & there is no reason to build the build-essential 'source' anyway

What you may wanted was to install  the build-essential package which just installs a number of build related packages, itself, -  it's nothing. So - 
```
sudo apt-get install build-essential
```

As far as using *apt-get build-dep*, it's used on actual sources via  a package name. (sudo apt-get build-dep packagename
So for example to install any build deps for nautilus that aren't already installed you'd go -

sudo apt-get build-dep nautilus

---

### Post by oldos2er on 2015-04-05
> **ajgreeny said:**
> You also missed the word [COLOR=#ff0000]install[/COLOR] from your first command ie[B] sudo apt-get [COLOR=#ff0000]install[/COLOR] build-dep build-essential
[/B]

The "build-dep" variable is enough by itself, no "install" required.

---

