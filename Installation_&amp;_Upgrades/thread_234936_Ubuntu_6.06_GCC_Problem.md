---
title: "Ubuntu 6.06 GCC Problem"
date: 2006-08-12
forum: Installation &amp; Upgrades
---

### Post by wuhaa on 2006-08-12
Hi,

I'm trying to install the color wrapper (cw) on Ubuntu 6.06. I have gcc installed, but keep getting this error when i run 'make install':

* Compiling cw(color wrapper)...
src/cw.c: In function ‘execot’:
src/cw.c:1445: warning: missing sentinel in function call
src/cw.c: In function ‘execcw’:
src/cw.c:1541: warning: missing sentinel in function call
* Compiling cwu(color wrapper directive updater)...
* Installing color wrapper...
/bin/sh: -c: line 1: syntax error near unexpected token `do/usr/bin/install'
/bin/sh: -c: line 1: `/usr/bin/install -c -o 0 -g 0 -m 755 $FILE /usr/local/bin;\'
make: *** [install] Error 2


Is there a specific lib missing? If so, which one?

Thanks..

---

### Post by taurus on 2006-08-12
First of, you probably need to install "build-essential" because it comes with everything that you need to build package from source.  Then, you need to run "sudo make install" if you want to install it on your system since you need root permission to write to it!!!

---

### Post by wuhaa on 2006-08-12
Hi,

I have the build-essential pkg installed  but i still get the error. I tried installing with sudo as well. :mad: 



wuhaa: ~/cw-1.0.14 # sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
wuhaa: ~/cw-1.0.14 # sudo make install
* Cleaning cw and cwu binaries, and definitions...
* Compiling cw(color wrapper)...
src/cw.c: In function âexecotâ:
src/cw.c:1445: warning: missing sentinel in function call
src/cw.c: In function âexeccwâ:
src/cw.c:1541: warning: missing sentinel in function call
* Compiling cwu(color wrapper directive updater)...
* Installing color wrapper...
/bin/sh: -c: line 1: syntax error near unexpected token `do/usr/bin/install'
/bin/sh: -c: line 1: `/usr/bin/install -c -o 0 -g 0 -m 755 $FILE /usr/bin;\'
make: *** [install] Error 2

---

### Post by taurus on 2006-08-12
What program are you trying to build/install on your Dapper?  Does it just say "make install" as root in README/INSTALL or does it say something else like

```

./configure
make
make install

```

---

### Post by wuhaa on 2006-08-13
The program is a color wrapper for the linux console. It basically colours the command output so its easier to rear and also looks nice :D 

Its downloadable from [http://sourceforge.net/projects/cwrapper/](http://sourceforge.net/projects/cwrapper/)

It looks neat if it works

The wierd thing is that i have it running fine on Kubuntu 5.


In the INSTALL file it says:

for installing globally(as root):
# ./configure && make install

So i tried running 'sudo ./configure && make install'

Once that failed, i tried 'sudo ./configure' which works fine.

Then i tryed 'sudo make install' and its giving me the same error as with  'sudo ./configure && make install'

---

### Post by wuhaa on 2006-08-14
Is there a way to check which c libs are installed on any given system?

Maube I can check my Kubuntu box to see which lib i'm missing. Hopefully that can solve the problem!:D

---

