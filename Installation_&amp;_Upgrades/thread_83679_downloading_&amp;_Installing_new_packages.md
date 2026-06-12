---
title: "downloading &amp; Installing new packages"
date: 2005-10-29
forum: Installation &amp; Upgrades
---

### Post by dabster on 2005-10-29
I want to install some new packages But I don't have internet Access at home PC, I want to download packages from the College where we hve a fast leased line,
But the Biggest problem is the dependencies....You may download the main package file But there could be dependencies on other Packages so I am supposed to Download them also This makes it really Hectic....

Has anybody having any idea That How i can Download directly all the .deb's(including dependencies) for the specific package....

We have only Windows comp in our college, So i can't use and python scripts to do it for me....
Help me out.....
--
Anurag

---

### Post by Xian on 2005-10-29
Sure, this is not a problem. Just go to [Ubuntu Packages](http://packages.ubuntu.com/) and do a keyword search for the package(s) that you want to install on your system. Click on the link that is provided and it will not only list the application that you queried but also all the dependencies and links to get them as well.

For example, here is the page for the [VLC media player](http://packages.ubuntu.com/breezy/graphics/vlc).
The needed deps are color-coded in red.

---

### Post by dabster on 2005-10-29
each of the package with red bullet is sometime dependent on some other packages Which creates lol of mess...
Then What I am supposed to do, I am fed up following links and downloading each of them....

---

### Post by Xian on 2005-10-29
There's no way around that. 
Each package needs the dependencies in order to work.

However, a lot of those files which are listed are probably already installed on your system, so I really doubt that you would end up having to chase all of them down and download locally. 

To find out if a particular package is installed you can:

$ apt-cache search packagename

or

$ apt-cache policy packagename

---

### Post by Xian on 2005-10-29
Another method (it can provide for more deps than are required) that is more exhaustive is use the build-dep command and then fetch the packages which are listed. For example, here are the listed deps for streamtuner that need to be installed on my system:

```
$ sudo apt-get build-dep streamtuner
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  libatk1.0-dev libcairo2-dev libcurl3-dev libglib2.0-dev libgtk2.0-dev
  libidn11-dev libpango1.0-dev libpng12-dev libssl-dev libtag1-dev
  libtagc0-dev libxcursor-dev libxfixes-dev libxinerama-dev libxml2-dev
  python-dev python-gtk2-dev python2.4-dev x11proto-fixes-dev
  x11proto-xinerama-dev
0 upgraded, 20 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.4MB of archives.
After unpacking 33.4MB of additional disk space will be used.
Do you want to continue [Y/n]?
```

---

