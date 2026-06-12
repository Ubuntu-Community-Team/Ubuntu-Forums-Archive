---
title: "Help Installing Functional GNU GCC and G++"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by alexkaz on 2010-01-02
Hello Community, 

Can anyone lend their expertise installing GNU GCC and G++?
I installed Ubuntu Linux during this week, and have been struggling with the GCC and G++ download, configure, build.

Problem: when I try to implement gcc hello.c -o output or g++ hello.cpp -o output 
the following errors occur: 
hello.c:1:20: error: isotream: no such file or directory //but libpstreams-dev (a C++ iostream interface to POSIX process I/O) shows to be installed by Synaptic. 

There are other errors that also suggest a path error or non-existence of the C Standard Library. 
the other error is: 
hello.c:6:error: 'cout' undeclared (first use in this function) // never seen that before.. 

help.. I'm not sure what is going on, any thoughts or corrections?
Thanks

---

### Post by alexkaz on 2010-01-02
SOLUTIONS for GNU-GCC and GNU-G++ INSTALL: 
SOLUTIONS for GCC and G++ test script hello.c and hello.cpp. 

Thank you for everyone's assitance over some pretty naive errors (guess that's the only way to learn something new). 

A suggestion for Ubuntu is to add the simple instructions to a download and install common software posting, for specific software, i.e. GCC. 

Here are the solutions to be shared: 

1. My installation of GCC and G++ were chaotic because I coudn't get the ./configure command to work as provided by the GNU GCC Homepage that provides instructions. 
Fortunately, the Ubuntu Software Center makes downloading the software and installing it easier than the GNU Homepage Instructions. Also the Synaptic Package Manager simplifies finding  and verifying the correct package versions for the 'build'. 

Summary:  Just use the Ubuntu SW Ctr to download and install, then the Synaptic Mgr for finding the most current upgrades and explanations for the file functions. 


2. The gcc and g++ would not find the gcc or g++ file until a symbolic link was created between the folder with code and the gcc-4.4.2 folder. 

Also the failing to code the differences between hello.c and hello.cpp prevented their compilation. .c uses #include "stdio.h" and .cpp uses #include <iostream> for
printf("hello\n"); //.c version and using namespace std cout << 'hello\n'; //.cpp version.

---

### Post by lisati on 2010-01-02
Why bother downloading GCC etc when it comes as standard with Ubuntu? All you need to do is install the build-essential package.

---

### Post by alexkaz on 2010-01-03
when I was preparing to install ubuntu, there was a ubuntu forum thread where one person complained ubuntu did not come with a c compiler and a response was to use suse?
 
But it is now running, but have bugs trying to run an svm_light software. 
 
when I enter: 
prompt: gcc -o svm_learn example1/train.dat example1/model
the error is: example1/model not found
 
then:
prompt: gcc -o svm_learn example1./train.dat
errors: example1/train.dat: file not recognized: file format not recognized.
 
how can I correct 1) recogition of .dat files and 2) recognizing a file that exist in the subdirectory example1   that is named train.dat  ?

---

