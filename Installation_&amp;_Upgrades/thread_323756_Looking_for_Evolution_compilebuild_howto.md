---
title: "Looking for Evolution compile/build howto"
date: 2006-12-22
forum: Installation &amp; Upgrades
---

### Post by ariel on 2006-12-22
Hi, 

  I'm trying to build evolution 2.8.2.1 in my edgy box, to replace the official 2.8.1 version, which I find a bit buggy for everyday office use (I use it as an exchange client).

  I downloaded the sources and I am trying to do the usual ./configure; make; sudo make install, configure always succeeds but make always fails in both evolution and evolution-data-server.

I tried a few tweeks like
./configure --with-openldap=yes --without-nspr-includes

but this is way too complex. I can't find any howto or more or less detailed procedure on how to build all evolution's packages. 

If someone can shed some light here or post a link to an existing howto that would be much appreciated...
Thanks!

---

### Post by ariel on 2007-01-02
Ops.... it looks like compiling Evolution is harder than I thougt  :(

---

### Post by cloaking_device on 2007-01-11
I just built Evolution 2.8.2.1 on Envy (this time w/o data-server or exchange)

Of course, the first thing to do is

```
sudo apt-get build-dep evolution
```

However, there are a few wierd problems that I ran into:

**1. libcamel-1.2.so.0 is missing**

Solution: I made a symlink from /usr/lib/libcamel-1.2.so0 -> /usr/lib/libcamel-1.2.so.8, which should exist

**2. Expected Specifier Qualifer List error**

I got an error like this:

```
gtkobject.h:97: error: expected specifier-qualifier-list before 'GInitiallyUnownedClass'
```

This is because I had an old version of glib-2.0, which was located at /usr/local/include/glib-2.0, while the new version was at /usr/include/glib-2.0. Since I had two glib-2.0's, I actually had two pkg-config files. pkg-configure read the old one, and returned the wrong paths.

Solution: delete the old pkg-config file (which was in /usr/local/lib/pkgconfigure)

**3. Missing files /usr/lib/libgnomeprintui-2-2.la and /usr/lib/libgnomeprint-2-2.la**

This one was trickier. In the new libgnomeprintui-dev (and libgnomeprint-dev) version 2.12.1-4, there are no libtool archive (la) files. Where to find them?

Solution: What I did was download the sources for these packages (i.e. [http://www.linuxfromscratch.org/blfs/view/cvs/gnome/libgnomeprint.html](http://www.linuxfromscratch.org/blfs/view/cvs/gnome/libgnomeprint.html) and [http://www.linuxfromscratch.org/blfs/view/cvs/gnome/libgnomeprintui.html](http://www.linuxfromscratch.org/blfs/view/cvs/gnome/libgnomeprintui.html)).

For each of these, I did a ./configure, and a make. I then just copied the .la files for both to /usr/lib. You may be able to make install them instead, too.

That's all I needed to do this time... just let it go! However, I've built evolution before, so I may have done some steps in the past that I've forgotten to mention. Last time I built evolution-data-server, a major obstacle was that I had to force the configure script to detect glib-genmarshal.

Oh yeah. The build commands I used were:

```

./configure --prefix=$(pkg-config --variable=prefix ORBit-2.0) \
            --sysconfdir=/etc/gnome/2.14.3 \
            --localstatedir=/var/lib \
            --libexecdir=$(pkg-config \
                --variable=prefix ORBit-2.0)/lib \
            --enable-nntp \
            --enable-nss \
            --enable-smime &&
make
make install
```

---

