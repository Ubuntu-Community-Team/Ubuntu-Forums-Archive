---
title: "Installing gtk+-2.0 library."
date: 2012-01-23
forum: Installation &amp; Upgrades
---

### Post by spotsnz on 2012-01-23
Hi guys. So I've been working on this programming project on the university computers. I'm writing in C and using the gtk+-2.0 library. Program compiles and runs fine on the university computers. (They use a Fedora distro). 

So I'm wanting to be able to work on this project at home. I have both a desktop and a laptop, and they both run Ubuntu 11.10.

So can someone talk me through the installation of libraries? 

For a start - when i #include <libraryinsidethesebraces.h> how does the compiler or whatever actually know where to look? 
(As opposed to #include "doublequotemarks.h" it looks in the specified folder). 

On my laptop I just quickly googled to find the installation, on most results are suggesting using something like :

```
$ sudo apt-get install libgtk2.0-dev
```

I've done that, and it still doesn't compile. It gives me 'undefined reference to... [all the gtk funtions I use]'. 

the compile line looks like: 
```
gcc `pkg-config --libs gtk+-2.0` -o mainout main.o draw.o floyds.o simpletools.o graph.o tads.o bucket.o
```

what am I doing wrong?



Also: as a side, while we're here -
Looking at this page
[http://developer.gnome.org/gtk3/stable/gtk-building.html](http://developer.gnome.org/gtk3/stable/gtk-building.html)

What do they mean by
'Compiling gtk+ libraries'?
And 'building gtk+'? 

The way I thought it would work - is that these libraries would be still in source code form, and when you use them and compile your own program, it compiles them then? (Or perhaps that would take too long?).

---

