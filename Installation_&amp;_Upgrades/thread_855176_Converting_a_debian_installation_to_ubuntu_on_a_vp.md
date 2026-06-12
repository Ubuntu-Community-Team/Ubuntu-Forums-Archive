---
title: "Converting a debian installation to ubuntu on a vps"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by zalg on 2008-07-10
HI,

The vps I'm renting (xen based) only provides images for debian, fedora, centos and gentoo but I would like to install and use ubuntu on it (mainly because of the shorter release lifecycle than debian, I want to be able to use a relatively recent version of nginx without compiling it by hand for example). How would one go about installing gentoo?

Is it possible to just use the debian etch image and then tell it to use the ubuntu repositories? Would I run into problems down the road?

Thanks...

---

### Post by kerry_s on 2008-07-10
if you use debian + the lenny/testing repo's you'll be more up-to-date than ubuntu.

you really should read the debian manual so you can understand how it all works.
[http://www.debian.org/doc/user-manuals](http://www.debian.org/doc/user-manuals)

---

### Post by zalg on 2008-07-10
Actually about 2-3 years ago, I tried using debian and the testing repo on a server and got burned by packages that didn't work or that were too old for my use....

EDIT: I just looked a bit over and it seems that since 2005 debian provides security updates on testing so that invalidates a big part of my reason for wanting to use ubuntu.... I guess I'll have to check a bit more.... thanks

---

