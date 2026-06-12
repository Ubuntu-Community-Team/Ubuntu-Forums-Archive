---
title: "Trying to install opengl dev (compile an opengl program)"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by someoney3000 on 2010-06-04
Hello, I'm new to Ubuntu.  I was using fedora before and all the opengl development files were in a single package (+ dependencies).  I can't seem to track down that for Ubuntu.

Sure, I found the mesa libraries (libgl1-mesa-dev and libglu1-mesa-dev) and even tried freeglut3-dev, but none compiles the opengl program that runs on my fedora fine.

I get this error message:

```

/tmp/ccFnAvO6.o: In function `display()':
RoamingTerrain.cpp:(.text+0x6067): undefined reference to `gluLookAt'
/tmp/ccFnAvO6.o: In function `myReshape(int, int)':
RoamingTerrain.cpp:(.text+0x60e5): undefined reference to `gluPerspective'
collect2: ld returned 1 exit status

```

Anyone know what I am missing?  I compile via g++ -lglut RoamingTerrain.cpp

---

### Post by someoney3000 on 2010-06-06
Help, anyone?  Please?  ;_;

---

### Post by someoney3000 on 2012-10-15
> **someoney3000 said:**
> Help, anyone?  Please?  ;_;

For anyone who finds this thread, go here: [http://ubuntuforums.org/showthread.php?t=345177](http://ubuntuforums.org/showthread.php?t=345177)

Furthermore, I noticed it matters where the -lglut command comes in; i.e.  g++ RoamingTerrain.cpp -lglut

---

