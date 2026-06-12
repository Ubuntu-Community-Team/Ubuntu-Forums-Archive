---
title: "problem bulding an app with libpng"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by 999alfred on 2007-11-21
i am posting this here because I can find no other forum for app develoment and building.

I just installed 7.1 and I am trying to build a third party package that uses libpng. The problem is that it looks for libpng and fails. Now in my research I find there is a libpng AND libpng12. 7.1 has libpng12. Plus, there is NO /usr//lib/pkgconfig file for libpng or libpng12. Why?

I am trying to locate a reason for the two libpngs.

Can i safely build the latest libpng from it's site and install it via
./configure --prefix lib
make
make install

without screwing up the apt-get mechanism?

Also, I am a longtime Slackware user.

999alfred

---

### Post by monktbd on 2007-11-21
did you also install the dev package of libpng?

my - old dapper - apt-cache search output:
> 
libpng12-0 - PNG library - runtime
libpng12-dev - PNG library - development


your libpng is actually a link to libpng12, so that you do not have to change source files when you include something like
```
#include <libpng/png.h>
```

it automatically uses the lib pointed to, libpng12 in this case.

---

### Post by 999alfred on 2007-11-21
That's good to know about the differences between the two.

But, that still does not explain the missing .pc file in the /usr/lib/pkgconfig directory. Or, the same file missing for libz.

999alfred

---

### Post by jespdj on 2007-11-21
> **999alfred said:**
> But, that still does not explain the missing .pc file in the /usr/lib/pkgconfig directory. Or, the same file missing for libz.
Well, that's strange, because libpng12.pc really is included in the package libpng12-dev, as you can see when you use the search function on [http://packages.ubuntu.com](http://packages.ubuntu.com)

So if you installed libpng12-dev and you do not have libpng12.pc in /usr/lib/pkgconfig, then maybe something went wrong with the installation of the package.

---

