---
title: "Newbie needing help with multipl distro installation"
date: 2007-11-20
forum: Installation &amp; Upgrades
---

### Post by adkoge on 2007-11-20
Hi,
I am just now switching to linux and was wondering if someone could give me step by step instructions for installing some distributions.  I want to install ubuntu, opensuse, as well as have a small part for my windows xp.  I have no idea what to do with the partitioning.  I have a 60 gig harddrive and would like to dedicate around 25 to 30 gigs to ubuntu, about 15 to 20 to opensuse or any other distro, and 10 to xp.  How would I do this?  I am a complete newbie to this and beginner talk would be great.  Any help would be much appreciated.  Thanks.

---

### Post by tommcd on 2007-11-20
> **adkoge said:**
> Hi,
I am just now switching to linux and was wondering if someone could give me step by step instructions for installing some distributions.  I want to install ubuntu, opensuse, as well as have a small part for my windows xp.  I have no idea what to do with the partitioning.  I have a 60 gig harddrive and would like to dedicate around 25 to 30 gigs to ubuntu, about 15 to 20 to opensuse or any other distro, and 10 to xp.  How would I do this?  I am a complete newbie to this and beginner talk would be great.  Any help would be much appreciated.  Thanks.

First, install winXP to a 10GB partition, or if winXP is already installed, defragment it first.
Then download ubuntu and burn an iso image CD to install ubuntu from. Here is a way to burn an iso image from windows:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29)
Boot up the ubuntu install CD (you may have change the boot settings in your computer's BIOS to boot from cdrom).
When you get to the partitioning part, choose manual partitioning. If winXP is already installed choose "resize existing partitions" (or whatever it says). Shrink windows to 10GB and create these partitions:
1) 10GB ext3 partition for ubuntu's root partition
2) 1GB swap partition
3) 10GB ext3 partition for suse's root partition
4) the rest as ext3 partition for /home

Install ubuntu then suse. Install ubuntu's grub to master boot record, then install suse's grub to suse's root partition, and add it to ubuntu's grub like this:
[http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile](http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile)

If all of this seems too complicated, just start with ubuntu for now as per this excellent guide. 
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
You can always repartition for multiple distros later after you learn the basics.

EDIT: Choose different user names for Ubuntu and Suse in order to keep the hidden configuration files stored in /home separate so they don't conflict with each other.

---

### Post by adkoge on 2007-11-20
Ok I have one more question.  Which of these partitions do i need to have as primary and which as logical

---

### Post by maybeway36 on 2007-11-20
The Windows partiton needs to be primary. Linux doesn't really care, but you might as well make them primary too (the way it works out, you will have 4 partitions.)

---

### Post by adkoge on 2007-11-20
Do I have both root partitions for Ubuntu and Suse mounted on "/"?

---

### Post by adkoge on 2007-11-20
Ok I have all 3 systems installed now.  Under open suse i see a 10GB Media ext3, and a 10GB Media ntfs.  Under Ubuntu I can see my other two drives for suse and windows.  I partitioned 20 something GB towards "/home" so does that mean I have that free space for windows, ubuntu, and suse all together?

---

### Post by tommcd on 2007-11-20
> **adkoge said:**
> Do I have both root partitions for Ubuntu and Suse mounted on "/"? 

When installing ubuntu the 1st 10GB ext3 partition will be ubuntu's root. The 2nd 10GB ext3 partition can be mounted under any name you want. By default, ubuntu mounts other partitions under /media/sdaX, where X = the partition number. When installing suse, make the 2nd 10GB ext3 partition suse's root, and mount the 1st 10GB partition under either /mnt/NAME or /media/NAME, where NAME can be whatever you want. (I guess you figured that out by now since you got them installed). To see a list of your partitions from ubuntu run "sudo fdisk -l" in terminal.

---

### Post by tommcd on 2007-11-20
> **adkoge said:**
> Ok I have all 3 systems installed now.  Under open suse i see a 10GB Media ext3, and a 10GB Media ntfs.  Under Ubuntu I can see my other two drives for suse and windows.  I partitioned 20 something GB towards "/home" so does that mean I have that free space for windows, ubuntu, and suse all together?

Both ubuntu and suse will be able to share the /home partition to store data, music, videos, or whatever. You could install as many distros as you want with all of them sharing /home.
Windows does not recognize linux partitions and will not be able to read or write to linux partitions.
You could have made /home a fat32 partition. Both linux and windows can write to fat32. But fat32 has limitations compared to ext3, so it is not worth it imo.
Congratulations on getting everything installed, and welcome to the ubuntu forums!
One piece of advice: Learn to use the terminal, and learn basic linux commands. Learning the terminal will really pay off if you want to try other distros, since terminal commands are (more or less) consistent in all distros. Here is a good place to start:
[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

---

### Post by adkoge on 2007-11-21
Alright, thank you very much everyone.  Tommcd you were a great help you have no idea.  It's nice to finally get away from Windows especially since I am getting into computer science.

---

