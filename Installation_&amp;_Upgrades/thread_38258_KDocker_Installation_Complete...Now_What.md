---
title: "KDocker Installation Complete...Now What?"
date: 2005-05-30
forum: Installation &amp; Upgrades
---

### Post by jblanco on 2005-05-30
I just installed KDocker and I have no idea how to run the program. I tried using the syntax on their website which is supposed to be "KDocker" in the command line, but it's not found. I used Alien to install it and it didn't throw any errors so I assume it's in here. I'm a noob and don't know how to find out either. Any help would be greatly appreciated!!  :)

---

### Post by tread on 2005-05-30
Start synaptic, and search for kdocker. Once you have located it, you can right-click and see a list of installed files.

---

### Post by jblanco on 2005-05-30
Alright, I opened it up and I found it but all it says underneath is:

Converted Slackware tgz package

(Converted from a tgz package by alien version 8.50.)

There's no information how to run the program. I tried kdocker but that didn't seem to work either.

---

### Post by jblanco on 2005-05-31
Well after some playing around, I tried removing the program and re-installing it using apt-get. When I try it though it comes up with this error:

[I]Package kdocker is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source[/I]

And when it was installed I got this error when I tried to run kdocker in the command line:

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

So I guess my question is, how do I get these packages with apt-get install when it won't let me? I'm a noob, so please be easy on me :) Thanks!

---

