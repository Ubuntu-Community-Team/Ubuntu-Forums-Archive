---
title: "Kernel upgrade causes video problems"
date: 2011-10-04
forum: Installation &amp; Upgrades
---

### Post by AlistairOxford on 2011-10-04
This relates to a Compaq Evo desktop PC running Lucid.
 
A recent update has upgraded the kernel from 2.6.32-33 to 2.6.32-34.
 
When booting with the new kernel, video problems occur: the mouse pointer persists on screen, and text fails to display.
 
Booting with 2.6.32-33 works absolutely fine.
 
I'm using standard repositories.
 
The workaround (so far) is to edit /boot/grub/menu.lst and change the default to 2: this boots using the third kernel in Grub's list, i.e. 2.6.32-33, skipping 2.6.32-34 and its associated recovery mode.
 
So the questions are:
 
* Is this an error with graphics drivers in the updated kernel?
 
* How would I update the drivers in the new kernel?
 
Many thanks
 
Alistair, in Oxford, England.

---

### Post by roscheer on 2011-10-14
I am having the same problem on the same computer model. I'm also working around the problem by booting the older kernel.

---

### Post by collisionystm on 2011-10-14
> **AlistairOxford said:**
> This relates to a Compaq Evo desktop PC running Lucid.
 
A recent update has upgraded the kernel from 2.6.32-33 to 2.6.32-34.
 
When booting with the new kernel, video problems occur: the mouse pointer persists on screen, and text fails to display.
 
Booting with 2.6.32-33 works absolutely fine.
 
I'm using standard repositories.
 
The workaround (so far) is to edit /boot/grub/menu.lst and change the default to 2: this boots using the third kernel in Grub's list, i.e. 2.6.32-33, skipping 2.6.32-34 and its associated recovery mode.
 
So the questions are:
 
* Is this an error with graphics drivers in the updated kernel?
 
* How would I update the drivers in the new kernel?
 
Many thanks
 
Alistair, in Oxford, England.

It seems like everyone but INTEL graphics users are having problems.

---

### Post by roscheer on 2011-11-23
The problem continues after the automatic update to kernel 2.6.32-35. 
 
Is there any chance that someone will ever take a look at this? Is there a process for end users to file a bug?

---

### Post by fantab on 2011-11-23
To Check - Boot into the Old, known to work, KERNEL and see if there are any problems with graphics. It it works as before then, use the Working Kernel.

I suggest this to ensure it is actually the kernel issue and not the issue of having to reload the graphic drivers. 

Yes you can file a BUG with [**Launchpad**]("https://bugs.launchpad.net/"). [Before you report the bug ensure that it has not been reported first... if not then follow the necessary instructions to report the bug].

---

### Post by raja.genupula on 2011-11-23
some times kernel upgrades will cause for this type of things , so boot into recovery mode and failsafex mode and then try to install your graphics drivers . 

I hope its gonna solve your issue.

---

