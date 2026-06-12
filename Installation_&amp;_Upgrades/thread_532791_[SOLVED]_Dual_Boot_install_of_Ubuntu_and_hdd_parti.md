---
title: "[SOLVED] Dual Boot install of Ubuntu and hdd partition"
date: 2007-08-23
forum: Installation &amp; Upgrades
---

### Post by abhilash82 on 2007-08-23
Hello,
I have a P4(2.4GHz, 256MB RAM, 40GB) PC at home and have 4 partitions on it each around 10GB. I have Windows XP installed on my 3rd partition and have installed Ubuntu (Feisty Fawn) using Wubi installer in the 4th partition. I have the following clarifications for installing Ubuntu (from live CD) after restructuring my hard disk.

1. When I try to uninstall Ubuntu through Wubi from Add/Remove Programs in Windows XP, I get a dialog box asking me to backup all my existing Ubuntu configurations in .iso format. My doubt is what will this backup cover and will I be able to restore all the apps I downloaded from the net to be restored to my new installation? If so how do I go about doing it?

2. Since each of my partitions are of the size 10GB, I would like to restructure my hdd in such a way that i have 2 partitions of 20GB each. One for Windows XP and other for Ubuntu. Is it possible to restructure my Windows partition without affecting its contents?  If so how do I go about doing it? Or is there any other suitable partition sizes I should follow? Please suggest.

3. I will be installing Ubuntu from the live CD, so should I use the Manual option there for editing the partition?

Thanks
Abhilash

---

### Post by Pumalite on 2007-08-23
I don't know anything about Wubi. You can partition your hard drive using Gparted: 
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) 'Extend' your XP to 20 GB, delete the other 2 10 GB partitions and make one large one of 20 GB. Install with Alternate CD. With that RAM I would advise Xubuntu. You cannot boot a LIVE CD with that RAM.
You need 10 GB for '/'
500MB to 1GB for 'swap'
The rest for /home

[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by abhilash82 on 2007-08-23
Thanks for the info. But will my usage of GParted to change my working Windows Partition affect it? And how do I go about this Wubi thing?

---

### Post by Pumalite on 2007-08-23
Using Gparted should not affect your XP . Read Documentation: [http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
As for Wubi, I'm sorry, somebody else will have to help you with that.

---

### Post by mrfelker on 2007-08-23
I never heard of Wubi either so I can't help you there.  It isn't simple (in fact I've tried it) to create an Ubuntu ISO which has data and config files on it.  But I'm sure you can look through Synaptic for a program to do it.  Sorry don't know the name of the prog at the moment.  Perhaps some kind soul can post it.

---

### Post by Pumalite on 2007-08-23
After you get the iso you can burn using ImgBurn:[http://imgburn.com/](http://imgburn.com/)
Once you install ImgBurn, go to Mode and choose ISO, then BURN. That's all there is to it.

---

### Post by abhilash82 on 2007-08-24
Thanks for the info. I hope with this I can start manipulating my Ubuntu installations. BTW here is the link about Wubi. [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide).

I also came to know that there is another tool called LVPM which can be used to transfer the Wubi based Ubuntu installation under windows to a dedicated partition. I got the info here [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591).

---

### Post by abhilash82 on 2007-08-26
> **Pumalite said:**
> I don't know anything about Wubi. You can partition your hard drive using Gparted: 
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) 'Extend' your XP to 20 GB, delete the other 2 10 GB partitions and make one large one of 20 GB. Install with Alternate CD. With that RAM I would advise Xubuntu. You cannot boot a LIVE CD with that RAM.
You need 10 GB for '/'
500MB to 1GB for 'swap'
The rest for /home

[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

I have partitioned my hdd as 25GB for XP, 12GB for ext3 and 1GB for swap. I installed Ubuntu from the live cd and to my surprise my system is quite fast and responsive now even with the faulty 256MB RAM  that I have!! Anyways that is not going to stop me from upgrading my RAM. Thanks for the help folks.

---

