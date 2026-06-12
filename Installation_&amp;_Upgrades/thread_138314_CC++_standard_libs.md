---
title: "C/C++ standard libs"
date: 2006-03-01
forum: Installation &amp; Upgrades
---

### Post by invictus on 2006-03-01
How can I get all the C and C++ standard libs and headers?

Tried doing g++ main.cpp on the following code but it failed on the includes:

#include <stdlib> //also tried with stdlib.h
#include <stdio> //also tried with stdio.h
#include <pthread.h>
#include <iostream>
using namespace std;

int main()
{
  cout << "hello world" << endl;
  return 0;
}

but it failed on every single include. except iostream. On iostream I get tons of errors in the header file.

if I use cstdlib and cstdio instead same happenes there...it gets included, but get tons of errors saying the methods isnt declared.

---

### Post by taurus on 2006-03-01
Try

```

sudo apt-get install build-essential

```

---

### Post by jibril on 2006-03-01
I know gcc exists in /usr/lib/gcc and the only way i can run C code is by giving the entire path ... 

I put the path variable in .bashrc as 

[color=red]set path=(/usr/lib/gccc/i386-linux/4.0.2//usr/local/bin)$PATH[/color]

I tried that and sourced the file but still wont work. 

Also , i checked the jvm, it has a "java" executable but not a javac one.

Could someone help?

jibril

---

