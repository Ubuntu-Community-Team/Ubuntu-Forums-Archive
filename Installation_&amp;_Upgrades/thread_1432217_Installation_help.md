---
title: "Installation help"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by killachandra on 2010-03-17
Hi. I am new to ubuntu and really liked it via Wubi. but now i want to install it in a seperate partition. 
I have a 500GB hard disk
C:\ = 100 GB **Windows 7**
D:\ = 300 GB **Softwares, files, data**
E:\ =  50 GB **empty and i want to install ubuntu 9.10 here**
F:\ =  15 GB **Recovery partion created by dell when shipped**
 
Now i want to install ubuntu in E:\ but when i run the cd and choose a partition i get a 100 gb partition which i suppose is c:\ and the other is 376 or sumthing which i guess is the rest of the drives. why is it not recognizing the partitions and showing them as a whole. wat do i do to install it in e:\.
Please advice.

---

### Post by tom4everitt on 2010-03-17
Linux names the partitions differently: 

If they're all on the same hard drive, C: becomes /dev/sda1, D: becomes /dev/sda2 etc. 

If say E: is on a different hard drive, that partition will probably become /dev/sdb1.

Ubuntu should recognize all your partitions though, don't go ahead and install before it makes sense (risk is you overwrite your windows, as you mentioned). 

Did you choose manual setup?

---

### Post by killachandra on 2010-03-17
Thanks for the info bro. I will try that again. by the way its a single harddrive. Also even if names it differently atleast it should show it as 50Gb but all the other partitions other than c:\ (the one with windows) are showing clubbed as one partion of 376GB. i wonder why that is? and how can i  get through from this. any more ideas?

---

### Post by tom4everitt on 2010-03-17
Which file systems are your partitions? NTFS and FAT32 are the most common windows file systems. If you use some other file system that could possibly explain ubuntu not recognizing them (although it sounds unlikely). 
What happens if you choose boot from live cd, and then go to: System->Administration->gparted. Does it find your partitions?


Your other option is to create two NTFS partitions on the 50 gb that you have free (in windows). One 49 gb for your ubuntu, and one 1 gb for swap.

Then choose manual install in the ubuntu installer.
For the 49 gb choose: file system: ext4, use as: /, and check the format box.
For the 1 gb choose: use as: swap, and check the format box.

Given that ubuntu discovers your two partitions this should be rather safe, although perhaps not as safe as if it had discovered all your partitions. Do a backup of everything important!

---

### Post by killachandra on 2010-03-17
[[IMG]http://img151.imageshack.us/img151/7551/screenshotum.png[/IMG]]("http://img151.imageshack.us/i/screenshotum.png/")

This is wat i mean is happening. the last partition is actually d:\ and e:\ in windows thats 300 + 50 gb and its NTFS. but its getting clubbed and i dont no why its not accessible either. Pls advice

---

### Post by tom4everitt on 2010-03-17
Okay, so your recovey partition is obviously /dev/sda1. And your windows is /dev/sda3, that makes sense. 

And it says unknown about the rest (which includes your data partition and your empty space for ubuntu). That explains why it chunks it. 

Further suggestions:
- install ntfsprogs on your live cd (type: sudo apt-get install ntfsprogs in a terminal, applications->accessories->terminal) and check again (ntfsprogs adds further ntfs support).
- try formatting your empty space as I said above, and check if it finds it. it might help.
- Start a new thread with the title "ubuntu confused by ntfs partition" or similar, it might attract more experts :)

---

