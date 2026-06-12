---
title: "Partition problems"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by Freetech on 2008-01-27
I have spilt my 250GB disk into 2 on the first part i have the "evil" vista and the rest of the disk is free space that have not been used for any thing (100GB)

when i boot the 7.10 installer disk i get to te point where i have to choose the free space i wan't to use for 
Ubuntu

But NOOOO!!  my crapy machine show's a mess of partition's  
i show's the install disk and a few 100MB of free disk space and then a used space og 60GB then 100MB of 
free space and then 160GB of used space and about a 100MB of free disk space again.

I am shure that the free disk space of a 100GB if there Both windows vist install disk (recovery console) can see it and a Opensource disk tool i found on Sourceforge can finde it.
But if i use the disk tool to make a partition for ubuntu, the install disk still can't finde it.

I have reset mbr  no luck there.

My machine is a Acer travelmate 6592 with 250GB disk and 2 GB ram and ATI HD 2400 XT

Please help !!!!!!!

---

### Post by logos34 on 2008-01-27
does gparted see it correctly?

live cd desktop>system>admin>gnome partition editor

---

### Post by zvacet on 2008-01-27
Try with manual partitioning.That should show you all your partitions and free space.It will be wise to make separate home partition.All this with screenshots you can find [here](http://www.psychocats.net/ubuntu/installing).

---

### Post by Freetech on 2008-01-27
i am using the manual mode  
and it is in the manual mode that it is showing all the weird stuff  and not even the pertitions i made with the disk tool i have on a nother boot disk

and gonna reboot now and try gparted

---

### Post by Pumalite on 2008-01-27
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.
If your partition shows up, make sure is formatted and not 'unclaimed space'
Then you could prepare your partitions (inside that partition) before the installation:
10 GB for '/'
2x RAM up to 1 GB for /swap unless is a laptop in which case /swap=RAM
The rest for /home
Then install Ubuntu. Go Manual and use the already prepared partitions.
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by Freetech on 2008-01-27
i know how to partition my disk  the problem is  when i am trying to install ubuntu this shows up when i am trying to locate the unused space og 100GB

Remember the disk only has 1 partition 1.st 130GB  and 100GB of unused space 
I know this and have checked it over and over again but ubuntu can't see it 

[IMG]http://android.dk/1.png[/IMG]

[IMG]http://android.dk/2.png[/IMG]

---

### Post by Freetech on 2008-01-28
Sorry  but its getting urgent that a fix for this problem comes

---

### Post by Bartender on 2008-01-28
Are you sure Windows is still on there?  It should be recognized as "NTFS" with a bootable flag.  GParted recognizes no file systems.  The 200MB EFI partition has something to do with the damned Acer recovery stuff, which is way more complicated than it should be!

Can you:
1)  delete sda3
2)  combine it with the unallocated space
3)  then set it up as an extended partition
4)  then format as ext3?

If you can, then Ubuntu should install to the partition. 

Try to apply each step as you go.  I recommend an extended partition because that will give you the freedom to make several partitions inside in case you want a separate /, /home, etc.  GParted will get very uncooperative when you have three primary partitions and try to make a fourth partition, even if you're making it logical.

---

