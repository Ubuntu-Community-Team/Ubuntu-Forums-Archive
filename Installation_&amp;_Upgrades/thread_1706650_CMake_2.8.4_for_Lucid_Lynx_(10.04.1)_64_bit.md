---
title: "CMake 2.8.4 for Lucid Lynx (10.04.1) 64 bit"
date: 2011-03-14
forum: Installation &amp; Upgrades
---

### Post by dsupriya on 2011-03-14
I have a box with Lucid Lynx (10.04.1) 64 OS. I want CMake 2.8.4 and higher. The package manager does not give this. I can install it directly from CMake website, but this has only i386 versions. Is it okay to install this?

---

### Post by andrewthomas on 2011-03-14
You are considering grabbing the wrong file from the cmake download page.

Download source
[http://www.cmake.org/files/v2.8/cmake-2.8.4.tar.Z](http://www.cmake.org/files/v2.8/cmake-2.8.4.tar.Z)
**Get the above tar.Z file NOT the tar.gz file**

```
sudo apt-get install build-essential checkinstall automake
[FONT=Arial]sudo apt-get build-dep cmake[/FONT]
```extract the files to the folder you want to build in ( in your home directory)

then you should be able to run cmake on it ( making sure to change the prefix to /usr instead of /usr/local
then make and **checkinstall** to build a .deb

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

