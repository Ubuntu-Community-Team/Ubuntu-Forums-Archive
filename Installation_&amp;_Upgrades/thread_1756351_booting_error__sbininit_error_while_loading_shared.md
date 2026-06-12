---
title: "booting error:  /sbin/init: error while loading shared libraries: libdbus-1.so.3:"
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by bhaskarsanta on 2011-05-12
I am the newbie to ubuntu and recently i installed ubuntu 11.04 natty Narwal on my dell laptop. The installed ubuntu works fine until today, but i tried to install file libc.so.6 in shared library and in this process i had done some mistake and that i don't know what exactly it is. Now i tried to restart my computer and every time it was not booting either through graphical or recovery mode and in both processes i got the error like this "/sbin/init: error while loading shared libraries: libdbus-1.so.3: cannot open shared object or file: No such file or directory ", even i tried with live cd still i was not able to recover from this problem.
Please give me a solution to the above problem and i don't want to reinstall ubuntu again and again.

Question information

---

### Post by Buntumatic on 2011-05-12
The mistake you made was messing with libc. It is the most important system library, practically everything is compiled against it. Replacing any of glibc package components - libc.so being one of them - is a certain way to kill the system.

---

### Post by bhaskarsanta on 2011-05-12
> **Buntumatic said:**
> The mistake you made was messing with libc. It is the most important system library, practically everything is compiled against it. Replacing any of glibc package components - libc.so being one of them - is a certain way to kill the system.
Hello Buntumatic, thanks for your suggestions and finally restored system using my ubuntu live cd. The main problem from this is removed all the third-party softwares from my system. This is not a difficult task and i can reinstall all my favorite applications.

---

### Post by shgn on 2011-08-01
> **Buntumatic said:**
> The mistake you made was messing with libc. It is the most important system library, practically everything is compiled against it. Replacing any of glibc package components - libc.so being one of them - is a certain way to kill the system.

i have the exactly the same problem as above. but i mixed up by your description about the solution. please help me in begginers of linux. (i have ubuntu 11.04)
tanx.

---

### Post by bhaskarsanta on 2011-08-01
This is a old ubuntu forum and you can use new forum at ubuntu launchpad. you can solve the issue by using the following link that was helped me at long back.
[https://answers.launchpad.net/ubuntu/+source/dbus/+question/157181](https://answers.launchpad.net/ubuntu/+source/dbus/+question/157181)
 and this is my personal launchpad id in that website and if you want you can create a
id in that website.

---

