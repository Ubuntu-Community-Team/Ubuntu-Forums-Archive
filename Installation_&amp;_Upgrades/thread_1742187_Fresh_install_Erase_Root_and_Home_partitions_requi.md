---
title: "Fresh install: Erase Root and Home partitions required?"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by Paulgirardin on 2011-04-28
I will be installing Natty using the alternative CD.My system has a separate Home partition.
Do I need to erase the contents of the Root and Home partition with gparted or similar,prior to the fresh installation of Natty or will the installer take care of all that automatically?

---

### Post by Derek Karpinski on 2011-04-28
Check this out.  I wonder if someone else can confirm this? :confused:
 
[http://ubuntuforums.org/showthread.php?t=1741994](http://ubuntuforums.org/showthread.php?t=1741994)

---

### Post by ratcheer on 2011-04-28
> **Paulgirardin said:**
> I will be installing Natty using the alternative CD.My system has a separate Home partition.
Do I need to erase the contents of the Root and Home partition with gparted or similar,prior to the fresh installation of Natty or will the installer take care of all that automatically?

If you want them all fresh, then you should format the partitions during the installation process. If you want to retain your profile and settings, you do not have to format and you can install Natty over the prior release. If you do the latter, you will have to reinstall all your apps, but their configurations will remain mostly intact. This is known by some as a "dirty install".

Tim

---

### Post by Hedgehog1 on 2011-04-28
One of the points of having a '/home' partition is to make a clean install easier by separating your data and OS.

Here are the instruction for doing this manually:


Here is what the allocation screen looks like:

[IMG]http://img27.imageshack.us/img27/6770/03allocdrivespace1.png[/IMG]

First, make /dev/sda5 your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Next, set up the swap partition.  This usually sets itself up just fine, but double check it.

[IMG]http://img263.imageshack.us/img263/7656/06allocdrivespace4.png[/IMG]

The last partition to setup is the '/home' one:

**[SIZE="4"]IF YOU ARE DOING AN UPGRADE, DO NOT FORMAT THIS PARTITION![/SIZE]**

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

This brings you to here:

[IMG]http://img34.imageshack.us/img34/6017/08allocdrivespace6.png[/IMG]

[SIZE="4"]**Please install the Boot Loader on /dev/sda !**[/SIZE]

Press "Install Now" and you are on your way:

[IMG]http://img855.imageshack.us/img855/7153/09installbegin.png[/IMG]



***The Hedge***

:KS

---

### Post by Nesaskewatch on 2011-05-01
Hey thanks for that Hedge.  I am about to embark on my first upgrade with a separate /home partition and have seen several explanations for upgrading a separate / and /home install and yours is by far the best.  I have two independent instances of Ubu; 10.10 and momentarily 11.04, both with separate /home.  That is if all goes well.  I intend to use one instance (actually two partitions) as a test-bed for future development candidates.  I may wait a bit before overwriting 10.10 though...  I may not like 11.04!  :)  

Your instructions are nice and straight forward, and the screen shots make a huge difference.

Cheers!

---

### Post by Paulgirardin on 2011-05-01
Thanks for the replies.

Cheers

---

