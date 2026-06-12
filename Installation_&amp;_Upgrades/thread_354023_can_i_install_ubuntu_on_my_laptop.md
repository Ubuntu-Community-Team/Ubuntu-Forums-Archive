---
title: "can i install ubuntu on my laptop?"
date: 2007-02-05
forum: Installation &amp; Upgrades
---

### Post by djvic87 on 2007-02-05
Hi, i was wondering if is it possible to install ubuntu on my toshiba satellite s3094 as a second boot? Because im using windows xp as my regular OS, and i was wondering if i can make ubuntu as a second boot up without deleting windows xp. Please respond soon, thanks.

---

### Post by kebes on 2007-02-05
I see no reason why it wouldn't work. I don't see your exact model of laptop in the Ubuntu hardware wiki, but it looks like most Toshiba models work:
[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsToshiba](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsToshiba)


If you want to keep your current Windows XP install, you will have to use the installer partitioning program to resize your current partition and make space for Ubuntu. (Be safe and backup your important data before doing this!)


Post to these forums should you run into troubles or have more questions.

---

### Post by housam on 2007-02-05
> **djvic87 said:**
> Hi, i was wondering if is it possible to install ubuntu on my toshiba satellite s3094 as a second boot? Because im using windows xp as my regular OS, and i was wondering if i can make ubuntu as a second boot up without deleting windows xp. Please respond soon, thanks.

If you have 256 RAM or more , 5Gb free space  pll processor or higher, you can have a dual boot . Try to use [this guide.]("http://www.psychocats.net/ubuntu/installing")

---

### Post by djvic87 on 2007-02-07
Wow thanks for the help you guys have simply answered my question, thanks. 

I also been wondering will wifi be able to work on ubuntu?

By the way, will i be able to browse through saved files from windows? Such as movies, mp3s, etc.?

---

### Post by kebes on 2007-02-07
> **djvic87 said:**
> Wow thanks for the help you guys have simply answered my question, thanks. 

I also been wondering will wifi be able to work on ubuntu?

By the way, will i be able to browse through saved files from windows? Such as movies, mp3s, etc.?

Short answer: yes everything should work.


Longer answer:
Wifi can usually be made to work in Ubuntu, althought sometimes it requires a bit of work.

In terms of browsing Windows files, there's no problem. Linux can read from Windows drives (fat32, ntfs) easily. There are plenty of music players and video players for Ubuntu, so that's fine too. Note that a standard install of Ubuntu doesn't include mp3 support, DVD support, or media codecs (this is due to legal/licensing reasons). However it only takes a minute to install all those features. There are lots of documents explaining how. There is also a program for Ubuntu called automatix that will automatically install all of these "must have" add-ons.

---

### Post by djvic87 on 2007-02-07
O ok, so all i got to do is insert the cd, make a partition (or what else?), and then install that patch right? 

I also been wondering about those crazy graphics such as beryl, etc. How can i start that on my laptop? Is it easy?

Sorry guys if its so many questions, this is my very first time trying this out. I dont even know anything about partitioning the appropriate way. I really do appreciate all the help you guys give back to me. I want to be really part of this experience.

EDIT -  When it comes to partition, my harddrive is 74GBs of space, and the only space free is about 22.6GB. Can i still be able to partition?
Also, what does it mean about resizing the harddrive and use the freed space?

---

### Post by kebes on 2007-02-07
> **djvic87 said:**
> O ok, so all i got to do is insert the cd, make a partition (or what else?), and then install that patch right? 

There are lots of good guides online to help with installation. For instance:
[http://www.debianadmin.com/ubuntu-edgy-eft-desktop-installation-with-screenshots.html](http://www.debianadmin.com/ubuntu-edgy-eft-desktop-installation-with-screenshots.html)

The only 'hard' part of installation is the partitioning part. If you want to keep your current Windows install intact (so that you can dual-boot with Ubuntu and Windows), then you need to select 'manual partitioning' and shrink your Windows partition to make space. (Always backup your data before doing this!) Then tell the Ubuntu installer to 'use free space'.


The rest of the install is very easy. Just click and that's it.


> When it comes to partition, my harddrive is 74GBs of space, and the only space free is about 22.6GB. Can i still be able to partition?
Also, what does it mean about resizing the harddrive and use the freed space?

That's a little tight, but still possible for a Ubuntu install. You just won't have much room to grow. You should backup your important data in Windows. (Some people recommend defragging Windows, too.) Then you'll have to shrink your Windows partition. So you're currently using 51 Gb out of 74 Gb, leaving 22 Gb free. So you could shrink Windows down to 64 Gb, which still leaves 10 Gb free for Windows.

This gives you 10 Gb for your Ubuntu install. A basic install with a bunch of programs is about 4Gb, so this will be good enough for playing around. However if you start accumulating lots of files and installing lots of programs, you may run out of space.


When I say 'shrink Windows partition' I mean resize it. In the Ubuntu installer you will reach a stage where you can manually repartition your drive. The program that lets you do this is called "gparted". You will have to go into manual mode, select the Windows partition and click 'resize' (or whatever its called). Then you can install Ubuntu into the newly created free space.




> I also been wondering about those crazy graphics such as beryl, etc. How can i start that on my laptop? Is it easy?

Beryl is not too difficult to set up... There are lots of guides in the forums and on the [Beryl wiki]("http://wiki.beryl-project.org/wiki/Main_Page"). It does require becoming a bit comfortable with the Linux commandline. Beryl also needs a fairly good graphics card to work. According to the [Beryl FAQ]("http://www.beryl-project.org/faq.php#gq5"):
> 
 What are the system requirements for Beryl?
    Beryl runs acceptably well on a GeForce 3/i855/Radeon 7500, 256MB of RAM, and a 1.2GHz processor. It also works best with Xorg 7.1 and requires a recent version of Mesa. 

The main requirement is getting 3D acceleration working for your card. Sometimes this is really easy... sometimes it requires some fiddling.


> Sorry guys if its so many questions, this is my very first time trying this out. I dont even know anything about partitioning the appropriate way. I really do appreciate all the help you guys give back to me. I want to be really part of this experience.

No problem. I'm happy to help. I hope you find Ubuntu fun to use... I found it a little different/confusing at first, but now that I'm used to it, I couldn't live without my Ubuntu! Good luck, and feel free to ask more questions.

---

### Post by djvic87 on 2007-02-07
Wow, thanks man. You people rock.

When you mean about i should back up my data, does that mean that my data such as mp3s and files would be deleted when I do the partition?

So basically, all i got to do is resize the harddrive, right? And resizing windows doesn't that makes windows worst or delete any of my personal files?

EDIT - Kebes, can you tell me how I can do this step by step from you because even if i go through the tutorial i still find it confusing. I dont know how to mess with the manual partitioning. I consider it to be lots of stuff with confusing options.

---

### Post by kebes on 2007-02-08
> When you mean about i should back up my data, does that mean that my data such as mp3s and files would be deleted when I do the partition?

The re-sizing of partitions doesn't erase any data. However, re-partitioning can sometimes lead to errors (whether you use partition magic, gparted, whatever), so it's usually a good idea to back up important stuff, just in case.

Like I said, if all goes well, no data is lost. However it's always good to have a backup, so now would be a good time to make one!

> 
So basically, all i got to do is resize the harddrive, right? And resizing windows doesn't that makes windows worst or delete any of my personal files?

You will resize the Windows partition. As long as you don't make it smaller than the amount of data you have on it, you won't lose anything.

> 
EDIT - Kebes, can you tell me how I can do this step by step from you because even if i go through the tutorial i still find it confusing. I dont know how to mess with the manual partitioning. I consider it to be lots of stuff with confusing options.

Sure, no problem. Okay, refer to this better tutorial:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

That tutorial has very good explanations, and links to more information should you need it. I'll make a few extra comments...


Go down until you see the step "Prepare disk space". There are three options. If you only have one big partition on your hard drive, with Windows on it, then you can select option 1: "Resize IDE1 Master, partition #1 (hda1) and use free space." You will then be given a choice about how small to make your Windows partition, and then Ubuntu will install in the free space. Easy!

If, however, your hard drive has multiple partitions (some computers ship with hidden recovery partitions), you want to select the third option, "Manually edit partition table." Actually you can select this option to see what the partition table looks like. If you select this option you'll be brought to a new screen (the screenshot that says "prepare partitions"). It will list all your partitions. If you only see one listed, then you can just cancel the install, restart it, and select option 1 "Resize IDE1 Master..." instead.

If you see multiple partitions, then you need to resize the big Windows one to make room for Ubuntu. Right-click on it, select "modify" (or "resize" or whatever its called). Then you pick the new size (64Gb or whatever). This will create a new entry called "free space." Let's say the free space is 10Gb big. Right-click in that area and first create a partition that is 9 Gb. Make the type "linux-ext3". Then in the remaining free space, right-click and make a partition that uses all the space, with type "linux swap".



Click "Forward." (Nothing on disk will be changed yet...)

You will then see options about "mounting". You want the 9 Gb "linux-ext3" to the root of the Linux system, so set the mountpoint for that one to "/", and say "yes" to reformat. Set the swap you just made to be "swap", and reformat it. For your Windows partition, tell it to mount at "/media/windows/" but **don't click** the reformat option!!

Click "Forward." On the next screen you'll have a summary of the things that will be changed. It should say "resize partition #1 of /dev/hda". Make sure that it will NOT format that partition, however! Look over the changes. If everything looks right, click "Install" and it will re-arrange your hard drive!



I'm doing all this from memory (and the screenshots), so I may have missed something. If you have any more questions, feel free to ask. Re-partitioning can be scary, because it is possible to mess up your drive... but the Ubuntu installer does a good job of telling you exactly what it's doing.


Other than the partitioning stage, the rest of the installer is pretty simple. It will just copy over the files, and then reboot. Upon reboot, you should be given an option to boot into Linux or Windows.

---

### Post by djvic87 on 2007-02-08
O ok because on my laptop there is no more bigger partition that i know of, or where i go to my computer in windows, it doesnt show any other partition. By the way, when i choose the third option in ubuntu,  on the table it shows another partition of 305.93MB with the filesystem saying unknown with an exclamation mark.

That's weird because i never seened that partition on windows, I think its probably a backup or something.

Do you recommend me resizing it automatically or manually? The size of the harddrive is 74.23GB and is Using 48.22GB. Now, 26.01 GB is free

When im the options and when the first one is selected, on the bottom there is a bar in which of course i select the new partition size. It automatically goes to 50% (36.0GB)
Any suggestions over that?

EDIT - What im hoping for most is that i can be able to download and use stuff from Windows and Ubuntu. Like in Ubuntu, I want to be able to locate files that i use from windows in ubuntu, I hope that is possible.

---

### Post by kebes on 2007-02-08
> **djvic87 said:**
> when i choose the third option in ubuntu,  on the table it shows another partition of 305.93MB with the filesystem saying unknown with an exclamation mark.

Yes, that's probably some sort of recovery partition that the manufacturer put there. You don't want to change that one: just resize the Windows one.

> Do you recommend me resizing it automatically or manually? The size of the harddrive is 74.23GB and is Using 48.22GB. Now, 26.01 GB is free

I would do it manually, to make sure that you are not affecting that other partition. You can only resize it a bit because it is already quite full. The partition is 74 Gb and is using 48 Gb, so that leaves 26 Gb currently free. So I would shrink it down to 61 Gb. This means that in Windows you will have 13 Gb free, and that you will have 13 Gb for Linux.


> When im the options and when the first one is selected, on the bottom there is a bar in which of course i select the new partition size. It automatically goes to 50% (36.0GB)

In your case you can't shrink windows that much because you have too much data in that partition! The minimum size would be 48 Gb (65%), but like I said, since you want free space in Windows, don't make it too small! I suggest shrinking to 61 Gb (82% of current size).

> EDIT - What im hoping for most is that i can be able to download and use stuff from Windows and Ubuntu. Like in Ubuntu, I want to be able to locate files that i use from windows in ubuntu, I hope that is possible.

Yes. When you're in Ubuntu you will be able to read files from Windows, so you will still have access to your documents, music, etc. There is also a plugin for Windows that will let you read and write to the Linux partition, so regardless of which OS you are using, you will be able to see the files on the other OS.

---

### Post by djvic87 on 2007-02-08
Kebes this is what I did, I resized the windows partition to 62GB and and made a new partition as ext3 with 12.87GB,  now it took me to the prepare mount points, what should I do next? 
Or did I did something wrong?

EDIT - the mount points are 

1. zmedia/sda1 - partition 1 disc primary
2. (blank)         -  partition 2 disc primary - then there is like a checkmark on the second mount if i want to reformat
3. (blank)         - (blank?)

---

### Post by kebes on 2007-02-08
> **djvic87 said:**
> Kebes this is what I did, I resized the windows partition to 62GB and and made a new partition as ext3 with 12.87GB,  now it took me to the prepare mount points, what should I do next? 
Or did I did something wrong?

Sounds like you're doing everything right. In addition to creating a 12Gb ext3, you should have create a small (~1Gb or 500Mb) swap partition.

On the "prepare mount point" you simply assign names to the partitions. So the 12Gb ext three has to be called: "/"
The Windows should be called "/media/windows/" (it can be anything, actually, so if it assigned it a default name, that's fine).
Then you should have a swap partition that is called "swap".

---

### Post by kebes on 2007-02-08
> **djvic87 said:**
> 1. zmedia/sda1 - partition 1 disc primary
2. (blank)         -  partition 2 disc primary - then there is like a checkmark on the second mount if i want to reformat
3. (blank)         - (blank?)

1. This is Windows. The name is fine. Make sure it will NOT reformat.
2. This is probably the ext3 Linux (is the size 12Gb?). If so, then set mountpoint to "/" and click the checkbox for reformat.
3. I don't know if this is a linux swap that you made, or the "mysterious" extra partition on your hard drive...

---

### Post by djvic87 on 2007-02-08
So what do you think about the swap? Because i didnt made any partition for the swap. Also im worried about the partition part of the swap, it is blank.  Isnt the swap suppose to have a size because on the size part it doenst show any size for the swap.

Oh yeah, the third mount point is 3.swap size, blank, and partition is blank also.

---

### Post by kebes on 2007-02-08
Since you didn't make a swap that partition you are seeing is some sort of system partition, so leave it alone.

You can go back to the previous step and remove the Linux partition, and then recreate it a bit smaller (12.0 Gb instead of 12.87). That way you will have a bit of space to insert a swap partition. A swap is diskspace for virtual RAM, so it doesn't have to be big. 512 Mb or 1Gb is enough.

Hope that's clear.

---

### Post by djvic87 on 2007-02-08
O ok, so simply, when i go back to making the partitions, how do I make the swap partition, like where should I put it?

---

### Post by kebes on 2007-02-08
> **djvic87 said:**
> O ok, so simply, when i go back to making the partitions, how do I make the swap partition, like where should I put it?

Instead of a single 12.8Gb partition for Linux, make two partitions:
12.0 Gb for Linux (ext3)
0.8 Gb partition for swap (swap)

Put the Linux one first, the swap right after it. The exact sizes don't matter, so make Linux 12.0 Gb and then use the rest of the space for swap.

---

### Post by djvic87 on 2007-02-08
whhen i try to do a new partition, it doesnt let me under the second partition, neither the firs partition. Or do i have to extend the second partition for the swap?

EDIT - Can you tell me how to start it up all over again for that swap on the prepare partition part? make believe that you are me and write down everything that you are about to do lol sorry if this sounds ridiculous, im excited that im halfway there.

---

### Post by kebes on 2007-02-08
Well probably nothing on disk has been changed. So press "Back" until you get to the "prepare disk space" screen, then select "manual" again and start over. You will then again see your big Windows partition (74 Gb). Right-click, resize it to 62 Gb. You will then have free space that is 12.8 Gb big.

Right-click in the free space, add a new partition that is 12 Gb, formatted ext3.

This will leave 0.8 Gb free space. Right-click there, add a partition that uses all the space (0.8 Gb) and make the type "swap".


Then click forward and assign the names:
```

/media/sda1  62 Gb (partition #1) format: NO
/                   12 Gb                     format: yes
swap             800 Mb                   format: yes

```

---

### Post by djvic87 on 2007-02-08
what i did now was thate the "/" part 12 GBs and then the swap is partition 3, with 502MB is that ok? Also, is it normal if they are all primary partitions? 

And finaly, when i made the the swap partition, the filesystem i named it was ext3 BEFORE preparing the mount, is everything ok so far?

EDIT - and of course media/sda1 is the windows partition, which is the first one

---

### Post by kebes on 2007-02-08
> **djvic87 said:**
> what i did now was thate the "/" part 12 GBs and then the swap is partition 3, with 502MB is that ok? Also, is it normal if they are all primary partitions? 

Sounds perfect.

> And finaly, when i made the the swap partition, the filesystem i named it was ext3 BEFORE preparing the mount, is everything ok so far?

Not sure what you mean by that. I think you mean that when you made a new partition for swap, the default said "ext3" but you changed it to "swap"... right? If so, you did the right thing!

> EDIT - and of course media/sda1 is the windows partition, which is the first one

Sounds like everything is ready. So in your prepare mount points you have three things:
```

/media/sda1  62 Gb (partition #1) format: NO
/                   12 Gb                     format: yes
swap             502 Mb                   format: yes

```

You can now click "Forward" and it will confirm that this is what you really want to do. If you click "Install" it will then resize and do formatting!

---

### Post by djvic87 on 2007-02-08
lol the thing about it, before doing the partition for swap, it said linux-swap, is that ok? And no, i named it ext3. But is it ok to place it as swap when im going to the mount option?

---

### Post by kebes on 2007-02-08
> **djvic87 said:**
> lol the thing about it, before doing the partition for swap, it said linux-swap, is that ok? And no, i named it ext3. But is it ok to place it as swap when im going to the mount option?

Er... I'm a little confused. Can you post a screenshot?

The 12 Gb partition should be type "ext3" and will be mounted at "/"
The 500 Mb partition should be type "linux-swap" and will be mounted as "swap"

---

### Post by djvic87 on 2007-02-08
O lol nevermind now i got it thanks!

I hit next and now it say grub will install to hdo 
What do you think?

It also says that it will install to partition 2 and somethin of swap for partition 3

---

### Post by kebes on 2007-02-08
Sounds good!

("grub" is the "bootloader" that allows you to pick between Windows and Ubuntu at boot time.)

Click "Install" and let it go!

---

### Post by djvic87 on 2007-02-08
now it told me to go back because partition 1 doesnt have a filesystem, something like that. What now?

---

### Post by kebes on 2007-02-08
Can you write the exact message? (Or post a screenshot...)

In the previous screen, partition was was set to mount at "/media/sda1/" right?

---

### Post by djvic87 on 2007-02-08
yes, it was to mount to media/sda1 without the / at the end though

---

### Post by smradek on 2007-02-08
Hi.
I have the same problem. I bought HP Pavilion dv6151 (dv6000 serie):
# Intel Core 2 Duo 5200 (1.6 GHz, 1MB L2 Cache, 533MHz FSB) Chipset Intel® i945PM
# 1024MB DDR2 667MHz FSB (2 DIMM)
# Hard disc 120GB 5400ot/min SATA
# Display 15.4WXGA high definition BrightView (1280x800)
# Grafika NVIDIA GeForce Go 7400 s 128MB
# DVD+/-RW SuperMulti
# Webcam 1.3megapixel
# 5-in-1
# Ports: 1 express card/54, 3x USB 2.0, 1394, IR for remote control, RJ-45, RJ-11, 2x headphone output with 1x SPDIF, S-Video output, VGA output, Repro Altec Lansing
# 56K modem, 20/100 LAN, 802.11 a/b/g Intel MOW, Bluetooth

Windows XP Media Center and Software QuickPlay (boot without running Windows - be it slightly start and when skip to this software) preinstalled. Here information about partitions:
/dev/sda1 - ntfs - 102.28 GB, 10.42 GB (used), 91.86 (unused)  boot -- Windows
not alocated - not alocated - 7.84 MB  -- --
/dev/sda2 "!" - fat32 - 8.50 GB -- -- this part should be for Recovery DVDs...
/dev/sda3  - ntfs - 1GB, 9.78 (978.99 MB) - 48.61MB -- this should be for for QuickPlay

I want QuickPlay partition to stay in function. 
What do you recommend to do with Windows boot partition?
And what version of Ubuntu?
I tried Ubuntu LiveCD 6.06 and Kubuntu6.10_amd64 DVD as a live CD and find hereabove partitions.
Everything (volume control,wifi,LAN,remote control!) looks that works proprely but I couldn't find network manager in Kubuntu's KDE and don't know how to use bluetooth.
What do recommend me?
Thank you very much. I'd like to have both systems (Windows and Ubuntu) on my laptop.

---

### Post by kebes on 2007-02-08
> **smradek said:**
> 
/dev/sda1 - ntfs - 102.28 GB, 10.42 GB (used), 91.86 (unused)  boot -- Windows
not alocated - not alocated - 7.84 MB  -- --
/dev/sda2 "!" - fat32 - 8.50 GB -- -- this part should be for Recovery DVDs...
/dev/sda3  - ntfs - 1GB, 9.78 (978.99 MB) - 48.61MB -- this should be for for QuickPlay


Yeah like djvic87, your best bet is to resize /dev/sda1 to make room for Ubuntu. You will need a minimum of ~7Gb for Ubuntu. In your case you have more space to work with, so it's up to you. (Depends on what you want to use Ubuntu for.)

So you could take /dev/sda1 and resize it to 80 Gb. Then in the 20 Gb free space created, make a 19 Gb Linux root partitions (type: ext3; mountpoint: /), and in that final 1Gb, make a swap (type: linux-swap; moutpoint: swap).

Leave the other partitions intact, and everything should be fine.


(Note that manufacturer-installed recovery tools will normally erase Linux without warning if you ever use them...)

---

### Post by djvic87 on 2007-02-08
kebes, what should i make sure about the partitions before getting that warning message again? now, im in the normal desktop.

EDIT - i added the "/" next to the letters of the first mount , and looks like its installing now. is it ok?

---

### Post by djvic87 on 2007-02-08
oops sorry twice post

---

### Post by kebes on 2007-02-08
djvic87,

Start the install over. Do the same thing as before. Make sure that you set the linux partition as "ext3" and the swap partition as "linux-swap" during the partitioning phase.

Then in the mount phase that follows, make sure that you mount the (bigger) linux partition as "/" and swap as "swap."

The windows partition will be automatically set as "/media/sda1", which is fine. Don't change it. (And don't format it.)


Then click "Install". If it gives you an error message, copy it down carefully and post it here. (It would also help if you copied exactly what it shows on screen during the partitioning and mounting phases.) It's hard to know what's going on, since I can't see exactly what you're seeing!

Good luck!

---

### Post by djvic87 on 2007-02-08
uh oh, too late.

when i started it all over, i put the / next to the /media/sda1. and yes i did the other part, right now seems to be installing. Do you think that it is fine that the first partition is /media/sda1/ ?

---

### Post by kebes on 2007-02-08
> **djvic87 said:**
> uh oh, too late.

when i started it all over, i put the / next to the /media/sda1. and yes i did the other part, right now seems to be installing. Do you think that it is fine that the first partition is /media/sda1/ ?

If it's installing, that's fine. It doesn't matter what order the mountpoints are listed in. As long as you didn't format the Windows partitions (/media/sda1) then you're fine.

---

### Post by djvic87 on 2007-02-08
!! Holy smokes I did it thanks Kebes!! 
Wow, i feel much better now. 

I dont know from where to start, but man thanks again for your help. im happy that windows xp is still there, whats funny is that there are other ubuntu boot up, what's the appropriate one?
but thanks again man..

---

### Post by kebes on 2007-02-08
> **djvic87 said:**
> !! Holy smokes I did it thanks Kebes!! 
Wow, i feel much better now. 

I dont know from where to start, but man thanks again for your help. im happy that windows xp is still there, whats funny is that there are other ubuntu boot up, what's the appropriate one?
but thanks again man..

On the bootup, you probably see options like:
Ubuntu, kernel 2.6.15-26-386
Ubuntu, kernel 2.6.15-26-386 (recover mode)
Ubuntu, memtest
Windows XP

The first is "normal Ubuntu"... that's the one you want.
"recovery mode" is in case you run into problems and can't load normal Ubuntu. You'll probably never use it.
"memtest" is to test your memory, again if you have problems.
"Windows XP" is your Windows, of cours!

Note that as you update Ubuntu, it will add entries to this list. That means that you'll be able to pick the newer or older kernel, as you wish. Normally you want the newest kernel (the one with the highest number, first on the list)...


Anyways, I'm glad you got it all working! Now you can play with it and see if you like it. I hope you enjoy it. You're quite welcome for all the help. In a couple of months you'll be the one answering questions from new users!


If you have any more questions about Ubuntu, you can post in the forums again. (It's best to start a new thread for each new question/problem you have.)

---

### Post by smradek on 2007-02-08
> **kebes said:**
> Yeah like djvic87, your best bet is to resize /dev/sda1 to make room for Ubuntu. You will need a minimum of ~7Gb for Ubuntu. In your case you have more space to work with, so it's up to you. (Depends on what you want to use Ubuntu for.)

So you could take /dev/sda1 and resize it to 80 Gb. Then in the 20 Gb free space created, make a 19 Gb Linux root partitions (type: ext3; mountpoint: /), and in that final 1Gb, make a swap (type: linux-swap; moutpoint: swap).

Leave the other partitions intact, and everything should be fine.


(Note that manufacturer-installed recovery tools will normally erase Linux without warning if you ever use them...)
Thanks.
I want to use Ubuntu for work (Now I have Suse and Ubuntu on my computer in my job). So I would like to use the most large part of the space for Ubuntu and linux aplications.
How would you suppose to resize /dev/sda1? I'm not sure if to use grub..I heard and read that it is maybe better to let boot windows disc and change it before linux instalation. I fear about QuickPlay Part how I would it boot if this way will break down....

---

### Post by kebes on 2007-02-08
> **smradek said:**
> Thanks.
I want to use Ubuntu for work (Now I have Suse and Ubuntu on my computer in my job). So I would like to use the most large part of the space for Ubuntu and linux aplications.
How would you suppose to resize /dev/sda1? I'm not sure if to use grub..I heard and read that it is maybe better to let boot windows disc and change it before linux instalation. I fear about QuickPlay Part how I would it boot if this way will break down....

You can resize /dev/sda1 to a small as you want, if you want more space for Ubuntu.

During the Ubuntu installation, when you reach the partitioning phase, you can select "manual" and change the size of your current partitions.

You need to install grub so that you can pick between Windows and Ubuntu at boot. (There are other ways of doing it, such as not installing grub and always using a CD or floppy disk to initiate the Ubuntu boot...)

I know nothing about QuickPlay so I don't know if moving partitions around will break it.

---

### Post by smradek on 2007-02-08
> **kebes said:**
> You can resize /dev/sda1 to a small as you want, if you want more space for Ubuntu.

During the Ubuntu installation, when you reach the partitioning phase, you can select "manual" and change the size of your current partitions.

You need to install grub so that you can pick between Windows and Ubuntu at boot. (There are other ways of doing it, such as not installing grub and always using a CD or floppy disk to initiate the Ubuntu boot...)

I know nothing about QuickPlay so I don't know if moving partitions around will break it.

Nevertheless, thank you. I'll try to do some copies of the most important partition of disc - recovery and that part for QuickPlay (software for playing movies, audio and enable to show pictures) - based on QuickTime I suppose, before the very first try...I hope that this partition will be possible to recover.

---

### Post by smradek on 2007-02-10
Hello Once more.

I worked!

Here solution for HP (Pavilion dv 6151) laptops:

I suppose that you have partitions like me (and always than you have 4 partition on your hard disc)

/dev/sda1 - ntfs - 102.28 GB, 10.42 GB (used), 91.86 (unused) boot -- Windows
not alocated - not alocated - 7.84 MB -- --
/dev/sda2 "!" - fat32 - 8.50 GB -- -- this part should be for Recovery DVDs...
/dev/sda3 - ntfs - 1GB, 9.78 (978.99 MB) - 48.61MB -- this should be for for QuickPlay


First of all you should shrink your Windows partition.

Defragment your windows disc.

I would recommend Partition Magic (8.0) since GParted using live version of Kubuntu 6.10 (maybe problem only with that version) fell down.

You will do partitioning with Partition Magic - change the first partition as you want (40GB for example)

-make the rest partition as extended and unallocated.


This will not work with Partition Magic 8.0 and XP. It will stop at the beginning and show error message #983 = "too many errors". 
This is common error when your hard disc drive has one unallocated partition with less than 8MB! Typical for some other HP (Compaq) laptops.

When you will boot to your system. Please make chkdsk /f or chkdsk /r in command line or simply start Check disc. System will ask you to reboot so let him to do.

After check disk your partition magic will work


Now you have disc partition on that you could write your system.

Chose your Ubuntu version according tu your experience from live CD. I do not recommend Kubuntu 6.06 - I installed it but neither touchpad nor volume controls worked properly.... I finally chose Kubuntu 6.10

As my machine is 64bit I choose amd64. For this special case - we will install GRUB to the extended partition ! I strongly recommend to use alternate CD or complete DVD and chose install in text mode. Otherwise you will install it to primary partition and Grub will not be able to start QuickPlay!!!!

So install using text mode, chose partitioning according to what installation recomend you:

I will show you for example:

1. primary 40GB K ntfs /media/sda1 ..........."Windows"

5. logical 12GB F ext3  / .........."root"
6.logical 43GB F ext3 /home......."home - only if you decide like me to do home and root separated"
7.logical 2.2GB F swap......"swap - depends on your RAM, me 1GB RAM"
2. primary 9.1GB K fat32 /media/sda2..........."Recovery for Windows"
3.primary 1.1GB K ntfs /media/sda3.............."QuickPlay"

Write down for you your partitioning.

When installation ask you where put GRUB. Chose NO for primary disc and type for ex. /sda5   - our root partition.


No You have installed Ubuntu but you couldn't start it and boot to it. To do this you firstly take some Linux live CD (for example your instalation - if DVD - of Ubuntu) and type:

dd if=/dev/sda5 of=/bootsek.lnx bs count=1

this will make a file that will enable boot to linux. You should copy this file to Windows C:\

I am not sure if direct write to your ntfs disc is the best way after everything..:)..So I recommend to made a copy to some device you could after connect to your Windows - CD, DVD, USB or your remote computer....


When boot to windows and copy bootsek.lnx to C:\

Find C:\boot.ini (hidden) and edit. You can find procedure how to do it on Micrtosoft Windows pages...

and write on the last line:
C:\BOOTSEK.LNX="Linux"

save.

maybe you should change attributes but I don't how to do it now..some manual I found.


Now you could finally reboot and you will see:
-Microsoft XP
-Linux

 if you choose Linux it will start GRUB where you could choose Ubuntu or Windows too...


And it should work properly.
Only if you will start to QuickPlay you should shut down it properly or in other words you could not let Windows "hibernating" (as happend to me..:-)). If it happend you must only restart to windows and terminate it properly!


For me still problem with wifi...? and ADSL instalation...?

I hope that it could help somebody with the same problem with QuickPlay on hardisc....

---

