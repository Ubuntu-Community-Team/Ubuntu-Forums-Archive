---
title: "How to prevent a package from being removed"
date: 2009-01-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by LordVeovis on 2009-01-17
Is it possible to prevent a package from being removed when I try to install another package?

In particular I am trying to install the legacy nvidia driver for my geforce 4 series laptop.  It wants to uninstall the xorg related packages.  I should be able to make it not remove them and add the 'IgnoreABI True' option to xorg.conf

---

### Post by Kow on 2009-01-17
[LP308410]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/308410")

---

### Post by LordVeovis on 2009-01-17
> **Kow said:**
> [LP308410]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/308410")

has nothing to do with legacy drivers.  legacy is the 96 driver

---

### Post by danf_1979 on 2009-01-18
Try reading section 3.10 here: [http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html)

---

### Post by LordVeovis on 2009-01-18
> **danf_1979 said:**
> Try reading section 3.10 here: [http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html)

That doesn't quite look right either as I have no nvidia driver installed currently, and installing the nvidia driver removes the xorg because it thinks there is a conflict.  I need a way to install a new package and force an old package to not be removed.  Or to force install of a package while ignoring, and not resolving, conflicts?

---

### Post by albinootje on 2009-01-18
> **LordVeovis said:**
> That doesn't quite look right either as I have no nvidia driver installed currently, and installing the nvidia driver removes the xorg because it thinks there is a conflict.  I need a way to install a new package and force an old package to not be removed.  Or to force install of a package while ignoring, and not resolving, conflicts?

Afair the apt documentation mentions hold package.
See here :
[http://www.cyberciti.biz/ref/apt-dpkg-ref.html](http://www.cyberciti.biz/ref/apt-dpkg-ref.html)

```

echo ``<package> hold'' | dpkg --set-selections Put <package> on hold (command line method)

```
With that you can prevent packages from being uninstalled.
I've also read about the 
```

aptitude --keep-all

```
parameter.
[http://newbiedoc.berlios.de/wiki/Aptitude_-_using_together_with_Synaptic_and_Apt-get](http://newbiedoc.berlios.de/wiki/Aptitude_-_using_together_with_Synaptic_and_Apt-get)

---

### Post by LordVeovis on 2009-01-18
Hold didn't work.  When i put them on hold it just refused to let me install nvidia driver.  Perhaps a way to force install now?

---

### Post by albinootje on 2009-01-18
> **LordVeovis said:**
> Hold didn't work.  When i put them on hold it just refused to let me install nvidia driver.  Perhaps a way to force install now?

With dpkg you can use the --force-all parameter, but please make sure what you're doing, or have proper backups :)
See :
```

dpkg --help | less
man dpkg

```

---

### Post by LordVeovis on 2009-01-18
ok, this is going to take a while. it's about 29 packages.. i used aptitude hold before to hold them (which allowed me to copy and paste the names,) but I will hold with dpkg it and try a force install with dpkg

---

