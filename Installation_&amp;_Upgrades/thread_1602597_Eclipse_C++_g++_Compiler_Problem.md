---
title: "Eclipse C++ g++ Compiler Problem"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by fumini on 2010-10-21
Hello,

i get different errors when I want to compile c++ files with Eclipse. I installed everything several times and checked many options (like SDK Path in eclipse and many else)

but every time i get an error it depends to g++ package. I think the compiler does not work correct.

So my first question:
**How can i deinstall or reinstall the g++ compiler packages??**


My second qustion refers to eclipse with ubuntu:
the last error when i tried to compile was:
> Building file: ../demo.cc
Invoking: GCC C++ Compiler
arm-angstrom-linux-gnueabi-g++ -O0 -g3 -Wall -c -fmessage-length=0 pkg-config --cflags playerc++ -MMD -MP -MF"demo.d" -MT"demo.d" -o"demo.o" "../demo.cc"
/usr/local/angstrom/arm/bin/arm-angstrom-linux-gnueabi-g++: 1: Syntax error: "(" unexpected
make: *** [demo.o] Fehler 2but if can*t open usr/local/angstrom/arm/bin/arm-angstrom-linux-gnueabi-g++ in order to edit it.
Can someone helb me with this error?

---

### Post by GregBrannon on 2010-10-21
Recommend this thread be moved to Programming Talk sub-forum.

fumini, based on the error message you've gotten from gcc, I'm guessing there's something wrong with your code, though I'm wondering how you're getting a simple syntax problem using Eclipse.  Oh well.

To help us figure it out and help you, write a simple "Hello, World" program, copy it (cut and paste it) from somewhere if you have to, compile it and run it in Eclipse.  If you're still getting the error message, paste the code and the error message for us to see.

Keep coding!

---

### Post by axi.torvalds on 2011-04-30
> **fumini said:**
> Hello,

i get different errors when I want to compile c++ files with Eclipse. I installed everything several times and checked many options (like SDK Path in eclipse and many else)

but every time i get an error it depends to g++ package. I think the compiler does not work correct.

So my first question:
**How can i deinstall or reinstall the g++ compiler packages??**


My second qustion refers to eclipse with ubuntu:
the last error when i tried to compile was:
but if can*t open usr/local/angstrom/arm/bin/arm-angstrom-linux-gnueabi-g++ in order to edit it.
Can someone helb me with this error?
Did you install eclipse from software center and g++ and gcc?

---

