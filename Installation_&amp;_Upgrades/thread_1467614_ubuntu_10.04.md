---
title: "ubuntu 10.04"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Feelin_froggy8877 on 2010-04-30
Did anyone else have any trouble with samba after upgrade? While trying to share a folder I'm getting error... 

"libtalloc.so.1  no such file or directory" And does not seem to be in the repos. I made an attempt at install samba3.5.2 from source. Ran "autogen.sh" then moved on to ./configure, but that reports I need "python 2.(4, 5, or 6) installed.

---

### Post by Feelin_froggy8877 on 2010-05-01
I have been searching for whatever I could find on this issue. Couldn't seem to find much at all. I thought of the 9.10 install I had on another hdd in that comp, found the missing library on that hdd and simply copied it over to /usr/lib and it seemed to do the trick. As for the problem, it does not seem anyone else is running into this.

---

