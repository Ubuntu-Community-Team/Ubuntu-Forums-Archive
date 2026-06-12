---
title: "Help installing GIMPshop"
date: 2006-12-04
forum: Installation &amp; Upgrades
---

### Post by Sprite1990 on 2006-12-04
I'm following the guide on [http://linux.suramya.com/tutorials/Install_GIMPShop/](http://linux.suramya.com/tutorials/Install_GIMPShop/) about installing GIMPshop.

I've got as far as:

```

Now we configure GIMPShop by running the following command:  

./configure --prefix=/usr
```

However when I type this in it comes up with:
```

dan@DanLinux:~/gimp-2.2.8$ ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
```

Help please ?

---

### Post by janbockaert on 2006-12-04
i know, this doesn't help, but reading the GIMP handbook is faster than installing the ugly hack gimpshop is. In my opinion, installing programs that are not in the repositories is somthing you only should do when you don't have a alternative. In this case, the GIMP is an obvious alternative.

---

### Post by rejser on 2006-12-04
Gimpshop is no problem to install. 
But from a ubuntu-view, that was no good tutorial.
Btw. I think you miss the build-tools (build-essentials?)
Check in synaptic

---

### Post by taurus on 2006-12-04
> **Sprite1990 said:**
> I'm following the guide on [http://linux.suramya.com/tutorials/Install_GIMPShop/](http://linux.suramya.com/tutorials/Install_GIMPShop/) about installing GIMPshop.

I've got as far as:

```

Now we configure GIMPShop by running the following command:  

./configure --prefix=/usr
```

However when I type this in it comes up with:
```

dan@DanLinux:~/gimp-2.2.8$ ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
```

Help please ?

```
sudo aptitude update
sudo aptitude install build-essential checkinstall
```
Then, build your gimpshop again...

---

### Post by asi on 2007-01-21
I hawe problem to run skript configure because is not on the package but there's the fille that's similar and looks like it configure.bin
how tu use him?

---

### Post by loell on 2007-01-21
if you just wanted to draw simple shapes and simple graphics  try xara extreme.

---

### Post by asi on 2007-01-22
There's plenty of basic editors but I need Photoshop alternative
so how to compile it if I amweing configure script and what does it means that all the files has  .bin? but looks the same

---

### Post by fishmorg909 on 2007-02-08
I'm used to Photoshop, so I think Gimpshop is pretty nice -- it make the menus much more familiar! And there's an easy way to install it: a deb for Ubuntu/ Debian.

[http://www.plasticbugs.com/blogimg/gimpshop_2.2.11-1_i386.deb](http://www.plasticbugs.com/blogimg/gimpshop_2.2.11-1_i386.deb)

download and double-click to install.

Gimphop creator Scott Moschella's site:

[http://plasticbugs.com/?page_id=294](http://plasticbugs.com/?page_id=294)

---

### Post by gsiliceo on 2008-05-04
sudo apt-get install build-essentials
and
sudo apt-get build-deb gimp

---

