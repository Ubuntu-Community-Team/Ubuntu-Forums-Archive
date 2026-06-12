---
title: "Ubuntu 10.10 Dual boot, newbie question"
date: 2010-11-22
forum: Installation &amp; Upgrades
---

### Post by JojAGT on 2010-11-22
Hi all!
Well just let me tell you that I'm a total newbie on ubuntu, so please forgive me for that. #-o

All right, want I want to do is to have both OS, win7 and ubuntu 10.10 and I was reading a "How to dual boot with ubuntu" on here [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

So I read everything, but I still have some questions I hope this site of the forum is the right place to ask.

Ok, so I have 2 partitions, in the first partition I have win7 on it and a have a second partition (50gygs) that is NTDS where I want to install ubuntu. 

1) In that guide, it mentioned that Win vista doesn't have the same boot system that winXP has, so you have a prosidure for Win vista that it's explained there. So my question is. Is it the same procedure on win7?

2)On that guide they suggest you to do a Backup of your data. I don't really want to do it. So my second question is: Does ubuntu format my disk? or can I just install it on my second partition

3) I was reading that ubuntu should be installed on a ext4 format disk (Read a guide for double booting with ubuntu 9.10),but i didn't saw anything of that on that guide. And if my partition need a different type of partition, how can I take it from NFTS to ext4.

---

### Post by cwa on 2010-11-22
*"2)On that guide they suggest you to do a Backup of your data. I don't really want to do it. So my second question is: Does ubuntu format my disk? or can I just install it on my second partition"*

You should always back up, even if you don't want to. I have learned many hard lessons of not having backups or current backups. Unless you truly don't care about your data or need it. But ubuntu can/does/will format your disk, but it will only format what you tell it to format. and you can choose to partition your hard drive so that you can install it where you want to. 

[I]"3) I was reading that ubuntu should be installed on a ext4 format disk (Read a guide for double booting with ubuntu 9.10),but i didn't saw anything of that on that guide. And if my partition need a different type of partition, how can I take it from NFTS to ext4."
[/I]

I don't know if Ubuntu performs best on ext4, but You can run Linux on many partition types, even FAT in some cases. Though I don't think I would recommend that. You can set the partition type typically during the partitioning section of the install.

cwa

---

### Post by Quackers on 2010-11-22
The Ubuntu installer will format the partition to ext4.
If you install Ubuntu in the second partition on your system you will lose whatever is in that partition now! 
If you decide to install anyway I would recommend you use the manual partitioning option, not the alongside option - things can go horribly wrong choosing the alongside option!

---

### Post by JojAGT on 2010-11-23
@cwa thank you very much, for the info.

@Quackers than pretty much answer my 2 questions

but I still wonder if the Dual booting process is the same for Windows Vista and Windows 7

PS: Thank you very much guys.

---

### Post by oldfred on 2010-11-24
Vista & win7 use the same boot sectors and work the same way. They have the same boot files, but those are totally different from XP,  and use a BCD instead of XP's boot.ini to list windows systems.

If a new install of win7, you will also have a hidden 100MB boot/recovery partition that is essential to the boot process. If you create partition in advance or overinstall Vista it does not create the 100MB partition.

If you want to know more about windows this is a good site. If you just want the quick version to somewhat understand just review the pictures. Also helps to understand how computers boot in general.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by JojAGT on 2010-11-24
@oldfred thanks a lot for the info, that solved my last question! :) I will read info you provide.

Once again thanks a lot to you all guys!

---

### Post by QBALL263 on 2010-11-24
Good afternoon,
     I, too, am a green-as-a-gourd, newbie, cherry virgin when it comes to Ubuntu.  I have been told by many techs that this OS is top notch. I downloaded and burned CD, but am still lost as to dual-booting.  Am currently using Win7/32 on "old" laptop w/Centrino Duo & Google.  I am not a heavy computer user (multi-tasking, gaming) and was wondering what benefits that I would gain by using Ubuntu.  Will I improve or am I justing going WEE-WEE in the wind?  Thanks in advance...

---

### Post by oldfred on 2010-11-24
It posted twice see below.

---

### Post by oldfred on 2010-11-24
Your question is not a install question but more of a question for 
The Community Cafe

Ok, I like Ubuntu.

But I still dual boot just for one application to XP, and hope to convert soon, (I have said that for about a year). 

But with any system, it should be the applications your need and want that drive what system to use. Then if both systems offer the same or similar apps is one system easier to use, maintain, update, repair etc.

My main apps are Firefox, Thunderbird and OpenOffice. Linux runs these apps as well or better than windows. But if you are a professional running CADD, Photoshop, or like games you just about have to run windows.

Linux is not windows and it works differently, part of that is why it is more secure. It has a learning curve, but you can install it and click on a Firefox icon on be on the web without any real knowledge of how Linux works (or how windows works).

We see a lot of issues on the forum as it is about solving issues, so we do not know how many have just installed it and have it work. There are so many combinations of hardware and Ubuntu works for most, but some required some settings. I had to do the same to get Windows to work also. 

I always hated the windows way of having to have serial numbers, not even being able to change motherboard without asking permission, and having to search the net for applications to install. Ubuntu has no serial numbers, I install new hardware without issue (If changing Video card you may have to make some settings), and almost all the software I could ever want is in the repository and I can click to download & install.

Have you tried running the liveCD to test if your system works. LiveCD will be slower booting, and loading new applications, but once in an app if you have a fair amount of RAM it works ok and lets you see how Ubuntu works.

---

