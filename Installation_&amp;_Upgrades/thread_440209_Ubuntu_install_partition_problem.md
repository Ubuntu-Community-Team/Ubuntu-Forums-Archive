---
title: "Ubuntu install partition problem"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by prem1er on 2007-05-11
First time installing Ubuntu 7.  I have a 28g ext3 partition already created on my hard drive where I intend to install Ubuntu.  When I get to the part of the install labeled 'prepare disk space' I run into a problem.  If I use the 'Guided' selection, the installer is ignoring the 28g partition I have created and treating the drive as one partition (no help to me because I don't want to repartition the entire drive).  If I use the 'manual' option, the installer is recognizing my partition, but when I select to use it, I get the message 'No root fiel system defined.  Please correct this from the partitioning menu.'  Any help?

---

### Post by m@ra on 2007-05-11
Hi,

If you get no root file system specied error that is not a reason yet to worry..
On phase where you are choosing the file system to be installed define also that it will root file system ("/") Then it will let you go forward.

-m@ra

---

### Post by prem1er on 2007-05-11
Yes, thanks for the reply.  I'm just not quite sure where to do this.  My mount point is /media/sda3, do I need to change this?

---

### Post by prem1er on 2007-05-11
> **prem1er said:**
> Yes, thanks for the reply.  I'm just not quite sure where to do this.  My mount point is /media/sda3, do I need to change this?

...Problem solved.  But now I'm getting the error ' File system doesn't have expected sizes for Windows to like it.'  It gives me two options 'ignore' or 'cancel'.

---

### Post by eccofire on 2007-05-11
***"...Problem solved. But now I'm getting the error ' File system doesn't have expected sizes for Windows to like it.' It gives me two options 'ignore' or 'cancel'."***

How do you solved the error about *"System root file on the partitioning menu"? *

_Where/what's would be the syntax that i should aply?_

I've two partitions C:\ and D:\
D:\ would be 4 UBUNTU.  

Thanks :)

---

### Post by eccofire on 2007-05-11
Dahhhhh!
Problem solved. 

Build a partition disk tou mount Ubuntu then select a disk space avaiable to Swap. That's it.

---

### Post by Lightmywifire on 2007-06-11
I'm not too sure of your solution. Anyone else have any luck with this problem?

---

### Post by richer.pierre on 2007-06-14
Same problem and same interest in the solution but I don't understand the method proposed.
Do I have do delete and recreate my existing ext3 partition?

---

### Post by richer.pierre on 2007-06-15
Success!
I deleted my ext3 partition and recreated it.
It now comes in already marked. You only have to then highlight your swap partition and it lets you go through!

---

