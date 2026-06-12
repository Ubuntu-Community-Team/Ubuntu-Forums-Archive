---
title: "How to get a full install on a diskless client"
date: 2006-09-25
forum: Installation &amp; Upgrades
---

### Post by blumi00GT on 2006-09-25
Hi,

I am setting up a diskless workstation. I finished the hardware and for the operating system, I gave Ubuntu a try.

I managed this [HowTo]("https://help.ubuntu.com/community/Installation/OnNFSDrive") and installed the base system correctly. It boots in textmode (run level 2) and works - as much as it can do with only the basic tools installed.

To get a little further, I apt-get'ed some packages like the man-db and NIS, but my question is - is there a way I can get the full system with X.org, GNOME and all, without installing all packages separately?

Also, I tried `apt-get -install gnome` in the hope, it would install all depended packages with it, but it tells me that gnome isn't available (like a dead link or something).

Thanks,
Bastian

---

### Post by bernied on 2006-09-25
Try the ubuntu-desktop package. It should get all the dependencies. Or kubuntu-desktop or xubuntu-desktop.

If you want to know what it will install, before committing yourself:
sudo apt-get -s install ubuntu-desktop
The -s is for simulate.

---

### Post by blumi00GT on 2006-09-25
Okay, I will try it this evening.
Sorry, I am not new to Linux, but new to the Debian-style packages and configuration. And the package "gnome" seemed right for me at the moment.

Do I need the "desktop-base" package before? It seems not to be in the dependencies of "ubuntu-desktop", but its content seems to be somewhat important(?)!
[http://packages.ubuntu.com/dapper/x11/desktop-base](http://packages.ubuntu.com/dapper/x11/desktop-base)

Bastian

---

### Post by bernied on 2006-09-25
Hmm, maybe, perhaps it would make no difference, so it wouldn't hurt to install desktop-base first.

I'm pretty sure that those packages (desktop-base, ubuntu-desktop etc) are empty (there's another word for this) - they are only a list of dependencies, so once installed, you can actually delete the ubuntu-desktop package with zero effect. Except that, if the developers decide that the desktop should include a new package, then you won't get the new package as part of an updgrade. So all of those dependencies in desktop-base are probably in ubuntu-desktop as well - I think. You could check.

And having a look at that link of yours I just found the gnome package, but it's in the universe repository, which is porbably why you didn't find it. Have a look in /etc/apt/sources (or similar). You will probably find the universe repository commented out.
[http://packages.ubuntu.com/dapper/gnome/gnome](http://packages.ubuntu.com/dapper/gnome/gnome)

There is a ubuntu handbook somewhere as well.

I'm no expert on ubuntu packages, I just did a quick google to answer your first post.

---

### Post by blumi00GT on 2006-10-05
Hi - sorry I didn't get back here lately.
Just want to tell that installing the package "ubuntu-desktop" did it. It took around six hrs, tough (ubuntu server was delivering only at 20kB/s).

Thanks!

---

