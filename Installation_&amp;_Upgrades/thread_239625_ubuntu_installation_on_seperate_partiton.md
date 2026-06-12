---
title: "ubuntu installation on seperate partiton"
date: 2006-08-19
forum: Installation &amp; Upgrades
---

### Post by happyweb on 2006-08-19
before installing ubuntu 6.06 ,
i started my pc with a bootable cd and ran fdisk command ,after that i deleted one of my extended dos partitions ( D: ) that was 20 GB in space and was completely empty , and then i shutdowned my pc and then restarted it and ran Ubuntu 6.06 and during installation steps when it reached the option to select hard drive space it is showing three options:
1) erase master hard drive etc..... (which i dont wanna do as i want to keep my windows 98 SE intact and untouched which is on my C
2) install in the largest continous free space.
3) make manual partition..

Now i selected the second option
and then it processed the step and then is showed me
that partition #3 will be formatted
and partition #7 will be used for swap purpose..

and then i got confused and aborted the installation

now was this second option correct and would this step had
installed ubuntu in D: (that was previously one of my partitions)

or do i have to follow some other steps in order to install ubuntu in the unallocated space (this unallocated space has been created when i deleted D: partition using fdisk)

---

### Post by ajgreeny on 2006-08-19
Difficult to say without knowing exactly what the sizes of all partitions on your disk are.  Do you just have one at present for windows or are there others on the disk?  Do you only have one disk?  If you run ubuntu as the live CD and use gparted to check what is on your disk at the moment it will be easier to help you further, but I can't quite work out why you were given partitions numbers 3 and 7.

I think using the largest continuous free space will be the best option but better to check first.

---

