---
title: "Wubi hangs in Window 7 Home Edition 64bit"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by gtdarthyoda on 2009-11-26
Wubi hangs in Window 7 Home Edition 64bit when it gets to Creating the virtual disks
I really would like to install Ubuntu but its not going so well

I'm trying to install 9.10 64bit
32bit hung up at the same spot

---

### Post by lemming465 on 2009-11-30
Have you tried running *chhdsk /f* and rebooting before doing the WUBI install?  Windows will boot dirty partitions, but Linux won't mount & write to them.

---

### Post by gtdarthyoda on 2009-11-30
no problems and tried to install with still no luck
btw it did add it to the OS choices
but when it loads it can't find the root drive or something like that

---

### Post by Mark Phelps on 2009-12-01
If this is a clean install of Win7 (meaning, no other OS on the machine when it was installed), you're probably yet another victim of the Win7-with-Ubuntu-9.10-in-Wubi problem.

LOTS of folks have encountered pretty much the same problem -- and no one has published a solution yet.

My guess is that the new special boot partition scheme used with Win7 is confusing the loader for the installed Ubuntu in Wubi.

But as I've said, no one has published a solution to this yet.

---

### Post by lemming465 on 2009-12-01
I wonder if this [compatibility mode hack]("http://www.clububuntu.com/2009/01/how-to-solve-windows-7-and-ubuntu-810.html") to run wubi.exe like a vista app would help?

---

### Post by gtdarthyoda on 2009-12-01
trying now... is it maybe not working because its a partition of my main drive?

Edit: You got it!!! I tried compatibility mode with winxp not vista... vista worked thx

Edit: nvm it finished the install but still won't boot gonna try to reformat the partition and then reinstall
if it give me the same error I'll post it

---

### Post by gtdarthyoda on 2009-12-02
sorry no luck

it finished the installation then I fired it up and got this message
No root file system is defined. Please correct this from the partitioning menu.

---

