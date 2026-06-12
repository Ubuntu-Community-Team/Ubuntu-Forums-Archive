---
title: "need help with ./configure for GNU GCC install"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by alexkaz on 2010-01-02
when attempting to implement ./configure to , the respnse is "source not found".

Help?

---

### Post by alexkaz on 2010-01-02
As  a newbie, still struggling with downloading, configuring and installing GNU GCC 4.4.2 and GNU G++ 4.4.2.

understanding is should be as simple as these following steps: 
1. Download tar.gz from GNU GCC download mirror site (but which folder or directory path should it be downloaded to?)

2. Extract files into 'srcdir', which is different than the build directory 'objdir' (should those 2 directories have the same parent folder, i.e. GCC/srcdir and GCC/obdir ?)

3. Then create 'objdir'   prompt: mkdir objdir, then cd objdir, then ./configure. 
Those steps should cause the configure file to run, then at the prompt: make, then enter makefile install. 

However, ./configure tells the computer to run the configure file in the directory you're currently in (./ syntax).  So if you're supposed to build in a different directory than the srcdir, should you run the ./configure in the srcdir? and if so, how do you tell the computer to build in the objdir ?  or is the build a seperate step from the sequence: ./configure  ;  make  ; makefile install?

So in a nutshell - should the gnu-gcc zip file be downloaded anywhere (i.e. Download file),?
 then extracted in the administrative file system, such as user/bin or is a specif folder mandated or required?
then create an adjacent, same level folder  for the 'srcdir'  as the 'objdir'?
then cd in to the objdir and implement the command sequence: ./configure  ; make ; makeinstall ?

Thank you for your help. 
I have gotten as far as th asp-get -s file command to verify that the gcc and g++ are the uptodate versions. 
But when ./configure is implemented, the error file not found, or source not found appears. 

Also, I understand gcc needs to be in the $Path for the ./configure file to run, should the gcc folder be the partent of both srcdir and objdir?
Again, thank you for your help.

---

