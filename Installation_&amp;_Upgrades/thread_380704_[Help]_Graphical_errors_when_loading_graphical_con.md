---
title: "[Help] Graphical errors when loading graphical content"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by Deray on 2007-03-10
At first I tried installing ubuntu using the default install disc stortly after it loaded the first window that cameup gliched out only displaying green pixels and a silver of the windows top, that was indiscernible. 

    I downloaded and used the alternate text install disc to install, no problems, i started up got to the enter password screen still no problems. I entered the user name and password and as soon as the next window opened the computer froze again with the same problem from the install disc.

    The next thing i tried was to open the terminal and run some of the scripting that was suggested. When the terminal panel loaded it was stuck the to the lower right hand side and the text was completely illegible. In that the entire window was a collage of pixels.
I suppect my graphics card is the culperate. However i am unsure of how to proceed. 

The specs for my computer are as follows:
3800+ X2 AMD 939 processer
A8N-SLI deluxe motherboard
2GB of ddr 3200 ram
80GB Sata hard drive and a dvd/cd reader
7800GT Geforce evga graphics card

I verified the install disk before i installed.

The problem looks alot like when you have ethier overclocked or the graphics has over heated 
the pixelation is very similar.

Since i am not very familar with linux please discribe, each step in detail when you provide a solution.

thanks,
Deray

---

### Post by pradeepadapa on 2007-03-10
can u tell us which version of ubuntu u tried to install, nd did take UBUNTU for AMD64 bit edition.........................'

give some details abt the version which u tried to use...

---

### Post by Deray on 2007-03-10
Installed the most recent version. I downloaded this version ubuntu-6.10-alternate-i386.iso.

---

### Post by Deray on 2007-03-10
i have yet to resolve this issue.

---

### Post by Deray on 2007-03-10
read around some more still no solution.

---

### Post by Deray on 2007-03-11
almost given up hope...

---

### Post by jksigurd on 2007-03-11
You are describing my problem to a T.   I have the same video card but the BFG version, the 7800 GT.  That has to be what is causing the problem.  I was installing the amd64 version, so I guess the i386 fares no different.  There must be some way to get around this.

I'm not suggesting but just asking, have you tried the Dapper or Feisty builds?

---

### Post by jksigurd on 2007-03-11
Just did some snooping around searching specifically for problems with the 7800GT. 

Apparently there is a conflict with the Nvidia driver on the LiveCD and the 7800GT, resulting in the problems we've been having.

[http://ubuntuforums.org/showthread.php?p=2268952](http://ubuntuforums.org/showthread.php?p=2268952)

There is the post that tells you how to get around it so you can get Ubuntu installed.

Not many people seem to know about this aside from 7800GT owners.

It's kind of funny, Linux is touted as being one of the most hardware compatible operating systems. Oh well, I'm gonna go give this a try, good luck with your installation.

---

### Post by pradeepadapa on 2007-03-11
hello deray,

                   u must download and install UBUNTU 6.10 x64 alternate cd not x386 bec of ur processor, since it is 64bit processor, just try using the latest 6.10 ubuntu AMD64 edition cd, then if u hav any problm let us know, dont loose hope easily man...................

---

