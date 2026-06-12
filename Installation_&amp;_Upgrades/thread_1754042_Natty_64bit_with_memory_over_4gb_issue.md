---
title: "Natty 64bit with memory over 4gb issue"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by l0gix on 2011-05-09
I have a clean install of 11.04 64bit on a Asus EEE 1201N netbook with 8gb of BIOS seen memory. 

OS only see's 4gb of memory
> EEE-PC:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3269       1916       1352          0        118        550
-/+ buffers/cache:       1246       2022
Swap:         3325          0       3325


Did some googleing and found the PAE update that other versions of Ubuntu would allow to see more memory. 

When I try this with Natty I get the following error: 
> EEE-PC:/usr$ sudo apt-get install linux-generic-pae
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-generic-pae


Did some more research and find that PAE Kernel is available in 32 bit for Natty but not 64bit. [Source Link Here]("http://ubuntuforums.org/archive/index.php/t-1727459.html")

Is there anything that I can do or should I just go back to 32 bit?

Thanks, 
L0GiX

---

### Post by l0gix on 2011-05-11
Issue is limitation with the Atom 330 Processor. It is not able to use anything over 4gb. The rest of the hardware is able to see the memory over the initial 4gb, but is not usable.

---

