---
title: "help with sudo apt-get install."
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by hoodlum on 2007-09-28
when ever i do a sudo apt-get install wut-ever.tar.gz it gives me this error:

hoodlum@hoodlum-laptop:~$ sudo apt-get install wine-doors-0.1.tar.gz
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wine-doors-0.1.tar.gz

E is the letter of my CD/DVD drive. wut the hell dose tha have to do wit this. Ubuntu is installed to my hard drive. 
Wut am i doin wrong?

---

### Post by lisati on 2007-09-28
1. Are you trying to install from a file that you have downloaded?
2. "E:" means "Error"

---

### Post by Warren Watts on 2007-09-28
apt-get install is for installing packages from the repositories.

Usually g-zipped tarballs are source packages that would have to be compiled.

Have you looked in the repo's to see if wine-doors is available?
(I'm don't have a Ubuntu box handy at the moment or I would look myself..)

---

