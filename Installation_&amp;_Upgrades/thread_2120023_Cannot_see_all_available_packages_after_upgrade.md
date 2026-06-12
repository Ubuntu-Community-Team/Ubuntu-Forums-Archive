---
title: "Cannot see all available packages after upgrade"
date: 2013-02-25
forum: Installation &amp; Upgrades
---

### Post by richard1054 on 2013-02-25
I hope that someone can help with this one.  I am going round in circles.

I have upgraded a server from natty to precise, via oneiric.   All seems to be working well, until I try and install some additional packages - which apparently do not exist.  I know they exist, because I've got them installed on another precise box, and I can see them on packages.ubuntu.com.  I'm not sure whether I'm explaining myself very well here, so let me demonstrate.

ON the problem box:
root@thistles:/etc/apt# aptitude search graphicsmagick
root@thistles:/etc/apt#

On the working box:
richard@nice:~$ aptitude search graphicsmagick
p   graphicsmagick                  - collection of image processing tools      
p   graphicsmagick:i386             - collection of image processing tools      
p   graphicsmagick-dbg              - format-independent image processing - debu
p   graphicsmagick-dbg:i386         - format-independent image processing - debu
p   graphicsmagick-imagemagick-comp - image processing tools providing ImageMagi
p   graphicsmagick-libmagick-dev-co - image processing libraries providing Image
v   libgraphicsmagick++-dev         -                                           
v   libgraphicsmagick++-dev:i386    -                                           
p   libgraphicsmagick++1-dev        - format-independent image processing - C++ 
p   libgraphicsmagick++1-dev:i386   - format-independent image processing - C++ 
i A libgraphicsmagick++3            - format-independent image processing - C++ 
p   libgraphicsmagick++3:i386       - format-independent image processing - C++ 
v   libgraphicsmagick-dev           -                                           
v   libgraphicsmagick-dev:i386      -                                           
i   libgraphicsmagick1-dev          - format-independent image processing - C de
p   libgraphicsmagick1-dev:i386     - format-independent image processing - C de
i A libgraphicsmagick3              - format-independent image processing - C sh
p   libgraphicsmagick3:i386         - format-independent image processing - C sh

further:
root@thistles:/etc/apt# aptitude search '\-dev' |wc -l
323
richard@nice:~$ aptitude search '\-dev' |wc -l
9779

I've tried removing /var/lib/apt/lists/*
I've tried using sources.list from the box that is behaving
I've run apt-get update many times

Nothing works.

I've used Ubuntu almost since the beginning, and I've never encountered this before.  Please help, I think I'm on the verge of a nervous breakdown.

---

### Post by richard1054 on 2013-02-25
Ah, the confessional method of debugging... problem solved.  Somehow (and I don't remember doing this) I had removed from sources.list everything except the security repositories.  I've put the repositories back now, and everything seems to be working.

Perhaps I'm getting too old for 18-hour days...

---

