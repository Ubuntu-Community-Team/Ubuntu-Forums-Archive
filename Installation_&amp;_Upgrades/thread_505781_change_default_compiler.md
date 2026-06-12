---
title: "change default compiler?"
date: 2007-07-20
forum: Installation &amp; Upgrades
---

### Post by adnk on 2007-07-20
Hello everybody,

I have used Ubuntu on my computer and I want to change default gcc compiler, that's to say, how can i switch between compilers?  Could you please  describe me in detail how can i do that ?

yours sincerely,

adnk

---

### Post by kevinlyfellow on 2007-07-20
Do you mean you wish to use a different version of gcc?  If so, /usr/bin/gcc is just a symlink.  For example, you would need to
```
sudo rm /usr/bin/gcc
sudo ln -s /usr/bin/gcc-3.5 /usr/bin/gcc
```
to change the default gcc to gcc version 3.5

---

### Post by shiptar76 on 2007-07-23
hello,

as far as i know ubuntu supports gcc-3.3 and gcc-3.4, at least mine feisty 7.04. 

i am not sure but what i recommend you is to install them by issuing;

sudo apt-get install gcc-3.3
sudo apt-get install g++-3.4

and then later tell your makefile new compiler;

CXX   += gcc-3.3
CPP   += g++-3.3

is it possible?

cheers,
e.

---

