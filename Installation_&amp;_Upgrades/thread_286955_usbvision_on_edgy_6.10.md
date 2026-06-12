---
title: "usbvision on edgy 6.10"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by dliloch on 2006-10-28
hello.. this is my first time here .. I just upgraded to edgy from dapper on a dell 7500 laptop .. no major problems except that it took longer that if I had just downloaded the entire distro and installed from the CD.. 

I noticed though that my XAWTV did not work so I tried to reinstall usbvision .. usbvision worked fine on dapper but it can't find modules on the install .. any ideas?? thanks.

---

### Post by dliloch on 2006-10-28
i had better add some details .. the usbvision is at 0.9.8.3
and when i run make I get this..

don@linux-laptop:~/Desktop/usbvision/src$ ls
bt819-new.c                          Makefile       usbvision.c
Do_not_copy_Makefile_to_kernel_tree  saa7111-new.c  usbvision.h
i2c-algo-usb.c                       saa7113.c      usbvision_ioctl.h
i2c-algo-usb.h                       saa7113-new.c
don@linux-laptop:~/Desktop/usbvision/src$ make
make -C /lib/modules/2.6.17-10-386/build SUBDIRS=/home/don/Desktop/usbvision/src modules
make[1]: Entering directory `/lib/modules/2.6.17-10-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.17-10-386/build'
make: *** [default] Error 2
don@linux-laptop:~/Desktop/usbvision/src$

---

### Post by philipgm on 2006-10-29
I think you need to install the header packages for 2.6.17. 

The next problem that I have is that when I try to do make this is what I get.

[COLOR="RoyalBlue"]make -C /lib/modules/2.6.17-10-386/build SUBDIRS=/home/philip/usbvision/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-386'
  CC [M]  /home/philip/usbvision/src/i2c-algo-usb.o
/home/philip/usbvision/src/i2c-algo-usb.c:45: error: expected ‘)’ before string constant
make[2]: *** [/home/philip/usbvision/src/i2c-algo-usb.o] Error 1
make[1]: *** [_module_/home/philip/usbvision/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-386'
make: *** [default] Error 2
[/COLOR]

I've noticed that a number of other people are getting the same sort of behaviour when building applications from source for Edgy which suggests a compiler issue of some sort.

Hopefully someone clever has already fixed this and can tell me how to proceed...

---

### Post by philipgm on 2006-10-29
downloading from cvs rather than using the downloaded archive seems to fix that problem.

---

### Post by dliloch on 2006-11-13
that is exactly what I got when I fixed up the header issue.. what do you mean downloading from cvs?? can you post the instructions for doing this .. thanks! :-)

---

### Post by dliloch on 2006-11-14
> **dliloch said:**
> that is exactly what I got when I fixed up the header issue.. what do you mean downloading from cvs?? can you post the instructions for doing this .. thanks! :-)
answer to my own question..
cvs -d:pserver:anonymous@usbvision.cvs.sourceforge.net:/cvsroot/usbvision login 
 cvs -z3 -d:pserver:anonymous@usbvision.cvs.sourceforge.net:/cvsroot/usbvision co -P usbvision

this does work!! so is the source messed up?? 
anyway thanks!!

---

### Post by jrafonso on 2007-01-27
> **dliloch said:**
> answer to my own question..
cvs -d:pserver:anonymous@usbvision.cvs.sourceforge.net:/cvsroot/usbvision login 
 cvs -z3 -d:pserver:anonymous@usbvision.cvs.sourceforge.net:/cvsroot/usbvision co -P usbvision

this does work!! so is the source messed up?? 
anyway thanks!!


Hello friend,

I'm new in this world, however i have my wi-fi card now running, the problem is my usb tvcard...

I downloaded usbvision but i also cannnot compile it to our edgy,,, i don't understand very weel how i can edit with csv,

can you help me with this?

i just need to know what i should do to compile, because with the standard package we found an error because kernel, i think.,.

if you can send me the directory ready to compile, or explain how can i do that, i appreciate,

Thank from your time

Joao Afonso from Portugal

[email]jrafonso@gmail.com[/email]

---

### Post by darthchaosofrspw on 2007-02-02
> **dliloch said:**
> answer to my own question..
cvs -d:pserver:anonymous@usbvision.cvs.sourceforge.net:/cvsroot/usbvision login 
 cvs -z3 -d:pserver:anonymous@usbvision.cvs.sourceforge.net:/cvsroot/usbvision co -P usbvision

this does work!! so is the source messed up?? 
anyway thanks!!

Dude...you rule. I successfully ran make after downloading the CVS version as well.

I did the following :

1. sudo apt-get install cvs make gcc-3.4 linux-headers-2.6.17-10 zapping
2. cvs -d:pserver:anonymous@usbvision.cvs.sourceforge.net:/cvsroot/usbvision login
    (When asked for a password, just hit Enter.)
3. cvs -z3 -d:pserver:anonymous@usbvision.cvs.sourceforge.net:/cvsroot/usbvision co -P usbvision
4. cd usbvision/src
5. sudo make
6. sudo make install
7. sudo modprobe usbvision
8. echo -e "modprobe usbvision\n" >usbvision
9. sudo cp usbvision /etc/init.d
10. cd /etc/init.d
11. sudo chmod 755 usbvision
12. sudo update-rc.d usbvision start 51 S .
       (Do NOT forget the . at the end of the line.)

NOTE: If you cannot copy and paste lines 2 and/or 3, visit [http://sourceforge.net/cvs/?group_id=27255](http://sourceforge.net/cvs/?group_id=27255) and scroll down to **Anonymous CVS Access** and copy and paste the lines from there. Just make sure for the second part to substitute the word **modulename** with **usbvision**.

---

