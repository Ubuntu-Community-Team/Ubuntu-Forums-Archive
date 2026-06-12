---
title: "Create a /boot partition, is it a good ideia?"
date: 2005-02-10
forum: Installation &amp; Upgrades
---

### Post by Ruediger on 2005-02-10
I remember reading somewhere (I couldn't find a link, but it was probably in these forums) that it is a good a ideia to create a small (16MB-32MB) boot partition (/boot). What are the advanteges of doing it? 

I got a new HD so I'll install Ubuntu 4.10 and Windows XP from scratch.

---

### Post by darkcoder on 2005-02-15
[QUOTE=Ruediger]I remember reading somewhere (I couldn't find a link, but it was probably in these forums) that it is a good a ideia to create a small (16MB-32MB) boot partition (/boot). What are the advanteges of doing it? 

I got a new HD so I'll install Ubuntu 4.10 and Windows XP from scratch.[/QUOTE]

The only advantage I know about the separate boot partition is that you can add the option of noauto thus protecting its data a little bit.  But the problem with ubuntu is that if you do that, then the system will not be able to update the menu.lst entries, and save the kernel image to the boot partion in case of a kernel update because the partion will not be mounted.

---

### Post by darkcoder on 2005-02-15
A good idea?  In Ubuntu, No.

---

