---
title: "Installation hints on partition"
date: 2012-12-08
forum: Installation &amp; Upgrades
---

### Post by Bisneff on 2012-12-08
Hello everyone :) 

I've an Acer Extensa 5620Z (dual core processor T2330 1.6 ghz, 533 MHz FSB, 1 MB L2 cache) with 2,5 Gb Ram and 120 GB HDD.

Now I've two different partion: on one I've windows XP, on the other Ubuntu 12.04 PP. 
Now, since my last installation was a looot of time ago, and on october (with release of 12.10) I realized that I cannot upgrade without backup, cause I don't have  a data partion nor home on separated partition from SO, I want to format and reinstall everything.

Now I've  3 partition: one for windows service (5.86 GB), one for windows os (52,96 GB), one for ubuntu and swap partition (an extended partition of 52,97 GB, with only 2.49 of swap).

I've thinked a lot about how make new partitions, but I understood that I've to know more about my new installation before make it.

When I separe /home from OS in ubuntu, where new programs will be install?  And this partion with /home can be see from windows?

I've to undestand how much GB use for every OS installation and how much for /home folder and/or ntfs data partition.

Any ideas?

Thank you

---

### Post by oldfred on 2012-12-08
The extended partition is just the container for the logical partitions inside it. So that is not separately useable space.

A separate /home has to be formatted in Linux format to support ownership & permissions. It cannot really be read from Windows. If you want to have a partition to share data it may be better to create a shared NTFS data partition.

I used a shared NTFS data partition with my XP for years. It has my Firefox & Thunderbird profiles so I can use the the same email & bookmarks in both systems.

Your / (root) can be as small as 10GB, I suggest 10 to 25GB typically depending on your hard drive size. But if Ubuntu install is a total of 30GB or less I do not suggest the separate /home.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

       [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by Bisneff on 2012-12-08
Thank you for your answer.

Now I want to understand: if I make separated partitions for /home and / when I run *sudo apt-get install something* in shell from which partition the space is taken to install? 

My first idea was to make:
partition #1 - 25 gb - ntfs= Windows OS and Windows Service
partition  #2 - 30 gb - ext4 = Ubuntu OS
partition #3 - 3 gb - swap = Ubuntu Swap
partition #4 - 62 gb - ntfs = data partition

But I see that in this configuration, when I want to install new version of ubuntu I lose all my settings on programs.

Then I think:
partition #1 - 25 gb - ntfs= Windows OS and Windows Service
partition  #2 - 15 gb - ext4 = Ubuntu OS
partition #3 - 3 gb - swap = Ubuntu Swap
partition #4 - 77 gb - ext4 = /home

I lose the shared memory for data but I gain the certain of can change version without lose anything.

but I'm not sure this is a better configuration. 


I use windows only for Cubase 5, but other things I make are on Ubuntu.

---

### Post by darkod on 2012-12-08
If you don't need windows to access data you work with in ubuntu, I would go with the second layout. It is very useful to have separate /home since you can easily do clean installs.

If sometimes you need to transfer data from ubuntu to windows, you can always use usb stick or usb hdd.

Depending how much software you plan to install in ubuntu, it might be better the / partition to be 20GB instead of 15GB. Otherwise, it looks good to me.

---

### Post by oldfred on 2012-12-08
I would probably use second choice also, if you are not planning on using Windows much.

---

### Post by debodas on 2012-12-08
The second looks better. Having a separate / and /home partition is really useful.

---

### Post by Bisneff on 2012-12-11
Thank you all. I will do it soon :)

Someone know a good guide to make the installation with separated / and /home?

---

### Post by oldfred on 2012-12-11
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by cybrsaylr on 2012-12-11
oldfred, that was a very useful link above. Thanks.
It answered many questions I had about creating a separate /home partition.

Also it explained swap nicely. 
I have 8GB of RAM and that link indicates a swap is no longer needed since hibernation has been eliminated and sleep or a total PC shutdown is all I do.

---

### Post by oldfred on 2012-12-11
I like to have some swap. Someone posted that system boots better as it does not have to search for swap and not find it. 

Herman changed to use swapfile.
       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

---

### Post by debodas on 2012-12-11
> **Bisneff said:**
> Thank you all. I will do it soon :)

Someone know a good guide to make the installation with separated / and /home?

When installing, simply give the partition you want to OS to go on a / mount point, and give the partition you want files to do on a /home mount point.

Programs will install onto your / partition.

---

