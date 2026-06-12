---
title: "libxfce4util-1.0 isn't in Synaptic?"
date: 2006-09-23
forum: Installation &amp; Upgrades
---

### Post by dannyboy79 on 2006-09-23
I am trying to upgrade my Thunar install to the latest release per [http://thunar.xfce.org/download.html](http://thunar.xfce.org/download.html) and when I run ./configure --prefix="/usr/local" on the libexo package first as this website states [http://thunar.xfce.org/pwiki/documentation/installation](http://thunar.xfce.org/pwiki/documentation/installation) I get an error about the above mentioned package, this is what it says, 
checking for libxfce4util-1.0 >= 4.2.2... not found
*** The required package libxfce4util-1.0 was not found on your system.
*** Please install libxfce4util-1.0 (atleast version 4.2.2) or adjust
*** the PKG_CONFIG_PATH environment variable if you
*** installed the package in a nonstandard prefix so that
*** pkg-config is able to find it.
So I figure ok, easy fix, I'll just install that dependency but guess what, 
sudo apt-get install libxfce4util-1.0
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libxfce4util-1.0
So what the hell do I do now????
I am a newbie, I have already tried upgrade all of XFCE to the new RC1 release but my mouse was super slow barely worked and instead of messing around with it I just went and reinstalled Dapper from scratch. This is just on my laptop so I don't have any files to worry about. So I figured I would just install the new Thunar for the trash support etc etc and I am getting stuck on the very first configure. Can anyone help?

---

### Post by Jussi Kukkonen on 2006-09-23
The package is probably named something a little different.
```
apt-cache search libxfce
```
That shows you possible hits... Try e.g. *libxfce4util4*

---

### Post by K.Mandla on 2006-09-23
I think you're after libxfce4util4?

[http://packages.ubuntu.com/dapper/libs/libxfce4util4](http://packages.ubuntu.com/dapper/libs/libxfce4util4)

Maybe try *sudo aptitude install libxfce4util4*? Or libxfce4util4-dev?

---

