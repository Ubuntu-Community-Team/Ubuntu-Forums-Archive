---
title: "Can't login to windows 10 after ubuntu installation"
date: 2015-11-24
forum: Installation &amp; Upgrades
---

### Post by venk2 on 2015-11-24
Hi 

i am new to ubuntu and linux. i have installed ubuntu from live cd on windows 10 machine. now i cannot login to windows . Please find the boot summary in the below link.

Please help

[http://paste.ubuntu.com/13498789/](http://paste.ubuntu.com/13498789/)


Thanks
Venk

---

### Post by yancek on 2015-11-24
Your problem is that you selected to install Grub code to sda1 which is a windows partitions, your system partition.  This has overwritten the windows boot files for windows 10.    I saw a post here yesterday from someone who had done the same thing with the same result.  You may need the windows installation medium for this to repair this.  Not sure what else you could do but I'm sure others who are more familiar with windows will have suggestions.

---

