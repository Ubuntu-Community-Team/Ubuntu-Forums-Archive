---
title: "libdl.so not found"
date: 2012-07-06
forum: Installation &amp; Upgrades
---

### Post by mattyclarkson on 2012-07-06
I am using a Ubuntu Amazon EC2 cloud instance and cannot build anything on it because [FONT="Courier New"]libdl.so[/FONT] is missing.

```
g++ -g -O2 -o .libs/DllPlugInTester DllPlugInTester.o CommandLineParser.o  -ldl ../../src/cppunit/.libs/libcppunit.so -lm  -Wl,--rpath -Wl,/home/ubuntu/cppunit/lib
../../src/cppunit/.libs/libcppunit.so: undefined reference to `dlsym'
../../src/cppunit/.libs/libcppunit.so: undefined reference to `dlopen'
../../src/cppunit/.libs/libcppunit.so: undefined reference to `dlclose'
```

```
ubuntu@ip-10-196-63-1:~/junit/source$ whereis libdl
libdl:
```

And I have [FONT="Courier New"]libc6[/FONT] installed

```
ubuntu@ip-10-196-63-1:~/junit/source$ sudo apt-get install libc6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

I'm more of a Fedora/Red Hat guy so this is quite confusing - why isn't there [FONT="Courier New"]/lib(32|64)/libdl.so[/FONT] available?

What do I need to install to start compiling?

This is what I installed as a start on the instance:
```
sudo apt-get install python python3 subversion openjdk-7-jdk wget tar unzip gcc g++
```

---

### Post by kc1di on 2012-07-06
you may have to install the ia32 libs also if your building in a 64 bit environment.

---

