---
title: "Virtual Box installation"
date: 2008-09-20
forum: Installation &amp; Upgrades
---

### Post by nuke_fluke on 2008-09-20
I installed virtualbox-ose just for the heck of seeing what it was...

I got the following message in the teminal..
 * Starting VirtualBox host networking...                                [ OK ] 
 * Starting VirtualBox kernel module vboxdrv                                    
 * No suitable module for running kernel found.

But still the Virtual-Box somewhat seemed to work...
But after creating a 5GB virtual drive for Windows XP, when I started off to install it..I got the error message that the kernel module is not available and I can't go further with the installation...

Now it seems that the 5GB virtual drive I created was not deleted even after I deleted it in the options and removed VirtualBox...
coz some 5 GB of free space fails to show up on my comp..

How can I regain my missing 5 GB..??

Thanks

---

### Post by howefield on 2008-09-20
go to Applications > Accessories > Terminal and type

sudo rm ~/Virtualbox/name of vdi


where name of vdi file is the name of your Virtualbox XP file.

---

