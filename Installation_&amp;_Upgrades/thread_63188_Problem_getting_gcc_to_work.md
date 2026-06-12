---
title: "Problem getting gcc to work"
date: 2005-09-07
forum: Installation &amp; Upgrades
---

### Post by chantal on 2005-09-07
Hello everyone,
I have an old Pentium 333 with Ubuntu 5.04 installed on it. To install gcc,  I did:
sudo apt-get -install build-essential
and now according to Synaptic Manager I have gcc, gcc 3.3 and gcc 3.3 base; libgcc1 is installed too. I have made  'MyPrograms' in my home directory where I will put source files.
When I tried the command : gcc hello.cpp  on
#include <iostream>
using namespace std;
int main() { cout << "Hello Chantal\n"; return 0; }   I got a lot of "undefined refs" :

/tmp/ccmHXAsm.o(.text+0x1b): In function `main':
: undefined reference to `std::cout'
/tmp/ccmHXAsm.o(.text+0x20): In function `main':
: undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'       etc

Do I need to configure gcc with a path or something? Any help would be welcome

---

### Post by rafakl on 2005-09-07
I dont think this is the best forum to post a compiler question, thats why no one is answering.  :razz: 

Try in other forum/thread, and you will have best luck !!!  ;-)

---

### Post by invalid on 2005-09-07
Try 

apt-get install gcc cpp g++

Cheers,
Cb

---

### Post by chantal on 2005-09-07
Thanks for the replies. I'm afraid the c++ compiler still doesn't work, though  gcc works ok with a simple c program.

I'll try in a compiler forum.

---

### Post by chantal on 2005-09-07
Thanks to Shen from the uk for tip to use the command:

g++ myfile.cpp -o myfile.exe         

option -o is for the output file name

'Cos using gcc myfile.cpp -o myfile.exe caused the problem. By the way (for other newbies like myself), myfile.exe will have 'ugo' executable permissions right away 755.

---

