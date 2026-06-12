---
title: "Problem With Make Command In Ubuntu 6.10-please Please Anybody Help Me"
date: 2007-04-04
forum: Installation &amp; Upgrades
---

### Post by krisvamc on 2007-04-04
****

Hi,

I am trying to install MCS ( MULTICAST CONTROL SERVER) in ubuntu .

1) I decompressed the file "mcop_mcs.tgz".

2) In the directory mcop_mcs,type "make". It will compile all the necessary source files and creates the executable program.

**My problem is when I type make command in that directory, it tells command not found.**

**Could anybody please help me with this as I am struggling with installation**

[B]vamsi@vamsi-laptop:~/Desktop/mcop_mcs$ make
g++ -ansi -pedantic -Wall -W -c mcs.cc
make: g++: Command not found
make: *** [mcs.o] Error 127[/B]


thanks,
vamsi.

---

### Post by christhemonkey on 2007-04-04
You need to install the basic compilation tools:
```
sudo apt-get install build-essential 
```

---

### Post by krisvamc on 2007-04-04
is it enough to just type that command to run make. do i need internet connection or ubuntu cd.

---

### Post by christhemonkey on 2007-04-04
Cant remember whether its on the ubuntu cd, if its not then you will need an internet connection.
Try it and find out, first add the cd as a repository (insert the installation cd and then click add as a repository) then search for build-essential in synaptic.

Then once thats installed you will need to run the make command in the terminal again.

---

### Post by krisvamc on 2007-04-04
thanks for your help. I will try that.

---

