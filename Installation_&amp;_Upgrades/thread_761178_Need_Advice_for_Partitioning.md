---
title: "Need Advice for Partitioning"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by rey1321 on 2008-04-20
[SIZE="2"][SIZE="3"]Hi guys!
I'm  just so excited and waiting for my new baby (hardy 8.04), and wants to install it in a  fresh, clean and well organized 160GB, since this baby will be a LTS, I want to have this drive well partitioned, right now I'm running Feisty using the default (the whole drive as a root,swap,and extended), I read some article about Unix Disk partition scheme and it recommended this:

 /boot
 /
 /home
 /usr
 swap

 I'm gonna use this just for home computer, nothing heavy, just internet, gimp,dvd burning, etc, etc
also this gonna be a solo OS, no Window$ or another linux distro 

so my questions are: 
 How many GB will you recommend for each partition?
 If I'll have just one OS, why do I need  /boot, because I can flag / and boot from it.
 Do I really need /usr? , it seems that is very important in the tree hierarchy 

I have 1Gb of ram.

Thanks for your advice.[/SIZE][/SIZE]

---

### Post by Spartan.II.117 on 2008-04-20
my personal recommendation is:
/
/home
swap
giving about 10 gigs as /, 1-2 gigs as swap and the rest as /home.i personally use a setup very simular to this. the only difference being a separate drive with a backup of my important data. good luck!

---

### Post by MrFSL on 2008-04-20
Obviously your amount of swap depends highly on how much ram you have. Personally I think 1024 MB or 1 GB will do in most if not all home user applications.

My setups look like this:

1 GB = swap
20GB = /  (more for gaming)
All the rest = /home

---

### Post by erginemr on 2008-04-20
+1 to the above setups and to emphasize there is no need for **/boot** or **/usr**.

---

### Post by shaggy999 on 2008-04-21
If it were me, I'd do it this way:

/boot 256 MB*
encrypted partition - all the rest
LVM - on entire encrypted partition
/ - 10 GB on encrypted partition
swap - 1 GB on encrypted partition
/home - all the rest on encrypted partition

You need the alternate CD for that, though :)

* NOTE: /boot is required to be separate and on an unencrypted partition in order for the system to bootstrap itself.

---

