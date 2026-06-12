---
title: "grub error problems"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by mechanicfox on 2008-01-29
Hello  everybody!

I have installed Ubuntu 7.10 on my Pc with the intention for dual booting, first of all with 
Ubuntu installed on the second HDD.....but after 2 days, the machine crashed, the 2nd 
HDD was finished, and I have received an error message on booting"Loading Grub stage 1.5", 
and immediately"Grub error 18", and my machine wasn't able to boot.

I have removed the crashed HDD, I have reinstalled Ubuntu on the 1st HDD, 
but on booting I have received the same message, like the first time "Loading Grub stage 1.5",
 and immediately"Grub error 18", and my machine wasn't able to boot.

Unfortunately,I had many installations with dual booting Win XP with Linux, but with Ubuntu it wasn't 
a lucky experience.

I have tried to repair the Grub both times....without success.

In my mind, Ubuntu remain a good system, but for me, the result is "A BIG HDD CRASHER"!!!!!!!!

Can anybody tell me what it was happened and to suggest me which is the right way to install it again?

I love Ubuntu, and I  want to try again.

Thank You ALL 4 all your replies.

---

### Post by zakaroo on 2008-01-29
Hi - I've dealt with the grub loader a few times.  Question:  What sector did you install the MBR?  On what disk was that sector?  and how did you specify primary/logical configuration of the harddrives (since you had two)?  If you can give me this info, I might be able to point you in a direction.

---

### Post by mechanicfox on 2008-01-30
Hi dear friend,and thank a lot for inquiry to help me.
The config was :HDD1-Mzoft :mbr=hd0, hda1=C, hda2=D......hda5=e, hda6=H, named by Win
                           HDD2-Ubuntu: hdb1=root, hdb2=swap,hdb3=/home
The partitions hda1, and hdb1 was the primary, the HDD set like-1st=master, 2nd=slave
The boot 4 Ubuntu was set on hd0-default.
It seems the configuration was right, but what else could be?
With all my best....mechanicfox

---

### Post by hums07 on 2008-01-30
You've got a grub error
Loading Grub stage 1.5
means Grub is looking for files in /boot/grub/ and any of the files may be corrupt. This is grub error, not kernel or ubuntu error.
Try this solution: [http://users.bigpond.net.au/hermanzone/p15.htm#Grub_loading_stage1.5](http://users.bigpond.net.au/hermanzone/p15.htm#Grub_loading_stage1.5)

If I were you, I would try to reinstall grub with live CD (just in case it works). And I dont think Ubuntu has crashed your harddisk.

---

