---
title: "like to try kde 4.3"
date: 2009-08-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by terry_gardener on 2009-08-05
just a quick question 

i know that i can install kubuntu desktop package to try kde 4.3 but is there an easy way to remove it and all other packages it installs if i dont like it.

---

### Post by taavikko on 2009-08-05
all of the resulting binaries and apps should be removed when
```
sudo aptitude purge kdelibs5
```
Just make sure you install kubuntu-desktop with aptitude.

But it might be an little hassle to get rid of all the cruft...(warning)

---

### Post by prshah on 2009-08-05
> **terry_gardener said:**
> 
i know that i can install kubuntu desktop package to try kde 4.3 but is there an easy way to remove it and all other packages it installs if i dont like it.

Here's what I did; before installing KDE, I made a list of all the packages it installs with the command```
sudo apt-get -s install kubuntu-desktop > kubuntu-packages
``` The "-s" is important, it means "simulation only", no actual installation. When the command finishes, you will have a list of the installed packages in the file kubuntu-packages.

You can then proceed with the actual installation without the "-s", and if you decide to remove KDE, you can do so by individually removing the packages as mentioned in the kubuntu-packages file.

You will also have to reconfigure gnome to be default desktop manager with ```
sudo dpkg-reconfigure gdm
```

---

