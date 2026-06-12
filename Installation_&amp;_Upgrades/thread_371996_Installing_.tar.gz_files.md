---
title: "Installing .tar.gz files"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by Tobywuk on 2007-02-27
Hello,


can you please tell me how to install a .tar.gz file?

I have been doing some reading, and have found out that .tar.gz contains the source code for the program, and it needs to be compiled. 

What software do i need to compile the code? and how do i use the program to do this, and then how do i install the program once compiled, and then finaly how to run it?

I am a primary windows user, so im not 100% farmilier with all the unix talk :)

Thanks!

---

### Post by bruenig on 2007-02-27
You need to install build-essential and then any program specific dependencies. Link to the package, and I will see exactly what it wants (it varies package to package). Generally speaking there is a configure script that you run and then you make and make install.

---

### Post by johnc4510 on 2007-02-27
To add to bruenig, here is a site with more detail, but build-essential is necessary. Install it via synaptic. Here is the site:
[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

---

### Post by vayde on 2007-02-27
tar stands for 'tape archive'- think of it as a fancy zip file with a ton more functionality.

tar archives are often referred to as 'tarballs'

You'll need to untar your tarball  before you can use it. Tarballs come in 3 common flavors: 1- simple tarballs (.tar extension usually) 2- gzipped tarballs (.tgz and .tar.gz) 3- Bzipped tarballs (.tar.bz2).  Each one needs a slightly different method for handling.

untar a simple tarball: type 'tar xvf <filename>'

untar a gzipped tarball: 'tar xzvf <filename>'

untar a bzipped tarball: 'tar xjvf <filename>'

You are calling the tar program with various options: x for extract z for unzip v for verbose (it will tell you what it's doing) j for unbzip and f to give it a file name.

Read the man page for tar by typing: 'man tar' at a command prompt.  Man pages are a pain in the neck in the beginning, but once you get used to them, they are your friend.

You should also be able to simply double click on the tarball in your graphical file manager window (it's called nautilus, but you won't see the name unless you go digging for it).

Welcome, and good luck.  You'll find lots of support here.

---

### Post by aysiu on 2007-02-27
Usually you don't need to compile a .tar.gz

Read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by bruenig on 2007-02-27
> **vayde said:**
> tar stands for 'tape archive'- think of it as a fancy zip file with a ton more functionality.

tar archives are often referred to as 'tarballs'

You'll need to untar your tarball  before you can use it. Tarballs come in 3 common flavors: 1- simple tarballs (.tar extension usually) 2- gzipped tarballs (.tgz and .tar.gz) 3- Bzipped tarballs (.tar.bz2).  Each one needs a slightly different method for handling.

untar a simple tarball: type 'tar xvf <filename>'

untar a gzipped tarball: 'tar xzvf <filename>'

untar a bzipped tarball: 'tar xjvf <filename>'

You are calling the tar program with various options: x for extract z for unzip v for verbose (it will tell you what it's doing) j for unbzip and f to give it a file name.

Read the man page for tar by typing: 'man tar' at a command prompt.  Man pages are a pain in the neck in the beginning, but once you get used to them, they are your friend.

You should also be able to simply double click on the tarball in your graphical file manager window (it's called nautilus, but you won't see the name unless you go digging for it).

Welcome, and good luck.  You'll find lots of support here.

untarring any tarball can be done with:
tar xf <filename>

---

