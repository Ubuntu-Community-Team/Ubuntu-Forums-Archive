---
title: "Serious problem with installation of GLUT"
date: 2013-04-21
forum: Installation &amp; Upgrades
---

### Post by majorka on 2013-04-21
Hi! I have a problem with installation of glut
I've tried many different commands such as: **yum install freeglut-devel, sudo apt-get install freeglut3-dev  **and it is not working. When I do it like here: [http://freeglut.sourceforge.net/docs/install.php](http://freeglut.sourceforge.net/docs/install.php) it does not work either.
When I use commands: **[FONT=arial]sudo apt-get install freeglut3 freeglut3-dev, [/FONT]**[FONT=arial]**sudo apt-get install binutils-gold** , it tells me that it is installed but when I try to compile a program it tells me that it cannot find glut.h and shows many many errors. I have no idea what I should do and what is wrong. I would be reaaaaally grateful if you could help me.[/FONT]

---

### Post by MG&amp;TL on 2013-04-21
I just tried this, you need to

```
#include <GL/glut.h>
```

Not:

```
#include <glut.h>
```

And obviously you need to link against GLUT.

---

### Post by majorka on 2013-04-21
Actually I already have:
#include <GL/glut.h>
#include <GL/glext.h>
#include <GL/gl.h>

What do you mean by link against GLUT?

---

### Post by majorka on 2013-04-21
Ok, now I have a different problem. I have errors such as : undefined reference to std:: ......
I've installed build-essential but i still have those errors. What's wrong?

---

### Post by MG&amp;TL on 2013-04-21
> **majorka said:**
> 
What do you mean by link against GLUT?

You need to specify '-lglut' on the compile command-line.

E.g.:

```
cc somefile.c -lglut
```

This tells the linker that you need to include symbols from the GLUT library.

> **majorka said:**
> Ok, now I have a different problem. I have errors such as : undefined reference to std:: ......
I've installed build-essential but i still have those errors. What's wrong?

Quick checks:

[LIST]
[*]Have you installed a C++ compiler? (*g++*, *clang*)
[*]Are you using it? (e.g. invoke *g++* not *gcc*)
[*]What compiler flags are you using?
[/LIST]
Cheers.

---

