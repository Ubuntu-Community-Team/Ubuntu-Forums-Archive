---
title: "Partition problem during 9.10 install: device busy"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by Pratik Ali on 2010-03-08
Hi,
 
  
 Upon partitioning during install, I receive the following message:
    
Error informing the kernel about modifications to partition /dev/sda2 -- Device or resource busy. This means Linux won't know about any changes you made to /dev/sda2 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
 
  
 It is repeated over and over again.
 
  
This is during the installation of Karmic, and I have tried it in various possible ways, i.e., first by manually assigning the partitions, then even by letting the setup do it for me. 
 
  
 My specifications were:
 
  
 swap  2833mbs
 /           10288mbs
 /home  10000mbs
 fat32    20000mbs
 
  
 have been running on live cds ever since.
 
  
 Please help.

---

### Post by khelben1979 on 2010-03-08
It can be that the Linux kernel don't like your hardware. Have you tried installing an older version of Ubuntu?

Also, if it's a hardware problem, it could be that your harddrive has been damaged in some way and that [SpinRite]("http://en.wikipedia.org/wiki/Spinrite") would be able to fix it for you, but now I'm just guessing. Is it a laptop? Because then harddrives have a tendency to get damaged faster.

---

### Post by Pratik Ali on 2010-03-09
I retried it. This time, i gave up dreams of making a fat32 partition (a bird in hand is worth two in bush, eh?). I also made [COLOR=Red]**ext3[COLOR=Black] partitions[/COLOR]**[/COLOR] instead of [COLOR=Red]ext4[COLOR=Black] for / and /home mountpoints. 

[B][COLOR=Red]AND IT WORKED!![COLOR=Black]

[/COLOR][/COLOR][/B][COLOR=Red][COLOR=Black]But i wonder why.... :(

somebody care to explain??
[/COLOR][/COLOR][/COLOR][/COLOR]

---

