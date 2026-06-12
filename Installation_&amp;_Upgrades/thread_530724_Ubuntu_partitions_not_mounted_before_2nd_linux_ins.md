---
title: "Ubuntu partitions not mounted before 2nd linux install.Ubuntu lost?"
date: 2007-08-20
forum: Installation &amp; Upgrades
---

### Post by Stan_1936 on 2007-08-20
Hello, I have just switched over to Ubuntu but also installed a 2nd operating System from Linux.  It was Sam Linux and I have got no option to select Ubuntu at the system start.  I did some searching and find it maybe caused by a LILO software package being installed to the MBR.  Did this happen because I did not mount the Ubuntu partitions before installing the 2nd operating system?  I set separate Ubuntu partitions for /home, / and swap and then just casually installed the other system (with its own /home and /) not knowing about such a thing called mounting.  Will my Ubuntu install be wiped out?

If yes, then I would like to reformat and install them again.  How would I go about mounting Ubuntu befoer installing the 2nd operating system?

If no, then how do I go about mounting Ubuntu and the 2nd operating system now.i.e. after having installed the 2nd operating system?

Advice from greater minds would definitely help me as I am brand new to Linux and want Ubuntu regardless of what other operating system I have installed on the hard disk.

---

### Post by Pumalite on 2007-08-20
Sam Linux probably has a boot loader that doesn't recognize Ubuntu. It overwrote the MBR. Just re-install Grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Ubuntu will again recognize everything in your system, including Sam Linux.

---

### Post by Stan_1936 on 2007-08-20
Thank your for the reply.  What about the mounting?  How could I properly mount the two systems?

---

### Post by Pumalite on 2007-08-20
I don't know about Sam Linux, but from Ubuntu, with Nautilus you mount everything with a double click. Something tells me though that's not the question you wanted to ask me. You don't need to mount anything to do what I advised you, just follow the guidelines I gave you.

---

### Post by Stan_1936 on 2007-08-20
Thanks, I'll give those GRUB instructions a try.

One LAST question regarding the mounts, would I be able to use it to mount even SamLinux's partitions?

Thanks for the assistance.  It helps.

---

