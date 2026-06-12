---
title: "codec's"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by pedrom169 on 2008-01-13
i was wondering if someone could point me in the direction in some codec's for my linux pc

my linux pc isnt on the internet
so i need someway of installing them by downloading them on a pen drive

thanks

Peter

---

### Post by Dark Savant0 on 2008-01-13
Whenever you install a package, there is a local repository cache of deb files which you can access at /etc/apt/cache/ . You can download the codecs on another computer and then install them on the offline computer.

You can also create a cd cache from some other Ubuntu computer if the cache has not been cleaned using APTonCD ( [http://downloads.sourceforge.net/](http://downloads.sourceforge.net/) ). There is a deb file for Ubuntu on that website, and the Application is under "System--Administration".

I can't recall the exact package names, but you can also grab the packages manually from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) by searching for the package and grabbing the correct package for your architecture (i386, x64, ppc) and distribution (feisty, gutsy, hardy etc).

---

### Post by pedrom169 on 2008-01-13
if i have a 32 bit provessor and gusty what which one should i download?

the i386 one?

+

the pc that is on the internet is the family one which is windows (which is a pain)

+

when i find an audio codec
i click on it and it says this is Dependant

libavcodec1d (= 3:0.cvs20070307-5ubuntu4)

will that have to be installed to install it?


cheers

Peter

(sorry im new)

---

