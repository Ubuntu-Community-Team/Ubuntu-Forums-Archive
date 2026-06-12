---
title: "Cs50 library on c"
date: 2016-02-27
forum: Installation &amp; Upgrades
---

### Post by Mrminime on 2016-02-27
Good day,
I am new to Ubuntu as new to c programing. Now i am watching cs50 videos to understand better about c and cs all together.
I tried to install this by using these guide lines: 


 **Debian, Ubuntu**

  First become root, as with:
 
  sudo su -
 
  Then install the CS50 Library as follows:
 
   apt-get install gcc
wget [http://mirror.cs50.net/library50/c/library50-c-5.zip](http://mirror.cs50.net/library50/c/library50-c-5.zip)
unzip library50-c-5.zip
rm -f library50-c-5.zip
cd library50-c-5
gcc -c -ggdb -std=c99 cs50.c -o cs50.o
ar rcs libcs50.a cs50.o
chmod 0644 cs50.h libcs50.a
mkdir -p /usr/local/include
chmod 0755 /usr/local/include
mv -f cs50.h /usr/local/include
mkdir -p /usr/local/lib
chmod 0755 /usr/local/lib
mv -f libcs50.a /usr/local/lib
cd ..
rm -rf library50-c-5 
 
 

I used it, and i think everything went as planned, but as soon as i try to run gcc demo.c i get fatal error message
this error:
adder.c:2:18: fatal error: cs50.h: No such file or directory
 #include <cs50.h>

So as it seems that somewhere something went wrong and I don't really know how to fix it, could anyone guide me a little bit how to fix it or how reinstall everything that c automatically would include that library?
Thanks

---

