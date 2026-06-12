---
title: "Problem with qt library (?): QMainWindow: No such file or directory"
date: 2013-03-13
forum: Installation &amp; Upgrades
---

### Post by mparsani on 2013-03-13
Good morning everybody,
I am installing a third party software, i.e. silo 4.9, on Ubuntu Quantal.

During the compilation phase with make I always get the following error:

Explorer.h:58:23: fatal error: QMainWindow: No such file or directory
compilation terminated.

I have seen few discussion online where it seems that the problem can be fixed by installing libqt4-dev. I did install it with and I also installed all the other qt4 libraries but the problem is still there. 

Do you have an idea which could be the probelm?

Could you please help me to find where qt is installed by the package manager? I see that something is installed in /usr/share/qt4. Such a directory contain:

bin/          include/      phrasebooks/  
doc/          mkspecs/      translations/

but not lib. Where the right qt4 directory lib is located?

Thank you.

Bye bye

---

### Post by mparsani on 2013-03-13
I have searched for the  qmainwindow.h and I cannot find it.

Probably this is my issue.

Is there a way to install the full qt4-x11 library in Ubuntu Quantal?

Thank you

---

