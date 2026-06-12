---
title: "upgrades being HELD BACK but no explanation why"
date: 2013-08-01
forum: Installation &amp; Upgrades
---

### Post by arvevans on 2013-08-01
Why are these 3 upgrades being held back and not upgraded?

[COLOR="#FF0000"]arv@Workstation:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  gir1.2-cogl-1.0 gir1.2-coglpango-1.0 libclutter-1.0-0
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
arv@Workstation:~$ [/COLOR]

This is a minor complaint relating to a lack of information, and not a fault of the system.

Recently completed a dist-upgrade to Ubuntu 13.04.  
Running Gnome Classic on AMD 2X64-3800 with 4GB RAM & 1TB HD

Thanks,

---

### Post by Bashing-om on 2013-08-01
arvevans; Hi !

Try this terminal command:
```

sudo apt-get dist-upgrade

```
See if the "smart" mode will resolve the conflict.
see:
[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)
for complete disclosure.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by Frogs Hair on 2013-08-01
Do you or have you used a Gnome Shell PPA ? I had problems with that group of packages while attempting to go back to Gnome 3.6 from 3.8.

---

### Post by arvevans on 2013-08-05
Yes.  I do use Gnome in classic or no-effects mode.  It is required for efficient access to CAD and CNC programs that I use regularly.

Doing a "sudo apt-get dist-upgrade" is what seems to have brought on the problem of undocumented hold-backs.
Are there any particular reasons why a software package might be "held back and not upgraded".  Surely someone
wrote the code to do this, and thus should know why it happens?

---

### Post by Frogs Hair on 2013-08-05
Packages are usually held due to lack of a repository  connection or conflicting dependencies I have never tried classic on Lubuntu so can you describe how the classic session was installed ?

---

### Post by bapoumba on 2013-08-05
Which versions do you currently have installed ?
```
bapoumba@SonyBlue:~$ apt-cache show gir1.2-cogl-1.0
Package: gir1.2-cogl-1.0
Priority: optional
Section: libs
Installed-Size: 103
Maintainer: Rico Tzschichholz <ricotz@ubuntu.com>
Architecture: i386
Source: cogl
Version: 1.14.0-0ubuntu1

```

[http://packages.ubuntu.com/raring/gir1.2-cogl-1.0](http://packages.ubuntu.com/raring/gir1.2-cogl-1.0)

---

### Post by arvevans on 2013-08-07
Standard apt-get install gnome.  That all went fine and installed Gnome-3, which I use in the Gnome Classic mode because those big garish icons are of no use to me (I'm not that blind...yet).\

---

### Post by arvevans on 2013-08-07
> **bapoumba said:**
> Which versions do you currently have installed ?
```
bapoumba@SonyBlue:~$ apt-cache show gir1.2-cogl-1.0
Package: gir1.2-cogl-1.0
Priority: optional
Section: libs
Installed-Size: 103
Maintainer: Rico Tzschichholz <ricotz@ubuntu.com>
Architecture: i386
Source: cogl
Version: 1.14.0-0ubuntu1

```

[http://packages.ubuntu.com/raring/gir1.2-cogl-1.0](http://packages.ubuntu.com/raring/gir1.2-cogl-1.0)

Installed versions are the standard ones that come with apt-get update followed by apt-get upgrade, so it is a pretty much vanilla setup.

---

### Post by arvevans on 2013-08-07
> **Frogs Hair said:**
> Packages are usually held due to lack of a repository  connection or conflicting dependencies I have never tried classic on Lubuntu so can you describe how the classic session was installed ?

Packages being held back by one thing or the other are fine, but I would like a bit more information to be provided when a package is held back.  If I need to troubleshoot a problem with a package being held back...it would be nice to know the exact reason it was held back.  That way I would know where to start working on fixing the problem.  If the package is being held back because of a missing repository it should be easy to tell the user that fact.  If the package is being held back because of conflicting dependencies that information should be provided so I can know where to start working fixing the problem.

There were no repository read failures, so that can guess can probably be excluded, unless it needs a repository that was not enabled.

Apt-get install -f does not indicate any problem, and there are no complaints about missing or conflicting dependencies.

---

