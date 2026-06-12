---
title: "Boot Up Question"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by swhitman6 on 2007-11-03
I just installed Ubuntu on a secondary internal hard drive.  My primary drive is loaded with Windows XP.  I thought the installation would auto-sense XP but this may not work because I have it on a separate HD.  What do I do to boot from Ubuntu on the second drive?

Thank you,

Shawn

---

### Post by lunamystry on 2007-11-03
I don't know how its done but I think its possible. When I install Ubuntu it always "senses" any other operating system I may have and I also have two hard-drives. Did you install Ubuntu while both hard drives were connected?

---

### Post by Pumalite on 2007-11-03
I doubt it. It seems that Grub got installed to it's own partition. Changing boot order in BIOS should get you Grub.

---

### Post by swhitman6 on 2007-11-03
When I go to the system boot menu my secondary drive is not given as a bootable drive.  I can see it in the "drives" list but not in the boot sequence list.  When I installed Ubuntu it saw both drives and I selected the secondary.  I can no longer see the drive I installed Ubuntu on when loaded up in XP.  Do I need to install something on the main drive to have it go and look for other OSs on the secondary drive?

---

### Post by Pumalite on 2007-11-03
Did you install with both drives connected? Did you install Grub to the MBR?

---

### Post by rollerdiscoman on 2007-11-03
try snooping around your /boot/grub/menu.lst file (you must be root), and search for anything that might help you to boot up.

usually under the
"#####END DEFAULT OPTIONS#####"
is where the boot-up configurations are.

---

### Post by lunamystry on 2007-11-04
I need to know how to change my default grub. 

I have two hard drives, I installed gutsy and loving it and then I found out I could only make a repo DVD using feisty. I then installed feisty without thinking twice and now I don't need feisty anymore and i don't want to use the hard drive in which it is installed. 

How do I change my grub to be the gutsy one rather than the feisty one?

---

### Post by Pumalite on 2007-11-04
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

