---
title: "revert gcc to version 3.2 or 3.4"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by Niroth on 2007-03-28
Hello,

     I recently installed Ubuntu 6.10 in order to use a particular application.  This application needs to be built using gcc 3.2 or 3.4 and I am not sure exactly how to go about switching.  I did an apt-get remove gcc and it appears to have removed gcc 4.x just fine.  I think did an apt-get install gcc-3.4 as I saw it there on the list.  It seems to work OK except that in order to run it one needs to enter "gcc-3.4 <input>" whereas I would need it to work with a simple "gcc" in order to get the application to run.  Is there a different way to install gcc 3.2 or 3.4 such that it will work with a good-old "gcc" command?

Thanks!

---

### Post by lloyd_b on 2007-03-28
> I recently installed Ubuntu 6.10 in order to use a particular application. This application needs to be built using gcc 3.2 or 3.4 and I am not sure exactly how to go about switching. I did an apt-get remove gcc and it appears to have removed gcc 4.x just fine. I think did an apt-get install gcc-3.4 as I saw it there on the list. It seems to work OK except that in order to run it one needs to enter "gcc-3.4 <input>" whereas I would need it to work with a simple "gcc" in order to get the application to run. Is there a different way to install gcc 3.2 or 3.4 such that it will work with a good-old "gcc" command?

An easy way to accomplish this:
```
cd /usr/bin
sudo ln -s gcc-3.4 gcc
```

This creates a symbolic link (symlink) named "gcc", which points to "gcc-3.4"

Note: the gcc-3.4 package is intended to co-exist with the gcc4 package.  Depending on the application you're trying to compile, it's usually as simple as changing a single ".configure" option to select which of the two compilers you're going to run.

Lloyd B.

---

### Post by Niroth on 2007-03-28
Thanks for the reply.  I figured the reason it was as such was so it could coexist with gcc 4, perhaps I will look into trying to make the change but for now the symbolic link should work fine.

---

