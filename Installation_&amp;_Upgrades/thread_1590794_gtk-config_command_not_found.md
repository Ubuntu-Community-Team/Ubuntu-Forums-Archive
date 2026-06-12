---
title: "gtk-config: command not found"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by viralmeme on 2010-10-08
Trying to install Cinepaint from a tar.gz file. Running ./configure brings up the above error. Where do I get gtk-config from?

---

### Post by andrewthomas on 2010-10-09
Debian  
[LIST]
[*]libc6-dev
[*]libglib1.2-dev
[*]libgtk1.2-dev
[*]libjpeg62-dev
[*]libpng-dev
[*]libtiff3g-dev
[*]xlibs-dev
[*]zlib1g-dev
[*]lcms-dev
[/LIST]

[http://cinepaint.bigasterisk.com/SourceTarball/](http://cinepaint.bigasterisk.com/SourceTarball/)

---

### Post by viralmeme on 2010-10-09
> **andrewthomas said:**
> Debian ..
I checked that the packages are installed, I still get the  gtk-config missing error.

---

### Post by andrewthomas on 2010-10-09
```
sudo apt-get install gcc automake g++ libfltk1.1-dev libgtk2.0-dev zlib1g-dev libjpeg62-dev libpng12-dev libtiff4-dev libopenexr-dev libxpm-dev libgutenprint-dev libgutenprintui2-dev liblcms1-dev pkg-config ftgl-dev libxmu-dev libxxf86vm-dev flex python-dev libtool
```**  ./configure --enable-gtk2**


[http://cinepaint.cvs.sourceforge.net/viewvc/cinepaint/cinepaint-project/cinepaint/ubuntu.sh?content-type=text%2Fplain](http://cinepaint.cvs.sourceforge.net/viewvc/cinepaint/cinepaint-project/cinepaint/ubuntu.sh?content-type=text%2Fplain)

---

