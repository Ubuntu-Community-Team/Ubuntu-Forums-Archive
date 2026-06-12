---
title: "Why so many installation problems?"
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by st3vo on 2008-07-03
Hi there,

For the last week I have been trying to install Ubuntu and failed on 2 different computers.

I'm basically trying to do a dual-boot on both.

On my vista laptop, i cannot even get to the installation process once reboot and on pc (has XP) everything goes fine till it starts creating the partitions, the progress bar just hungs forever.

I would love to move completely to linux in the future, if I ever get to use it :(

Linux is far a better OS than Windows BUT windows is simple to install and hardly gives any problems during installation.

I can bet anything that a lot more people would use linux if it didn't give people so many problems trying to install it on their machines.

Is this an issue that should be resolved in the furture? I am currently forced to stay with windows because I can't even get to install linux on any of my pc's.

Linux is better than Windows (FACT) but until these issues get solved linux is going to continue being in the background. (FACT).

The mayority of users are not IT Wizard's and if they cannot get the install linux without having major issues, linux will remain in window's shadow. No offence, but if I cannot get something working, no matter how much I'd like to use it at some point I will just give up and wait till the OS if stable enough to at least install without any problems.

I am an IT person but used to windows and new to linux who wants to move to linux but unless Ubuntu (for example) get's sorted I will not be able to use it.

Hope you take this in the right way. I'm not saying that Ubuntu (Linux) is no good, I believe it's better than Windows but with lot's of issues to get solved during the installation process!

Hope this helps and someone clarify's my questions.

Thanks again

ST3VO

---

### Post by Sealbhach on 2008-07-03
Are you sure your Install disk is OK? Did you do a checksum?



.

---

### Post by st3vo on 2008-07-03
Yes, I have already burned 3 copies and verified the checksum which is correct!

---

### Post by st3vo on 2008-07-03
WOW, I really thought I would get a lot more feedback :)

---

### Post by Rayaz on 2008-07-03
Have you run a  disk integrity check at the begining of an install? As for a VISTA install its a pain in the a@@! I recently did one on my brothers HP DV 6000. I had to resize the VISTA drive using Gparted. Sorry for the truncated reply, typing on a mobile phone is a pain in the a@@ too;)

---

### Post by st3vo on 2008-07-03
I run the winMd5Sum application to do a checksum and it was ok.

About the disk integrity check...where is that option?

I selected (on both pc's) the "Install inside Windows" option.

---

### Post by wpshooter on 2008-07-03
St3vo:

I think you would have a lot better chance at success if you would FORGET about this dual boot thing and find yourself a computer to use with strictly Ubuntu.  Choose one, WIPE everything off of the hard drive using [www.killdisk.com](www.killdisk.com) and then install only Ubuntu preferably from the ALTERNATE install CD version.

Good luck.

---

### Post by Rayaz on 2008-07-03
Ok, pop in the CD, boot and you'll be presented with some choices. Third or fourth will be a choice to check the integrity of the install disk. Please use the alternate install CD.

---

### Post by st3vo on 2008-07-03
I only get 3 options under Ubuntu CD Menu:

1. Demo and Full Installation

2. Install inside windows

3. Learn more...

That's all I'm getting.

Also, alternate install CD??? Is this another download?

Thanks for your feedback? As you can see, I'm a total N00b to linux :)

---

### Post by st3vo on 2008-07-03
Never mind, found it and downloading it now!

Thanks!!!

---

### Post by Rayaz on 2008-07-03
Yes there is, basically two versions. One a Live Install CD and the other an alternate install CD. The one you have is the Live Install CD. To have total control you need to download the alternate CD.

---

### Post by pooyaplus on 2008-07-03
Hi, you will find the checkbox to download the alternate cd at the bottom of the download page of the ubuntu website.

Why do not you boot the live disk and install form the live disk environment? There you can play around with the features and apps to get used to it.:)

Good luck.

---

### Post by st3vo on 2008-07-03
Ref: Why do not you boot the live disk and install form the live disk environment? There you can play around with the features and apps to get used to it.

-- That's the first thing I tried but it wouldn't work either, so I tried the installation inside windows option, which didn't work either.

-- About getting myself another pc...well, i don't have the money :(
And I have 3 computers but all setup for major stuff that if I get rid off I won't be able to do certain jobs.

--Also, yes thanks a lot I found the .iso and burned it and it's ready.

I just need to ask one thing...Does the Alternative version have the dual boot option?

Thanks all

---

### Post by avtolle on 2008-07-03
Once installation is complete, there is no difference between Ubuntu installed from the Live Cd and Ubuntu installed from the alternate install cd. However, the above is for installing Ubuntu on its own partitions, etc. One cannot do a Wubi install from the alternate cd (such as you tried from the Live CD).

---

### Post by st3vo on 2008-07-03
Right! I understand and thanks a lot for letting me know!!!

Sad though, that I'm going to have to stick with just windows until i can wipe one of my pc's. :(

Well, I guess that's it then!

Thanks all and I hope to be able to try out Ubuntu in the near future!

---

### Post by ChameleonDave on 2008-07-03
> **st3vo said:**
> 
Linux is far a better OS than Windows BUT windows is simple to install and hardly gives any problems during installation.


You shouldn't over-extrapolate from your personal experience.  I have never had trouble installing Linux, and I had quite a lot of hassles installing Windows.

---

### Post by Lod on 2008-07-03
> **st3vo said:**
> 
Well, I guess that's it then!Oi, don't give up so quickly. We're not done yet with your salvation.

I have had similar problems about a year and a half ago. The partitioning tool of the Ubuntu install cd didn't like the way my drives where partitioned, I don't know exactly how or what. But if I used fdisk (the basic, default Linux partitioning tool) it was complaining about something incorrect in the partition table.
So I created a partition with free space on my own. In my case it was easy, I just deleted my D-partition in Windows. You also could use a program like PartitionMagic in Windows if you don't have a spare partition.
After you've done this try the install again and choose the option: "use largest continuous empty space" (or something).

Good Luck.

---

### Post by pooyaplus on 2008-07-03
> **st3vo said:**
> Ref: Why do not you boot the live disk and install form the live disk environment? There you can play around with the features and apps to get used to it.

-- That's the first thing I tried but it wouldn't work either, so I tried the installation inside windows option, which didn't work either.

-- About getting myself another pc...well, i don't have the money :(
And I have 3 computers but all setup for major stuff that if I get rid off I won't be able to do certain jobs.

--Also, yes thanks a lot I found the .iso and burned it and it's ready.

I just need to ask one thing...Does the Alternative version have the dual boot option?

Thanks all
Hi,
I think you may like to read the installation docs or other guides available on the Internet - some time for Googling. Those may help you get over the problems. A dual boot is really no big deal. 

Good luck.

---

### Post by rockface on 2008-07-03
Interesting problem. I use either the native Ubuntu partitioning tool or Parted Magic even when installing Windows to Fat32/NTFS. The Microsoft tools are mediocre by comparison.

Fact of the matter is this. If these three machines are working to your satisfaction and all have critical software you need maybe for you Windows is the answer.

As much as I dislike Windows it does have software and tools I could not live without.

---

### Post by st3vo on 2008-07-03
Hi all again :)

First of all thanks for trying to save my soul from windows :)  

On my second laptop I have a partition D: with 40GB of space left.

My first try was to install it there and it didn't work so I tried on the C: drive...but no luck either.

On my second laptop It installs fine on the C: and it rebooted and the graphic GUI came out and it verifies the installation BUT when it says formating ... it just hangs there forever, so unless it should take more than 20 minutes on an Alienware, Top of the range Giant Laptop, designed for gaming there is something wrong with the installation.

I am willing to try anything to get Ubuntu installed Except (at this point get rid of windows completely as it's all my work tools, code etc...that I have there!)

Thanks :)

---

### Post by hman1945 on 2008-07-03
Hi ST3VO, I agree with you. I want to get away from WindowsXP and Internet Explorer but I'm having problems with the install also.
I'm even willing to pay for tech support, just to get me started and off on the right foot, but right now it's frustrating.
I'm going to back off on Ubuntu for now and wait until I have more time to trouble shoot this.

---

### Post by st3vo on 2008-07-03
I totally understand you! 

My plan was to install Ubuntu and keep XP and Vista, then gradually get rid of all the windows software I use and find replacements or write my own for linux then just get rid of windows FOREVER and never look back, but it just doesn't seem to be happening.

Let's do a deal! If you keep on trying I'll give it another shot too :)

I REALLY want Ubuntu really bad but I cannot just swap OS as my job requires windows OS until I migrade everything to Linux OS.

People are really useful here and I feel they are keen on getting as many people to leave windows an possible so that one perfect day windows will fall under the sea forever!!! :)
:guitar:

---

### Post by Sef on 2008-07-03
> You also could use a program like PartitionMagic in Windows if you don't have a spare partition.

1) Partition Magic and GNU/Linux tend not to get along.  Best to use another partitioner.

2) With Vista, you need to use its partitioner to shrink its partition.

---

### Post by st3vo on 2008-07-04
But don't you think I've got enough space with 40GB on my D: Partition?

Does Ubuntu care if I install it on the D: ???

---

### Post by rogier.de.groot on 2008-07-04
1) Use the alternate install CD; it will typically work when the livecd won't (one of the reasons it exists I guess).
2) You can install Ubuntu on your D: drive, but may I suggest moving your data off it, and replacing the whole partition with a linux-native one (like ext3).
3) The partitioning tool in the alternate install cd is a bit... well, if you're used to fdisk it's great:) Anyway, you select the D: partition, delete it, and make two new ones (ext3 partition for root (/) mount point and a swap partition about twice as big as your RAM).

---

### Post by Lod on 2008-07-04
> **st3vo said:**
> But don't you think I've got enough space with 40GB on my D: Partition?

Does Ubuntu care if I install it on the D: ???40 Gb is more than enough, it could even be installed on 4 gb or less. 
It's just that sometimes the used partitioning tool on the installation cd can't handle the existing partition-tables when he has to resize a drive. By doing this resizing with another tool you can create free space on you harddisk. This the installation cd can handle.

Linux doesn't care if it's installed on the c, d, e or whatever drive. Most of the times :-)

---

### Post by Partyboi2 on 2008-07-04
> **st3vo said:**
> But don't you think I've got enough space with 40GB on my D: Partition?

Does Ubuntu care if I install it on the D: ???
Using the wubi install option, installs inside the windows partition, (which you are having problems with) If you decide to go with the other method that has been suggested to install ubuntu to its own partition you would either need to shrink down your d: partition or delete the partition and use the space to install ubuntu. This option will allow you to dual boot or even triple boot with windows.

---

### Post by st3vo on 2008-07-04
OK, Thanks all!

I'll give it a shot. :)

Let's rock'n'roll :guitar:

---

### Post by hman1945 on 2008-07-10
Hi st3vo,
Have you been able to install Ubuntu? I'm thinking about trying the install VIA Parallels Workstation and see what happens. 
hman1945

---

### Post by pooyaplus on 2008-07-13
> **hman1945 said:**
> Hi st3vo,
Have you been able to install Ubuntu? I'm thinking about trying the install VIA Parallels Workstation and see what happens. 
hman1945

Hi,
could you go through the installation process?

---

