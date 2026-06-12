---
title: "fatal error: gtk/gtk.h: No such file or directory"
date: 2015-03-24
forum: Installation &amp; Upgrades
---

### Post by lokesh_chakka on 2015-03-24
i was trying to do gtk programming

i need gtk.h file

I tried to do
[LIST=1]
[*]apt-get install libgtk-3-0
[LIST]
[*]it failed 
[/LIST]
  
[*]apt-get install gtk+3.0
[LIST]
[*]apt-get is success 
[*]but gtk lib was not installed 
[/LIST]
  
[/LIST]

I am still seeing the following error:

fatal error: gtk/gtk.h: No such file or directory

I am using Ubuntu 14.10. can Some one please help me in fixing the issue ?

---

### Post by Impavidus on 2015-03-24
You need the development version of the package to get the header files. On my system that's **libgtk-3-dev**, but I'm running 14.04. On your system it might be **libgkt+3.0-dev**. The package you tried installing contains the library without the headers, which is good enough for running gtk applications, but not for compiling them.

---

