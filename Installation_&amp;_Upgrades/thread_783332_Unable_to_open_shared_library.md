---
title: "Unable to open shared library"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by Sid1980 on 2008-05-05
Hello Everyone,

I m using ubuntu 8.04 version and trying to execute dreamup software for dreambox but whenever i try to execute the error comes " error while loading shared libraries: libglib-1.2.so.0 :cannot open shared object file: No such file or directory" 

Can anyone tip me pls :)

Thx

---

### Post by macaholic on 2008-05-05
My guess is you don't have libglib 1.2 installed. What is the output of ```
dpkg -l | grep libglib 
```

---

### Post by Sid1980 on 2008-05-05
> **macaholic said:**
> My guess is you don't have libglib 1.2 installed. What is the output of ```
dpkg -l | grep libglib 
```

Macaholic the output is 

ii  libglib-perl                               1:1.161-1                                          Perl interface to the GLib and GObject libra
rc  libglib1.2                                 1.2.10-17build1                                    The GLib library of C routines
ii  libglib2.0-0                               2.16.3-1                                           The GLib library of C routines
ii  libglib2.0-cil                             2.12.0-2ubuntu3                                    CLI binding for the GLib utility library 2.1
ii  libglibmm-2.4-1c2a                         2.16.0-1                                           C++ wrapper for the GLib toolkit (shared lib

---

### Post by ps2chiper on 2008-07-14
I also have this same problem and need a solution.

---

