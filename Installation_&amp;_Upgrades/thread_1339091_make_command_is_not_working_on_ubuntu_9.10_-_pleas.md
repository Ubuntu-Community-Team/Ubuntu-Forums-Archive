---
title: "make command is not working on ubuntu 9.10 - please help"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by peprex on 2009-11-27
Hi!
I was trying to make the ndiswrapper sources, with my new ubuntu 9.10. I have no internet because it can't recognize my usb wifi. So I decided to try "ndiswrapping" the windows xp driver. 

I downloaded the code for ndiswrapper, but before I made:

-apt-cdrom add (with the ubuntu 9.10 installation cd spinning)

-aptitude update (I get errors when trying to access the repositories, it seems quite normal, I can't get to internet yet)

-aptitude install build-essential linux-headers-`uname -r`

Everything seemed to work! So I untar the ndiswrapper packet, enter the new directory, and start typing:

-make clean (works)

-make 

make -C driver
make[1]: Entering directory `/home/pep/Desktop/ndiswrapper/ndiswrapper-1.55/driver'
make -C /usr/src/linux-headers-2.6.31-14-generic M=/home/pep/Desktop/ndiswrapper/ndiswrapper-1.55/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/pep/Desktop/ndiswrapper/ndiswrapper-1.55/driver/crt.o
In file included from /home/pep/Desktop/ndiswrapper/ndiswrapper-1.55/driver/crt.c:16:
/home/pep/Desktop/ndiswrapper/ndiswrapper-1.55/driver/ntoskernel.h: In function ‘PushEntrySList’:
/home/pep/Desktop/ndiswrapper/ndiswrapper-1.55/driver/ntoskernel.h:905: error: implicit declaration of function ‘cmpxchg8b’
make[3]: *** [/home/pep/Desktop/ndiswrapper/ndiswrapper-1.55/driver/crt.o] Error 1
make[2]: *** [_module_/home/pep/Desktop/ndiswrapper/ndiswrapper-1.55/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/pep/Desktop/ndiswrapper/ndiswrapper-1.55/driver'
make: *** [all] Error 2


Something is telling me that make install won't work ...

-make install

make -C driver install
make[1]: Entering directory `/home/pep/Desktop/ndiswrapper/ndiswrapper-1.55/driver'
make -C /usr/src/linux-headers-2.6.31-14-generic M=/home/pep/Desktop/ndiswrapper/ndiswrapper-1.55/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/pep/Desktop/ndiswrapper/ndiswrapper-1.55/driver/crt.o
In file included from /home/pep/Desktop/ndiswrapper/ndiswrapper-1.55/driver/crt.c:16:
/home/pep/Desktop/ndiswrapper/ndiswrapper-1.55/driver/ntoskernel.h: In function ‘PushEntrySList’:
/home/pep/Desktop/ndiswrapper/ndiswrapper-1.55/driver/ntoskernel.h:905: error: implicit declaration of function ‘cmpxchg8b’
make[3]: *** [/home/pep/Desktop/ndiswrapper/ndiswrapper-1.55/driver/crt.o] Error 1
make[2]: *** [_module_/home/pep/Desktop/ndiswrapper/ndiswrapper-1.55/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/pep/Desktop/ndiswrapper/ndiswrapper-1.55/driver'
make: *** [install] Error 2

What's exactly happening? Sorry, I'm newbie, and I can't keep going ...
Thanks in advance !
P

---

### Post by lloyd_b on 2009-11-27
Don't fixate on "make" - it's just a tool to simplify compiling projects.

The problem you're having is with the code that you're trying to compile.  Specifically:```
/home/pep/Desktop/ndiswrapper/ndiswrapper-1.55/driver/ntoskernel.h: In function ‘PushEntrySList’:
/home/pep/Desktop/ndiswrapper/ndiswrapper-1.55/driver/ntoskernel.h:905: error: implicit declaration of function ‘cmpxchg8b’
```It's failing the compile because there's no explicit declaration for the function 'cmpxchg8b'.

I have no clue what this means - it's a type of error that probably only someone who has actually worked on developing ndiswrapper will understand.

Now for the real question - why are you compiling ndiswrapper?  The kernel module should have been installed by default.  You *might* need to get the packages "ndiswrapper-utils-1.9" and "ndiswrapper-common" to support it, though.  Both of these packages should be on the install disk, so "sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common" should be all you need to do to get them installed.

Note: If you need help on *using* ndiswrapper, please open another thread on that topic (after searching the forums, of course).

Lloyd B.

---

### Post by peprex on 2009-11-28
Hi !

Great! I got the ndiswrapper from the installation cd and there was no problem, as you adviced. The only thing that I can't understand is that I make exactly the same code in ubuntu 9.04 and I could make install ndiswrapper and even use it ! It seems strange to me ...

Anyway, ndiswrapper is ready to go, thanks for your advice !

P

---

