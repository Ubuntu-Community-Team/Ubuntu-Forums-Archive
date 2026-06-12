---
title: "help needed regarding libx11 package!"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by alberto.m.vasquez on 2007-04-25
Hi,

I'm running Ubuntu 6.10 (edgy) on my computer at work.
Due to an uncompatibility of the latest libx11 update
(2:1.0.3-0ubuntu4.1) with a data analysis software that I use 
(see link below if  you are a IDL user), I desperately need to 
DOWNgrade back to: 

libx11-6 (2:1.0.3-0ubuntu4)

Can anybody pass me the aptitude, or apt-get line that will 
do so? I really do not know the package name or how to
do it. Thanks A LOT!

-Alberto.
p.s. see following link for a technical description of the IDL problem 
[http://www.ittvis.com/services/techtip.asp?ttid=4177&pv=yes](http://www.ittvis.com/services/techtip.asp?ttid=4177&pv=yes)

---

### Post by alberto.m.vasquez on 2007-04-25
problem solved.
I went to [http://www.ittvis.com/services/techtip.asp?ttid=4177](http://www.ittvis.com/services/techtip.asp?ttid=4177),
dowloaded the package: libx11-6_1.0.3-6_i386.deb
and then from the dir where that package is I did as
root the usual debian command:
dpkg -i libx11-6_1.0.3-6_i386.deb

and now IDL can do all the graphs!

cheers!
Alberto.

---

