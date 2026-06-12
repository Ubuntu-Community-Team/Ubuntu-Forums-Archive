---
title: "Problem installing Ubuntu 7.04 as guest OS on VMWare Server"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by manish_date on 2007-09-28
Hi 

Got the Ubuntu 7.04 CD yesterday, trying hard to get it installed on the VMWare as guest OS since list night with no luck. Please help the details are as follows :

Ubuntu Version : 7.04
VMWare Version : Version 1.0.4 Build 56528
Host OS : MS Windows XP SP 2
Problem Description : When I start the virtual Machine and it boots perfectly from the CD, displays the initial screen, when I hit enter for the option 'Start or Install Ubuntu'. The virtual machine hangs forever, the CD Drive and the HDD light is burning in the ful go as if something is working there but nothing happens.

Virtual Machine Configuration : 
Gust OS : Linux
Version : Ubuntu
No. of processors : 1 (I have core2Duo)
HDD : 30GB
RAM : 1GB
Networking : NAT

Please help if you know any leads in this problem.

Thanks & Regards 

Manish

---

### Post by charles.g.moore on 2007-09-28
I don't know whats up it seems like all is ok.  I would try d-loading a 7.04 image (just do a google search for: vmware ubuntu 7.04 image) and then point your VM HDD at the image and fire it up...

---

### Post by Shazaam on 2007-09-28
manish_date...
Your memory (1gb) is that what you have installed on your host machine or is it the amount of memory reserved for your Ubuntu vmx? My rule of thumb is to allocate no more than half of your physical memory to the vmx.

---

### Post by manish_date on 2007-09-29
Charles, I was trying to avoid 700 MB download but its OK. I think I dont have much options.

Shazaam, I have a total of 4GB RAM out of which I am assigning 1 GB to the virtual machine.

---

