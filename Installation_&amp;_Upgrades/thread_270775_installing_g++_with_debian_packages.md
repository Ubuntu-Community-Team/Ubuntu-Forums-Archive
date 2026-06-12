---
title: "installing g++ with debian packages"
date: 2006-10-03
forum: Installation &amp; Upgrades
---

### Post by gletare on 2006-10-03
Hi,

I am trying to install g++ on an AMD64 computer. I have already install cpp and gcc-3.3-base, but when I try to install gcc with the following command

```

sudo dpkg -i gcc_3.3.5-3_amd64.deb

```

It tells me :

> 
Selecting previously deselected package gcc.
(Reading database ... 72195 files and directories currently installed.)
Unpacking gcc (from gcc_3.3.5-3_amd64.deb) ...
dpkg: dependency problems prevent configuration of gcc:
 gcc depends on cpp (>= 4:3.3.5-3); however:
  Package cpp is not configured yet.
dpkg: error processing gcc (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gcc


So how shall I do to configure gcc?

Thanks in advance

---

### Post by ciscosurfer on 2006-10-04
Have you tried installing [COLOR=Purple]build-essential

[COLOR=Gray]You can also [grab it from here]("http://packages.ubuntu.com/dapper/devel/build-essential") via the Web
[/COLOR] 

[/COLOR]

---

