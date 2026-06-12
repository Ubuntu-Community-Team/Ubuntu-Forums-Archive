---
title: "Ubuntu php suhosin patch - how to apply correctly?"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by Windows_ on 2008-10-17
Hello!

I'm going to use nginx and php-fpm for my server.

That is why I must recompile php in Debian/Ubuntu with their pathes from folder debian/patches:


# $apt-get build-dep php5
# $apt-get source php5
# $cd php5-2-6
# export QUILT_PATCHES=debian/patches
# quilt push -a
# ./configure
# make

But suhosin gets me errors:

ext/standard/info.c error: expected ')' before 'SUHOSIN_LOGO_GUID'
ext/standard/info.c error: 'SUHOSIN_PATCH_VERSION' undeclared (first use in this function)
and so on...

If I remove suhosin from debian/patches/series file - ./make will be all right.


How can i apply corectly suhosin from debian/patches for recompiling php?

---

