---
title: "Ubuntu Software Center"
date: 2010-11-04
forum: Installation &amp; Upgrades
---

### Post by Axman10 on 2010-11-04
Everytime I try to install, or unistall anything, I get an error: 

Errors were encountered while processing: 
 man-db

there are a few different ones, but they all have that.

---

### Post by cipherboy_loc on 2010-11-04
What version and flavor of Ubuntu? This will help us narrow down what is causing the issue. 



Cipherboy

---

### Post by Axman10 on 2010-11-04
I'm not sure, Ubuntu 10.10 I think.

I downloaded it from here: [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by cipherboy_loc on 2010-11-06
Okay. Can you open up a terminal (Alt+f4 and in the box type gnome-terminal)? When this loads, enter dpkg --list | grep -i 'man-db' and post the output. Also post the output of sudo dpkg --configure -a. The sudo dpkg --configure -a command will prompt for a password, BTW. 

The first command will list the status of the man-db package. The second command will configure all un-configured packages. What are the programs that you are trying to install?



Cipherboy

---

