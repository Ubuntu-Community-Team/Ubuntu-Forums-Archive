---
title: "hardy haron double boot with xp on existing partition"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by sarin pedro on 2008-04-30
Hi

i was wandering if it is possible to install 8.04 with this configuration: I have 2 hard disks, one of 80G with XP installed on it (master), the other one for data - 250G (slave). when i partitioned the 250G i left a 25G partition clean and eampty. i would like to install on it Ubuntu 8.04. should i use grab to enable me to boot from which one i choose? will 8.04 installed on the slave have a problam with that? would i be able to reach all the data stored on both disks from both systems?

i would much apritiate a reaplly

thank you for your reply
sarin

---

### Post by dabang on 2008-04-30
Should be no problem. If you let the Ubuntu installer create two partitions (one swap and one for "/") on your unpartitioned space everything should be OK.
Yes, grub can - and if you use the desktop CD - will be installed to the MBR. You will be able to choose which OS you'd like to boot.
You should be able to see all data on NTFS or FAT32 partitions when running Ubuntu, but Windows cannot read Linux partitions. I know there are some tools for this purpose, but never tried them...

---

### Post by bulldog on 2008-04-30
The install is no problem,ubuntu can be installed on a slave device.
You shouldn't  have a problem to read and write to your NTFS partitions fom ubuntu,to read your ext3 partition [/home] from windows is possible but you have to install the  [http://www.fs-driver.org/](http://www.fs-driver.org/)  in windows.
GRUB will be installed and and it will add windows to your menu.list so you can choose which OS you want to boot [default will be ubuntu,but you can change this if you want]

---

### Post by sarin pedro on 2008-05-01
Hi, it is I

thank you both for your reply. it does seem like a nice people's community. 
so, should i now give it a try or wait for next week when i get my external drive and backup my material before? is it safe enough ?

thanks again
sarin

---

