---
title: "Kernel Compile"
date: 2011-08-13
forum: Installation &amp; Upgrades
---

### Post by Cazzimma on 2011-08-13
Question 1.
I am following the serveral tutorials for recompile source kernel. 
*(for example [http://newbiedoc.sourceforge.net/system/kernel-pkg.html](http://newbiedoc.sourceforge.net/system/kernel-pkg.html) )*
All goes ok BUT when i modify a _single_ files
*(for example just fs.h)*
and i redo all the steps, it recompiles ALL the .o and all the files in the kernel without "touching" only the modified file.
why is that ? am i missing something? Is it normal ?

Question 2.
I got some kernel code how can i know for which kernel version has been written? 
I ask this because this code is working for sure but it wont compile on my kernel version so I have reasons to believe that it is written for some particular kernel versions
(example i am using the 2.6.38.8, is it possible that the code suits for the 2.6.3x.y ? what is for sure that the code is written in 2.6.z.w)
  
p.s. i'm very sorry about my bad english :D

---

### Post by dino99 on 2011-08-13
kernels ready to use:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

download into an empty folder:
 headers-all + header-i386 (or amd64) +image-i386 (or amd64)
then goto that folder and run: sudo dpkg -i *

kernel to compile:
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by Cazzimma on 2011-08-18
@Dino that link is great and very useful. But how can it solve my problem? i need to recompile kernel because i changed some stuffs on kernel-side code. Why should i need pre-compiled images ?
 
Pheraps i did not explain well my problem.

Problem 1 "it recompiles all the .c again and again" :
t1 : compile kernel source.
t2 : compilation succesfull.
t3 : mount image ...
[COLOR="Lime"]t4 : all happy.[/COLOR]
[COLOR="DarkRed"]t5 : modify kernel source.[/COLOR] (a single file for example open.c )
[COLOR="Red"]t6 : compile ALL files again.[/COLOR] (not only open.c but everithing) --> waste of time.

I am just doing the steps of
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
this very guide.

[COLOR="red"]why it recompiles all the files even if i modified only one??[/COLOR]

---

