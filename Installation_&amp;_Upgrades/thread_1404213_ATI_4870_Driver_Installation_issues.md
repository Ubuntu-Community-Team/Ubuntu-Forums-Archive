---
title: "ATI 4870 Driver Installation issues"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by Bluesymbol on 2010-02-11
Hey people, 

relative linux noob, so please be gentle! haha


I've just installed 9.10 x64 onto my desktop running a 4870. Try to build the package with the command.  



[I]sudo sh ./ati-driver-installer-10-1-x86.x86_64.run --buildpkg Ubuntu/karmic
[/I]


It fails with the following output in terminal...


[I]dpkg-shlibdeps: error: couldn't find library libatiuki.so.1 needed by debian/xorg-driver-fglrx/usr/lib/xorg/modules/linux/libfglrxdrm.so (ELF format: 'elf64-x86-64'; RPATH: '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: dpkg-shlibdeps returned exit code 2
make: *** [binary-predeb-IMPL/xorg-driver-fglrx] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.GYd8Y1
[/I]


plus alot more similar output... the standard ubuntu fglrx installed ok, but this does not even attempt to see the dual head card as to add to this lil problem im running dual screens!


My overall goal is to get the duals running to allow me to run virtualbox giving me access to the full 8GB RAM ive got as of course ubuntu's overhead is a hell of a lot less than Vista/7s!

Cheers

Blue

---

