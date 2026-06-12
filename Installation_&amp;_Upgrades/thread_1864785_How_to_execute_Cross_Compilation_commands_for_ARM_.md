---
title: "How to execute Cross Compilation commands for ARM in UBUNTU"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by Ramesh Satyavaram on 2011-10-19
HI,



 We want to set up "ARM" base cross compilation tools for ECOS operating system on UBUNTU System.



We are using "UBUNTU 11.04" version.



I did the following.



a. Placed the "ARM Cross compilation binary utilities" in the /opt/gnutools/arm-elf/bin "



b.Now added the path in the "/etc/profile" file in the following way.

      " PATH=/opt/gnutools/arm-elf/bin:$PATH ; export PATH"



c. Restarted the UBUNTU System.

d. Now from command line i can access the commands such as "arm-elf-gcc" with out any problem.



e.But when i tried to compile a file using the command "arm-elf-gcc -c main.c -o main.o"



THe system returning with the following error " bash: /opt/gnutools/arm-elf/bin/arm-elf-gcc : no such file or directory"





Actually i can access command "arm" with TAB.The system is showing all the commands but when i tried to compile i am getting the above error 

message.



Can any one help me in this.


Thank you,
Ramesh.

---

