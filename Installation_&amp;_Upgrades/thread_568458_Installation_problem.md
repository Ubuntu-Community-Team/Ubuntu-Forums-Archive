---
title: "Installation problem"
date: 2007-10-05
forum: Installation &amp; Upgrades
---

### Post by anko-dw on 2007-10-05
I am a new user of ubuntu. I love it but I need to learn how to install something inside it. I need to install beryl and also GIMP 2.4 inside it but I cant do that. Every installation of a program always failed and there is a massage like this:

anko-dw@anko-dw:~/Desktop/beryl-manager-0.2.0$ ./configure 
checking for a BSD-compatible install... /usr/bin/install -c 
checking whether build environment is sane... yes 
checking for gawk... no 
checking for mawk... mawk 
checking whether make sets $(MAKE)... yes 
checking whether to enable maintainer-specific portions of Makefiles... no 
checking for style of include used by make... GNU 
checking for gcc... gcc 
checking for C compiler default output file name... 
**configure: error: C compiler cannot create executables **
See `config.log' for more details. 
anko-dw@anko-dw:~/Desktop/beryl-manager-0.2.0$ 


what should I do????

---

### Post by raja on 2007-10-05
You do not need to compile from source for Beryl and Gimp. These programs are available as packages binaries.
For Gimp. all you have to do is type ```
sudo aptitude install gimp
``` in a terminal.
For Beryl, you may have to enable some extra repos and then install it - look at the Beryl site for details.
However, Beryl is not going to be developed now and merged with Compiz. So you may be better off upgrading to Gutsy which has compiz-fusion by default.

---

### Post by Ub1476 on 2007-10-05
Hehe, you make things hard for yourselves:rolleyes:

First, just make sure you can use 3d (right drivers installed etc). An easy way to do this is to try to enable the default effects (look for it in preferences).

If you want to install Beryl, just go to Applications>Add/Remove> and search for Beryl. Although I recommend you to install Compiz-Fusion, since it's more stable and have more effects. Compiz-Fusion will be preinstalled in the next Ubuntu v. (12 days left, I think), but for now you can install it by following this [Guide]("http://ubuntuforums.org/showthread.php?t=536149").

---

