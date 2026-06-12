---
title: "Dual Boot Ubuntu &amp; Windows 7"
date: 2010-09-14
forum: Installation &amp; Upgrades
---

### Post by efren386 on 2010-09-14
I format my laptop with windows 7 then after that I install the other half partation with ubuntu

partation A: Windows 7

partation b: Ubuntu

we all now that boot.ini been back up and the main now is grub right?

so we all know that most microsoft OS attraction with virus.

what if windows 7 will crush then, then format windows 7 

then format partation a: 

Can we still load ubuntu after new partation?

if this a problem how to solve, thanks alot

---

### Post by grahammechanical on 2010-09-14
It is a while since I used the format command in MS Dos. I seem to remember that you can tell the program which drives or partitions to format. Partition manager in Ubuntu lets you do the same. When you install you can mark the Ubuntu partition to be formatted but do not mark the windows partition to be formatted otherwise you will loose you windows OS.

By the way, Do you know about putting  /home on a separate partition? Create a 20GB partition for the Ubuntu OS and create a third partition for you data. Give it the mount point of /home. Then whenever you re-install Ubuntu you put the OS on the partition mounted as /  which can be formatted but you do not mark the /home partition to be formatted otherwise you will lose all your data. Then when Ubuntu installs it will take all your settings that are store on /home and adjust itself accordingly. You will not need to put in your email information and stuff.

I have just thought of something! Re-installing windows may (I am not sure but I am almost certain) wipe out the GRUB boot loader. There is a way to re-install GRUB. I am not sure how to do it. There is also a way to get rid of GRUB and re-install the MBR - Master Boot Record which will only see a windows OS. Should you ever need to give the Ubuntu partitions back to windows - scary thought!

Regards.

---

### Post by efren386 on 2010-09-15
thanks alot, now it clear to me

---

