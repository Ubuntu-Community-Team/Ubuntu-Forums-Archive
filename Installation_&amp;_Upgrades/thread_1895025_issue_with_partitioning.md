---
title: "issue with partitioning"
date: 2011-12-13
forum: Installation &amp; Upgrades
---

### Post by bradpurvis on 2011-12-13
I tried to install ubuntu 11.10 and the default practitioner wasn't there. I was trying to install via USB disk and it wanted me to set up partitions manually and I'm not sure how to do this. I need to keep my windows partition on the drive.

---

### Post by 73ckn797 on 2011-12-13
> **bradpurvis said:**
> I tried to install ubuntu 11.10 and the default practitioner wasn't there. I was trying to install via USB disk and it wanted me to set up partitions manually and I'm not sure how to do this. I need to keep my windows partition on the drive.
You are saying the default partitioner? Do you mean that you do not have another option to install in any other manner, such as allowing you to manually designate/create the partition? If you can enter the screen that shows the partitions of the hard drive(s) you can resize the Windows partion to create space to install Ubuntu. That is if the drive is only partition as a Windows drive. You could try booting from the Live CD and "Try Ubuntu". There you can use "gparted", the partition editor and create/manipulate the drive before running "Install Ubuntu". Then during to installation you can chose other options presented and designate the new partition for the Ubuntu OS.

---

### Post by fantab on 2011-12-13
> **bradpurvis said:**
> I tried to install ubuntu 11.10 and the default practitioner wasn't there. I was trying to install via USB disk and it wanted me to set up partitions manually and I'm not sure how to do this. I need to keep my windows partition on the drive.

During installation when 'allocating space' you have to choose **SOMETHING ELSE** option to manually designate the installation to the partitions of your choice.

---

### Post by bradpurvis on 2011-12-13
The option for the default practitioner isn't even on there, I have to use the manual one and i'm not sure how. I'll try and get some screenshots up to better show what I mean

---

### Post by bradpurvis on 2011-12-13
[http://i.imgur.com/ZQy3h.png](http://i.imgur.com/ZQy3h.png)

because its in a virtual machine it seems to be working -.-

can anyone point me to a tutorial for the "something else" option so i can add a partition to my actual drive?

---

### Post by fantab on 2011-12-14
> **bradpurvis said:**
> [http://i.imgur.com/ZQy3h.png](http://i.imgur.com/ZQy3h.png)

because its in a virtual machine it seems to be working -.-

can anyone point me to a tutorial for the "something else" option so i can add a partition to my actual drive?

**[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)**

This should get you started. There is plenty more if you care to Google.

---

