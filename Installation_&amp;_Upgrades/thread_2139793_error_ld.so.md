---
title: "error ld.so"
date: 2013-04-27
forum: Installation &amp; Upgrades
---

### Post by Pedroski55 on 2013-04-27
Hi again!

I am getting the following error message. Also I have a 'prohibited' sign top right in my desktop. Anyone know the problem??

pedro@pedro-bedro:~$ sudo apt-get check
ERROR: ld.so: object '/lib/$LIB/liblsp.so' from /etc/ld.so.preload cannot be preloaded: ignored.
ERROR: ld.so: object '/lib/$LIB/liblsp.so' from /etc/ld.so.preload cannot be preloaded: ignored.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ERROR: ld.so: object '/lib/$LIB/liblsp.so' from /etc/ld.so.preload cannot be preloaded: ignored.
ERROR: ld.so: object '/lib/$LIB/liblsp.so' from /etc/ld.so.preload cannot be preloaded: ignored.
pedro@pedro-bedro:~$

This has become a major problem: I can't start Ubuntu, I get a line saying can't preload ld.so, then a kernel panic!! Help!!

---

### Post by MAFoElffen on 2013-04-28
That error seems to be localized to the packages for Astrill VPN. If you tried to install it, please remove it for now:
```

sudo apt-get --purge astrill

```
There seems to be an upstream problem with the packages from Astrill... with users reporting this same problem from both their deb and RPM packages. I first heard about this in the Debian forums 3 weeks ago.

---

### Post by Pedroski55 on 2013-04-28
I would like to do that, but look at this:

pedro@pedro-bedro:~$ sudo apt-get --purge astrill
ERROR: ld.so: object '/lib/$LIB/liblsp.so' from /etc/ld.so.preload cannot be preloaded: ignored.
[sudo] password for pedro: 
ERROR: ld.so: object '/lib/$LIB/liblsp.so' from /etc/ld.so.preload cannot be preloaded: ignored.
E: Invalid operation astrill
ERROR: ld.so: object '/lib/$LIB/liblsp.so' from /etc/ld.so.preload cannot be preloaded: ignored.
ERROR: ld.so: object '/lib/$LIB/liblsp.so' from /etc/ld.so.preload cannot be preloaded: ignored.
pedro@pedro-bedro:~$ 

Can't even remove it. I'm going to reinstall Ubuntu from scratch. There are too many problems.

---

### Post by Pedroski55 on 2013-04-28
I'd like to know what is calling liblsp.so It is there in /etc/lib/x86-64-linux-gnu so why it can't preload, I don't know, maybe a permissions thing. That's why I 'd like to know what calls it

---

### Post by Pedroski55 on 2013-04-28
I modified /etc/ld.so.preload 
It had one line: /lib/$LIB/liblsp.so 
but liblsp.so is in /lib/x86_64-linux-gnu/

so I changed the line.

But Astrill vpn still does not work!

---

### Post by MAFoElffen on 2013-04-28
As I said, Astrill is having problems with their latest source package... So users are holding off on installing it for now. 

If /etc/ls.so.preload was a file containing the line "/lib/$LIB/liblsp.so"... which would mean it was written as a generic with a variable named "LIB" which would probably be set to mean either "x86_64-linux-gnu" or "i386-linux-gnu"... what happens if you change that line to "/lib/x86-linux-gnu/liblsp.so" to hardcode point it directly to that file? If a symlink, recreate it with the right pointer. 
```

ls -l /lib/x86-linux-gnu/liblsp.so

```
Would tell you whether it is a file or symlink...

Reason I say that is... I don't have that installed, but I do have an arch x86_64... and it doesn't have anything assigned in the ENV for the variable $LIB.

---

### Post by Pedroski55 on 2013-04-28
Having changed the line to point it at the right place, it then finds and preloads, I do not get an error message. I do not know what it does!!
Does this mean to say, every script in /etc is run on boot??? And, since I was getting the error when say, calling up a terminal, this script was obviously being called, and producing the error message. Why, when I open a terminal, is /etc/ld.so.preload run??

---

