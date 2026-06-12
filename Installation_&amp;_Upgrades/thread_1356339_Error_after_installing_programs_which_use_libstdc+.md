---
title: "Error after installing programs which use libstdc++5"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by kaleem.sa on 2009-12-16
HI Everyybody,

i am an IT administrator and we recently migrated from windows to ubuntu (jaunty).

every thing was smooth in jaunty but recently we installed the newer version of UBUNTU i.e; KARMIC.

we used to run some applications which had libstdc++5 as their dependency.

whenever we are installing the same applications in KARMIC we are getting error starting nautilus and any other application (apt,software and sources etc)

the error i get is 
 libstdc++.so.6: version `GLIBCXX-3.4.11' not found (required by libexempi.so.3)

can anyone help with this.

thanks in advance.

regards,
KALEEM

---

### Post by Ellouafiq Ali on 2011-05-26
*Hello Kaleem *

Sorry for the late reply, I had the same problem as you and I solved it. I was crawling on forums, where I've found this post, I didn't found any solution so I tried to figure it on my own. Thanks to god I fixed it.

I hope this will be helpful for the other users.
Anyway.

The Problem is created because you've replaced the standard C++ library by an older version.
In order to know which libraries, or versions your package supports,
fetch the string inside **libstdc++ **using:
```
strings /usr/lib/libstdc++.so.6 | grep GLIBC
```so that you get all the versions of **GLIBC** that your libstdc++ supports
(to have a clear idea what you are missing)
to decide which version to install, to know your missing version or how far you are from it

Now to get practical:
Here where you can find the fixes , **GLIBC 3.4.11** is available starting **lucid lynx**
you may need a newer version according to your Ubuntu distribution.
(click-able links!!)
  
[LIST]
[*][I][COLOR=Black][dapper]("http://packages.ubuntu.com/dapper/libstdc++6") (base): [/COLOR]    The GNU Standard C++ Library v3            
4.0.3-1ubuntu5: amd64 i386 powerpc               [/I]
[*][I][hardy]("http://packages.ubuntu.com/hardy/libstdc++6") (base):     The GNU Standard C++ Library v3            
4.2.4-1ubuntu3 [**security**]: amd64 i386               [/I]
[*][I][hardy-updates]("http://packages.ubuntu.com/hardy-updates/libstdc++6") (base):     The GNU Standard C++ Library v3            
4.2.4-1ubuntu4: amd64 i386
(old distributions in italic)
[/I]
[*][COLOR=SeaGreen][lucid]("http://packages.ubuntu.com/lucid/libstdc++6")[/COLOR] (libs):     The GNU Standard C++ Library v3            
4.4.3-4ubuntu5: amd64 i386
[*][COLOR=SeaGreen][maverick]("http://packages.ubuntu.com/maverick/libstdc++6")[/COLOR] (libs):     The GNU Standard C++ Library v3            
4.5.1-7ubuntu2: amd64 i386
[*][COLOR=SeaGreen][natty]("http://packages.ubuntu.com/natty/libstdc++6")[/COLOR] (libs):     The GNU Standard C++ Library v3            
4.5.2-8ubuntu4: amd64 i386
[*][COLOR=SeaGreen][oneiric]("http://packages.ubuntu.com/oneiric/libstdc++6")[/COLOR] (libs):     The GNU Standard C++ Library v3            
4.6.0-7ubuntu1: amd64 i386
[/LIST]
[COLOR=Red]**NB: **[/COLOR]**Before Installing or Replacing any package on your machine, please check the compatibilities and the requirements of each package. To avoid wasted hours of fixes.**

Best Of Luck
Ali Elouafiq (aka Keelhaule)
**[COLOR=MediumTurquoise][http://twitter.com/keelhaule](http://twitter.com/keelhaule)[/COLOR]**

---

