---
title: "Ubuntu only recognising 1 cpu"
date: 2007-01-19
forum: Installation &amp; Upgrades
---

### Post by emersony on 2007-01-19
Hi, 

   I have a 2 cpu system with 2 P-II's which are both being recognised by th bios on start up. 

   However in Ubuntu, /proc/cpuinfo only lists one of them. I am using the multi-cpu kernel 2.6. 

    If someone could just get me an idea where to start to fix this, I have tried Googling but need to narrow this search down!

    mucho thankso, 

Emerson.

---

### Post by smartsphere on 2008-06-23
1) I read on other Threads that 
if you install the **linux-generic**
not the **linux-386** 

the second CPU will be activated.

2) On another Thread they said to install **linux-686** would activate
    my second CPU

This seemed to work for awhile when the next upgrade came by with the update manager and my system fell back to the one CPU.

3) I install the grub _updatemanager_ using
   **apt-get install updatemanager**

 when I opened it it said I was running the **linux-386** by default ( ubuntu 8.04 kernel 2.6.19-386).

I am going to change the default to the **linux-generic** and see what happens.
I went looking to try the **linux-686** but it did not appear in the PICK list of the **updatemanager**

4) I would like to know what is the difference between using the generic or the linux-686. Which one should I pick to optimize my system.


Smartsphere

---

### Post by smartsphere on 2008-06-23
Ok that solved the missing CPU !!!
I used **System -> Administration -> System Monitor **
and I have the two CPU's running.


I Still would like to know the 
difference between the 

linux-generic
linux-686

Is  one better than the other???

Se-ya:

---

