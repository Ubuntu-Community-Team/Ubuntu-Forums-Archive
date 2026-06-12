---
title: "Trying to understand partions and the upgrade process"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by bultmann on 2008-05-18
Hi there, 

I am trying to understand partitioning and how that can help with upgrading or backups. For example, every few months there is a new version of Ubuntu. Is it possible to do a clean install of the new version without having to reinstall all your applications? If so, how do you do this? 

I have a 120GB hard drive. Currently I have an NTFS partition for Windows XP which is about 105GB in size which leaves 15GB for ubuntu. These were sizes that were recommended to me. It was also recommended to have a separate partition for / which is 5GB, a 8GB partition for /home and 2GB for swap space. Does this partitioning scheme make sense and how does it help with upgrading or backing up? 

Also, I was told that 5GB for / would be plenty of space. Currently I don't have many applications installed, I'm just test driving ubuntu before making a real installation. For some reason my / partition is already 99% full and many times I am getting a warning message that there is not enough space to perform some operations. How can that be? I do have some ridiculously large Lotus applications installed that we use at work, but I don't know if they are that big... 

So now I am thinking about repartitioning my hard drive again and giving more space to Linux. Any recommendations as to which partitions to create and how big they should be?

Thanks.

---

### Post by iaculallad on 2008-05-18
Yes, you can do a clean install on Ubuntu without reinstalling all your applications. Ubuntu LiveCD comes with pre-Built applications (such as open-office, brasero, rhythmbox, etc..). But, you have to do manual installation for applications that are not pre-built with the LiveCD (usually third-party/non-free applications).

You can free some space on your / by issuing:

sudo apt-get clean

More on Partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
More on Partitioning Scheme:
[https://help.ubuntu.com/7.04/installation-guide/powerpc/apcs03.html](https://help.ubuntu.com/7.04/installation-guide/powerpc/apcs03.html)

---

### Post by bultmann on 2008-05-19
So you are saying that if I do a clean install of a new Linux version, then I have to reinstall all the Lotus applications that I installed? And programs like VMWare that I would like to install eventually? I have to do that every few months? That sounds painful... Or am I missing something here? How does a separate /home partition come into play with all this?

I know how to create, resize and delete partitions. I'm just trying to figure out a good partitioning scheme that saves me a lot of headaches in the future. I'm still new to this aspect of Linux. That's why I would also like to get some recommendations on size. The articles that I found on the internet so far weren't really that helpful...

---

### Post by iaculallad on 2008-05-19
> **bultmann said:**
> So you are saying that if I do a clean install of a new Linux version, then I have to reinstall all the Lotus applications that I installed? And programs like VMWare that I would like to install eventually? I have to do that every few months? That sounds painful... Or am I missing something here? How does a separate /home partition come into play with all this?

I know how to create, resize and delete partitions. I'm just trying to figure out a good partitioning scheme that saves me a lot of headaches in the future. I'm still new to this aspect of Linux. That's why I would also like to get some recommendations on size. The articles that I found on the internet so far weren't really that helpful...

Yes, im saying that you have to re-install applications categorized as non-free/third-party-softwares. This is because Ubuntu does not automatically ship it with their LiveCD's, you manually get it from the Internet. You actually don't do this (install applications) every couple of months if what you're telling is updating your current Ubuntu installation would mean Re-Installing Ubuntu. No, installed applications are not deleted when you update Ubuntu.
Separate /home partition comes into play when you want a 100% safekeeping of documents since we cant avoid intermittent errors which could cause data loss or unrecoverable folders. Here is a link on how you could create a [separate /home partition]("http://www.psychocats.net/ubuntu/separatehome").
For the partition size, you could give:
swap 1GB swap
/boot 100MB boot, Ext3
/tmp 500MB Ext2
/var 3GB Ext3
/var/log 500MB Ext3
/var/tmp 500MB Ext3
/usr/local 2GB Ext3
Or any way you like that fits your need.

---

