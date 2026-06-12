---
title: "Installing software"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by layers on 2010-10-18
Hi. I have never installed anything on Ubuntu from files, and I do not know how to do it. There are have been internet pages I have visited, but each one tells you to do it in a different method, and each one is more complicated that the last. So, I was wondering if anyone knows the simplest way of installing Matlab - I have these files:
```
ibo@ibo-laptop:~$ ls -l Desktop/matlab
total 1732
-rw-r--r-- 1 ibo ibo    3262 2010-10-11 14:43 activate.ini
-rw-r--r-- 1 ibo ibo   43320 2010-10-11 14:43 install
drwx------ 3 ibo ibo    4096 2010-10-11 14:35 InstallForMacOSX.app
-rw-r--r-- 1 ibo ibo   73937 2010-10-11 14:43 license.txt
-rw-r--r-- 1 ibo ibo 1615703 2010-10-11 14:43 mac_install_guide.pdf
-rw-r--r-- 1 ibo ibo    5839 2010-10-11 14:43 readme.txt
drwx------ 6 ibo ibo    4096 2010-10-11 14:35 update
drwx------ 3 ibo ibo    4096 2010-10-11 14:35 utils
ibo@ibo-laptop:~$ 

```

What would be the easiest way?

---

### Post by TNT1 on 2010-10-18
Is that a mac program?

---

### Post by layers on 2010-10-18
> **tnt1 said:**
> is that a mac program?

unix

---

### Post by TNT1 on 2010-10-18
> **layers said:**
> unix

That's a broad term... Hope you get the help you need.

---

### Post by Don544 on 2010-10-18
Try this how to page at Clemson, but from what I saw the Linux edition contains linux in the title not Mac os x.
Hope this is some help
[http://learn.clemsonlinux.org/wiki/Clemson:Matlab](http://learn.clemsonlinux.org/wiki/Clemson:Matlab)

---

### Post by TNT1 on 2010-10-18
> **Don544 said:**
>  from what I saw the Linux edition contains linux in the title not Mac os x.


That's what I was getting at...

---

### Post by Don544 on 2010-10-18
Or you could try an iso bootable dvd with image burn and use that to install. That is if it is the linux variety.
ImgBurn supports all the [**Microsoft Windows**]("http://www.microsoft.com/")  OS's - Windows 95, Windows 98, Windows Me, Windows NT4, Windows 2000,  Windows XP, Windows 2003, Windows Vista, Windows 2008 and Windows 7  (including all the 64-bit versions). If you use [**Wine**]("http://www.winehq.com/"), it should also run on [**Linux**]("http://www.linux.org/") and other x86-based Unixes. 
And image burn is freeware.
Don

---

### Post by Don544 on 2010-10-18
And one last
 Since MATLAB is a licenced software, And  each time we run MATLAB, licence verification is needed. 


[Scilab]("http://scilabsoft.inria.fr/") is a good alternative (it is free) and as powerful as MATLAB. 

[http://www.scilab.org/products/scilab/download](http://www.scilab.org/products/scilab/download)

 Octave which comes in RH distro CDs is also quite good.
[http://ubuntuforums.org/showthread.php?t=663634](http://ubuntuforums.org/showthread.php?t=663634)
Don

---

### Post by layers on 2010-10-19
I just went with SciLab. Thanks for letting me know.

---

### Post by layers on 2010-11-23
OK, so now in SciLab, I am trying to get the Laplace transform of a few functions, but this is what happens every time I try that:
```
-->syms s t;
  !--error 4 
Undefined variable: syms
```
Does anyone know what I have to install to make this work?

PS: I'm trying to find Laplace inverses like here:

[http://www.cert.fr/dcsd/idco/perso/Magni/s_sym/html/ilaplace.html]("http://www.cert.fr/dcsd/idco/perso/Magni/s_sym/html/ilaplace.html")

---

