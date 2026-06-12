---
title: "open watcom c linux 1.9 unable to install"
date: 2010-12-16
forum: Installation &amp; Upgrades
---

### Post by m_z_farooqui on 2010-12-16
Hi 
Few days ago I started to use ubuntu. So i am a new user. I am using ubuntu-10.10-desktop-i386. I want to install open watcom C/C++ and fortran compiler which I had downloaded from the following site
[http://openwatcom.mirror.fr/](http://openwatcom.mirror.fr/)

I downloaded the following files
1 - open-watcom-c-linux-1.9.md5
2 - open-watcom-c-linux-1.9 
3 - open-watcom-f77-linux-1.9.md5
4 - open-watcom-f77-linux-1.9

but I don't know how to install these files on Ubuntu. Kindly help me in this regards or tell me some other solution to install open watcom C/C++ and fortran Compiler

Regards.
Farooqui

---

### Post by brujoquizz on 2010-12-16
Hi! Welcome to the forums!

First of all, the md5 files are only to know if what you have downloaded is correct, so you don't need them.

Open a Terminal (Aplications -> Accesories -> Terminal) and browse to the directory where you have the files ("cd Downloads", or wherever are your files). Once you are there give permission to execute the files:
```
chmod ugo+rwx open-watcom-f77-linux-1.9
chmod ugo+rwx open-watcom-c-linux-1.9
```

Once you have permission to execute the files you can try to install them:
```
sudo ./open-watcom-f77-linux-1.9
sudo ./open-watcom-c-linux-1.9
```

I don't know exactly if this procedure would work because I run a 64bit-ubuntu and I get a coma exception when trying to execute them.

If you want another Fortran or C compiler you can search the Software Center for some of them (gfortran is like fortran 95 and g++ and gcc are like c++ and c).

---

