---
title: "[SOLVED] Compiling from source - C compiler cannot create executables"
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by amba on 2008-06-20
hi,
i'm new with Kubuntu, i'm trying to compile a driver for my wacom touchscreen.
When i type
./configure --enable-wacom
 i get this error:
*checking for C compiler default output file name... configure: error: C compiler cannot create executables*

Linux kernel headers are installed, i've also installed manually autoconf package. No clue why gcc should'nt create execs :(
Thanks!

(ps: sorry for crossposting, i didn't get answer in the wacom thread)

---

### Post by diaa on 2008-06-20
GCC(the compiler) doesn't come with ubuntu so you have to install it manually, I think that's what you need.
To install the compiler and required tools:
```
sudo apt-get install essential make
```

---

### Post by Rocket2DMn on 2008-06-20
What you want is the metapacke build-essential.  This includes compilers for all sorts of languages so you can build any software from source, as well as your own programs
```
sudo apt-get install build-essential
```

---

### Post by amba on 2008-06-20
thank you guys!
My old slackware had almost every tool in a full install, i'm a bit ashamed here :oops:
Well i tested "gcc" command before posting here, it correctly said "no input file :-k
Then installed build-essential, and all works fine.

Can i ask one more little thing? What's difference between aptitude and apt-get? They both retrieve packages. Different config files? I only gave a look on /etc/apt. Improved functions?
I don't get it :confused:

---

### Post by Rocket2DMn on 2008-06-20
They use the same source.list file and are both built on dpkg - apt-get, synaptic, aptitude all perform the same function.  Aptitude has a little bit more functionality than apt-get in that it has a terminal based GUI and can remember dependencies after install (so you can remove metapackages).  Otherwise, they are the same - most people use apt-get from the terminal.

---

