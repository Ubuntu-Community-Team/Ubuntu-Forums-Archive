---
title: "Shared partition between 9.04 and Vista"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by AimeeTheGreat on 2009-11-20
If you're lazy just read the bold parts. I'm not sure how much of this is actually important, so I just decided to do it all.

First: I'm a noob, but I know some things about computers, so try not to use too much baby talk with me. (If I don't know something, I'll ask.) 

For some reason, I couldn't shrink the NTFS partition (I tried several tools.) So I did a backup and wiped the whole thing and then installed Ubuntu 9.04 yesterday. Because I had a proper disc for it. My CD drive is extremely noisy with burned CD-Rs. 

Then I upgraded to 9.10, which killed my sound, so I reinstalled back to 9.04. I was up till 2 am and I had to recopy all my files over which was a major pain in the ***. I'll wait till the bugs are ironed out until I upgrade it.

**Then the next morning, my mom freaked out over me installing Ubuntu.** Because this is technically a rent-to-own computer and although they said they had no problem with me using different OS, my mom's convinced that they'll charge us for reinstalling Windows.

I made a compromise with her and said **I'll do a dual-boot of Vista Home Premium** (I have a retail version) and Ubuntu.

So, what I want to do, is **create a shared data partition between the two OSes.** I have a slight habit of borking up operating systems ;) and it's a pain to restore from a backup. And I don't want the files to be trapped on one operating system in case something happens.

**I have a 500 gig drive.** For the data partition, I have a lot of large DVD files, so it needs to be somewhat big enough. (Also be nice to share the Firefox settings between them.) For the Windows partition, I play a couple of multi-gigabyte games and would need some space for that, too. I don't know how big Ubuntu should be because I haven't used it long enough. I know it only takes up about 4 gigs so it could probably be a bit smaller.

Couple questions:

1) Which filesystem should it be? I think Vista doesn't like ext3. I read Ubuntu doesn't like NTFS (although it might be slightly outdated what I read.) I read FAT32 is crap.

2) What should I use to partition the partitions? Also, which letter should I assign to each logical drive?

3) How big would you make each partition? 

4) What is this about a Ubuntu swap partition? I'm not sure what it means.

5) What about Vista overwriting the bootloader? Should I empty the hard drive, partition it, install Vista, THEN install Ubuntu? I'm not scared of the command-line, but I suck at it.
6) Anything else I miss?

Also, any instructiions, could you please put into small steps for me? I have a bit of a developmental disability (not going into it right now) making it hard for me to digest more than a little bit at a time. Which is why I'm having some trouble currently with stuff I googled.

Thanks for bearing with me.

---

### Post by darkod on 2009-11-20
1. NTFS. Windows can not see linux partition at all. Ubuntu is quite good with NTFS, it was long ago when it didn't work good.
2. You can use vista installer for the first ntfs for the system. After you have vista up and running it's your choice whether to create the data ntfs with windows or ubuntu. You have to create ubuntu partitions with ubuntu, windows can't do that.
3. For Ubuntu it's enough 10-15GB for / (root), 2-5GB for swap, and 10-15GB for /home. If you don't want separate home add that space to /. Depending how much space you can spare for Ubuntu, tweak the numbers. You don't need more than 25-30GB in total depending what you will do with it. Just for comparison, when installed Ubuntu takes 2.7GB on / while Vista around 20GB.
4. swap partition is like windows swap file only it isn't a file but actual partition mounted as swap area. You can do wihout it and actually create swap file but the default way is better.
5. Empty drive is always perfect for start, if you can delete all partitions/data on it. Then Vista is always first, Ubuntu second. It will pick up Vista automatically. And there is no "command line" if you mean when installing Ubuntu. While you can do it with command line if you want, the standard installer is GUI.

After you decide the space for Ubuntu and Vista system, use the rest for the ntfs data. That should be it. Enjoy Ubuntu.

PS. The rule for swap size was twice the amount of ram but with todays systems having loads of ram you don't have to follow that. If you are not often using sleep/hibernation in Ubuntu, even 2GB will be enough for swap. For example I have 4GB ram and 2GB swap and I think it's not even used often. Select the size depending how many GB you can spare.

---

### Post by AimeeTheGreat on 2009-11-20
Thanks.

The command-line thing is from something about the bootloader issue that I printed off at school. (I look up stuff on the computers when I'm finished work and as long as I don't overdo it the teachers don't mind me printing things. My printer's out of ink and just makes pink lines.) Something about editing certain files which seemed overly complicated for me. For NOW. :p

One other question: For the data drive, what's the best way to get compatibility between the Ubuntu home folder and the Vista user folder? 
Suppose you have the pictures folder. In Ubuntu, I want to be able to go to Places > Pictures and get into the folder. In Vista, I want to be able to go to User Folder > Pictures and get into the same place. Do I make sense?

---

### Post by darkod on 2009-11-20
In 99% of situations everything will work perfect automatically. Lets hope you're not in the 1%. :)

---

### Post by AimeeTheGreat on 2009-11-20
I'll give it a try now.

---

### Post by confused_user on 2009-11-20
HI, i have not got time to read all the responses to your post but i just wanted to say that i am dual booting windows 7 and ubuntu 9.04 and am successfully sharing a home partition.

I've done this a number of times in the past and have found the best way to do it is to not use NTFS for the shared file system.  You get very high cpu (and poor performance) when using the linux NTFS driver and limited permission management. 

What i have done is set my /home partition to be ext3 (i dont trust ext4 yet) and in windows i use Ext2 IFS ([http://www.fs-driver.org/](http://www.fs-driver.org/)) in windows to be able to mount / read and write to it from windows.

It's great.

SO you have all your linux settings and files on a separate /home partition in ext3.  You can reinstall your OS and still keep all your settings and files.  Windows can read and write to it as well.

IN terms of sharing a firefox profile, i'm working on that right now, i'm making some progress - i can use the default UBuntu profile in Windows but have not yet managed to get my user profile working in windows, close though.

This thread should help you (near the bottom is some links) - [http://ubuntuforums.org/showthread.php?t=786395](http://ubuntuforums.org/showthread.php?t=786395)

---

### Post by darkod on 2009-11-20
I am sharing my Thunderbird profile on a NTFS drive but I have no experience beyond that. Not sure whether you can share pictures/documents/music folders just like that.

Besides one of the main characteristics of linux is the reliability working on its ext3/ext4 filesystem. Having linux look into ntfs constantly might degrade performance seriously.

---

### Post by confused_user on 2009-11-20
A quick how to on how to share your firefox profile between os's

1: I use ext2 volume manager to mount my ext3 /home partition in windows 7
[http://www.ext2fsd.com](http://www.ext2fsd.com)

2: Close firefox

3: backup your C:\Users\matt\AppData\Roaming\Mozilla\Firefox\prof iles (my username is matt)

4: your profile file looks like this

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=Profiles/j0zg5dyb.default

5: All you need to do is change the Path to point at your ubuntu firfox profile.

Mine is located in F:\matt\.mozilla\firefox\6rkdyos0.default since i used ext2fsd to mount my /home partition on F:/

6: MY new profile file looks like this

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=F:\matt\.mozilla\firefox\6rkdyos0.default
Default=1

7: Start firefox

8: Bask in the glory of having the same bookmarks, saved passwords and, extensions (addblock filter!!) and everything else on both your windows and your ubuntu OS.

It's more or less the same process with Thunderbird i think, i dont use thunderbird though so have not tested it.

---

### Post by AimeeTheGreat on 2009-11-20
I set it up this way:

About 200 gigs for Vista (may shrink later if it's too big, but I'd rather have too much space than too little)
200 gigs for Data
the remaining for Ubuntu. (Logically, it should be 100, but for some reason it's 85.6 or something. Ubuntu is small, so I'm not too worried.)

The Vista and Data are both NTFS, the Linux is ExtSomething (I dunno which number it is currently.)

The Data partition shows up in Vista, however in Ubuntu I open up Places>Computer and get the Vista drive, the CD drive, and the filesystem. Where did the Data partition go? 

Sorry for my noobishness.

EDIT: Here's a screenie. I have no idea why the Vista drive shows up as 214, unless it's something to do with the sector size. I can access it just fine.

[IMG]http://img121.imageshack.us/img121/3740/screenshotcomputerfileb.png[/IMG]

ANOTHER EDIT: LOL, I googled it, and this thread was the first result. Got mostly outdated stuff, though.

---

### Post by darkod on 2009-11-20
If your NTFS partitions have names (you can set it up in windows, doesn't need to be in ubuntu), then they will show in Places, usually under Computer (but not inside Computer).
As a protection measure, the NTFS partitions are not mounted automatically when starting Ubuntu. In Places click on the NTFS partition, it will ask you for your Ubuntu password again, and it will mount it. Then you can browse it.
Latr if you want to, there are tools to automount NTFS partition when ubuntu starts.
PS. Even if the partition have no names they will show in Places, but with names it will be easier to tell them apart especially since both are equal.
And you were left with only 85GB for ubuntu, because of the way HDDs are marketed.
500GB means 500 bln of bytes. But in fact 1GB is not 1bln, instead it is 1024*1024*1024. That creates the difference.

---

### Post by AimeeTheGreat on 2009-11-20
I didn't name it yet. In Vista it just shows up as D (or something like that.) I'll boot to Vista and try renaming it.

When I looked in Places, it just showed the Vista one. When I tried browisng it asked for my password but otherwise was fine.

Actually, a while ago, I was doing some research on hard drives. And I found out that the manufacturers often define a gigabyte as 1000x1000x1000. Which is technically correct. The 1024x1924x1024 is a gibibyte (I think.) This is as far as I understand. Something about binary/decimal.

Thanks, I'll be back in a couple minutes unless something comes up

---

### Post by AimeeTheGreat on 2009-11-20
OK, I booted to Vista and tried to rename it. It was very simple, I forgot to format the partition. I named it to Data. It now shows up.

Now, how do I move the home folder to it?

---

### Post by darkod on 2009-11-20
Can't help there. You have to read more about it. And I'm not sure it's advisable to have home on NTFS partition.

---

### Post by AimeeTheGreat on 2009-11-20
Well, I do know how to get the Vista folders onto another drive. I'll try googling about the Home folder, if I find anything that works I'll post it.

EDIT: Found out that moving it apparently breaks it. Is there a way to get the Documents/Pictures/Music/Videos to point to a different place?

---

### Post by darkod on 2009-11-20
If you are asking about windows documents/videos/music links, yes they can point to other drives but not linux ones. They can't see the filesystem. That's why you have only C: and D: in Computer (windows).
There are some ways to read ext2/ext3/ext4 from windows but I don't think it should be used all the time. And many people think it's a very, very bad idea to let windows mess around with your linux partitions and that's exactly what you would let it do. There must be a good valid reason for it. :)

---

### Post by AimeeTheGreat on 2009-11-20
Think you misunderstood. Data is a NTFS partition, so I can get Vista to point to it. Is there a way to get the Ubuntu folders to point to it instead of the folders created?

---

### Post by darkod on 2009-11-20
Don't think so. Either way round I don't think it will work, not without major procedure and risk. :)

---

### Post by AimeeTheGreat on 2009-11-20
I googled it, and got something about changing them to symbolic links. How exactly do I do that?

I'll be right back again, just going to change the Vista folders. :)

(Another thing is that while a lot of people call Vista crap, I haven't had too much problem with it. Except when I tried to install SP1.)

---

### Post by AimeeTheGreat on 2009-11-20
Here's a screenshot to try to better explain:

[IMG]http://img688.imageshack.us/img688/4846/screenshotg.png[/IMG]

What I want to do is take the icons from "aimee -- file browser" and have them point to the folders in "Data." Does that make sense now? I'm terrible at explaining things.

---

### Post by darkod on 2009-11-20
I understand you perfectly even without the screenshots. But I am also quite new to Ubuntu and have no idea if it's possible at all. I don't think you can just point /home folders just like that, plus to a ntfs partition. And even if you manage to do it it will probably affect performance and data integrity.

---

### Post by AimeeTheGreat on 2009-11-20
I figured out how to create a symbolic link. I think I've got it all setup now. Yay!

---

### Post by AimeeTheGreat on 2009-11-21
For some reason I couldn't find the thing to change it to Solved. But I got it all figured out now so could someone change it for me? Thanks :)

---

