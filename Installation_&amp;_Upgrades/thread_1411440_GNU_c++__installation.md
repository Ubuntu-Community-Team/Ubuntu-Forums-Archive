---
title: "GNU c++  installation"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by roydl on 2010-02-19
Hi - while I am trying to install c++ compiler, I came across a problem.
 
I need to install:
libstdc++6-4.0-dev (4.0.3-1ubuntu5) 
which is dependent on g++-4.0. And if you try to install g++-4.0 you will notice that it has cross dependency on libstdc++6-4.0-dev (4.0.3-1ubuntu5) 
 
How are you going about it?
I am installing dapper gnu c++ compiler.

---

### Post by GregBrannon on 2010-02-20
I don't know the dapper compiler, but you could try:

```
sudo apt-get install build-essential
```

to complete the g++ install and then try completing the dapper install.

---

