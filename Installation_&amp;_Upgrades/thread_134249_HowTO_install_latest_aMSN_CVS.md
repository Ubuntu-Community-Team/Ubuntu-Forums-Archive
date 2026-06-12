---
title: "HowTO install latest aMSN CVS?"
date: 2006-02-21
forum: Installation &amp; Upgrades
---

### Post by ashrack on 2006-02-21
This is how I tried installing latest CVS
```

sudo -s
apt-get install build-essential tcl8.4-dev tk8.4-dev imlib11-dev esound-clients
cd /usr/share
mv amsn amsn.tomi #move the original to a different directory
wget http://amsn.sourceforge.net/amsn_cvs.tar.gz
tar xvfz amsn_cvs.tar.gz
mv msn amsn
cd amsn
./configure 
```
and here's the output of './configure'
```
checking for prefix by checking for wish... /usr/bin/wish
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking tcl build dir... configure: error: Unable to find Tcl directory or Tcl package is not tcl-dev

```
So then I tried:
```
root@pegasus:/usr/share/amsn.cvs# whereis tcl
tcl: /usr/lib/tcl8.4 /usr/lib/tcl8.5 /usr/include/tcl8.4
################################################
root@pegasus:/usr/share/amsn.cvs# whereis tk
tk: /usr/lib/tk8.4 /usr/lib/tk8.5 /usr/share/tk8.4 /usr/share/tk8.5 
```
and then did:
```
./configure --with-tcl=/usr/local/lib/ --with-tk=/usr/local/lib/
```
and this is what I got:
```
checking for prefix by checking for wish... /usr/bin/wish
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking tcl build dir... using tcl library in /usr/local/lib/
./configure: line 2822: /usr/local/lib//tclConfig.sh: No such file or directory 
```

```
root@pegasus:/usr/share/amsn.cvs# whereis tclConfig.sh
tclConfig:

```
tclConfig appears no where to be found.
Any ideas guys?

---

### Post by ashrack on 2006-02-21
I made a typo. Now ti works. This is what I had to do.
```
root@pegasus:/usr/share/amsn.cvs# ./configure --with-tcl=/usr/lib/tcl8.4 --with-tk=/usr/lib/tk8.4

```

curious:
why did I have to supply TK and TCL librarys path manually to '.-configure'

---

### Post by oopsz on 2006-02-22
Have you installed tcl-dev and tk-dev?

Run sudo apt-get build-dep amsn, that should grab everything you need.

---

### Post by ashrack on 2006-02-22
[QUOTE=oopsz]Have you installed tcl-dev and tk-dev?

Run sudo apt-get build-dep amsn, that should grab everything you need.[/QUOTE]
in my previous post I've already stated that I have installed TCL-dev and TK_DEV. Perhaps U should read more closels. And I also stated that I successfully lunched
'./configure'
but I had to type it like this:
```
./configure --with-tcl=/usr/lib/tcl8.4 --with-tk=/usr/lib/tk8.4
```

But my questoin now is why didn't the program automaticly detect where TCL and TK were stored?

---

