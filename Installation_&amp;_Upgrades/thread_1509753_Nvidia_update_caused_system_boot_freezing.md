---
title: "Nvidia update caused system boot freezing"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by fallenshadow on 2010-06-14
I had Ubuntu working perfectly until I installed updates for the proprietary Nvidia drivers.

Now Ubuntu freezes at the Ubuntu loading screen. Im using Ubuntu 10.04 64bit.

I used to know how to access the terminal at bootup but I no longer remember.

How can I get to the terminal? that would be a start!

---

### Post by fallenshadow on 2010-06-15
Bump!!

---

### Post by Xgen on 2010-06-15
I can give you a generic reply as I am using burg instead of grub. If you don't have a recovery menu for your kernel that you are using, then you can temporarily edit your startup kernel...probably pressing "e" on the highlighted kernel. At the line that says "ro" near the end, remove the rest of the line and add "single" after ro. Save and start the kernel.

---

### Post by fallenshadow on 2010-06-15
I think I read from somewhere that I have to hold shift to get the recovery menu.

Im gonna try the recovery options for a start. If ye are wondering I am posting from an 10.04 live CD.

---

### Post by fallenshadow on 2010-06-15
Ok holding down shift does not bring up the recovery menu.

So what does?  :confused:

---

### Post by fallenshadow on 2010-06-15
Beginning a fresh install... seems like the only way to solve Ubuntu problems.  :mad:

---

