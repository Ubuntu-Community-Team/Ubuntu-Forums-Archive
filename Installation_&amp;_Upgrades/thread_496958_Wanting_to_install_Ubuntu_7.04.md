---
title: "Wanting to install Ubuntu 7.04"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by wantin2wander on 2007-07-09
Ok, I have been reading all throughout this forum and now I am more confused than ever. I say this because I am seeing instructions/thumbnails that conflict with what I am seeing on my system. Because of this I am starting yet another thread about this subject hoping to get some clarity. If this is explained in detail elsewhere and i am missing it feel free to redirect me, but hear me out first as I do have a lot of variables here.

Heres what I am trying to do. I have 2 systems running....

System #1 has Vista Home Premium and is my main system (just built it). It has 2 SATA HD's, drive C: being 200gb and drive D: being 250gb, both have single NTFS partitions on them.  I would ultimately like to have a Linux OS on this system as it is a much faster system, but I am a bit leery to mess with this one just yet until I am a little more rehearsed with Linux and the installation process.

System #2, which the Vista one replaces is a P4 with 1gb RAM so it is capable I am sure. I just reloaded XP Home on it. It also has 2 HD's, but these are IDE's, drive C; being 160gb and drive D: being 80gb, again both only have one NTSF partition on each. I use the D: drive to back up my documents already as well as store music and video files. I have little concerns about screwing this system up as it is a 'toy' if you will and I have an external USB backup drive attached to it as well and back everything up weekly.

My plan is to use system #2 as a guinea pig and making drive C: a dual boot drive with XP Home and Ubuntu 7.04 and maybe use the 80gb drive D: as a swap drive? as well as a storage drive for documents and media. If I am missing something here steer me in the right direction if you would please.

So, I just attempted to install Ubuntu 7.04 desktop but when I get to step #4 this is where things get a bit confusing as the [detailed directions I am finding  here]("http://www.psychocats.net/ubuntu/installing") do not coincide with what i am seeing on my screen. 

My choices are...

1. Guided: use entire disk

2. Guided: use the largest continuous free space

3. Manual

but if you look at the pictured diagram of the above directions the options 1 and 2 are reversed and option one gives you a slide bar option to choose the new partition size.

Under option #3 'manual'  I believe I am able to divide the 160gb drive into two partitions during install to accommodate Ubunta, but I am not sure if I am making the right choices or if I needed a third partition as well so I backed out and came here for further advice.

Also, I am reading elsewhere here that I would probably be better off repartitioning the drive with GParted? I am assuming I would need to do this if i wanted to use option #2...yes? Just in case I have downloaded this already but have yet to divvy into it thinking I best ask for some further support here first.

I have already ran disk defrag and think I am ready to go? 

How many partitions do I need on drive C: to accommodate the existing XP OS and Ubuntu 7.04  on the same drive as a dual boot system? Do I need a separate partition on the same drive as a swap/storage or can I use a portion of drive D: for this?

Would I be better off using drive D: for Ubuntu, partitioning that drive into two or three areas so that I had a secondary backup space for my docs from XP and a swap file area and just leave XP as a stand alone on C:?

Confused yet? I am :confused:

Any and all suggestions are much appreciated :)

---

### Post by stchman on 2007-07-09
> **wantin2wander said:**
> Ok, I have been reading all throughout this forum and now I am more confused than ever. I say this because I am seeing instructions/thumbnails that conflict with what I am seeing on my system. Because of this I am starting yet another thread about this subject hoping to get some clarity. If this is explained in detail elsewhere and i am missing it feel free to redirect me, but hear me out first as I do have a lot of variables here.

Heres what I am trying to do. I have 2 systems running....

System #1 has Vista Home Premium and is my main system (just built it). It has 2 SATA HD's, drive C: being 200gb and drive D: being 250gb, both have single NTFS partitions on them.  I would ultimately like to have a Linux OS on this system as it is a much faster system, but I am a bit leery to mess with this one just yet until I am a little more rehearsed with Linux and the installation process.

System #2, which the Vista one replaces is a P4 with 1gb RAM so it is capable I am sure. I just reloaded XP Home on it. It also has 2 HD's, but these are IDE's, drive C; being 160gb and drive D: being 80gb, again both only have one NTSF partition on each. I use the D: drive to back up my documents already as well as store music and video files. I have little concerns about screwing this system up as it is a 'toy' if you will and I have an external USB backup drive attached to it as well and back everything up weekly.

My plan is to use system #2 as a guinea pig and making drive C: a dual boot drive with XP Home and Ubuntu 7.04 and maybe use the 80gb drive D: as a swap drive? as well as a storage drive for documents and media. If I am missing something here steer me in the right direction if you would please.

So, I just attempted to install Ubuntu 7.04 desktop but when I get to step #4 this is where things get a bit confusing as the [detailed directions I am finding  here]("http://www.psychocats.net/ubuntu/installing") do not coincide with what i am seeing on my screen. 

My choices are...

1. Guided: use entire disk

2. Guided: use the largest continuous free space

3. Manual

but if you look at the pictured diagram of the above directions the options 1 and 2 are reversed and option one gives you a slide bar option to choose the new partition size.

Under option #3 'manual'  I believe I am able to divide the 160gb drive into two partitions during install to accommodate Ubunta, but I am not sure if I am making the right choices or if I needed a third partition as well so I backed out and came here for further advice.

Also, I am reading elsewhere here that I would probably be better off repartitioning the drive with GParted? I am assuming I would need to do this if i wanted to use option #2...yes? Just in case I have downloaded this already but have yet to divvy into it thinking I best ask for some further support here first.

I have already ran disk defrag and think I am ready to go? 

How many partitions do I need on drive C: to accommodate the existing XP OS and Ubuntu 7.04  on the same drive as a dual boot system? Do I need a separate partition on the same drive as a swap/storage or can I use a portion of drive D: for this?

Would I be better off using drive D: for Ubuntu, partitioning that drive into two or three areas so that I had a secondary backup space for my docs from XP and a swap file area and just leave XP as a stand alone on C:?

Confused yet? I am :confused:

Any and all suggestions are much appreciated :)

On the LiveCD, bring up Gnome Partition Editor and make one of the drives Free Space by deleting a partition.  Then tell Ubuntu to use largest continuous free space.

---

### Post by wantin2wander on 2007-07-09
> **stchman said:**
> On the LiveCD, bring up Gnome Partition Editor and make one of the drives Free Space by deleting a partition.  Then tell Ubuntu to use largest continuous free space.

Wow that was fast...thanks for the reply and suggestion

In saying " make one of the drives Free Space by deleting a partition" do you mean make a portion of the drive I choose free space? 

There is only one partition on each drive...if I delete the partition then I will lose all data on said drive. Maybe I am misunderstanding what you are saying?

Perhaps I will understand better once in Gnome editor?

---

### Post by cmat on 2007-07-09
For some reason the partition editor isn't as nice as the 6.10 livecd. It gave me all kinds of problems.

---

### Post by wantin2wander on 2007-07-09
OK I understand now that I am in the editor. 

Next question is do I need 3 partitions on this drive or just two, one being the existing and a new one for Ubuntu? In other words do I need a small third partition for swap files, seems I read that somewhere?

Presently I have allocated 70gb for XP leaving me with 80gb free.

---

### Post by wantin2wander on 2007-07-09
> **cmat said:**
> For some reason the partition editor isn't as nice as the 6.10 livecd. It gave me all kinds of problems.

Yeah, I got an error after a while when changing the partition size, and it asked if I wanted to save the details, I said yes of course but they are no where to be found. Thing is once closed out it looks as though the task was accomplished. That may change once I reboot though :(

---

### Post by Odrodzona-Sarmacja on 2007-07-09
> **wantin2wander said:**
> 
System #2, which the Vista one replaces is a P4 with 1gb RAM so it is capable I am sure. I just reloaded XP Home on it. It also has 2 HD's, but these are IDE's, drive C; being 160gb and drive D: being 80gb, again both only have one NTSF partition on each. I use the D: drive to back up my documents already as well as store music and video files. I have little concerns about screwing this system up as it is a 'toy' if you will and I have an external USB backup drive attached to it as well and back everything up weekly.

My plan is to use system #2 as a guinea pig and making drive C: a dual boot drive with XP Home and Ubuntu 7.04 and maybe use the 80gb drive D: as a swap drive? as well as a storage drive for documents and media. If I am missing something here steer me in the right direction if you would please.

So, I just attempted to install Ubuntu 7.04 desktop but when I get to step #4 this is where things get a bit confusing as the [detailed directions I am finding  here]("http://www.psychocats.net/ubuntu/installing") do not coincide with what i am seeing on my screen. 

My choices are...

1. Guided: use entire disk

2. Guided: use the largest continuous free space

3. Manual

but if you look at the pictured diagram of the above directions the options 1 and 2 are reversed and option one gives you a slide bar option to choose the new partition size.

Under option #3 'manual'  I believe I am able to divide the 160gb drive into two partitions during install to accommodate Ubunta, but I am not sure if I am making the right choices or if I needed a third partition as well so I backed out and came here for further advice.

Also, I am reading elsewhere here that I would probably be better off repartitioning the drive with GParted? I am assuming I would need to do this if i wanted to use option #2...yes? Just in case I have downloaded this already but have yet to divvy into it thinking I best ask for some further support here first.

I have already ran disk defrag and think I am ready to go? 

How many partitions do I need on drive C: to accommodate the existing XP OS and Ubuntu 7.04  on the same drive as a dual boot system? Do I need a separate partition on the same drive as a swap/storage or can I use a portion of drive D: for this?

Would I be better off using drive D: for Ubuntu, partitioning that drive into two or three areas so that I had a secondary backup space for my docs from XP and a swap file area and just leave XP as a stand alone on C:?

Confused yet? I am :confused:

Any and all suggestions are much appreciated :)

1. You need now (after defraging C:) to use your partition magic or whatever you use in windows and shrink C: partition to as much as you feel to leave whatever is over for linux (Minimum 2gb for each intended ext3 partition and 0.5-1gb for swap partition).
2. You could go with "/" system partition and "swap" partition, but it is better to have also "/home/" partition as user working space partition. You are well off in preformating in windows partitioning program: 8-16 gb ext3 partition for "/", 2-100(or more :) ) gb work space for "/home/" partition and 0.5-1gb for "swap" partition. Ubuntu installer won't create succesfully anything but "/" and "swap" partition.
3. Time to leave the sweet windows xp home and start that livecd with ubuntu. When it comes to partitioning just choose manual setup and one of ext3 partition mark it as "/", second ext3 as "/home/" and mark the "swap" partition as "swap". Ubuntu will install like a dream and it will work much longer then it would do without "/home/" partition.
4. You need also to run your partion tool again from "livecd" or "boot a:" to mark "/home/" partition as xpartition, so you won't have any problems in booting windows after ubuntu install.

Also worth to remember is that Ubuntu has a bug in screensaver /hibernate/, which disconects every 30 mins innactivity all networking, but there is a work around for it.

Futhermore there is also gam_server bug, which can freeze and crash ubuntu, but there is also a work around for it.

When you have your install ready you may wish to look at blog:
[http://linuxondesktop.blogspot.com/2007/05/13-must-do-things-on-new-ubuntu-704.html](http://linuxondesktop.blogspot.com/2007/05/13-must-do-things-on-new-ubuntu-704.html)
to make your fresh ubuntu install to work as you would expect windows to work.
The only set back in ubuntu is you that you cant pack files in rar format. Otherwise there is no noticable difference. 

BTW. when you have ubuntu running online install simple firestarter firewall asap, as ubuntu comes without any firewall protection at all, which is rather odd and is not usuall with other linux distributions.

Good luck :)

---

### Post by wantin2wander on 2007-07-09
And there begins the debate of which Linux OS is superior, am I right? I chose Ubunta becasue it is #1 free and #2 stated as being beginner friendly for somewhat experienced . do you suggest a different build or is that tabo on this forum...lol <ducks>

---

### Post by wantin2wander on 2007-07-09
Thanks Odrodzona-Sarmacja, stchman and cmat for your replies.

Between your input and further research I was able to install Ubuntu using a /home partition as well. Hopefully this will help out in the future when it comes time for upgrades.

It appears to be running just fine. It found all of the hardware and the internet connection and instantly downloaded all the updates, all without my assistance other than giving it permission, which was a real treat.

> BTW. when you have Ubuntu running online install simple firestarter firewall asap, as Ubuntu comes without any firewall protection at all, which is rather odd and is not usually with other linux distributions.

This is my next step. thanks for the tip :)


Here is how I set up the C: drive.... 

40gb for XP                    NTSF
12gb for /                       ext3
76gb for /home              ext3
20gb for Data Share     fat32
2gb Swap

I believe this is right? If anyone sees where I made a mistake or can suggest resizing any of the partitions thinking they are either too large or small I would appreciate their input.

Incidentally, I chose Ubuntu after doing much research. In doing so it seemed to be the best option for my wants/needs/experience.

Thanks again

---

### Post by Skidpad on 2007-07-10
> **Odrodzona-Sarmacja said:**
> BTW. when you have ubuntu running online install simple firestarter firewall asap, as ubuntu comes without any firewall protection at all, which is rather odd and is not usuall with other linux distributions.

This is incorrect.  By default, Ubuntu uses IP tables for firewall protection.  Firestarter is simply a GUI front end for it.  You are protected without Firestarter, but it does give you some easy configuration/status options.

---

### Post by wantin2wander on 2007-07-10
> **Skidpad said:**
> This is incorrect.  By default, Ubuntu uses IP tables for firewall protection.  Firestarter is simply a GUI front end for it.  You are protected without Firestarter, but it does give you some easy configuration/status options.

I read this elsewhere here when I started researching installing Firestarter so I didn't go any further until I learn more about it. Thanks for the info.

---

