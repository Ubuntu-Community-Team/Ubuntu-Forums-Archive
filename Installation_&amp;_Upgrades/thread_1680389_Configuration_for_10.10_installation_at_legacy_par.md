---
title: "Configuration for 10.10 installation at legacy partition"
date: 2011-02-02
forum: Installation &amp; Upgrades
---

### Post by yrelle on 2011-02-02
Hi all, hopefully some one might help me out of this situation...

I used to have dual boot of Windows XP and Ubuntu 10.04 which encounters some severe problems working extremely slow.... 

Last night I tried install Ubuntu 10.10 with live CD into the existing partition of the previous 10.04. But the 'GRUB Loading Stage 1.5, error 15' appeared. With the help from the following link, still couldn't fix it.

 [http://ubuntuforums.org/showthread.php?p=10421327#post10421327](http://ubuntuforums.org/showthread.php?p=10421327#post10421327)

Unfortunately, I can not get into either of the OS afterwards.....
Now I am trying to reinstall again step by step. Anyhow, I am quite a beginner at non-windows OS, could guess the meaning of each command line rather than understand them well.

===============

1. I deleted the partition /dev/sda8 and added it again in ext4 format with choosing 'Format the partition'
2. Should I set the 'Mount Point' with any options? "/", "/boot", "/home" or any others?
3. How shall I set [I]**Boot loader** -> Device for boot loader installation: 
/dev/sda8[/I]  or[I]
/dev/sda ATA[/I] Hitachi HTS54323 (320.1 GB)

---

### Post by sikander3786 on 2011-02-02
First of all I assume you are doing a proper install and not using Wubi to install Ubuntu inside Windows.

Basically Ubuntu needs 2 partitions for installation. One '/' partition which holds the base install and your home directory. Second Swap partition which works as Virtual Memory.

You can have a separate /home partition if you want to. If you go for a separate /home partition, it would save all your data and in addition, configuration for different software such as Firefox bookmarks and profiles so in case you decide to re-install, you won't lose your settings. All you need to do is to choose your existing /home partition and choose NOT TO FORMAT IT.

/boot is not necessary and even not recommended for beginners. / partition will hold that stuff.

During the installation, you are choosing Manual partitioning and there, you need to define the mount points of your partitions such as /, /home and Swap.

The boot loader needs to go to the MBR of the HDD that you are booting from. In this case, it would be /dev/sda ATA Hitachi....... and NOT /dev/sda8.

---

### Post by yrelle on 2011-02-02
> **sikander3786 said:**
> First of all I assume you are doing a proper install and not using Wubi to install Ubuntu inside Windows.

[COLOR=Blue]*I am not using Wubi, intending dual boot.*[/COLOR]
> 
Basically Ubuntu needs 2 partitions for installation. One '/' partition which holds the base install and your home directory. Second Swap partition which works as Virtual Memory.

You can have a separate /home partition if you want to. If you go for a separate /home partition, it would save all your data and in addition, configuration for different software such as Firefox bookmarks and profiles so in case you decide to re-install, you won't lose your settings. All you need to do is to choose your existing /home partition and choose NOT TO FORMAT IT.

/boot is not necessary and even not recommended for beginners. / partition will hold that stuff.

During the installation, you are choosing Manual partitioning and there, you need to define the mount points of your partitions such as /, /home and Swap. [COLOR=Blue]*Then I'll try 3 partitions respectively at /, /home and /swap*[/COLOR]
> 
The boot loader needs to go to the MBR of the HDD that you are booting from. In this case, it would be /dev/sda ATA Hitachi....... and NOT /dev/sda8.[COLOR=Blue]*I'll select /dev/sda and try again....*[/COLOR]

---

### Post by sikander3786 on 2011-02-02
/ partition needs to be at least 20GB in my opinion.

/home, the better you add, the better you can use. Custom size greater than 4GB.

Swap partition = RAM x 2 or atleast = RAM if you plan to hibernate/suspend.

---

### Post by yrelle on 2011-02-02
Then there is a problem.... in ***Allcate drive space ***window, can I change the size of the partition? I tried to Change the size of partition /dev/sda6 to bigger size (suppose to move some 'free space' to it?), but it did not work then.....

---

### Post by sikander3786 on 2011-02-02
If you are talking about / partition, it can be anything more than 8 GB but my recommendation is 20 GB. Don't take it seriously if you don't plan to install a bunch of software later.

For increasing the size of a partition, you'll need to delete the partition next to it and then create both partitions once again with adjusted sizes.

---

### Post by yrelle on 2011-02-02
Thanks. Now both 10.10 and windows XP work fine....

btw, the support for dual display looks not good. The extended monitor does not work fine even set finshed in ***System-Preference-Monitors***

---

### Post by sikander3786 on 2011-02-02
Glad to know that your installation is working.

For the dual monitor setup, I think you need a new thread in the proper sub-forum for that dual monitor setup as the experts keep roaming those forums ;-)

Happy Ubuntu-ing!

---

