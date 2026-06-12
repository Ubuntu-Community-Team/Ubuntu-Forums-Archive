---
title: "install and compile R and rpy2"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by NewbieGeek on 2010-05-21
Hello,
I am trying to install a dev version of the R software and to compile it with the option --*enable*-R-shlib, in order to install Rpy2 (an interface from R to Python).
I did :
sudo apt-get install r-base-dev
But I do not know where the packages were downloaded, and how can I compile them.
Have anyone tried to do that? and more generally have you some experience with rpy2?

Thanks a lot

---

### Post by Ad@m on 2010-05-21
Open a terminal and type
[INDENT]apt-get source r-base
[/INDENT]This will download the source files in your home directory.

[http://cran.r-project.org/doc/manuals/R-admin.html](http://cran.r-project.org/doc/manuals/R-admin.html)

All the necessary info on how to compile from source is in the above.

---

### Post by NewbieGeek on 2010-05-21
Thanks a lot.
When I try ./configure ./configure --enable-R-shlib
It works till this error message :

checking for X... no
configure: error: --with-x=yes (default) and X11 headers/libs are not available

any ideas on that?

---

### Post by Ad@m on 2010-05-21
[http://cran.r-project.org/doc/manuals/R-admin.html#Essential-and-useful-other-programs-under-Unix](http://cran.r-project.org/doc/manuals/R-admin.html#Essential-and-useful-other-programs-under-Unix)

> Unless you do not want to view graphs on-screen you need &#8216;X11&#8217; installed, including its headers and client libraries. For recent Fedora distributions it means (at least) &#8216;libX11&#8217;,  &#8216;libX11-devel&#8217;, &#8216;libXt&#8217; and &#8216;libXt-devel&#8217;.  On Debian we recommend the meta-package &#8216;xorg-dev&#8217;.  If you  really do not want these you will need to explicitly configure R without X11, using --with-x=no.     

sudo apt-get install xorg-dev

---

### Post by NewbieGeek on 2010-05-21
I tried 
./configure ./configure --enable-R-shlib --with-x=no
and it seems to work. 
I think I will not have the X interface :-(

---

### Post by squirrelJC on 2012-02-08
So I'm trying to do the same thing. I was getting the import error using rpy2 and found out I need to compile R as a shared library. I proceeded to get the source for r-base and configure to enable share library. I installed R. When I went to try rpy2 again in python I still had the same import error

ImportError: libR.so: cannot open shared object file: No such file or directory

I did a locate on libR.so and it doesn't exist. Why isn't it being installed?

---

