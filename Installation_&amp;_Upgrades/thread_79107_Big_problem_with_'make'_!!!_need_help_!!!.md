---
title: "Big problem with 'make' !!! need help !!!"
date: 2005-10-19
forum: Installation &amp; Upgrades
---

### Post by quai_k8 on 2005-10-19
Hi all !!
I've got a problem with Breezy that i've never had before with Hoary ...
When I try to install something with :

> ./configure
make
sudo make install

I got this error : (exemple with Mplayer, ./configure was successful)

> quaik8@KQ8:~/Downloadz/MPlayer-1.0pre7try2$ make 
config.mak:23: *** missing separator.  Stop.


I really need help !!!!!
THX in advance !!!

---

### Post by skoal on 2005-10-19
That's a formatting problem.  I bet you don't have some particular development packages installed, like automake1.9 or something.  That should pull in the autconf suite as well.

Does it do this for any source you try to compile?  If so, then you don't have some dev package necessary.  Otherwise, check for a patch to that source...

\\//_

---

### Post by quai_k8 on 2005-10-19
Yeah I got this problem for any source I try to compile ..

I've tryed with automake1.9 installed but the same prob !!

---

### Post by quai_k8 on 2005-10-20
up !!! nobody ???

---

### Post by leezer3 on 2005-10-20
Try installing gcc 3.8- Mebbe this is a result of the changes in GCC4?

Cheers

-Leezer-

---

