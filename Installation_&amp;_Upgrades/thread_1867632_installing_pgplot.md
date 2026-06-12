---
title: "installing pgplot"
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by birdhen on 2011-10-23
Hi there,

I am trying to install pgplot.
I have followed the instructions given here [http://www.astro.caltech.edu/~tjp/pgplot/install-unix.html]("http://www.astro.caltech.edu/%7Etjp/pgplot/install-unix.html").
However, when I get to "make" the following error is given:

f77 -c -u /home/angela/etc/pgplot/src/pgarro.f
make: f77: Command not found
make: *** [pgarro.o] Error 127

I have seen a previous post with exactly the same problem (13/01/10-**Trying to install pgplot **), which has not been resolved. I do have the file pgarro.f in the src folder though.
I have installed gfortran.
Can anyone help with this?

Thanks.

---

### Post by ~!geek!~ on 2011-10-23
> **birdhen said:**
> Hi there,

I am trying to install pgplot.
I have followed the instructions given here [http://www.astro.caltech.edu/~tjp/pgplot/install-unix.html]("http://www.astro.caltech.edu/%7Etjp/pgplot/install-unix.html").
However, when I get to &quot;make&quot; the following error is given:

f77 -c -u /home/angela/etc/pgplot/src/pgarro.f
make: f77: Command not found
make: *** [pgarro.o] Error 127

I have seen a previous post with exactly the same problem (13/01/10-**Trying to install pgplot **), which has not been resolved. I do have the file pgarro.f in the src folder though.
I have installed gfortran.
Can anyone help with this?

Thanks.

 Try this from the directory containing source files: 1) make clean 
2) sudo apt-get install fort77 
3) Now run make command as: make 
4) If make runs successfully, run sudo make install to finish installation..

---

