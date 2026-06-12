---
title: "Installing intel fortran"
date: 2015-02-25
forum: Installation &amp; Upgrades
---

### Post by nader3 on 2015-02-25
Hi everybody,
I am very new to ubuntu. I am trying to install ifort on 14.4 but it does not work.
The problem is, I installed ifort but when I type ifort on terminal, I get this result:
"ifort: command not found"
I tried to use the procedure in " http://ubuntuforums.org/showthread.php?t=1082782". but it didnot work for me. 
I want to know that can we still use the same procedure on ubuntu 14.4 ( since it has posted on 2008) or I need to follow another instruction?

Thank you

---

### Post by tgalati4 on 2015-02-26
What is the output of:

```
which ifort
```

Is there a reason that you can't use *gfortran*?

```
sudo apt-get install gfortran
```

---

### Post by nader3 on 2015-03-25
When I type

which ifort

 It does not show anything 

Actually I am going to install a software which is based on intel fortran compiler.

---

### Post by ubfan1 on 2015-03-25
Did you follow the PATH and LD_LIBRARY_PATH instructions in your link, altering to match where you installed the compiler?

---

### Post by MAFoElffen on 2015-03-25
I noticed other fixes for ifort on Ubuntu and on other distros... is that ifort install does not configure itself in the path... so if you add the path to your user .bashrc file, it show then see it. Other? You are using it on 32 bit sys? Cause if on a 64 bit sys, then you need the lib32 package installed... cause "ifort" is a 32bit build.

Hope those tips help you out.

---

### Post by nader3 on 2015-03-31
Yes I did. 
I am too new to ubuntu and I think I followed what was in the procedure. I think it would be wonderful if someone could update this page "http://ubuntuforums.org/showthread.php?t=1082782" for ubuntu 14.04 (since the intel page has also changed )

---

