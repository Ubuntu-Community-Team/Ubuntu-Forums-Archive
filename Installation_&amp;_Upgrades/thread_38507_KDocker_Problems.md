---
title: "KDocker Problems"
date: 2005-05-31
forum: Installation &amp; Upgrades
---

### Post by jblanco on 2005-05-31
I'd like to install KDocker on my system, but when I try and use "apt-get", I get the following error:
[I]
Package kdocker is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source[/I]

And when I installed it via downloading the .deb package, I got this error when I tried to run kdocker in the command line:

*kdocker: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory*

After doing some research, I found that the following packages are required to run the program:

[I]/bin/sh
/bin/sh
rpmlib(PayloadFilesHavePrefix) <= 4.0-1
rpmlib(CompressedFileNames) <= 3.0.4-1
libc.so.6
libc.so.6(GLIBC_2.0)
libc.so.6(GLIBC_2.1)
libc.so.6(GLIBC_2.1.3)
libgcc_s.so.1
libgcc_s.so.1(GCC_3.0)
libm.so.6
libqt-mt.so.3
libstdc++.so.5
libstdc++.so.5(GLIBCPP_3.2)
libX11.so.6
libXext.so.6
libXmu.so.6
libXpm.so.4[/I]

So I guess my question is, how do I get these packages with "apt-get install" when it won't let me? I'm a noob, so please be easy on me. Thanks!

---

### Post by Mez on 2005-05-31
are you running KDE? cause you should have the files you need if you are.

---

### Post by jblanco on 2005-05-31
No, I'm using Gnome with Ubuntu 5.04 Hoary.

---

### Post by Hikaru79 on 2005-08-03
Add the following two lines to your sources.list:```
deb http://dinton.no-ip.org/ kubuntu main
deb-src http://dinton.no-ip.org/ kubuntu main
``` That will have KDocker and take care of all dependencies for you. Enjoy :)

---

### Post by lazyrussian on 2006-05-07
Good evening,

These links do not work anymore - adept, kynaptic, synaptic are all reporting this error.

Could anyone help with this? I am looking to install kdocker on to Kubuntu 5.10 - the install options on the tarball file from sourceforge were not helpful to me - I could not "make install" etc... ---> anyway I could get it into my sources.list and install it via adept?

thanks in advance!

---

### Post by TitusDalwards on 2006-05-07
try these for kubuntu:
deb [http://dinton.no-ip.org/](http://dinton.no-ip.org/) kubuntu main
deb-src [http://dinton.no-ip.org/](http://dinton.no-ip.org/) kubuntu main
they must work because they are written on the offical site
[http://kdocker.sourceforge.net/]("http://kdocker.sourceforge.net/")

---

### Post by lazyrussian on 2006-05-07
Nopenot working. Try clicking on those links too ;)- they are dead. 
No-IP is a redirection site from what I remember. Maybe the main site is down or gone...

Thanks for trying though.

Any other suggestions?

---

### Post by x64Jimbo on 2006-07-19
Any news on this? I have quite a few apps that I'd like to start docking to the systray, and none of them support it natively.

---

