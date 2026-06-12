---
title: "Ponyprog installation in ubuntu"
date: 2012-12-09
forum: Installation &amp; Upgrades
---

### Post by Raj 89 on 2012-12-09
Hi All.... ):P

I have been using ponyprog2000 in mandriva for a while. Now i have switched to ubuntu and i am trying to install ponyprog in ubuntu. The OS version i am using is ubuntu 12.10.  The tarball version of ponyprog that i have downloaded from website is "ponyprog-v1_17h-03Nov2000.tar.gz". I downloaded it directly from the ponyprog official site. I am in the process of installing it and i guess i went wrong somewhere. 

I edited Config.mk file and did make. It shows me an error so... 

> 
[eswar @ ponyprog] make
g++ -I/home/eswar/Downloads/ponyprog/v/includex -I/usr/X11R6/include  -O2 -DAthena -D_LINUX_ -D_PONYPROG_ -D_UDP_SERVER -Wall -c e2app.cpp -o e2app.o
In file included from e2app.cpp:33:0:
e2app.h:41:20: fatal error: v/vapp.h: No such file or directory
compilation terminated.
make: *** [e2app.o] Error 1


What can i do to clear the error. I am in need of ponyprog. Is there any .deb packages available for ponyprog?

---

