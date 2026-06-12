---
title: "Cannot execute program on Ubuntu 16. and 14"
date: 2017-12-27
forum: Installation &amp; Upgrades
---

### Post by asalex2 on 2017-12-27
hi,
I have program compiled for Linux and runs in Debian. So, I tried to execute in Ubuntu. Permission is 775:

root@mx:/home# ./infoisisnet.cgi
-bash: ./infoisisnet.cgi: No such file or directory

root@mx:/home# bash infoisisnet.cgi
infoisisnet.cgi: infoisisnet.cgi: cannot execute binary file

root@mx:/home# sudo infoisisnet.cgi
sudo: unable to resolve host mx.localhost
sudo: infoisisnet.cgi: command not found

root@mx:/home# export PATH=$PATH:/home
root@mx:/home# echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/home

root@mx:/home# bash infoisisnet.cgi
infoisisnet.cgi: infoisisnet.cgi: cannot execute binary file

root@mx:/home# sh infoisisnet.cgi
infoisisnet.cgi: 1: infoisisnet.cgi: Syntax error: "(" unexpected

root@mx:/home# file infoisisnet.cgi
infoisisnet.cgi: ELF 32-bit LSB  executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), not stripped
root@mx:/home#

Any help ? This program analys database and report in apache. So. Its echo version in command.  :-/

---

### Post by The Cog on 2017-12-27
My guess is that the program is trying to open a non-existent resource - a database file perhaps?
you could try 
```
strace infoisisnet.cgi
```There will be a lot of output, tracing all its interaction with the OS. But you might see what file it is failing to open near the end.

---

### Post by asalex2 on 2017-12-28
Thanks for you reply.
No. This program try open text file and put report on console (if inexist). I work for other guess: x64 X x86.   :-(

---

### Post by steeldriver on 2017-12-28
Is it trying to link a non-existent runtime library? what is the output of

```

ldd infoisisnet.cgi

```

---

### Post by ubfan1 on 2017-12-28
Please provide the output of:
ls /home
and
mount
/home is not the usual place for anything other than user home directories, but the file seems to be found sometimes.  The mount will show if there is anything odd  like a noexe mounted partition.

---

### Post by asalex2 on 2017-12-28
SOLVE. My problem is the app in x86 architecture. So install:

[COLOR=#0000cd]**sudo apt-get update **[/COLOR][COLOR=#0000cd][B]
sudo apt-get install libc6:i386 libncurses5:i386 libstdc++6:i386[/B][/COLOR]


and its run. Now... try to configure apache + cgi. thanks all!

---

