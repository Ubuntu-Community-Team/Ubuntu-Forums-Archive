---
title: "Install ns-2 on ubuntu 11.04"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by helyos on 2011-05-09
Hi there, 

I am a newbie and i have to simulate LEACH protocol in NS2 for a school project.

I tried to install ns-allinone-2.34 on ubuntu 11.04(i run it on a virtual machine) but afer i run ./install it gave me:

```
ld -shared -o libotcl.so otcl.o
otcl.o: In function `OTclDispatch':
/home/rares/ns-allinone-2.34/otcl-1.13/otcl.c:495: undefined reference to `__stack_chk_fail_local'
otcl.o: In function `Otcl_Init':
/home/rares/ns-allinone-2.34/otcl-1.13/otcl.c:2284: undefined reference to `__stack_chk_fail_local'
ld: libotcl.so: hidden symbol `__stack_chk_fail_local' isn't defined
ld: final link failed: Bad value
make: *** [libotcl.so] Error 1
otcl-1.13 make failed! Exiting ...
See http://www.isi.edu/nsnam/ns/ns-problems.html for problems
rares@ubuntu:~/ns-allinone-2.34$ ^C
rares@ubuntu:~/ns-allinone-2.34$
```

Can someone help me to install this network simulator? 
Thank you in advance

---

### Post by helyos on 2011-05-10
Nobody?

---

### Post by saylee on 2011-05-21
hey you can have a look at this url [http://erl1.wordpress.com/2011/05/12/installing-ns-2-34-on-ubuntu-11-04/](http://erl1.wordpress.com/2011/05/12/installing-ns-2-34-on-ubuntu-11-04/)

i am upgrading from ubuntu 10.10 to 11.04 and have ns 2.34 already installed in my pc...


i think installation process should be similar to the one in 10.10 after  all its a tar.gz file that you need to extract in the specified folder...

hope this helps... :)

---

### Post by tspradeepkumar on 2011-12-12
hey 
look at these websites for ns2 installation
[http://www.pradeepkumar.org](http://www.pradeepkumar.org)
[http://www.nsnam.com](http://www.nsnam.com)

---

### Post by sanaa on 2012-02-11
I have the same problem (as helyos) on Ubuntu 11.10, if you fixed this problem, pleace, tell me how.

---

### Post by sanaa on 2012-02-11
re, 
I could fix this problem by executing these instruction:
> 
Fix the error in the linking of otcl by editing line 6304 of otcl-1.13/configure so that it reads
SHLIB_LD="gcc -shared"
instead of
SHLIB_LD="ld -shared"

I suggest to follow these instructions to install NS2.34 on Ubuntu 11.04 [http://erl1.wordpress.com/2011/05/12/installing-ns-2-34-on-ubuntu-11-04/]("http://erl1.wordpress.com/2011/05/12/installing-ns-2-34-on-ubuntu-11-04/")or on Ubuntu 11.10 [http://erl1.wordpress.com/2011/10/14/installing-ns-2-34-on-ubuntu-11-10-oneiric-ocelot/#comment-232]("http://erl1.wordpress.com/2011/10/14/installing-ns-2-34-on-ubuntu-11-10-oneiric-ocelot/#comment-232")

Good luck

---

