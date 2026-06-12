---
title: "can an application installed with apt-get have a ./configure?"
date: 2007-07-24
forum: Installation &amp; Upgrades
---

### Post by czJake on 2007-07-24
If an application is installed with apt-get is it possible to use "./configure" on it, and if so where do I find the "./configure" file?

---

### Post by Nekiruhs on 2007-07-24
> **czJake said:**
> If an application is installed with apt-get is it possible to use "./configure" on it, and if so where do I find the "./configure" file?
No. That is only for compiling it. It just gathers info about your processor, compiler, etc.

---

### Post by czJake on 2007-07-24
So what do you do if you need to enable some options that are only available during the ./configure stage of the installation?

---

### Post by meyou on 2007-07-24
dpkg-reconfigure packagename

iirc

---

### Post by czJake on 2007-07-24
Where do I get dpkg-reconfigure?

---

### Post by meyou on 2007-07-24
you should already have it. you need to run it as superuser

sudo dpkg-reconfigure <packagename>

---

### Post by czJake on 2007-07-24
Ok, I found it now, but it won't work with my two configuration options for squid.

I basically just need to install squid from apt-get, but I need to use the --enable-storeio=null and --enable-linux-netfilter.

I need to accomplish the same thing as the following code would do.

./configure --enable-storeio=null --enable-linux-netfileter
make
make install

I guess the only reason I need apt-get is because when I follow the normal installation by compiling the tarball my Ubuntu Server 7.04 box doesn't recognize that squid is actually installed. Whenever I would try to run a squid command it would say, "squid is not installed you can install it by using apt-get install squid"

---

### Post by czJake on 2007-07-24
So what do you do if you need to enable some options that are only available during the ./configure stage of the installation?

---

