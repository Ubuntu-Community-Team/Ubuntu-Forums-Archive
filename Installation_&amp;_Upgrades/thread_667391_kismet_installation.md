---
title: "kismet installation"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by ttmw on 2008-01-14
im trying to install kismet on ubuntu 7.10 but because im really new to linux im finding it a bit hard. ive extracted the package then run ./configure in the terminal in the correct directory and im getting...

...
checking for C compiler default output file name...
configure: error: C compiler cannot create executables
See 'config.log' for more details.

Ive looked in config.log and it means absolutely nothing to me, d i need to post it on here aswell or can anyone hel pme in my problem without? thanks

---

### Post by tgalati4 on 2008-01-15
>sudo apt-get install build-essentials gcc

Try again.

Sorry, it was late last night:  sudo apt-get install build-essential gcc

---

### Post by ttmw on 2008-01-15
thanks for the reply. Now im getting this when i try the code you suggested... 

Reading package lists... Done
building dependency tree
Reading state information... Done
E: Couldn't find package build-essentials


got any further suggestions?

---

### Post by Partyboi2 on 2008-01-15
```
sudo apt-get install build-essential gcc
``` build-essentials without the s

---

### Post by ttmw on 2008-01-15
Ok, that work i inserted the ubuntu 7.10 cd to install the stuff and tried the kismet installation again, it went through a load of installing then stopped with the error...

configure: WARNING Unable to find libncurses
checking for initscr in -lcurses... no
configure: error: Unable to find libncurses or libcurses

jeez this shiz in confusing to start lol, any further suggestions?

---

### Post by Partyboi2 on 2008-01-15
Download libncurses5 from here
[http://packages.ubuntu.com/gutsy/base/libncurses5](http://packages.ubuntu.com/gutsy/base/libncurses5)
then install it by double clicking on it

---

### Post by ttmw on 2008-01-15
ok i've done that and it tells me that that version already exists,i re installed it just incase but still no luck.

---

### Post by Partyboi2 on 2008-01-15
try the dev package 
```
sudo apt-get install libncurses5-dev
```

---

### Post by ttmw on 2008-01-15
give yet another error of...

Reading package lists... Done
building dependency tree
Reading state information... Done
E: Couldn't find package libncurses5-dev

This is getting annoying now lol, thanks for your patience and answers so far btw

---

### Post by Partyboi2 on 2008-01-15
Make sure in Software Sources (System>admin>Software Sources) you have all of them ticked except source code under the first tab
you can also install the package manually from 
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libncurses5-dev&searchon=names&subword=1&version=gutsy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libncurses5-dev&searchon=names&subword=1&version=gutsy&release=all)

---

### Post by ttmw on 2008-01-15
ive ticked all apart from source code in the first tab and im still gettin the same error as last time

---

### Post by ttmw on 2008-01-15
ok, just downloaded it manually from that source n it now works, il probably have another problem in a minute tho lol. thanks alot!

---

### Post by Partyboi2 on 2008-01-15
Your welcome, I just realized you probably didn't have internet access and I don't believe that package is on the cd. Glad you got it sorted :)

---

### Post by ttmw on 2008-01-15
i was right and there is yet more errors ARGHGHGH!

it goes through the install and i followed the 'make' and 'make install' but at the end it give error...

install: canot remove '/usr/local/bin/kismet' : permision denied
make[1]: *** [commoninstall] error 1
make[1]: Leaving directory '/home/me/documents/kismet-2007-10-R1'
make: *** [install] error 2

---

### Post by Partyboi2 on 2008-01-15
try using sudo, seems like you don't have permission for it to remove a file
```
sudo make
```

---

### Post by ttmw on 2008-01-15
it returns..

make: Nothing to be done for 'all'

---

### Post by tgalati4 on 2008-01-15
Make doesn't require sudo priviledges, but make install does since it will copy the new executable to /usr/bin or somewhere important:

>sudo make install

Building from source can be a pain.  You have just gone through *dependency hell*.  Welcome to the club.

---

