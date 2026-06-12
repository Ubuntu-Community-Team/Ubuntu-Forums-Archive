---
title: "How to partition ?"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by Stray Coder on 2008-05-17
Hey guys I'm new to Ubuntu and I need a little help with partitioning. I already have Windows Vista installed on my hard disk and also ( as windows calls it when I'm logged into it) a backup drive(takes only 10 Gb's) . I have about 40 - 60 Gb's left on my hard drive(Hard Drive size is 100 GB's). How would I make Ubuntu install on only 20 GB's of the remaining space ? I do not wish to erase Windows or its backup area on my hard drive.

 Any help would be appreciated, thanks:KS

---

### Post by Mhurst1 on 2008-05-17
Just go through the install process like you normally would for Ubuntu. Then when you get to the partition editor choose manual and set up your swap partition and 20 GB partition for Ubuntu.

---

### Post by NightwishFan on 2008-05-17
Use Vistas built in partitioner. First, Defragment the drive. Then right click my computer -> Manage? -> Disk. Shrink the main partition by as much as you want. (20,000mb is about 20gb) Boot into the Ubuntu live cd, and install with the "use largest continuous free space" option, and you will have a dual boot my friend.

---

### Post by Pumalite on 2008-05-17
If you want a separate /home partition, you can go Manual and use the free space to create 3 'New' partitions:
10 Gb for '/'
1 GB for /swap (/swap=RAM in laptops for hibernation)
The rest for /home
Then press 'Forward'. The installer will do the rest.

---

### Post by housam on 2008-05-17
Remember , before doing any thing backup your data and defrag your HDD 2-3 times . then proceed as described above.

---

### Post by teaker1s on 2008-05-17
I would recommend following this
[http://ubuntuforums.org/showthread.php?t=724817]("http://ubuntuforums.org/showthread.php?t=724817")

---

### Post by Pumalite on 2008-05-17
You can inform yourself with this too:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by teaker1s on 2008-05-17
reason I recommended previous link is vista will not install sp1 with grub on mbr and or bitlocker/tpm module will have issues with grub mbr. You need to chain load vista boot loader to grub

---

