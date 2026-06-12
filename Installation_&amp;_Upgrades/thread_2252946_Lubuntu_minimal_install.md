---
title: "Lubuntu minimal install"
date: 2014-11-16
forum: Installation &amp; Upgrades
---

### Post by flaymond on 2014-11-16
Hello, anyone had try the minimal install? I gonna try it after this, the ram needed is super low for instaling...is it possible to installing minimal install, and after that download applications (whole) and become 100% similar like Lubuntu desktop packages?

I mean I can add any apps i want like Mozilla Firefox,flash etc. using command line?
I know that minimal install just install the engine, and not come with apps and environment?


So, I need help to install minimal (core) and how to set up and start having default apps for it same like Lubuntu?

Thanks.

---

### Post by deadflowr on 2014-11-16
You mean install from a mini.iso?
When you install from that, it first installs the core packages for Ubuntu, then when those are all installed, will ask you if you want to select other packages to install.
I believe lubuntu minimal is one of the selections, simply hit the spacebar to mark the selection.
(If you do not mark anything then the installer will assume you are done, and finish the process. When that happens, upon reboot you will get nothing but a prompt to log into...)

But basically, if you pay attention to each screen as they come up, you won't have problems.

---

### Post by sudodus on 2014-11-16
You can follow *deadflowr*'s instructions. You can also finish and reboot and then, in the text screen install whatever you like with

```
sudo apt-get install package-name
```

where package-name is one or several packages, that you want to install (separated with a space character).

If you install the meta-package lubuntu-desktop, you will get Lubuntu, etc, but the advantage with mini.iso is that you cat make your own custom installation with only the packages you want (plus what they need, for example library packages, which are identified automatically). If you read the manual page for apt-get

```
man apt-get
```

you will find several tips about what is possible, for example

```
       --no-install-recommends
           Do not consider recommended packages as a dependency for installing. Configuration Item:
           APT::Install-Recommends.

       --install-suggests
           Consider suggested packages as a dependency for installing. Configuration Item:
           APT::Install-Suggests.

```

---

### Post by ibjsb4 on 2014-11-16
The is also the alternate install cd.

[https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO)

---

### Post by vasa1 on 2014-11-16
FWIW, [http://amjjawad.blogspot.com/2013/07/ubuntu-mini-iso-installation-process.html](http://amjjawad.blogspot.com/2013/07/ubuntu-mini-iso-installation-process.html)

---

### Post by krupier on 2014-11-16
> **InterProg said:**
> Hello, anyone had try the minimal install?
I did. I went even a wilder path and installed it using debootstrap, meaning completely from scratch. And yes, it worked. Just another way to install the core system.

> **InterProg said:**
> So, I need help to install minimal (core) and how to set up and start having default apps for it same like Lubuntu?
Basically you can say Lubuntu is LXDE + Openbox as a window manager. Later you can install whatever you want. I don't remember the title, but there is a page on Ubuntu docs on how to do it. You WILL need however some skills, like setting up your locale for example. However if you know how to use Google and are not hesiteting to try, the sky is a limit :-)

---

