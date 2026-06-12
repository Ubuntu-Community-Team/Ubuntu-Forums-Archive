---
title: "torcs compile problem"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by estorque on 2010-10-25
Hi all,

I'm a newbie so please tell me if this is not the place for this kind of question.

I need to install torcs from the source, from binary it works but it is not the issue.

While i'm trying to compile torcs source with "make" command i got this error:

make[4]: Entering directory `/home/username/Desktop/torcs/torcs-1.3.1/src/libs/client'
g++ -shared -o libclient.so entry.o mainmenu.o splash.o exitmenu.o optionmenu.o -L/home/username/Desktop/torcs/torcs-1.3.1/export/lib -lalut -L/usr/lib -lplibssg -lplibsg -lplibul 
/usr/bin/ld: /usr/lib/libplibssg.a(ssg.o): relocation R_X86_64_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
/usr/lib/libplibssg.a: could not read symbols: Bad value
collect2: ld returned 1 exit status

It seems like a plib related error. I don't know how to solve it though. Plib installed successfully. Also in ./configure output plib usability is yes which makes it even weirder.

My system:
Ubuntu 10.04 - 64 bit
All dependencies like gl and plib seem to be working.

Thanks in advance for any help

---

