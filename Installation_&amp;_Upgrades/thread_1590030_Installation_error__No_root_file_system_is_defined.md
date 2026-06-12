---
title: "Installation error : No root file system is defined"
date: 2010-10-07
forum: Installation &amp; Upgrades
---

### Post by Funebreux on 2010-10-07
Hi,

I was installing Ubuntu on an MSI cx620 laptop via wubi with windows 7. My hard disk is patitioned as such : C:\ (OS) and D:\ (Data). I'm installing onto C:\. The installation itself seems to complete fine, and when wubi prompts, I reboot. However, after choosing Ubuntu on the dual boot screen, the finalization blocks at 271% with the error box : "No root file system is defined". Clicking ok merely make the box reappear, and I have to restart the computer.

Having googled the problem, I vaguely understand that a "\" is involved (sorry, I'm a bit of a noob when it comes to Linux ^^). Could you please offer a little more detail on the procedure ? Thanks !

---

### Post by e79 on 2010-10-07
Compared to Windows where the 'Root' Filesystem is **C:**, Linux has **/** as the root folder. So when prompted to specify the root folder, a 'forward-slash' is required (not a backslash).
 
Here's an example on both OS for the user home directory so maybe it will shed some light for you :
 
Windows way:
**C:\Users\Username\Documents**
 
Linux way:
**/home/user/Documents**
 
Hope this helps

---

### Post by Rubi1200 on 2010-10-07
Which version of Ubuntu did you try installing via Wubi? This information is important because it affects the possible solution that needs to be offered.

Thanks.

---

### Post by Funebreux on 2010-10-08
It's Ubuntu 10.04.

Thanks for explaining that, I get what the problem is now, at least. However I'm still clueless as how to solve it. I discovered I can access the console via grub, I hope that gives me more options ^^.

The main problem is that Wubi *dosen't* prompt me to choose a root directory, and I don't know ow to force it to choose one.

---

