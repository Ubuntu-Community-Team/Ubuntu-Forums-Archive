---
title: "ich10 fake raid"
date: 2010-07-03
forum: Installation &amp; Upgrades
---

### Post by Rody on 2010-07-03
I have been using Ubuntu for a long time now, but there is something that really bothers me. Why wont it use my raid array? I relize that it is fakeraid but i have not been able to use it on ich 9 or 10 and maybe some before that. 

So I have had some time off and have been banging my head trying to make it work, heck I would be happy if I could just access the raid array from my ubuntu install. 

There are other distributions out there where it just works, but I have really liked Ubuntu and the Ubuntu community and don't want to switch. I have been trying this every release and still no luck.
I don't need an expensive raid card I can do it with my motherboard raid and.....
[http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)
any way, if there is a simple way to do it please help, if not then I may have to play around till i find another distribution that I like.

---

### Post by darkod on 2010-07-03
Do you need to dual boot with windows on the fakeraid? Because if you don't, using software raid is much better solution.

Was there any particular errors/symptoms all those times the install was failing? You are using the Alternate Install CD right? Some people keep claiming you can use the Desktop version cd but I still think it's better to listen to ubuntu.com and use the alternate cd for raid and/or LVM as suggested.

---

### Post by Rody on 2010-07-03
yes I used the alt cd, and it will reconize that I have a raid array but that is it, it does not see partitions or even give me a screen where i could creat partitions. I have 3 drives on my computer 1 regular and 2 raid 0,and the only option it gives me is to use the non- raid drive.

I tried to install dmraid after the install and ran sudo dmraid -ay

and it listed my 2 arrays as active and my 3 partitions as inactive, and i could not figure out how to activate the partitions.

---

### Post by darkod on 2010-07-03
I'm not sure if it's related, but I have noticed that if there is any error in the partition table, Gparted shows a blank drive with no partitions on it. Maybe the alt cd partitioner does the same if it can detect any type of discrepancy in the array.

You could use the lice cd to boot into live mode, and run:

sudo fdisk -l

to see if the partition sizes and layout matches.

---

### Post by ronparent on 2010-07-03
If your only issue is accessing the raid, if your fakeraid chipset is supported by dmraid (and I believe it is), 10.04 will boot with your raid drives visible in nautilus and mountable. You can test this with the 10.04 desktop live cd. As darkod noted you might have to fix any partition table for a partition that doesn't show up. 

Can you see the 3 raid0 partitions in windows? Did you possibly move the drives from anothe MB?

There are other issues if you want to install to the raid. It is doable and I currently run Ubuntu 10.04 and Mint 9 on a raid0. If you are interested, I can provide more detail. 

The main issue you have to cope with in 9.04 and earlier is that you have to mount the individual raid partitions in fstab to mount points you have to create in your file system for that purpose.

---

### Post by Rody on 2010-07-05
windows is loaded on one of the raid partitions and the other 2 are storage. I don't think i could access them from the 10.04 desktop cd but I am not 100% sure I tried. 

I don't need to install on the raid, though If i can figure out a way to make it work I probably will.

thanks for the help.
rody

ps
on a side note I loaded up fedora 13 and it found my raid array and I could access it no problem. Unfortunately I have discovered that i truly dislike the way things are laid out and I don't like their package manager. I guess I have gotten to be a lazy Linux user, that didn't use to be possible.

---

### Post by ronparent on 2010-07-05
If you want to install 10.04  on the raid0, make sure you pre-create/format both the swap and /with an earlier version.  Also create those partitions in an extended (I don't know how many of your current partitions are primary, but, you are limited to four primaries including the extended). Yell if you need helo.

---

### Post by Rody on 2010-07-07
well I am backing up my raid array and going to give a few things a try. I discovered while messing around that the second drive in my array still has old partition information on it from a previous install when it was not in a raid array and maybe that has ubuntu confused a bit. 

I am going to zero both drives and see what there is to see.

thanks again for your help
rody

---

### Post by Rody on 2010-07-14
Well I had some time to mess around a bit and totally wiped my raid array and remade it, and discovered some interesting things.

Ubuntu will see the raid array and it will format the raid array as long as there is only one partition on it, so for windows 7 which makes a 100mb boot partition, It makes the whole drive unreadable to ubuntu, but if I format the drives while in ubuntu with ntfs the windows installer will not see the raid array. I wonder if the fact that windows trys to hide the 100mb partition has anything to do with the problem.

on a side note, not mater how I partition the drives fedora 13 can read the partitions no problem, so it seems that I need to do some manual configuration to make this work in ubuntu. 

I will do some research and find where dmraid hides its config files and compare the 2 versions.

rody

---

### Post by Rody on 2010-07-15
I am not sure what happened but I can read all raid partitions now. Very strange.

thanks again for everyone's help,

rody:p

---

