---
title: "Installing GDL in ubuntu"
date: 2007-03-01
forum: Installation &amp; Upgrades
---

### Post by lenluin on 2007-03-01
I've been trying to install GDL for quite a while..at first, I was missing some libraries, but I now have all of them.
I run:
./configure --with-python=no

With no problems. I'd prefer to try to keep ImageMagick in my install if at all possible. The error comes durign the make process:

plotting.cpp: In function ‘void lib::plot(EnvT*)’:
plotting.cpp:975: error: ‘class GDLGStream’ has no member named ‘gvpd’
make[3]: *** [gdl-plotting.o] Error 1
make[3]: Leaving directory `/home/sovellis/Desktop/gdl-0.9pre4/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/sovellis/Desktop/gdl-0.9pre4/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sovellis/Desktop/gdl-0.9pre4'
make: *** [all] Error 2


Any ideas would be greatly appreciated.

---

### Post by lenluin on 2007-03-01
I forgot to mention, ./configure works even without --with-python=no, but having it there allows make to run longer.

The GDL version I'm trying to install is 0.9pre4

---

### Post by Laerte Andrade on 2007-03-02
Are you using dapper or edgy? A friend of mine had this same problem when using dapper. After dist-upgrading, everything worked.

---

### Post by lenluin on 2007-03-02
I'm on Dapper.... Hmmmm, maybe I should update to Edgy. The reason I'm on Dapper is because I downloaded them both, and my Dapper iso worked, where as my Edgy iso didn't.

---

### Post by lenluin on 2007-03-03
Hey man, I really appreciate your help, your advice was dead on. After I updated to Edgy Eft, suddenly, the install, just....worked. I'm befuddled, but satisfied.

---

