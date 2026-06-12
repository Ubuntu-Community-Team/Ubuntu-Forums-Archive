---
title: "install help."
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by schwarza on 2010-06-17
please sirs

i want to install linux only on this machine. no dual boot, just linux.

i am at an option screen on my install related to partition of disks.

i obviously choose use entire disk however

what is (derrrr!!) LVM and encrypted LVM?

regards

---

### Post by lechien73 on 2010-06-17
LVM is the "Logical Volume Manager" - a more flexible way of allocating disk space than conventional partitioning.

Encrypted LVM is, as the name suggests, LVM with encryption :) If you have sensitive data on your disk - or just like privacy, then you may choose to encrypt the LVM.

---

### Post by darkod on 2010-06-17
Hmm..the standard Desktop version of ubuntu doesn't offer LVM. What are you installing?

LVM is Logical Volume Management. In theory, it allows you to resize the partitions later without having to reformat and lose the data on them. It's a nice thing if you manage to use it, you will have to do some reading about it though.

But ubuntu standard install doesn't offer LVM.

---

### Post by viralmeme on 2010-06-17
> **schwarza said:**
> please sirs

i want to install linux only on this machine. no dual boot, just linux.

i am at an option screen on my install related to partition of disks.

i obviously choose use entire disk however

what is (derrrr!!) LVM and encrypted LVM?

regards

Try and install using the following tutorial and report back if you have any difficulties.

[Installing Ubuntu]("http://www.psychocats.net/ubuntu/installing")

---

### Post by schwarza on 2010-06-17
one is installing server version.

regards

---

### Post by schwarza on 2010-06-17
**** BURGERS....

for ease of install i selected use entire disk option (without any LVM)

started to install base system and then i got errors warning of corrupt files.

the machine isn't connected to internet as the harddrive i am installing on has a broken version of windows which i was hoping to wipe off upon install of ubuntu. am i screwed now ?

:(

---

### Post by CharlesA on 2010-06-17
Boot off the CD and run "check for defects" see if it passes. Could have been a bad burn.

---

### Post by schwarza on 2010-06-17
thanks charles

i tried to check disk as you suggested. the integrity test failed.

how do i check the iso ? or MD5 checksum?

---

### Post by schwarza on 2010-06-17
would it download new files if i connect computer via cable to the router?

---

### Post by CharlesA on 2010-06-17
Verify the MD5SUM of the ISO that you downloaded. If that checks out, then try burning it again at a slower speed.

Could be that it was a bad burn.

If the MD5SUM doesn't match, download the ISO again. :)

---

### Post by schwarza on 2010-06-17
i have checked the md5sum using WinMd5Sum [http://www.nullriver.com/products/winmd5sum](http://www.nullriver.com/products/winmd5sum) and the iso has checked out with the check sum from [http://releases.ubuntu.com/10.04/MD5SUMS](http://releases.ubuntu.com/10.04/MD5SUMS)

that i guess would mean a bad burn?

---

### Post by CharlesA on 2010-06-17
Indeed. Give it another shot while burning at something like 4x.

---

### Post by schwarza on 2010-06-17
hello again

it will only let me go to 10x.

all working now. and "i think" installed only

there seems to be no operating system gui just:

servername:~$_

what i need is a computer running linux to use solely as a webserver with one site. is ubuntu server version the best system for this or is there a better/easier way to acheive this?

regards

headache

---

### Post by schwarza on 2010-06-17
bump

---

