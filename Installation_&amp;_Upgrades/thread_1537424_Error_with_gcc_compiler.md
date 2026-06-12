---
title: "Error with gcc compiler"
date: 2010-07-23
forum: Installation &amp; Upgrades
---

### Post by the tree stump on 2010-07-23
hey folks,

I had some serious problems with my ubuntu 10.4 partitions yesterday and fixed them using gparted - check partition.

But since then I cannot use gcc anymore (?):

[INDENT]name@machine:~/$ gcc
gcc: no input files
name@machine:~/$ gcc test.c
gcc: error trying to exec 'cc1': execvp: No such file or directory
[/INDENT]

I searched the forum and people suggested to reinstall multiple packages: cpp, gcc, build-essential, cpp-4.4

I reinstalled them but the error stays...

Thx for your reply, the tree stump

---

### Post by LinuxMorten on 2011-09-20
Hi

This seems to happen for people once in a while... For me purging and reinstalling didn't help... However I used:

```
gcc -print-search-dirs
```

-which showed me that gcc only searched for cc1 in:
```
/usr/lib/i386-linux-gnu/gcc/i686-linux-gnu/4.5.2/
```

and not in:
```
/usr/lib/i386-linux-gnu/gcc/i686-linux-gnu/4.5/
```

This could easily be solved by a nice symlink:
```
cd /usr/lib/i386-linux-gnu/gcc/i686-linux-gnu/
sudo ln -s 4.5/ 4.5.2

```

-and everything worked again!

---

