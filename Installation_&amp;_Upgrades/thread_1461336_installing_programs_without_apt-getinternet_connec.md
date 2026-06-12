---
title: "installing programs without apt-get/internet connection"
date: 2010-04-24
forum: Installation &amp; Upgrades
---

### Post by no_ordinary_funace on 2010-04-24
Hi there,

I don't yet have an internet connection on my machine so I am using cyber cafes to do my research and whatnot.  However, most of the stuff I read concerning updates and installations rely heavily on the machine using an internet connection to automatically install various packages.

I don't mind reading up myself on this kind of thing but I think I need a pointer in the right direction as "ubuntu package install without apt/get" doesn't bring up much on a google search (the only entry on the first page is a post on this forum back from 2005 about kernal compiling!). 

As an example, the file I would like to install is "aircrack-ng-1.0.tar.gz", which I've already downloaded and saved to my machine's desktop.  I'm not really asking how to install aircrack, per se, but just any kind of package without relying on an internet connection (i.e. download the program/package to a flash disk and then on to my machine).

Anyway, I'm still upset with Bill so I'm gonna persevere.

Thanks

---

### Post by utnubuuser on 2010-04-24
You can use CDroms for installation too, you just need to add them in Synaptic.

Presumably, you could use a Flash drive as a repo  -- probably just a matter of adding the right path to your sources.lst

Try googling > offline repo ubuntu> [https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

---

### Post by no_ordinary_funace on 2010-04-24
hi utn,

Thanks for those tips.  I'll have a look and see what I can see.  It really does look like I'm just going to have to learn something for this to work (*grinds teeth*).

---

### Post by 2hot6ft2 on 2010-04-24
Like going to Synaptic on the one needing the packages and marking all the packages you want to install then clicking on File > Generate package download script
Then moving or saving the script to a usb flash drive which you can take to any linux box that is online and double clicking on it and selecting "Run" or "Run in Terminal if you want to be able to see when it finishes" it will download the packages to the same location as where the script is.

Then you take the usb to the machine that created the script and open Synaptic and click on File > Add downloaded packages and point it to where the script and packages are to install them.

The machine that creates the script is the architecture it will download them for. Not for the one you run the script on to download them.

I think keryx works the same way and updates your sources as well.
[http://keryxproject.org/](http://keryxproject.org/)

---

