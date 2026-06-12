---
title: "Upgrades for C programming"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by TheUmer on 2010-02-09
Hi all!

I installed Ununtu and I want to run C programs while having them written in a simple text file and running them on the terminal. But it's not working. I've tried several times and in several ways. What would I have to install/upgrade for this? 

Thanks.

---

### Post by darkod on 2010-02-09
As far as I know, you only need the package g++ which is the c++ compiler. It should install the standard libraries with it. Any libraries of your own, you would have to have.

Try just:
sudo apt-get install g++

---

### Post by Dayofswords on 2010-02-09
[SIZE="1"]not a programmer[/SIZE]

i don't think C can be interpreted

only compiled

---

### Post by lisati on 2010-02-09
g++ is for C++. If you're using C, then use gcc

---

### Post by azagaros on 2010-02-09
if you want to c programming on Linux make sure the gcc package is installed.

<filename>.h is a c/c++ header
<filename>.c is a c file.
<filename>.cc or cpp is a c++ file name.

gcc <filename>.c
should generate an executable of <filename> and it doesn't matter which you start with c or c++ they are two different programming languages.

g++ is the c++ compiler direct path.

Another note about c/c++ compilers out there most of out there compile both c and c++.  It is making sure you start your code correctly and which syntax standards you maintain.

---

### Post by gmargo on 2010-02-10
> **TheUmer said:**
> I want to run C programs while having them written in a simple text file and running them on the terminal. But it's not working.

Install the **build-essential** package which will give you a C compiler (gcc), a C++ compiler (g++), make, and the header files and libraries you need for basic development.

Then start with The One True Program:
```

$ cat world.c
#include <stdio.h>
main()
{
    printf("Hello, World\n");
}
$ make world
cc     world.c   -o world
$ ./world
Hello, World


```

---

### Post by anglican on 2010-02-12
> **Dayofswords said:**
> [SIZE=1]not a programmer[/SIZE]

i don't think C can be interpreted

only compiled

There is a C interpreter, which compiles fine (under Hardy - haven't tried on a newer release) from:

[http://root.cern.ch/drupal/content/cint](http://root.cern.ch/drupal/content/cint)

you'll need the latest (or at least 5.16.25) from svn to compile with g++-4. As well as build-essentials you'll need libreadline5-dev installed. Then (after setting environment as per the README) you can do:

$ cat hello.c
#include <stdio.h>

main()
{
fprintf(stdout,"Hello World!\n");
}
$ cint hello.c
Hello World!
$

Of course, if you've installed gcc etc... whether you really need an interpreter as well is a moot point.

H

---

