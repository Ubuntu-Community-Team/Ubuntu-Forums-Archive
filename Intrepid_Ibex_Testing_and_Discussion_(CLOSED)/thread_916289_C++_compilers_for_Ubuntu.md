---
title: "C++ compilers for Ubuntu"
date: 2008-09-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by TitanEG on 2008-09-10
Hi folks,
   I am a noob to Ubuntu.  I am building a PC and plan on making it a Ubuntu PC.  I have been teaching myself C++ and have been using the dev-C++ and MS Visual C++ compilers.  I'd like to continue on learning to program in C++ but my question is this:  what are some good C++ compilers for Ubuntu.
Thanks!!!

---

### Post by damoxc on 2008-09-10
I'd have a look at gcc if I were you, the GNU C and C++ compiler.

---

### Post by cmay on 2008-09-10
[PHP]sudo apt-get install build-essential[/PHP]
this is the best c and c++ compiler i know. its free also. 
its the standard gcc compiler for linux. there is also a programming talk section in these forums. ask there if you get stuck
good luck :)

---

### Post by Joeb454 on 2008-09-10
Actually the C++ compiler is called g++

You can install both by installing [build-essential]("apt://build-essential") using ```
sudo apt-get install build-essential
```

---

### Post by inportb on 2008-09-10
Yeah, build-essential is a basic compilation environment; it's works well ;p

---

### Post by damoxc on 2008-09-10
> **Joeb454 said:**
> Actually the C++ compiler is called g++

You can install both by installing [build-essential]("apt://build-essential") using ```
sudo apt-get install build-essential
```

I was going by man :)

From man g++:
```
gcc - GNU project C and C++ compiler
```

---

### Post by Cenotaph on 2008-09-10
iirc dev-c++ uses gcc from mingw so you probably already have some experience with gcc even if you are not aware of it.

if you're looking for an IDE that's another story.

but in linux, for c/c++ programming, gcc is almost mandatory hehe. i think this thread is on the wrong forum however

---

### Post by Joeb454 on 2008-09-10
> **damoxc said:**
> I was going by man :)

From man g++:
```
gcc - GNU project C and C++ compiler
```

I think g++ is part of gcc. But to actually compile the code, I always use gcc for C, and g++ for C++

---

### Post by inportb on 2008-09-10
I believe gcc and g++ can be used interchangeably, with the appropriate commandline options -- gcc defaults to C and g++ defaults to C++.

---

### Post by Cenotaph on 2008-09-10
you can use gcc for both, if the file extension is .cpp instead of .c the gcc command will compile as if it was g++

---

