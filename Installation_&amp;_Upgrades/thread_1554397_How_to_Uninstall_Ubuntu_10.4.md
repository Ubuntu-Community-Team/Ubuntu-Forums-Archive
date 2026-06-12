---
title: "How to Uninstall Ubuntu 10.4"
date: 2010-08-16
forum: Installation &amp; Upgrades
---

### Post by elwayisgod on 2010-08-16
Hi,

I accidentally downloaded the 32bit version and installed it instead of the 64 bit version.  How should I go about uninstalling the 32bit and re-installing the 64bit.  I have never uninstalled a linux os before. But I'm computer savvy as I'm in the industry....

---

### Post by howefield on 2010-08-16
You could simply install 64 bit over your 32 bit install.

When it comes to partitioning simply mount your existing partitions and mark for formatting.

ps. This may not apply if you are talking about a Wubi install though.

---

### Post by elwayisgod on 2010-08-17
Now Ive got three choices at boot up...It didn't install over the top of the 32 bit.. Is there a way similiar to formatting the disk of the 32 bit install, then merging that partition with the current one?  Little rusty on unix commands.  Maybe there is partitioning software?

---

### Post by sydbat on 2010-08-17
> **elwayisgod said:**
> Now Ive got three choices at boot up...It didn't install over the top of the 32 bit.. Is there a way similiar to formatting the disk of the 32 bit install, then merging that partition with the current one?  Little rusty on unix commands.  Maybe there is partitioning software?Install GParted from Synaptic. Be careful. Make backups before doing anything (as someone in IT, you already know this, but there are others who might read this thread).

---

### Post by elwayisgod on 2010-08-17
I was thinking I could boot up into my Win 7 and use Acronis Disk Director from there.  Would that work, or must I use a linux based partitioning software?

---

### Post by Nick_Jinn on 2010-08-17
You could use a live CD and delete your partitions with Gparted. 



Can anyone tell me why Gparted is there in the live CD but its not installed by default in all distros even when they have it on the CD itself?

---

### Post by elwayisgod on 2010-08-17
Sorry for my ignorance.. What is a Live CD?

---

### Post by M93 on 2010-08-17
if u open 'wubi' its going to tell u that theres a version of ubuntu already installed...press 'uninstall'
then u can install the other version u want
_or_ u can go to drive 'C' and delete folder 'Ubuntu' then install again using live CD or wubi or any other method :)

---

### Post by uRock on 2010-08-17
> **Nick_Jinn said:**
> Can anyone tell me why Gparted is there in the live CD but its not installed by default in all distros even when they have it on the CD itself?
I am guessing they don't feel that many of the end users will need it as a permanent program. I have it installed, but never use it, except to make screenshots when explaining how to use it to other people.

---

### Post by M93 on 2010-08-17
> **elwayisgod said:**
> Sorry for my ignorance.. What is a Live CD?

wen i download the iso file u burn it to a CD and its called Live CD, caz u can try ubuntu without installing it using this CD

---

### Post by uRock on 2010-08-17
> **elwayisgod said:**
> Sorry for my ignorance.. What is a Live CD?
A LiveCD is the disk you use to install Ubuntu. If you downloaded the Ubuntu Desktop image from the website, then you have the LiveCD image. [https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

---

### Post by elwayisgod on 2010-08-17
Holy moly.. I don't know what wubi is either.. My second day on Ubuntu folks :)   I did burn the ISO do a DVD to Install so I guess I have a Live CD?

---

### Post by uRock on 2010-08-17
> **elwayisgod said:**
> Holy moly.. I don't know what wubi is either.. My second day on Ubuntu folks :)   I did burn the ISO do a DVD to Install so I guess I have a Live CD?
If you installed to your hard drive using a partitioner, then don't worry about Wubi. Wubi is a program that allows you to install Ubuntu as a program within Windows.

---

### Post by linux18 on 2010-08-17
you really don't need the 64-bit if you have a PAE kernel or less than 3.5 GB of ram even if your hardware supports it.

if you don't mind reinstalling one last time, specify 'manual' during the partitioning screen of the installer (the default it to put all of the systems alongside eachother) 

-specify manual (it's the last option)   
-erase all ext3 or ext4 partitions 
-format the FREE space as ext4 with the mount point set to '/'
-continue with the installation

---

### Post by elwayisgod on 2010-08-17
In general would you Linux pros recommend:

1 - Win 7 and Ubuntu in a dual boot situation sharing hard drive?
2 - Win 7 with an Ubuntu VM via Virtual Box?
3 = Ubuntu with a Win 7 VM via Virtual Box?

I still have a few windows programs (Quickbooks) that I have to have for my business.

---

### Post by uRock on 2010-08-17
I'd say, "run ubuntu in a vbox and see how you like it and if it is compatible with what you want to do." Then, if you like it, dual boot it. Windows doesn't work as well in a vbox, from my own experience. The down side to dual booting is the fact that you have to restart when you want to switch systems. With Ubuntu in a vbox, you can run it in seamless mode and have the best of both worlds.

---

