---
title: "Partitioning Problems (i think...)"
date: 2008-07-07
forum: Installation &amp; Upgrades
---

### Post by poisonidea on 2008-07-07
Hi All,

I know there are a few tech heads on here so just wondered if anyone could help...

Ok, so i'm trying to install Ubuntu on a pc I got from work. I managed to install it fine 1st time on saturday and it worked fine. Turned the pc on on sunday and Ubuntu booted up fine. I then tried to install Amrok (music software) and it crashed. Had to reset but it wouldn't boot up the ubuntu OS and kept trying to boot from the cd even though i've set it to boot from harddrive in the bios. So, i'll just reinstall i thought, booted from the ubuntu cd but when it got to the disk partitioning bit i get the following error message:

**"The attempt to mount a file system with type ext3 in SCSI1 (0,0,0), partition #1 (sda) at / failed. You may resume partitioning from the partitioning menu."**

Tried to play around with the settings a bit but couldn't get it to work so thought i'd reformat the HD and start from scratch. So I used a program called Tarik's boot and nuke or something to format and get rid of the partitions. This took about 5 hours. So this morning tried to reinstall on the clear harddrive and get the same message! grrr! I'm not trying to do a duel boot with windows or anything.

Any idea's would be much appreciated as I don't want another 3am bed time tonight! 

Thanks

Chris

---

### Post by meindian523 on 2008-07-07
Ok,if you have a clean HDD,unless you want extra partitions at /home,etc,just use the Use Entire Disk option in the partitioning.Let the installer do the work!

---

### Post by poisonidea on 2008-07-07
Hey, thanks for the reply.

Thats what I have been doing, it gets to 5% in the partitioning/install then I get the error message. It's an 80gb HD but in the partition manager screen thing it says it's only 13gb, maybe this is a symptom...?

---

### Post by meindian523 on 2008-07-07
Hmm,could you post ```
sudo fdisk -l
``` from Applications>>Accessories>>Terminal?

---

### Post by poisonidea on 2008-07-07
I'll try that, what am I looking for? I'm not at home right now so wont be able to do it till this evening.

---

### Post by meindian523 on 2008-07-07
fdisk -l will List all partitions on the Disk.You say that the partition manager says that only 13 GB is available,so probably the rest is already occupied by some or other partition.Since you don't need a dual boot,if any partitions ARE shown up by sudo fdisk -l,then we just need to delete them and proceed.Otherwise,if the disk is really clean of all partitions,we may have to go graphical.

---

