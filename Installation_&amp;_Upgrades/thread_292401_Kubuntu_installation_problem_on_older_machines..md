---
title: "Kubuntu installation problem on older machines."
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by grm on 2006-11-03
I am very frustrated trying to install Xubuntu on two older machines (Celeron with > 256 ram). I can run the Live CD and the applications run reasonably well but my problems start when I try to install to the hard disk. 


I have tried both 6.10 and 6.06 and am now concentrating on 6.06.    
I have checked the MD5sum’s and burned the CD at a relatively slow rate.   
I have used acpi=off and noapic for the boot parameters. 
In every case the system hangs at various places in the install procedure. In one instant using LiveCd install, I got as far as 99% and it failed while removing programs 
  –part of the syslog from that failure is attached:

Using the Alternate CD the process hangs at various places 30% to 88% –the latest attempt failed at “unpacking apt…”. 

Any ideas on how to go about diagnosing or rectifying the problem will be greatly appreciated. 

I should also mention that I have successfully installed Ubuntu, both 6.06 & 6.10, on a slightly newer machine and use it without any of these problems.

Thanks

---

### Post by ReaderRat on 2006-11-03
It would help others to help you if you give us some info about your system....RAM, video, size of HDD, partition info, etc.

---

### Post by aysiu on 2006-11-03
Why not just install Ubuntu first, then, and then add Xubuntu afterwards? ```
sudo aptitude update && sudo aptitude install xubuntu-desktop
```

---

