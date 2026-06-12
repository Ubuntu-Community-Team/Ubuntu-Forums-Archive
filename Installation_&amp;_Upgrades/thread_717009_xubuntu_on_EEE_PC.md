---
title: "xubuntu on EEE PC"
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by 2j4ez on 2008-03-06
Hello all ,

Ive got a EEE PC and managed to install xubuntu on it.
my model is a 2GB model so had to install it and use a 2gb memory card aswell to get it to install

my problem is it only sometimes boots i get a screen complaining about FIXING THE FILE SYSTEM MANUALY 

Ive no idea on what to type in to fix it?
Anyone no why this is happening?

I'm still new to linux  when it boots the machine is fine i can use wireless and surf the internet ok

Anyone ideas??

---

### Post by fdimmling on 2008-03-07
> **2j4ez said:**
> 
Ive no idea on what to type in to fix it?
Anyone no why this is happening?

Hi
I have a eeePC too with 4GB disk and 1GB RAM. I am running eeeXubuntu without any problems. My system takes 1.8GB which means that your disk might just running out of space. 

Checking the file system is done by fsck /dev/sda1 (your hard drive). 
But the drive must be unmounted to perform a fsck.

Friedrich

---

### Post by 2j4ez on 2008-03-07
thanks will try that would it be wise to but a 4 or 8gig card and install it on that?

---

### Post by fdimmling on 2008-03-09
> **2j4ez said:**
> thanks will try that would it be wise to but a 4 or 8gig card and install it on that?

I am not sure if it works to run the system from a SD card. You can do it as a Live system, ok, but if it really makes fun? At least you should deinstall anything you do not really need.

Friedrich

---

