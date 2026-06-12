---
title: "Installing g++: couldn't find package g"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by rabbit1986 on 2008-05-29
Hello, I had an older version of Ubuntu, just installed Hardy Heron. I do programming on my computer in C++. However, when I tried to install g++, here is what I get:

~$ sudo apt-get install g++

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package g


I already checked to find an answer to this on web, I tried apt-get update/build-essential, it's funny those won't work also and I have not found any solution. Any help'd be much appreciated.

---

### Post by Pumalite on 2008-05-29
It's in Synaptic. Open up all your repos.

---

### Post by rabbit1986 on 2008-05-30
Pumalite, thank you for your reply. I have tried getting the package on Synaptic, by just searching for g++, but it doesn't show anything. I assume it might well be because I don't have access to all the repositories. How would I activate/open all my repos? Thank you in advance.

---

### Post by Pumalite on 2008-05-30
System>Administration>Software Sources>Put a check in all of then (I don't use src, but maybe you do)

---

### Post by rabbit1986 on 2008-05-30
Thank you Pumalite. Problem solved. Upon your suggestion and visiting Software Sources, when I saw that all the check-boxes are already checked, I found out that the Download From: option was set to Server from Canada; I changed that to Main Server and now everything seems to be working. I just hope I did the right thing without side effects. Thank you so much anyways, keep up the good job.

---

### Post by Pumalite on 2008-05-30
Happy Ubuntuing!

---

### Post by sephiroth_slash on 2009-12-08
> **rabbit1986 said:**
> Hello, I had an older version of Ubuntu, just installed Hardy Heron. I do programming on my computer in C++. However, when I tried to install g++, here is what I get:

~$ sudo apt-get install g++

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package g


I already checked to find an answer to this on web, I tried apt-get update/build-essential, it's funny those won't work also and I have not found any solution. Any help'd be much appreciated.


Hi, 

I have the SAME Problems !! I installed ubuntu 9.10 desktop on more than 10 Desktop computer ( Pentium 4 )  in my university, these PCs can't read DVD & there is no internet in the room ( how they wont us to study in these conditions ???!!! :) 

   when I did : apt-get install g++, I got the same problem :  " couldn't find package g "

  I tried to install the g++ packages from the CD, but I got a dependance error with gcc ( even tough, gcc is installed and work correctly !!! )


Please, is there any solution ??? help me pleaase

---

### Post by sephiroth_slash on 2009-12-09
oh yeaaaaaaaah  !!! I got it !!

when I did : sudo apt-get install g++, I didn't specified to apt to search in the CDROM, so I had to do : 

  1 - sudo apt-cdrom add
  2 - sudo apt-get install g++


I just tested it ! i work perfectly !! :D

thanks anyway

---

