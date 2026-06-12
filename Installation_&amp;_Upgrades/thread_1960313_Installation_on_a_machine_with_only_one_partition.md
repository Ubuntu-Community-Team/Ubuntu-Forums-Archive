---
title: "Installation on a machine with only one partition"
date: 2012-04-17
forum: Installation &amp; Upgrades
---

### Post by sullafelix13 on 2012-04-17
This doubt might have been answered earlier.
OR 
is already part of the wubi documentation.
I am still posting it to be very clear before I go ahead with the ubuntu install on my machine.

This is the question:
Can I install ubuntu 11.10 using wubi on my XP OS with a single partition?

Why do I ask this?
Well, my laptop has only one partition: c:\
I am not in a position to create any more partitions since my employer policies restrict doing so.

Thanks in advance,
Sulla.

---

### Post by mastablasta on 2012-04-17
> **sullafelix13 said:**
>  
This is the question:
Can I install ubuntu 11.10 using wubi on my XP OS with a single partition?

yes. Wubi install linux in a virtual file inside windows NTFS file system.
> 
Why do I ask this?
Well, my laptop has only one partition: c:\
I am not in a position to create any more partitions since my employer policies restrict doing so.

 
you will need admin rights to install.
also wubi does change the boot loader so a less invasive install would be via virtualbox (you also need admin rights): [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
providing you have enough system resources (min 2 GB RAM, descent CPU, 8 gb free disk space)... virtual box also creates a virtual file for install. no new partition.

---

### Post by oldfred on 2012-04-17
Since it is a company computer you may want to just install to a flash drive if you can boot from a flash drive. Your hardware may not allow it or the company may have turned that off.

Installs to 4GB flash, newer versions require 4.4GB as minimum
HOW TO Avoid Wubi & Install Ubuntu 10.04 on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)
HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

---

### Post by Mark Phelps on 2012-04-17
If it's a company-furnished PC, they may have also imposed policies in the OS that prevent you from installing stuff.  Specifically, using Wubi requires Admin rights to change the Registry.

If your PC has those rights locked-out (a common practice for company-provided PCs), you will not be able to install using Wubi.

Also, you should check to see if installing ANYTHING on that PC is a violation of company policies.  In some cases, such things can get you fired.

---

