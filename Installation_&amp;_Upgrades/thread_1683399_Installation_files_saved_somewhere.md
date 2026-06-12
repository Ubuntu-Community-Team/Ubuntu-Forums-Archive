---
title: "Installation files saved somewhere?"
date: 2011-02-07
forum: Installation &amp; Upgrades
---

### Post by debd on 2011-02-07
I was wondering..when I install aps in ubuntu through ppa, the downloaded .deb file must be saved somewhere in the file system. Isn't it?  if so..where are the saved? 
it would be good if I can get those deb files bcoz next tym i install another linux distro in my pc , I'll not have to download the same files again.
Also, some of my frnds are keen on using Ubuntu..but the prob. is they have no internet connection. & without Internet ,using ubuntu is kinda running a lame os. So..it would be great if I can give them the apps and even the AV codecs on a thumb drive.

any idea whwre they are saved?  m also concerned about dependencies.... :-|

---

### Post by tommcd on 2011-02-07
> **debd said:**
> I was wondering..when I install aps in ubuntu through ppa, the downloaded .deb file must be saved somewhere in the file system. Isn't it?  if so..where are the saved?
All .deb packages that are installed are saved in the */var/cache/apt/archives/* directory. This should also apply to those unsupported PPA packages as well.
> **debd said:**
> 
it would be good if I can get those deb files bcoz next tym i install another linux distro in my pc , I'll not have to download the same files again.
You should only install Ubuntu .deb packages on Ubuntu (or Mint, or possibly other Ubuntu clones). These Ubuntu .deb packages should not be installed on any other distro.
> **debd said:**
> 
Also, some of my frnds are keen on using Ubuntu..but the prob. is they have no internet connection. & without Internet ,using ubuntu is kinda running a lame os. So..it would be great if I can give them the apps and even the AV codecs on a thumb drive.

For offline updating and installing packages on Ubuntu there is **keryx** [http://keryxproject.org/](http://keryxproject.org/) and **apt on CD** [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

I have read around here that keryx in particular works very well.

---

### Post by debd on 2011-02-08
thanks a lot...got 'em all

and I liked apt-on-cd.

kyrex seemed a bit complicated from the tutorial .

---

