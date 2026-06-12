---
title: "After upgrade to 11.10, can't compile ITK: ptrdiff_t’ was not declared in this scope"
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by sinan-lab on 2011-10-22
Hi all,

I've just upgraded to ubuntu 11.10, when trying to compile ITK I get the error:

..../ITK-3.20.0/include/IO/itkConvertPixelBuffer.txx:255:5: error: ‘ptrdiff_t’ was not declared in this scope.

before the upgrading everything was fine.

Thank alot for help.

---

### Post by caats on 2011-10-26
it happen to me today.. :(

i was working on Ubuntu 10.10 (but with some problems about some drivers) and to solve that problems
i've got this one. ( compiling itk) really bad luck!!

any solution?

thanks

---

### Post by sinan-lab on 2011-10-27
Hi caat,
am still trying but no solution sofar...
However, if you want to compile ITK alone, this will solve it
 
[http://www.vtk.org/Wiki/ITK/Git/Download](http://www.vtk.org/Wiki/ITK/Git/Download)
 
:)

---

### Post by caats on 2011-10-31
> **sinan-lab said:**
> Hi caat,

 
[http://www.vtk.org/Wiki/ITK/Git/Download](http://www.vtk.org/Wiki/ITK/Git/Download)
 
:)
thanks any way, but i've got to have this operational, so, i installed ubuntu 11.04. 
:P

---

