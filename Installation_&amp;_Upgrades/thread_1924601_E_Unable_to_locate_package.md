---
title: "E: Unable to locate package"
date: 2012-02-13
forum: Installation &amp; Upgrades
---

### Post by sravankumarg on 2012-02-13
Hi 
i am relatively new to ubuntu and also the network simulations.
now i require to work with GTNetS - [SIZE=1]Georgia Tech Network Simulator[/SIZE]
so i have somehow installed it seeing guidelines provided in GTNetS official website
and now having installed i am trying to use it by executing examples given in

after executing 
$ make debug 
it has generated executables with .dbg file extension 
now when i am trying to execute the nms-dbg.dbg using command 
sudo apt-get install nms-dbg
it is throwing an error  - E: Unable to locate package nms-dbg

i am coping the whole code below for reference

sravan@ubuntu:~/GTNetS/EXAMPLES$ sudo apt-get install nms-dbg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nms-dbg
 
anticipating help
Thanks & Regards
sravan

---

### Post by mikewhatever on 2012-02-13
Try this link: [http://www.opennms.org/documentation/InstallUnStable.html#preparing-for-install](http://www.opennms.org/documentation/InstallUnStable.html#preparing-for-install)

Ubuntu is a Debian-based distro.

---

### Post by sravankumarg on 2012-02-13
thank you for the reply this is my first day first post on ubuntuforums and ur my first friend here with first reply

i think i was not clear in my query my exact problem is with using the .dbg files being created as output of make with GTNetS Example programs. 
now i am trying to use the .dbg files so as to see and analyze the output

thanks & regards
sravan

---

### Post by mikewhatever on 2012-02-13
You've tried installing 'nms-dbg' which is not in the repositories. The link above explains how to get it.

PS: Welcome to the forums :~).

---

### Post by sravankumarg on 2012-02-14
Thankuuu.....

---

