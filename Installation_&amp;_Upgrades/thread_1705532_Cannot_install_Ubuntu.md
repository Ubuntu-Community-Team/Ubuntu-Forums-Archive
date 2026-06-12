---
title: "Cannot install Ubuntu"
date: 2011-03-12
forum: Installation &amp; Upgrades
---

### Post by Aragorn256 on 2011-03-12
After reading a lot about Ubuntu I decided to try it today. But despite all the reading and searching I have done I cannot get it to install to any of my machines. I tried almost all the current versions, in all the machines and I am ready to give up. As a last resort I decided to take the last futile installation on my main pc and try to ask for some help. I downloads (3 times) Ubuntu 10.10, I have tried installing it with Wubi, Cd , USB and failed miserably. Most of the time it will boot in the (?) purple desktop and stop there. A few times. a window popped about a wired connection and last time I got a screen looking like this :

stdin: error 0

[random number]Buffer I/O error on device fd0, logical block 0
         -//-              end_request: I/O error, dev fd0 sector o

Which it would repeat for quite a while with different numbers
And then

stdin: I/O error
stdin: error 0

My pc runs on a q6600 , 4gb RAM, nvidia 295gtx. Motherboard is the old P5k. My HD is partitioned in 3 smaller parts, 1 for windows 7, 1 for downloads and 1 for ubuntu in which i tried in vain to install. 

I tried the noacpi noacpi stuff when I was using Wubi but I have not found how to start the live cd/USB since the downloadable version is apparently the alternate one only. I tried downloading it 2 more times from the main page, but no success. What am I doing wrong here?

---

### Post by Rubi1200 on 2011-03-12
Hi and welcome to the forums :-)

Couple of things:

1. did you check the integrity? 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

2. have you tried nomodeset since you have an NVIDIA card?
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

---

### Post by Aragorn256 on 2011-03-12
Meh... I managed to install it, but now it loads to the desktop after log in and only the mouse is 

I started in safe mode and I wll be trying to update and install stuff for drivers

Despite the successful update and the enabling of nvidia drivers it still crashes on normal mode...any ideas?

And now there is black screen on safe mode as well

---

### Post by Aragorn256 on 2011-03-12
To summarize

Despite boot options, normal mode crashes at the purple desktop immediately after log in

Safe mode goes to black screen shortly after loading some stuff I don't have time to read

---

