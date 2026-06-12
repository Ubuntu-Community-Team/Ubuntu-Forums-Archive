---
title: "Compiling in an older version of gcc"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by WarholsGhost on 2010-04-27
I have some code for a class that only compiles in gcc 4.2.4 and i have installed on my system 4.4.1. i downloaded from synaptic gcc4.2 and ran the code to try to compile my code:

```
$ g++ -V 4.2.4 test.cpp

```

and the output i get is:

```
g++: error trying to exec 'i486-linux-gnu-gcc-4.2.4': execvp: No such file or directory
```

how can i get the -V command to see the older version of gcc and compile said code?

---

