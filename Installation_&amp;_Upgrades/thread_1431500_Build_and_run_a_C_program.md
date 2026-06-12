---
title: "Build and run a C program"
date: 2010-03-16
forum: Installation &amp; Upgrades
---

### Post by mooman001 on 2010-03-16
Hey I wanted to start working on a mud... But I cannot figure out how to build it... Help me please.

[http://sourceforge.net/projects/aime/files/]("http://sourceforge.net/projects/aime/files/")


:)

---

### Post by thegod_slayer on 2010-03-16
first you need to check whether you have got the c/c++ dependencies or not????

if not then go to the terminal and type sudo aptitude install build-essentials

this would install all the required dependencies.

now you need vim

to install this write

sudo apt-get install vi

now after all these installs go to the terminal
and type
vi your c program name.c
now you will enter into vi.
press i on your keyboard to insert.
afet writind the program press the escape buttton of your keyboard.
then press shift+: 
and write wq
your program will be saved in the home folder.
now you can compile the program program by typing
c your program name.c
and if your program is correct you will be directed to the next line without any output.
to see the output type ./a.out
this will show you the output.

---

