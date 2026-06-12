---
title: "difference between &quot;makefile&quot; and &quot;makefile.am&quot;s"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by blwfsoj on 2010-01-04
I'm installing a package but that package doesn't has "makeFile" file, it only has "makefile.am" and "makefile.in". 
therefore when ever i use the "make" command i get:
"make: *** No targets specified and no makefile found.  Stop."

what is the solution.
please help 

regards,

---

### Post by raffaele181188 on 2010-01-04
The Makefile will be generated from another script. Please, look for a "configure", "configure.py" or something similar (or read INSTALL / README)

---

### Post by zine92 on 2010-01-04
Most probably you need to go to your terminal and type,
```
cd /your/codes/location/ 
```

then type ./configure and then make and make install maybe with sudo command.
```
./configure
```
```
make
```
```
make install
```
and maybe 
```
make clean
```
Not too sure about this though.

---

