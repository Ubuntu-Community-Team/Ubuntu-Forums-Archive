---
title: "install c and c++ in ubuntu 11.04"
date: 2011-09-04
forum: Installation &amp; Upgrades
---

### Post by mugbomb on 2011-09-04
hi to all.
im trying to install c and c++ at ubuntu 11.04 but im facing some problems. ill post right above what i did for who wants to help see it and help me correct what i did wrong.

      For compilation of c code:
1.Open : applications>accessories>terminal
2.Type the following command in the terminal
gedit name of ur file.c
       // I HAVE GIVE MY FILE NAME AS main.c
For me i will type   gedit main.c   inside terminal
3.Write ur code inside the gedit editor:
#include
#include
int main(int argc, char** argv)
{
 printf(“NAMAH SHIVAY\n”);
 return 0;
}
4.save the code by pressing ctrl+s
5.In the terminal itself goto :File>Open terminal and do as follows in the newly opened terminal
6.Compile the code using the following command :
 cc -c main.c
7.This would produce an object file now you may need to add to the library.
Then create an executable using the following command :
cc -o main main.c
8.Now run this executable using the following command :
./main


so i did this at the first time and it didnt work!



at the second i tried the comand:
sudo aptitude install build-essential but the terminal dont know aptitud so i guess that this is the wrong way too.


then i tried:
sudo apt-get install build-essential and i got something but i just dont know how to go from here.
so any help will be great.


best regards from mugbomb

---

### Post by lmarmisa on 2011-09-04
If you are not sure if the C/C++ gcc compiler is installed on your computer, open a terminal and type this command:

```

luis@UB1104ZOTAC:~$ [COLOR="Blue"]cc -v[/COLOR]
Using built-in specs.
COLLECT_GCC=cc
COLLECT_LTO_WRAPPER=/usr/lib/i386-linux-gnu/gcc/i686-linux-gnu/4.5.2/lto-wrapper
Target: i686-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.5.2-8ubuntu4' --with-bugurl=file:///usr/share/doc/gcc-4.5/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.5 --enable-shared --enable-multiarch --with-multiarch-defaults=i386-linux-gnu --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib/i386-linux-gnu --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.5 --libdir=/usr/lib/i386-linux-gnu --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-plugin --enable-gold --enable-ld=default --with-plugin-ld=ld.gold --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu
Thread model: posix
gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) 
luis@UB1104ZOTAC:~$ 

```

If you get a result similar to this, your compiler is correctly installed.

---

### Post by IWantFroyo on 2011-09-04
GCC (Gnu Compiler Collection) supports C and C++.
It's installed by default.
Just type:
```
gcc main.c
```Edit- Wait a moment... I could be wrong. Try it anyways. Just a heads up.

Edit 2- I read you're supposed to use g++ for c++ code... It apparently isn't installed by default (at least not in my 10.04).

---

### Post by bikewrecker on 2011-09-05
I was having trouble with this earlier too. After you type gcc main.c it should be compiled and it should make a file named a.out. to run the compiled program after that you need to type "./a.out" and that should run it. With the -o command you can change the compiled output file name but I think you have to put .out on the end of it. 
ex: gcc -o main.out main.c

Then you will need to type "./main.out"

hopefully this helps!

---

### Post by mugbomb on 2011-09-05
> **lmarmisa said:**
> If you are not sure if the C/C++ gcc compiler is installed on your computer, open a terminal and type this command:

```

luis@UB1104ZOTAC:~$ [COLOR=Blue]cc -v[/COLOR]
Using built-in specs.
COLLECT_GCC=cc
COLLECT_LTO_WRAPPER=/usr/lib/i386-linux-gnu/gcc/i686-linux-gnu/4.5.2/lto-wrapper
Target: i686-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.5.2-8ubuntu4' --with-bugurl=file:///usr/share/doc/gcc-4.5/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.5 --enable-shared --enable-multiarch --with-multiarch-defaults=i386-linux-gnu --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib/i386-linux-gnu --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.5 --libdir=/usr/lib/i386-linux-gnu --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-plugin --enable-gold --enable-ld=default --with-plugin-ld=ld.gold --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu
Thread model: posix
gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) 
luis@UB1104ZOTAC:~$ 

```If you get a result similar to this, your compiler is correctly installed.
allright my compioler is already installed that means that i should run the program allready or i need to install some more thing to use c and c++?

best regards and thx all to awser the question.
the other awser that he doesnt know if it works but to try. i tried and it didnt work. but thx anyway for your time and patient.

best regards too all

---

### Post by haresear on 2011-09-05
@bikewrecker: If you use the option "-o <filename>" the output file will be named exactly <filename> -- no .out is necessary in the name.

@mugbomb: When you say it didn't work, what happened exactly? Were there any error messages?

Step 6 should have created an object file named "main.o". Did this happen?

Step 7 would normally use that object file:
cc -o main main.o
However the command you show is:
cc -o main main.c
which will ignore main.o and recompile main.c, so using this command makes step 6 unnecessary. Either command should create an executable file named "main". Did this happen? Were there any error messages?

What message do you get when you run ./main ?

The two lines in your main.c file:
#include
#include
should normally have file names at the end, e.g.
#include <filename>
Have you left something out?

---

### Post by haresear on 2011-09-05
Okay I tried to compile and run your main.c. The problems are:

1. Change the two "#include" lines to:

#include <stdlib.h>
#include <stdio.h>

2. The double quote characters used in the line

printf(“NAMAH SHIVAY\n”);

are not recognized by the compiler. The line should be:

printf("NAMAH SHIVAY\n");

(Note the subtle difference in the double quotes.)

---

### Post by mugbomb on 2011-09-05
ok i did this now:
i open the terminal and i type:
gedit main.c
```
#include <stdlib.h>
#include <stdio.h>
int main(int argc, char** argv)
{
printf("NAMAH SHIVAY\n");
return 0;
}
```
and as you said i put the <filename> and changed the quotes namah shivay,
so far no error's
but now at that part of:
cc -c main.c
here nothing happen
cc -c main.o
error: cc: main.o: linker input file unused because linking not done
and for last 
cc -o main main.c
NAMAH SHIVAY this is what i get but only if i make the comand cc -c main.c

so this was what i understand about you explanation you make if this was the thing and its done thx very much if not tell me what i did wrong again  because there is maybe something that im missing.

thank you for helping me and spending time trying to solved my problem
best regards:P

---

### Post by lmarmisa on 2011-09-05
These links could help you:

[http://books.google.es/books?id=8cPcMG68RH4C&lpg=PP1&dq=c%2Fc%2B%2B&hl=en&pg=PP1#v=onepage&q&f=false](http://books.google.es/books?id=8cPcMG68RH4C&lpg=PP1&dq=c%2Fc%2B%2B&hl=en&pg=PP1#v=onepage&q&f=false)

[http://books.google.es/books?id=ruHktiARJtgC&lpg=PA1&hl=en&pg=SA1-PA36#v=onepage&q&f=false](http://books.google.es/books?id=ruHktiARJtgC&lpg=PA1&hl=en&pg=SA1-PA36#v=onepage&q&f=false)

[http://books.google.es/books?id=oJaE_ikTMu8C&lpg=PP1&hl=en&pg=PA3#v=onepage&q&f=false](http://books.google.es/books?id=oJaE_ikTMu8C&lpg=PP1&hl=en&pg=PA3#v=onepage&q&f=false)

---

### Post by gardnan on 2011-09-05
Alright, doing the command
cc -c main.c
Only compiles the source from C code into binary, or "object code" and stores the result in main.o. This file is not very useful at this point because it is not linked (compiled with) the standard library. To do this, one can execute:
cc main.o -o main
To link the main.o "object code" to the C standard library code.
However, GCC can do all of these in one step by executing the command:
cc main.c -o main
Which is what you appear to be doing in the last step of your compilation process.
Basically the last step you are doing is doing the full compilation, while all of the other steps are manipulating object files, which I don't think you want to be doing until you know more about the compilation process.

---

### Post by haresear on 2011-09-05
I don't quite understand your question, but I'll give a couple of answers and hope one hits what your asking.

There are two ways to create the executable file:

Option 1:
cc -c main.c      -->(this should create object file main.o from source file main.c)
cc -o main main.o -->(this should create executable file main from object file main.o)
./main            -->(this should produce the output NAMAH SHIVAY)

Option 2:
cc -o main main.c -->(this should create executable file main from source file main.c)
./main           -->(this should produce the output NAMAH SHIVAY)

The single cc command in Option 2 combines the two cc commands in Option 1 into one command, and skips the step of creating the object file main.o. The command "cc -c main.c" does not produce any output if it is successful, but you can check if the object file was created with the command "ls -l main.o".

The command:
cc -c main.o
is not valid because the command "cc -c" needs to be followed by a source code file (.c), NOT an object file (.o).  "cc -c" is used to create (compile) an object file (.o) from a given source code file (.c). You have instead given it an object file (.o), so there is nothing to compile.

---

