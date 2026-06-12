---
title: "can't install ddd in ubuntu 8.04, help me!!!"
date: 2008-10-23
forum: Installation &amp; Upgrades
---

### Post by microtiger on 2008-10-23
I have installed ddd following this:
$sudo apt-get install ddd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ddd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

$ddd
ddd: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

so i have to installing ddd in source code, download ddd-3.3.9 from [ftp://ftp.gnu.org/gnu/ddd/](ftp://ftp.gnu.org/gnu/ddd/), after that, 
$sudo ./configure
###the error is
......
......
......
checking for streampos... no
checking for std::streampos... yes
checking whether the C++ compiler (g++) accepts -fpermissive... (cached) yes
checking for X... no
checking whether libXext is in the standard X library path... no
checking whether libXp is in the standard X library path... no
checking whether libXmu is in the standard X library path... no
checking for Motif... libraries /usr/lib, headers (none)
checking for Xpm... libraries /usr/lib, headers (none)
checking for Athena... libraries /usr/lib, headers (none)
checking whether compiling X headers requires -fpermissive... no
checking for XOpenDisplay in -lX11... no
configure: error: The X11 library '-lX11' could not be found.
                  Please use the configure options '--x-includes=DIR'
                  and '--x-libraries=DIR' to specify the X location.
                  See the files 'config.log' and 'ddd/config.log'
                  for further diagnostics.
anyone who install ddd on ubuntu 8.04 sucessful please help me!
thank you very much!

---

### Post by Partyboi2 on 2008-10-24
If you are going to compile it install the dev packages from the ubuntu repos. You can do this by opening a terminal and
```
sudo apt-get build-dep ddd
```

---

