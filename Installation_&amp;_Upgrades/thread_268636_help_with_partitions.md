---
title: "help with partitions"
date: 2006-09-30
forum: Installation &amp; Upgrades
---

### Post by cmaranhao on 2006-09-30
hi, i already used linux (a friend of mine made the installation for me), but i formated the pc and now i regret it big time.. and i don't have my friend to instal it this time for me!

so, i am trying to instal linux by myself but i am having some problems with the partitioning.. my version of linux is Ubuntu 6.06 LTS

ok, onto business, i hope you guys can help me..

i have 3 hard drives...one with 17Gb, other with 80Gb and another with 200Gb.

>i want to split the 80Gb in three partitions so:

in the first partition, 12Gb will be enough, i want to instal linux.
in the second partition, 12Gb will be enough, i want to instal windows XP so that i can have dualboot (i need to work with a certain program that only runs in windows!)
in the third partition, i want to have it for saving files.

>in the 17Gb hard drive i want to spit in two.. one partition for swap, the other for amule..so, will 1024mb be enough for swap?

>i don't want to mess up with the 200Gb hard drive, i have data there that i don't want to loose. like i said, i already used linux so this drive is ready to use with it because it was not formatted to use with windows.. it has 1024mb of space saved for the swap, can i delete these 1024 mb (i prefer using the 17Gb for swap) and keep the rest of the data?remember, i need that data so, i need to be sure if i delete the swap, i will not delete all the data of that hard drive!

i really need a detailed description on how to do this, i already tried different ways to install it but, after selecting the partitions, it always says:"no root file system"

i need help on how to make the partitions and what options should i choose in each case.. hope someone can help me, i really want linux again.

---

### Post by Psquared on 2006-09-30
That's pretty complicated for someone new to Linux. I've been using different versions of Linux for 2 years now and I still need help with partitioning.

What I would suggest is using the search function on this forum and find a topic that you can read that will help you. You can also do a google using something like

"multiple boot, multiple drives in linux" -- Google

here, just search for "partitioning multiple drives for multiple boot."

you should be able to find something to help you just by doing this and reading carefully. If not, keep asking the question and someone will come along and help you.

Sorry I couldn't be of more help.

---

### Post by cmaranhao on 2006-09-30
i am reading some documents on the internet but i don't think i can do it alone :(

---

### Post by missmoondog on 2006-09-30
what are you using for the partitioning tool? frankly, i think the partitioner on the ubuntu cd stinks. 
whatever you do, you must install winblows first. 

amount of swap is determined by that amount of physical ram you have. usually 1 1/2 - 2 times the amount.

---

### Post by cmaranhao on 2006-09-30
its the partitioner that comes with the cd

i am trying for almost 4hours in a row and i just can't do it

---

### Post by tagra123 on 2006-09-30
> **cmaranhao said:**
> hi, i already used linux (a friend of mine made the installation for me), but i formated the pc and now i regret it big time.. and i don't have my friend to instal it this time for me!

so, i am trying to instal linux by myself but i am having some problems with the partitioning.. my version of linux is Ubuntu 6.06 LTS

ok, onto business, i hope you guys can help me..

i have 3 hard drives...one with 17Gb, other with 80Gb and another with 200Gb.

>i want to split the 80Gb in three partitions so:

in the first partition, 12Gb will be enough, i want to instal linux.
in the second partition, 12Gb will be enough, i want to instal windows XP so that i can have dualboot (i need to work with a certain program that only runs in windows!)
in the third partition, i want to have it for saving files.

>in the 17Gb hard drive i want to spit in two.. one partition for swap, the other for amule..so, will 1024mb be enough for swap?

>i don't want to mess up with the 200Gb hard drive, i have data there that i don't want to loose. like i said, i already used linux so this drive is ready to use with it because it was not formatted to use with windows.. it has 1024mb of space saved for the swap, can i delete these 1024 mb (i prefer using the 17Gb for swap) and keep the rest of the data?remember, i need that data so, i need to be sure if i delete the swap, i will not delete all the data of that hard drive!

i really need a detailed description on how to do this, i already tried different ways to install it but, after selecting the partitions, it always says:"no root file system"

i need help on how to make the partitions and what options should i choose in each case.. hope someone can help me, i really want linux again.


First to be totally safe unplug the ide cable and the power cable from the 200GB drive in your computer.



Now you know that that dat is not going to be touched..

Boot with the live cd.

When it open choose gparted.

The 80GB harddrive first (Assume its hda)

Delete all the partitions using gparted ( I will use slightly different partions size to avoid confusion.

Create a new partition for ntfs with 13 GB
Create a new partition for ext3 (ubuntu root as /) with 11 GB 
Now I'd create a separate home partition too so:
Create a new partition for ext3 (ubuntu home  as /home) with 10 GB or more
Create a new partition fo fat (to share with windows and ubuntu) balance of drive.

Apply your changes.

Now select the second and give it 512MB ot whatever partion size you want for swap and any other partitions you want to be added can be added now.

Apply your changes.

Put in the XP CD and install it to hda1 (Drice C:) and dont let it partition the harddrive for you.

 When windows install is complete

Put in the ubuntu cd and install .Skip the create partitions step and select then select your existing partitions. When you get to the selecting partions stage choose manual and 
 11GB partition is root 
 10GB partition is home   and so on.

This should at least get you pointed in the right direction.
 root goes to root and home goes to home, etc...


And remember you can always automount existing later by edition the /etc/fstab file.

For additional help google for parted or gparted. There's all kinds of how tos already on the internet.

---

