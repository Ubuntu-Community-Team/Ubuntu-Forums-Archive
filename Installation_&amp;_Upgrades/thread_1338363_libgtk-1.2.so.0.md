---
title: "libgtk-1.2.so.0"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by zhaoyan on 2009-11-26
I'm trying to install [I]Oxford Advanced Learner's Dictionary on Ubuntu, but I got message: 

"...Error while loading shared libraries: libgtk-1.2.so.0
Cannot open shared object file: No such file or directory..."

I could not find this library via Synaptic Package Manager.

I'm using Ubuntu 9.10. Please give me a help.
[/I]

---

### Post by glorinand on 2009-11-27
The package has obviously been removed from repositories for >= karmic. I use OALD as well and thus I have the same problem...

---

### Post by glorinand on 2009-11-27
If you're still experiencing this problem, you can obviously install libgtk-1.2 from

deb [http://ftp.energotel.sk/pub/linux/ubuntu/](http://ftp.energotel.sk/pub/linux/ubuntu/) jaunty universe

However, it might be good to store these packages for future releases as jaunty repos won't be there to save us forever... :)

Just install the packages and then copy  libgtk1.2_1.2.10-18.1build2_i386.deb, libgtk1.2-common_1.2.10-18.1build2_all.deb and libglib1.2ldbl_1.2.10-19build1_i386.deb from cache (/var/cache/apt/archives).

Also, do not forget to remove the jaunty repo from sources.list once you're done, so as not to break your package mgt or something... :D ;)

---

### Post by zhaoyan on 2009-11-28
:p I did it! Thank you very much!

---

