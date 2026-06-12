---
title: "Installation  partition problems Ubuntu 6.10"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by saitoh on 2006-11-01
I am new to Linux and am trying to install Ubuntu 6.10 on my windows pc. I set aside a 16GB section for the root directory, and 512MB for the swap. When I try to install the GUI displays all my partitions and asks what I want to mount and where. I tried to mount the root "/" file on a logical partition(16GB), and the swap file on a 512MB logical partition. The GUI allowed me to remove the other partitions from the screen, but then gave me issues when I tried to move on to the next step. I then read that you must give all your partitions mount points. So I gave my windows partitions mount points(like "/windows"), unfortunately it is now saying that I must mount a root directory. I was under the impression that applying the "/"(root) symbol to 16GB partition was setting that partition as the root directory. If anyone has any insight I would appreciate it.

I forgot to add that I formatted these using partition magic, and they are ext3 format.

---

### Post by sligh on 2006-11-01
in partition magic select primary partition for the root, 
select logical for swap

---

### Post by g8m on 2006-11-01
I believe there are some issues with assigning root directory to an existing partition, delete the existing partition when possible en recreate. And don't touch the windows partitions, they will be mounted in /media and if not, you can always later on manually add the to /etc/fstab.

---

### Post by saitoh on 2006-11-01
Thank you, that was a big help.

For anyone reading this for info, they were both right. Root needs to be a primary partition and it seems to have problems if the ubuntu installer isn't the one doing the partitioning.

---

