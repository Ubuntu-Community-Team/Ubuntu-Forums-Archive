---
title: "Partitioning with 7.10"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by cheeseburger on 2008-02-25
Hello:

This is my first time trying Linux/Ubuntu and was installing 7.10 Dual Boot with XP, but I've run into some problems using the ubuntu partitioner.  Im pretty lost.  I put the CD in and start it up, but I dont know what to do for the partitions.  The installation guides on partitions have a different menu than mines.  I dont have the option of "resizing the partition"!  I dont have one of those sliding bars either.

The machine is a Shuttle ST61G4, Pentium 4, 512 Mb, SATA 160GB drive.  I have just one drive(no other partitions).

Heres some pictures of the menus.  What do I choose or do?


The options at the partition screen.
[IMG]http://img530.imageshack.us/img530/182/img0396gs5.jpg[/IMG]

This is when I choose the second option.
[IMG]http://img409.imageshack.us/img409/2840/img0396eh1.jpg[/IMG]

This is the next screen after I select the third option: Manual Partition.  What do i do?
[IMG]http://img176.imageshack.us/img176/7897/whatty5.jpg[/IMG]

Sometimes(1 out of 10) when I click manual I get this menu instead of the third picture.
[IMG]http://img403.imageshack.us/img403/7104/onceinacrapja9.jpg[/IMG]


What do I do? Which options do I select?

---

### Post by housam on 2008-02-25
- First of all you have to back-up your data - just in case.
- Do defrage your HDD 2-3 times and notice the position of the green sector ( windows file system ) . let say at 40% from the left side.
- This means that you cann't resize windows partition to less than that size of the HDD or you'll damage it.
- Use Gparted tool ( on the live CD ) to do the partitioning task.(system >> admin. >> Gparted )
- You can create up to only 4 primary partitions on single HDD.
-I suggest to create 3 primary partitions and make the 4th one as extended which can be devided to many logical partitions.
- You'll devide the extended partition to 2 partitions : one EXT3 ( 20 GB is a good space ) for installing ubuntu as a root partition ( / ). and the other one as a swap ( only 1 GB ).
- During the installation process when it comes to the partitioning choice choose the manual way and assign the EXT3 as a root ( / ) .

---

### Post by cheeseburger on 2008-02-25
Thanks housam!  I currently have 68GB free on my HDD.  I'll defrag it a few times and try to use gparted.

But on the partitions:  What are the 3 primary partitions for?  Can I just make one extrended(like you said 1 EXT3 20GB and another swap 1gb)?  and keep the rest of my HDD the same?

---

### Post by housam on 2008-02-26
The primary partitions are the common that all of us use it to install operating systems, data , swap and music like the one that has win-xp on it . the idea is if you need more partitions on your HDD ( more than 4 ) ,you can not create all of them as primary. then you'll have to reformet one of the primary to an extended partition which can be devided to any number of logical partitions ( and it works the same as the primary )

in your case , you can create them all as primary ( one ntfs for win-xp , one ext3 for root , one as swap and one ntfs for data/music ).

---

### Post by zvacet on 2008-02-26
[Here](http://www.psychocats.net/ubuntu/installing) is good partition guide.My advice is to make separate home partition.That way your settings and data,files will be safe,because it will be on separate partition.It will be important if it comes to reinstall or upgrades.

---

