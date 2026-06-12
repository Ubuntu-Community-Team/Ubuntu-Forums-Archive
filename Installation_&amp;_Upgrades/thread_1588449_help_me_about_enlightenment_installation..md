---
title: "help me about enlightenment installation."
date: 2010-10-04
forum: Installation &amp; Upgrades
---

### Post by jellay17 on 2010-10-04
how can i install enlightenment in my ubuntu server? please help me.. this is one of our projects.. i've been searching all day.. apt-get install doesn't work because the package is not available.. can someone please help me? i really need it.. thanks a lot in advance..

---

### Post by Sef on 2010-10-05
> how can i install enlightenment in my ubuntu server? please help me.. this is one of our projects.. i've been searching all day.. apt-get install doesn't work because the package is not available.. can someone please help me? i really need it.. thanks a lot in advance..

Enlightenment Window Manager is in the repositories.  Are multiverse and universe enabled? Just type in englightenment window manager.

---

### Post by foxmulder881 on 2010-10-05
Here you go, try this...

> sudo aptitude install e16

---

### Post by jellay17 on 2010-10-05
how about using wget? can you give me a link where i can download the enlightenment? a good link..

---

### Post by foxmulder881 on 2010-10-05
It's the same as what's in the Lucid repos, but here you go. You can download with wget using the following links. And don't forget to install with gebi and it'll pull in all the required dependencies also.

i386
[http://mirrors.kernel.org/ubuntu/pool/universe/e/e16/e16_1.0.0-3.1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/e/e16/e16_1.0.0-3.1_i386.deb)

amd64
[http://mirrors.kernel.org/ubuntu/pool/universe/e/e16/e16_1.0.0-3.1_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/universe/e/e16/e16_1.0.0-3.1_amd64.deb)

---

### Post by jellay17 on 2010-10-05
> **foxmulder881 said:**
> It's the same as what's in the Lucid repos, but here you go. You can download with wget using the following links. And don't forget to install with gebi and it'll pull in all the required dependencies also.

i386
[http://mirrors.kernel.org/ubuntu/pool/universe/e/e16/e16_1.0.0-3.1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/e/e16/e16_1.0.0-3.1_i386.deb)

amd64
[http://mirrors.kernel.org/ubuntu/pool/universe/e/e16/e16_1.0.0-3.1_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/universe/e/e16/e16_1.0.0-3.1_amd64.deb)


where can i find the gebi?

---

### Post by foxmulder881 on 2010-10-06
gdebi is already installed on your system. It's the command line system to install deb packages.

---

