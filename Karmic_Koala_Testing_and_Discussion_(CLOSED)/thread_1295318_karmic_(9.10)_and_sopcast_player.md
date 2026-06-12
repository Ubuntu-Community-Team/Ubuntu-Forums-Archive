---
title: "karmic (9.10) and sopcast player"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by c001os on 2009-10-19
Now after i upgrade my system to karmic, I cant install sp-auth_3.0.1_i386.deb from [http://sopcast-player.googlecode.com](http://sopcast-player.googlecode.com) 
I get the following error: libstdc++5 missing! I cant find the missing package in synaptic.

Is there some fix for it? 

thx

---

### Post by oboedad55 on 2009-10-19
> **c001os said:**
> Now after i upgrade my system to karmic, I cant install sp-auth_3.0.1_i386.deb from [http://sopcast-player.googlecode.com](http://sopcast-player.googlecode.com) 
I get the following error: libstdc++5 missing! I cant find the missing package in synaptic.

Is there some fix for it? 

thx

Have you installed medibuntu, as well as the restricted extras and so on?

---

### Post by filologen on 2009-10-19
Just for your information, on my 64 bit system with medibuntu enabled, the installation works.

---

### Post by dinxter on 2009-10-20
libstdc++5 is dropped in karmic, you can download it and from the sopcast page just below the linux sp-sc download (or get the 386 package from the jaunty repository)
[http://www.sopcast.com/download/](http://www.sopcast.com/download/)
[http://packages.ubuntu.com/jaunty/libstdc++5](http://packages.ubuntu.com/jaunty/libstdc++5)

---

### Post by c001os on 2009-10-20
Thx all the replies! With medibuntu i cant install but the seperated libstdc++5.deb dowload fixed the problem!

thx

---

