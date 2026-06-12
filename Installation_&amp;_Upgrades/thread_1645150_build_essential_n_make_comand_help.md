---
title: "build essential n make comand help"
date: 2010-12-14
forum: Installation &amp; Upgrades
---

### Post by siva_chowdhary on 2010-12-14
**I have build-essential, but make command not working** 			
 			 			 		   		 		 		I have *build-essential* package, but there is still a problem with **make** command. When I run it in a directory, it shows following message:

mudassar@javaDev-1:~/Desktop/gwget-0.99$ make
make: *** No targets specified and no makefile found.  Stop.

When I explicitly specify a make file, the following message appears:

mudassar@javaDev-1:~/Desktop/gwget-0.99$ make Makefile.in
make: Nothing to be done for `Makefile.in'.

Same message appears for all other files.

And, if I run **install** with **make**, it shows:

mudassar@javaDev-1:~/Desktop/gwget-0.99$ sudo make install
Password:
make: *** No rule to make target `install'.  Stop.

Guide me how to use **make** in this scenario.

---

### Post by oldos2er on 2010-12-14
Is there some reason you need 0.99? Gwget 1.0.4-1 is in the repositories.

---

