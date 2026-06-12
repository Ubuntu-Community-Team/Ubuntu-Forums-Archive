---
title: "Assembler instructions not being created correctly for mutiplication in GCC"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by MichaelMontcalm on 2008-06-26
Hello All,

I've tried searching for something like this through the forums and so far have not been able to find anything. If this is in fact a repeat, my apologies. I hope you can have a bit of patience with me as I'm new to both Linux in general, and the forum itself.

I'm currently running Ubuntu 7.10 (Gutsy Gibbon), and have installed and configured GCC 4.0.1 according to the following:

Target: sparc-elf
Configured with: ///configure --target=sparc-elf --witn-newlib --without-headers --with-gnu-as --with-gnu-ld --enable-languages=c --disable-nls
Thread model: single

I'm also using binutils 2.16. If you're wondering why I'm not using the newest versions it's because I'm attempting to follow a document for some research and don't want to stray from their instructions in the event I need to get help from them. I've followed almost every steps word for word form the following site ([http://www.cmpware.com/Docs/BuildingGcc.pdf](http://www.cmpware.com/Docs/BuildingGcc.pdf)) in an attempt to create a cross compiler for further research. 

I've actually managed to get the demonstration program they've provided to work, and it has been sent for testing with another student.

I've since gone on to try some other programs. It is here where I've run into some trouble. As I'll be doing a lot of work with multiplication, I decided to try a simple for loop that multiplies two numbers ten times. For example:

#include <stdio.h>
int main()
{
 int i;
 int a=2;
 int b=2;
 for (i=0;i<10;i++)
 {
  a=a*b;
 }
 return 0;
}

However, in the *.o file, the line where a multiplication assembler instruction should be is the line:

40 00 00 00   call 28<main+0x28>

When I attempt to follow the same method to create the *.elf file, I receive the error "undefined reference to '.umul'"

I'm wondering if anyone has ever heard of this error, and if you know what I'm missing or where I messed up so that I can get this resolved.

Any advice is appreciated

Thanks,
Michael

---

