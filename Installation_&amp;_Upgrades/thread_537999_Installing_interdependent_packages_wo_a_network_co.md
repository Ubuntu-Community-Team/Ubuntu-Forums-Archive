---
title: "Installing interdependent packages w/o a network connection"
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by hailtothethief on 2007-08-29
So here's my setup:

I have a linux machine which I use to do everything I need for work/school, and a Windows XP I use to connect to the internet, because all I have readily available is a 56k connection, and I haven't figured out how to setup my modem on linux, but that's not my question here.

Until I can get my modem running, I'm stuck ferrying packages I need from my XP machine to my linux laptop via  a jump drive. This means no apt-get, just using packages.ubuntu.com for all of my needed packages. The problem is that as I'm filling the dependencies, every once in a while I run accross a couple of packages that are interdependent. That is I can't install Package A because it depends on Package B, which I can't install because it relies on Package A.

I've found that using the following command will work sometimes:

```
dpkg -i --force-all a.deb b.deb
```

But other times I run that command, then try to install another .deb file and get an error saying that my dependencies are broken.

Is there a networkless command that can safely install interdependent packages?

---

