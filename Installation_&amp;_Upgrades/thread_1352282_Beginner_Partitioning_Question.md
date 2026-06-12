---
title: "Beginner Partitioning Question"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by Mington on 2009-12-11
Hi all,
I am new here.
I have been learning about Ubuntu client and server at work.
I want to install the client on my desktop or laptop at home.
I have a question about partitions:
Do I really need multiple partitions for just general home use?
I just do basic internet, word processing, and might try games.
I have read that you should have x number of partitions for this and that, but do I really for just casual or general home, personal use?
If so, what do you recommend?
Thanks in advance.
M

---

### Post by benjaminsuman on 2009-12-11
You will want at least 2 partitions, one for / and one for swap.  In most cases, using guided partitioning during setup works pretty well.  That being said, thoughtful partitioning of your hard drive can make your life easier in the future.

---

### Post by phillw on 2009-12-11
Hi & Welcome,

De-Frag your hard drive - and use what ever partitioning software that comes with your version of Win.

You want about 10GB free in one 'free' area - no operating system at all on it. Then just tell ubuntu to use the 'free-space'. It will go through it with you.

If asked, you want 1GB for swap, the rest for the install (9 GB)

If you are planning on putting a server onto your system, you may well want to geive yourself about 15GB total.

Regards,

Phill.

---

### Post by darkod on 2009-12-11
There is no need for more partitions than the minimum / and swap that will be created by ubuntu. Later on, if you start using it more and more, you might consider separate /home partition for your docs/music/videos/settings. Even if you reinstall ubuntu it will keep your /home if don't format it, and keep all your docs etc.
For home desktop that's enough for a start.

---

### Post by oldfred on 2009-12-11
Just starting out the standard 2 partitions for root (/) and swap are all that is required. After more experience you can backup data & reinstall or move data to new partitions if desired. 

More reading - I have saved these links:

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition](http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition)

---

### Post by amanda on 2009-12-11
You don't really need partitions for home use, no. However, as someone who subscribes to a lot of podcasts and recently got burned by a drive that filled up with them, I think putting your /home/ directories on their own partition would have been worth it.

---

### Post by PaulReaver on 2009-12-11
new to the forums :) hi

sorry if this is a bit confusing but i'll explain

I like to have three partitions

contrary to everyone else on the planet I have my swap file first
about 1.5x my amount of ram
I have it first because the start of a hard disk has the best performance
its 1.5x my ram because it needs to be bigger than the amount of ram in use if you want suspend to work.

then I have my root file system "/" right after the swap file.
I do it this way because it stops the hard disk thrashing across empty sections of the disk, minimises thrashing between "/" and swap

then I have my home partition.
I use a separate home partition because it makes upgrading easier.
when it comes time to upgrade or swap distro's I mount the home partition as home but do not format.


sorry I can't help with sizes but everyone's hard disk is different, 
and of course my layout is only my opinion of what is best.

---

### Post by phillw on 2009-12-11
> **amanda said:**
> You don't really need partitions for home use, no. However, as someone who subscribes to a lot of podcasts and recently got burned by a drive that filled up with them, I think putting your /home/ directories on their own partition would have been worth it.

As a newcomer - adding the home to the extended partition that swap is in  and getting it to happily mount, is technically challenging. with a Win system, Ubuntu & the extended area for swap - they have already used up 3 of the maximum 4 allocations. If a recent win installation they may well have a recovery area - So will be take it to4 !! As pointed out - moving home at a later date is not too hard.

Regards,

Phill.

---

### Post by pricetech on 2009-12-11
Since you're a beginner, just let Ubuntu do the partitioning for you.  Trying to manually partition could easily confuse you.  Save such tasks for later on when you feel a little more comfortable with the OS itself.

---

### Post by Mington on 2009-12-11
Thank you everyone for your fast and helpful replies! :D

---

