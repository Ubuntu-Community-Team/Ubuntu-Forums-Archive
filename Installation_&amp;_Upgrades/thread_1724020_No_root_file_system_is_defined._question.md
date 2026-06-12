---
title: "No root file system is defined. question"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by jquillian on 2011-04-07
When I get to installation step "Allocate drive space" I get this message,
 
"No root file system is defined.
 
Please correct this from the partitioning menu."
 
What is the source of this error and what do I need to do to correct it?
I don't see a partition menu other than a choice of using the whole drive or a partition?
 
 
Below are the choices that I have made.
 
Specify partitions manually (advanced)
Allocate drive space
 
Choice are  device (/dev/sda4)  Type ((ext3) size) Mount Point (no choices offered) Size (42088 mb) used (670 mb)
 
boot looder is sda Windows 7 
 
ext3 42088 MB
 
I am installing Ubuntu 10.1 on a seperate partition. Windows 7 is on another partition.
The machine is an ASUS A52F Laptop
 
I have done this before on two other computers and have never had a problem.

---

### Post by zvacet on 2011-04-07
Under mount point choose / root.You can also format partition as ext4.

---

### Post by Dutch70 on 2011-04-07
Click the drop down box in front of "mountpoint" and select "/"

---

