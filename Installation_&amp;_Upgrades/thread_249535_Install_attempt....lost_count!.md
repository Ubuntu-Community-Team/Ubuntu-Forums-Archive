---
title: "Install attempt....lost count!"
date: 2006-09-02
forum: Installation &amp; Upgrades
---

### Post by elpuerco on 2006-09-02
OK, new thread as suggested and a new attempt to install

I am running text mode on the alternate Kubuntu install and think I have found the cause of previous failed attempts on the Unbuntu desktop install.  I hope someone can help me!

I have a 100GB disk partitioned as follows:

1.6 GB manufacturers rescue partition which is wiped clean

63.8 GB which is my main C: drive Windows XP

8.4 GB I want to use for Kubuntu

26.3 GB which is my own rescue partition of my C: drive.

I am at the partition phase in Kubuntu setup and the list is as follows:

#1 Primary  1.6GB SWAP
#2 Primary 63.8GB /media/hda2
#3 Primary  8.4GB /
#4 Primary 26.3GB /media/hda4

When I select Finish partitioning and write changes I get the error:

The attempt to mount a file system of type ntfs in IDE1 master, partition #3 (hda3) at / failed.  Do you want to resume partitioning?

I have tried setting partition #3 to boot on and the #2 turns off but still get same error.

Help any one...........please

---

### Post by catlett on 2006-09-02
> The attempt to mount a file system of type [COLOR="Red"]ntfs[/COLOR] in IDE1 master, partition #3 (hda3) at / You cannot install Ubuntu to an ntfs partition. It must be formatted to ext2 or ext3 type filesystem.

---

### Post by elpuerco on 2006-09-02
SUCCESS!!!!!!!!

OK at last I have a working copy of Kubuntu ON my laptop:D 

I deleted the partiton on #3 and did an auto create and it created a extended/logical setup and everything installed and here I am on internet on Linux:D 

I am very happy, yes took me a lot of struggling to get here and am suprised the Ubuntu desktop install did not report the problem with partitioning rather than just dumping me back to the desktop with no explaination!

I doubt an every day joy with little computer knowledge would have got by this.

But I am happy now and shall start to play with my new OS=D>

---

### Post by meng on 2006-09-02
Thanks for letting us know that you were successful.
You seem to have fallen into the common trap of partitioning first before the LiveCD installer gives you the opportunity. This seemed to be the step that tripped you up. The everyday user you refer to would probably have let the Installer do this automagically, and thus circumvent the frustration you experienced.

The important thing, howver, is that you persevered and were rewarded.

---

### Post by elpuerco on 2006-09-02
=D> You bet =D> 

I am fandabbydoseyly happy.  I feel like I really have acheived something and am having fun exploring Kubuntu

:D

---

