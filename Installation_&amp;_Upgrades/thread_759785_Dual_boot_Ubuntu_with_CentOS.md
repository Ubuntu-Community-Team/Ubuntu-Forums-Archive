---
title: "Dual boot Ubuntu with CentOS"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by samus250 on 2008-04-19
So, I am primarily a Windows User, but I have this old computer lying around that I want to make good use of. I have used both, Ubuntu and CentOS before, but to be able to learn more about both of them I want to make the computer a dual boot system between the two.

So, the computer has 2 hdds, the first one is an 80GB one and the second one 40GB, a nice total of 120GB. Now I went on to install CentOS first, and I got stuck when it asks me about the partitions. I believe I have to select manual partitioning, but I don't know what I have to put as the drive's mount point (which I don't even understand what it is) or how or where will the bootloader install. In other words, I have no idea of how to partition the disks.

Can somebody help me? Which do I install first? How do I partition the disk? I want both OSs to be installed in the larger, faster 80GB drive and maybe the 40GB can be shared between the 2 or used as swap between the 2.

Please help me. Thanks a lot!

---

### Post by overdrank on 2008-04-19
> **samus250 said:**
> So, I am primarily a Windows User, but I have this old computer lying around that I want to make good use of. I have used both, Ubuntu and CentOS before, but to be able to learn more about both of them I want to make the computer a dual boot system between the two.

So, the computer has 2 hdds, the first one is an 80GB one and the second one 40GB, a nice total of 120GB. Now I went on to install CentOS first, and I got stuck when it asks me about the partitions. I believe I have to select manual partitioning, but I don't know what I have to put as the drive's mount point (which I don't even understand what it is) or how or where will the bootloader install. In other words, I have no idea of how to partition the disks.

Can somebody help me? Which do I install first? How do I partition the disk? I want both OSs to be installed in the larger, faster 80GB drive and maybe the 40GB can be shared between the 2 or used as swap between the 2.

Please help me. Thanks a lot!

HI and welcome, I have never used CentOS and I am assuming that I would install Ubuntu after. As for Partitioning this link may help
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
It will give you some ideas on the partitioning. And the mount point should be /  . You may look at installing Ubuntu and just using CentOS in a virtual machine with virtual box 
[http://www.virtualbox.org/wiki/VirtualBox](http://www.virtualbox.org/wiki/VirtualBox)

---

### Post by samus250 on 2008-04-19
I'll try that then. I'll first install CentOS completely on the disks, and then see if I can use the guided resize option. I'll post the results then.

---

