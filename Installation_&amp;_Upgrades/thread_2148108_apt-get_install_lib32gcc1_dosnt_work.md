---
title: "apt-get install lib32gcc1 dosnt work"
date: 2013-05-23
forum: Installation &amp; Upgrades
---

### Post by sorrensen on 2013-05-23
Multiverse and Universe were enabled by default so I dont realise why it didnt work. It gives me this error:

root@localhost:~# apt-get install lib32gcc1
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package lib32gcc1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'lib32gcc1' has no installation candidate

---

### Post by mjitkop on 2013-05-24
> **sorrensen said:**
> Multiverse and Universe were enabled by default so I dont realise why it didnt work. It gives me this error:

root@localhost:~# apt-get install lib32gcc1
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package lib32gcc1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'lib32gcc1' has no installation candidate

Maybe [this]("http://packages.ubuntu.com/search?keywords=lib32gcc1") will help.

---

### Post by sorrensen on 2013-05-24
It's all gibberish to me, what do I do?

---

### Post by mjitkop on 2013-05-24
> **sorrensen said:**
> It's all gibberish to me, what do I do?

Which version of Ubuntu are you using?

May I ask in which context you need this library file?

It looks to me like this library file is to be used with 64-bit AMD processors. Can you confirm that this is the kind of processor you have in your computer?

---

### Post by oldos2er on 2013-05-24
Have you tried ```
sudo apt-get update && sudo apt-get install lib32gcc1
```

---

### Post by sorrensen on 2013-05-24
[SIZE=4][SIZE=3]Old no it dosn't work. My VDS is running [/SIZE][COLOR=#000000][FONT=Helvetica Neue][SIZE=3]Ubuntu 12.04 32bit,[/SIZE][SIZE=4] and I am accessing it through a command line on putty, and I need the library file to run hldsupdatetool.bin to get a Garry's Mod server on my VDS. I have asked my VDS provider what type of CPU my VDS has, Ill post what type as soon as they reply.[/SIZE][/FONT][/COLOR][/SIZE]

---

### Post by sorrensen on 2013-05-25
Prossesor is a Intel e5

---

### Post by mjitkop on 2013-05-25
Sorry but this is the extent of my knowledge. It's confusing to me because it seems that this library file is for an AMD 64 processor. Hopefully someone else can chime in and provide a solution.

---

### Post by ibjsb4 on 2013-05-25
> **mjitkop said:**
> Sorry but this is the extent of my knowledge. It's confusing to me because it seems that this library file is for an AMD 64 processor. Hopefully someone else can chime in and provide a solution.

Thats what I also see.  That package is 64 bit architecture and you can't install it on your 32 bit system.

[http://packages.ubuntu.com/precise/lib32gcc1](http://packages.ubuntu.com/precise/lib32gcc1)

---

### Post by sorrensen on 2013-05-25
Say if i were to get a 64-bit version of ubuntu would there be much difference?

---

### Post by ibjsb4 on 2013-05-26
Do you have a 64 bit processor?

```
lshw -C cpu
```

Whats the width, 64 or 32?

---

### Post by sorrensen on 2013-05-27
The width is 64
```
slot: CPU 1
size: 2GHz
capacity: 2GHz
width: 64 bits

```

---

### Post by ibjsb4 on 2013-05-27
Ok, if you want to run lib32gcc1 you have to install the 64bit system.  There is no way to upgrade to 64bit, its got to be a fresh install.  good luck :)

---

### Post by steeldriver on 2013-05-27
It seems bass-ackwards to install a 64-bit OS just so that you can then  install a 32-bit compatibility layer in order to run a 32-bit  application... I can't believe that's what the original instructions are recommending

---

### Post by ibjsb4 on 2013-05-27
> **steeldriver said:**
> It seems bass-ackwards to install a 64-bit OS just so that you can then  install a 32-bit compatibility layer in order to run a 32-bit  application... I can't believe that's what the original instructions are recommending

Yep

---

### Post by sorrensen on 2013-05-27
Ok, dosn't matter if I need to get a fresh install couldn't do anything on the VDS anyway without [COLOR=#000000]lib32gcc1.
Thanks for your help![/COLOR]

---

### Post by ibjsb4 on 2013-05-27
Welcome :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by gordintoronto on 2013-05-27
Yes, the CPU is not important (as long as it is a 64-bit CPU, which all modern CPUs are), it's what version of Ubuntu you are using.

---

### Post by sorrensen on 2013-05-29
Ubuntu 12.10 64-bit now :)

---

