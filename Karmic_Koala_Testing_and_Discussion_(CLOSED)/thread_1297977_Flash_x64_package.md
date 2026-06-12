---
title: "Flash x64 package"
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Krause on 2009-10-22
Any reason why the x64 flash alpha isn't in the repositories?

I know its an alpha, but there is absolutely no way it is anywhere near as unstable and buggy as using the 32 bit version with nspluginwrapper.

Manually installing it is easy enough but still it just doesn't seem right that the only repository option that people see when installing flash is that buggy 32 bit nspluginwrapper one.

---

### Post by tonyric on 2009-10-22
Agreed I was rather surprised at this yesterday when I installed 9.10... Imeediately uninstalled it and manually installed the 64bit version.

---

### Post by novafluxx on 2009-10-22
Its an alpha, thats why theres not a package in the repos that downloads it for you. Once its released, it probably will be.

---

### Post by Mutiny32 on 2009-10-22
> **novafluxx said:**
> Its an alpha, thats why theres not a package in the repos that downloads it for you. Once its released, it probably will be.

Thae alpha moniker should not be taken as such when the 64-bit "alpha" is much more stable than the final alternative currently installed. In fact, I don't think I've had the 64-bit alpha crash even once on me. nspluginwrapper crashes when you look at it funny.

---

### Post by philinux on 2009-10-22
Looks like debian are ok with it. :confused:

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/326555](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/326555)

---

### Post by Kreative_Station on 2009-10-22
...found install information for 64-bit install...


[http://ubuntuforums.org/showthread.php?t=1259102&highlight=flash+64+bit](http://ubuntuforums.org/showthread.php?t=1259102&highlight=flash+64+bit)

---

### Post by philinux on 2009-10-22
Less information needed to install it.

Get the 64 bit alpha refresh from adobe labs.
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Extract to desktop or wherever.

Create this directory ~/.mozilla/plugins then

Copy libflashplayer.so to ~/.mozilla/plugins

Restart FF

Simple ;)

---

