---
title: "Change Grub Install Location"
date: 2011-05-27
forum: Installation &amp; Upgrades
---

### Post by Arel-kun on 2011-05-27
How do i specify to the Ubuntu installer where i want Grub to be installed? Each previous install it has done it has installed on the wrong hard drive and installed over the Vista loader then occasionally not detecting Windows at all, hence my want to put grub on my other disk.

---

### Post by ram0042 on 2011-05-27
It all depends on your configuration. Do you have Ubuntu on a separate hard disk drive? If so, install grub on that **sda** of which your machine has mounted the **/boot**. Make sure the menu.lst has specified the right **hd** and its corresponding number.

---

### Post by Arel-kun on 2011-05-27
Well, the problem is that Ubuntu installer seems to be detecting **sda **as the drive where Windows is installed, that isn't first in the boot order nor do the BIOS or other operating systems recognize as the primary drive.

What i want is a way **during installation** that i can specify where Grub should go instead of being subject to Grub placing itself where it wants.

---

### Post by Hedgehog1 on 2011-05-28
To specify it during installation, you will have manually install.

Here is a sample of the steps:

you will start the install and eventually get to the **Disk Space Allocation** screen.  

If you are installing Natty/11.04, select the '**Something Else**' option.

If you are installing 10.04 or 10.10, select the '**Specify Partitions Manually (Advanced)**' option.

Here is what the allocation screen looks like:

[IMG]http://img27.imageshack.us/img27/6770/03allocdrivespace1.png[/IMG]

First, define your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Next, set up the swap partition.  This usually sets itself up just fine, but double check it.

[IMG]http://img263.imageshack.us/img263/7656/06allocdrivespace4.png[/IMG]

If you have a '/home' partition:

**[SIZE="4"]IF YOU ARE DOING AN UPGRADE, DO NOT FORMAT THIS PARTITION![/SIZE]**

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.


**[SIZE="4"]This brings you to here:[/SIZE]**

[IMG]http://img34.imageshack.us/img34/6017/08allocdrivespace6.png[/IMG]

[SIZE="4"]**Install the Boot Loader on your preferred drive here!**[/SIZE]



***The Hedge***

:KS

---

### Post by Arel-kun on 2011-05-28
Thanks very much.

---

