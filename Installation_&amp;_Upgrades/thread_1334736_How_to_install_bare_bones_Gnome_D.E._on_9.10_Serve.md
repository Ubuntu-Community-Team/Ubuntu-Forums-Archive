---
title: "How to install bare bones Gnome D.E. on 9.10 Server"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by madhartigan on 2009-11-22
I'm looking to install a VERY basic gnome desktop environment on my new 9.10 server.

I'm not sure whether the steps mentioned in [THIS](http://ubuntuforums.org/showpost.php?p=1079206&postcount=12) thread will work.

I'd like the box to load to the CLI and when I want the gde, i can open it on demand and then return to the CLI when I'd like to.

I've also heard something like gnome-core is the most basic version of gde that I can install, but I'm not sure how to do this correctly.

Any help would be appreciated.

---

### Post by ram2500 on 2009-11-22
You might be introduced to "dependency hell" if you desire to remove default packages. It can be done, but Ubuntu is not completely friendly when it comes to removing default packages. You can opt to get Ubuntu Server, which (I don't think) comes with a GUI, otherwise, Fedora is best if you want to weed out packages. I do know that with a Fedora install (DVD) you can install everything or install just enough for a simple CLI server, and add whatever you need later on. I do know that you can boot the machine to the CLI, without enabling any Gnome or x.org daemons. I don't know particularly off the top of my head how to go about this in Ubuntu, but this sounds like something you want, is that right? I am not completely sure if this will accomplish what you wanted, but wouldn't 

update-rc.d -f gdm remove

do so? (as far as booting to command line) (Someone else might be able to explain better).

startx would get you to gdm if need be.

---

### Post by sc30317 on 2009-11-22
```
sudo apt-get install ubuntu-minimal
```

---

### Post by madhartigan on 2009-11-22
basically, i just want the gde available when I need it, but I don't want all the OpenOffice, etc. installed with it.

I know there's a simple way to do this and I don't think Fedora would be necessary.

I already have the Ubuntu 9.10 standalone server(CLI) running beautifully and I just want a GUI for every once in a while.

---

### Post by madhartigan on 2009-11-22
> **sc30317 said:**
> ```
sudo apt-get install ubuntu-minimal
```

Will that install so the server boots to the login and I have to type "startx" or something to get into the desktop?

---

### Post by wojox on 2009-11-22
```
sudo apt-get update && sudo apt-get install gdm xorg gnome-core
```

It's ugly but it works. You could substitute gnome-core for openbox or some window manager.

---

### Post by jerz4lunch on 2010-12-27
> **wojox said:**
> ```
sudo apt-get update && sudo apt-get install gdm xorg gnome-core
```

you can also just use

```
sudo apt-get install ubuntu-desktop
```

---

