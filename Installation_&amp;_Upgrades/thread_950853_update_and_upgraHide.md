---
title: "update and upgraHide"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by rania kamal on 2008-10-17
Hi all,
      i was check the version of g++ in my system, by g++ -v, and i found it gcc version 4.1.3 and i want to install g++ 4.2.4 to compile some thing, and i found the following:-

1- when check g++ version

rania@rania-desktop:~$ g++ -v
> Using built-in specs.
> Target: i486-linux-gnu
> Configured with: ../src/configure -v
> --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr
> --enable-shared --with-system-zlib --libexecdir=/usr/lib
> --without-included-gettext --enable-threads=posix --enable-nls
> --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1
> --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug
> --enable-mpfr --enable-checking=release i486-linux-gnu
> Thread model: posix
> gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
> rania@rania-desktop:~$ 
> 
and 
2- when try to install g++ 4.2.4

rania@rania-desktop:~$ sudo apt-get install g++ 4.2.4
>> Reading package lists... Done
>> Building dependency tree       
>> Reading state information... Done
>> g++ is already the newest version.
>> g++ set to manual installed.
>> E: Couldn't find package 4.2.4

what can i do to solve this problem
i wait ur responses
thanks

---

