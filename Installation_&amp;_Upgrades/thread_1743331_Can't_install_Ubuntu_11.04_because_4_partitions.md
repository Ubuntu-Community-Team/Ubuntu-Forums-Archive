---
title: "Can't install Ubuntu 11.04 because 4 partitions"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by delfo3 on 2011-04-29
Hello,

I want to install ubuntu 11.04 to my computer but I have this:

dev/sda1 Windows 7 (Loader) (ntfs) 208.7MB
dev/sda2 Windows Recovery Enviroment (Loader) (ntfs) 485.5 GB
dev/sda3 Windows Recovery Enviroment (Loader) (ntfs) 14.3 GB
dev/sda4 (fat32) 108.0 MB

I can't do another primari partition.

What can I do?

Thank you

---

### Post by Dutch70 on 2011-04-29
Hi and welcome to UF

You will have to decide which one of those partitions you want to get rid of.

---

### Post by delfo3 on 2011-04-29
But 
dev/sda3 Windows Recovery Enviroment (Loader) (ntfs) 14.3 GB
and
dev/sda4 (fat32) 108.0 MB
are not important? I can rid of one of those? 

Can you explain me how I can do it? 

Thank you,

Regards

---

### Post by Dutch70 on 2011-04-29
From the live cd/usb. 

Menu to System>>Admin>>Gparted
Take a screenshot of Gparted and attach the pic to your next post using the paper clip in the toolbar.

---

### Post by oldfred on 2011-04-29
You can & should make the recovery DVDs & repair CD if it lets you then the recovery partition may not be vital. The vendor utilities (sda4) is tiny and easily backed up.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first.
Shrinking a Windows 7 partition is best done in Windows. 
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show grahically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by ottosykora on 2011-04-29
I assume that you have HP computer, this is the formating of the hard drive by HP, either they are off any education or do it by purpose just to make any other install for the user as much complex as possible.

The 14.3gb recovery, well it conatins just the parts for complete reset of the computer to factory state. You can produce DVD disk set from it and restore computer from them if needed. You can also copy this to some temporary external media first, just to keep all.
The fat partition contains nothing important, so you can copy the contents somewhere temporary too.

The use the gparted either from live CD of ubuntu or you download parted magic CD (partedmagic.com), burn CD or create bootable usb stick from it and delete those two partitions. Make an extended partition in the now empty space. In that extended partition, you can create number of logical partitions. So you can make some for the 14.3gb restore data, you can make one for ubuntu , one swap and one fat32 as general data store and interchange place for example.

---

### Post by delfo3 on 2011-04-29
First of all, thanks for your interest in helping me. I love Ubuntu but always I use it in computers that they use this system.
I'm from spain and I don't use my english a lot and I have some problems with high level vocabulary. I am doing all my efforts in order to understand all you say but you have to be patient and for this reason I want to apologise :):
Then: 
1. [Dutch70]("http://ubuntuforums.org/member.php?u=595401"): I have posted the photo? I think that I have uploaded it correctly with the clip. This is what you want to see?

2.[oldfred]("http://ubuntuforums.org/member.php?u=852711"): I have no time now to read this links, I have no idea how to do a good recovery DVD & repair CD ... I'm new with this, I thing that where I have to find the option to do this operations but now I don't have time. Tomorrow I'll try to read all. Thank you :)

3. [ottosykora]("http://ubuntuforums.org/member.php?u=758846"): yes I have a HP, but a friend of I have a HP too but he hasn't got that partitions, he only has 2. But now we are in my problem :). 
I am runing ubuntu with a USB stik, I don't know how to delete this partitions and what is a logical partition, etc... I only know that I want 120GB for Ubuntu and I need to create space. If you can help me step by step how to do all this things you'll help me so much and I will learn a lot. 

Thank you all guys!
[[COLOR=Black][/COLOR]]("http://ubuntuforums.org/member.php?u=852711")

---

### Post by markymark64 on 2011-04-29
Oh come on guys. This is an easy one. If those partitions are empty reformat them as logical partitions. Windows has a limit to how many primary partitions you can have but you can have up to 8 logical partitions. If this is your first time installing Ubuntu I would recommend 10.10 as there are a lot of problems with this latest version that you can see just by looking at all of the threads. If you're doing a dual partition there are certain steps you want to take to ensure Ubuntu is installed correctly. Meanwhile, as mentioned, just make those partitions logical if you are doing a dual boot.

---

### Post by markymark64 on 2011-04-29
A logical partition, also referred to as an extended partition is one of two types of windows partitions that exist. Windows will only allow you to have a limited number of primary partitions but it will allow you to have double that amount in extended or logical partitions. Does this help any with understand the difference?

---

### Post by Dutch70 on 2011-04-30
I wouldn't pay much attention to the 2 post above. No offense markymark64, but most of the info is simply incorrect. 

Might want to give this a read before deleting any partitions. 
[[COLOR="Red"]http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360[/COLOR]]("http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360")

I don't usually recommend Wubi, also known as the windows installer, but it may be a good idea for you. 
It allows you to install Ubuntu directly into windows programs without partitioning. 
[[COLOR="Red"]http://www.ubuntu.com/download/ubuntu/windows-installer[/COLOR]]("http://www.ubuntu.com/download/ubuntu/windows-installer")
Thanks to Rubi1200, this thread will come in handy if you go with a Wubi install.
[[COLOR="Red"]WUBI MEGATHREAD[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1639198")

Keep in mind that if your computer is under warranty. Partitioning will void the warranty.

---

### Post by delfo3 on 2011-04-30
Thank you for your help, I'll respond the new threads:

1. Do you think that it's better install 10.10 before install the new ubuntu?? 

2.
{

Ok this post is good:
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)

but he explain the things you have to do... security copy, delete and then put it again logically, ... but my problem is that all this steps I don't know how I have to do it: where are this options, ...

The post of Wubi, Wubi is like as Virtual Box?

The third post:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)
the last thing that it's said is this:
**As a result I can now do nothing at all in Ubuntu! - not the desired result of the installation!**

Here that man explain a little of the partitions but he doesn't solve anything:
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

This link 
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360) 
helped me a bit more to understand some things. I don't know yet what is a logical partition and how I have to do all the things but I know what is the way I have to go. 

}

The HP_TOOLS partition, it have information from the BIOS system and they say that you can delete it... I can do a recovery disc from that partition coz it's 99MB easy to put in a CD but the other partition 14.6GB it's too big!, I can delete the fat32 partition (partition 4) put a 4 partition of 120GB for ubuntu and install it??  

you understand this? sorry with my english.


Thanks to all!

---

### Post by kansasnoob on 2011-04-30
Considering these two questions:

> 1. Do you think that it's better install 10.10 before install the new ubuntu??

2.
{

Ok this post is good:
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)

but he explain the things you have to do... security copy, delete and then put it again logically, ... but my problem is that all this steps I don't know how I have to do it: where are this options, ...


I really do think you should consider a Wubi install. I just performed a slew of testing because the new Natty live-installer offers Wubi as an option and the only drawback I see (or have ever seen) is the fact that the Wubi file system is more susceptible to damage from a power outage as shown here:

[http://wubi.sourceforge.net/faq.php](http://wubi.sourceforge.net/faq.php)

> Any gotcha?

Hibernation is not supported under Wubi, moreover Wubi filesystem is more vulnerable to hard-reboots (turning off the power) and power outages than a normal filesystem, so try to avoid unplugging the power. An Ubuntu installation to a dedicated partition provides a filesystem that is more robust and can better tolerate such events.


The full guide explains a lot:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

One thing though, no matter what installation procedure you decide to use, you should have some Ubuntu live media (CD or USB) to use for recovery and repair purposes.

Another thing, and most importantly, always back up any important data and have the proper re-installation media on hand should something go wrong! The failure you're NOT prepared for is the one that's most likely to happen :(

---

### Post by delfo3 on 2011-04-30
Well I have installed Ubuntu with Wubi and as it happens if I run ubuntu with the CD the monitor light are completely off... I can't see anything and if I put the monitor with a light I see that there are something like a menu but I can't read anything... 
I have deleted Wubi...

I prefer the partitions but I don't know and understand yet some problems.

---

### Post by ssican on 2011-04-30
1)- To learn about Partitions(Primary-Extended-Logical), you need to read the GParted Documentation:
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

[http://gparted.sourceforge.net/display-doc.php?name=help-manual&lang=C](http://gparted.sourceforge.net/display-doc.php?name=help-manual&lang=C)

[http://gparted.sourceforge.net/display-doc.php?name=help-manual&lang=es](http://gparted.sourceforge.net/display-doc.php?name=help-manual&lang=es)

2)- About "Recovery Partitions" on the -PRE-INSTALL PAGE- Chapter PARTITIONING RULES, 
[http://members.iinet.net.au/%7Eherman546/p17.html#Preparation_For_The_Install_](http://members.iinet.net.au/%7Eherman546/p17.html#Preparation_For_The_Install_)

there is this Information:

What not to do:
Never delete a recovery partition or any other partition unless you're sure you will still be able to re-install your old operating system somehow without it. 
 
What You might be able to do:
* Ask your computer manufacturer to give you a proper 'Installation Disk' for the software that you paid for when you purchased the computer, as without that you really don't have the software permanently.

---

### Post by delfo3 on 2011-05-01
OK thank you, I'll read it and I'll tell my problems or what I think.


If someone else wants to include something I'm here to learn and finally install Ubuntu.

---

### Post by kansasnoob on 2011-05-01
> **delfo3 said:**
> Well I have installed Ubuntu with Wubi and as it happens if I run ubuntu with the CD the monitor light are completely off... I can't see anything and if I put the monitor with a light I see that there are something like a menu but I can't read anything... 
I have deleted Wubi...

I prefer the partitions but I don't know and understand yet some problems.

I'm not quite sure what you're saying there, but have you ever been able to successfully run an Ubuntu Live CD/USB?

I'm guessing if neither a Wubi install or a live session will run that you'd be planning on installing with the alternate cd, and if so why would you expect the completed install to run?

Since you mention the monitor I suspect a graphics compatibility issue so we need to know the specific gpu info. It can be determined using a Linux Live CD and running the command:

```
lspci | grep VGA
```

---

### Post by delfo3 on 2011-05-01
If I run Ubuntu with USB I can see all but if I run it with live CD there are no light in the monitor... I see that there are something but I can't see without light.

How I can run this command if I can't see anything?

---

### Post by kansasnoob on 2011-05-01
> **delfo3 said:**
> If I run Ubuntu with USB I can see all but if I run it with live CD there are no light in the monitor... I see that there are something but I can't see without light.

How I can run this command if I can't see anything?

Do you not then have a Live USB?

---

### Post by delfo3 on 2011-05-01
I have Live USB

---

### Post by delfo3 on 2011-05-02
When you install ubuntu, it need 2 partitions to be installed? Or with one partition I can install ubuntu?

with my partitions: 
dev/sda1 Windows 7 (Loader) (ntfs) 208.7MB
dev/sda2 Windows Recovery Enviroment (Loader) (ntfs) 485.5 GB
dev/sda3 Windows Recovery Enviroment (Loader) (ntfs) 14.3 GB
dev/sda4 (fat32) 108.0 MB

I can delete fat32 and make more space again in order to install ubuntu?

---

### Post by Dutch70 on 2011-05-02
If you delete sda4 (fat32) 108MB. That will give you 2 things. 
1. Room to create an extended partition, which counts as one of your 4 primary prtns.
2. 108MB of extra space which is not enough to do anything. 

You will still need to shrink sda2. That must be done from within windows7. Search the web for how to shrink windows7 safely. There will be things you need to do such as defragging once or twice, turning off system restore...etc.

After you shrink windows7, run check disk once or twice to make sure there are no errors. Once you have successfully shrank windows7, you can do everything else from Ubuntu.

You will need to create an extended partition with all of your unallocated space. Then create 2 new partitions inside your extended prtn. One for each...
swap = size equal to your physical RAM or slightly larger.
/ aka root = the remainder of your unallocated space.

Format / to ext4 & format swap to "swap" 

[[COLOR="Red"]https://help.ubuntu.com/community/HowtoPartition[/COLOR]]("https://help.ubuntu.com/community/HowtoPartition")
[[COLOR="Red"]http://www.dedoimedo.com/computers/gparted.html[/COLOR]]("http://www.dedoimedo.com/computers/gparted.html")

---

### Post by dino99 on 2011-05-02
as previously said:
- resize windows partition(s) with windows tool to make room
- you can remove useless partition (up to you)

To work around max 4 primary partitions, after making room, create an extended partition wherein you can then create the needed partitions for ubuntu

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by delfo3 on 2011-05-03
To install ubuntu you need almost 2 partitions, one with memory space (what the installation search) and the other one to change or move documents... I can do the second one logical?? 

Can I have only one partition with for example 100GB the other 3 primary partitions for windows and a logical partition (the 5th) for ubuntu?

---

### Post by oldfred on 2011-05-03
The extended partition counts as one of the four primary partitions. So you can have 3 primary and then the extended. But inside the extended you can have just about as many logical partitions as you want. The extended is just the container for all the logicals.

Windows has to have a primary to boot from and if installing more than one copy of windows it will literally move all the boot files from the second install to the first that is in a primary. If you ever delete the first install it deletes the boot files for the second. The second can then only be repaired if it is also a primary parition.

Windows reads and second installs can be installed into logical partitions (not recommended, see above).

All of Ubuntu works from logical partitions.

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by Dutch70 on 2011-05-03
Here is a pic of my partitions on 2 different hdd's. Maybe it will help you understand what oldfred said.

The first pic has room for one more primary partition.

The second pic shows that I am using 3 primary prtns, plus the extended counts as the 4th. However, I have several logical prtns inside the extended.

---

### Post by delfo3 on 2011-05-04
You have a unallocated partition.

Uff it will be dificult! there are a lot of partitions and things buff! let me try something, if in a few days I don't say something you can believe that my pc is broken. jaja

Thank you :)

---

### Post by Dutch70 on 2011-05-04
:lol:

I don't have an unallocated partition. I have unallocated space that I can use to create more partitions. I can also use it *(or part of it)* to grow my data partition. There are a lot of things I can do with it.
Since I don't need the space right now, I'm leaving it that way until I do need it for something. It's fairly common for people that multi-boot & have extra space.

---

### Post by oldfred on 2011-05-04
I also have a fair amount of unallocated space. You do have to make sure it is already in the extended partition or next to the extended partition so you can expand extended & create new logical partitions. 

I went from two 160GB drives to a new 640 a couple of years ago. With that much new space I was not sure what I wanted to do with all of it so I just used what I thought I needed at the time & left the rest available. Since I made good sized data partitions, do not save many very large files, and only use 25GB for a / (root) partition, I have only created a few new root partition to test installs of other systems or betas.

I plan on using gpt for all new drives so I do not have to worry about extended partitions in the future. But you can only do that if you never want windows on the drive. I converted one of the 160GB drive to gpt and my current Maverick is on that drive.

---

### Post by srs5694 on 2011-05-04
I like using LVM when I don't plan on allocating all my disk space, or when I think I'll be making many changes to my partitions. LVM works like a filesystem -- you create a "logical volume" in the LVM area rather than a partition, and you don't have to specify start or end points for the logical volume, just a size. The LVM software figures out where to allocate space within the LVM, and that space need not be contiguous, as it must with a partition. Thus, you can add and delete logical volumes as you like without worrying about moving partitions, which is the most time-consuming and riskiest part of such operations when using regular partitions. You can also combine storage across disks (similar to linear RAID or RAID 0).

LVM does have its downsides, though. Linux's LVM implementation isn't understood by Windows or Mac OS, so it doesn't help much with juggling storage between Linux and non-Linux installations. (Multi-boots with several Linux distributions work fine, though.) It's also an added layer of complexity that adds to the learning curve and can complicate data recovery if you experience disk corruption. Because you don't know where your space is being allocated, you can't tweak partition placement to optimize performance; and because logical volumes can be fragmented, performance can suffer if you make a lot of changes. (You can flag a logical volume as requiring contiguous allocation, though, to minimize this problem.)

---

### Post by delfo3 on 2011-05-04
I have lost all my information! 10GB of information off. I have seen all my future now!

---

