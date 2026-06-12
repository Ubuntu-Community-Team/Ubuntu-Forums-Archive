---
title: "Lots of questions about installing ubuntu"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by Haama on 2007-04-30
Hi!

I'm right now running Ubuntu 7.04 on a VMWare player (typing this on Ubuntu :P) on Windows XP Professional SP2 (hate it...). I'm getting a new computer this summer and I want to Ubuntu on it... and probably the XP (just for gaming) so I'm gonna use grub right? Also if I understood this correctly I have to install windows first cause if I install it after Ubuntu it will mess up the master boot record and not start grub right?? That's what i found googling but there's soooooo much c**p in the net so you never know....

I've pretty clearly what are the specs of the new computer, so I can give some info if you need it to help.
The idea is to have one 250 GB hard drive. And I thought I'd make a XP partition and a Ubuntu partition. And Ubuntu can't write to NTFS so it needs a FAT32 partition..? Well if Ubuntu has a FAT32 then how about XP?? Is it possible to make the XP partition a NTFS one?? Or if not, can XP on a FAT32 partition and will that affect performance on gaming or something? Also, about driver support on Ubuntu. I'm probably getting a Intel chipset, an Intel processor and a GeForce video card. Are there up-to-date drivers form them? And the program support for those? I looked at WINE homepage and found out that it doesn't run on 64-bit? The processor will probably be a Intel Core Duo 2 E4300 so it's an x86(32-bit)? 

That's all I have to ask for now... Thanks in advance! :P

P.S. I'm not a native English speaker so I probably typed something wrong....

---

### Post by bulldog on 2007-04-30
Hi,
Well some basic info.
You can install Ubuntu and Windows on the same hdd,no problem,but think about two hdd's,they cost not that much.

Some basic partitioning for ubuntu.
Create a 10GB  partition for root  /
Create a 1GB partiton for swap
Create xxGB partition for /home

If you have space left,create a xxGB partiton as data store.
Format this ext3.

Now install in windows the [http://www.fs-driver.org/](http://www.fs-driver.org/)  driver,and you can read and write ext3 partitions from within windows.

The idea is to install windows and ubuntu on different hdd's,install GRUB on the ubuntu hdd and make this hdd master boot device.
Now you can boot windows and ubuntu from the GRUB menu,but in case of failure of GRUB,you can boot windows with is native bootloader,by making the windows hdd the master boot device in your BIOS.

In case you want to reinstall ubuntu or windows,the other hdd isn't affected so it should be much safer and easier to do.

Think about it,it has certainly advantages,and cost not that much money to do so :)

---

### Post by Haama on 2007-04-30
Thanks a lot!

About the data store thing. Did you mean that if I put a song there I can access it from both OSs? And if I do it like that then is there any use for the /home partition? And can Ubuntu installer change it to ext3 or do I need an external program?

---

### Post by bulldog on 2007-04-30
You should see the /home as a place where all the settings for the users are stored,it shouldn't be to big,depending on your needs.
I would make it 20GB max.

Yes you can use  the data partition,if you install the ext2FS driver,with both,windows and ubuntu.
The build in gparted in ubuntu can format it ext3,but it should be empty when you do so,otherwise your data is wiped from that partition.

I personally use the GParted live cd,to partition all my drives [b]before[b] I install any OS.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Burn it to a disk and boot from it,it gives you a graphical partitioner,which is much ,more clear as the build in one.

---

### Post by Haama on 2007-04-30
Nice!
I think I can handle that. But when I make the partitions how do i set them? I mean how do I make root work in it's own partition and home in it's own? Can Ubuntu installer do that?

---

### Post by bulldog on 2007-04-30
When you make the partitions on fore hand with the GParted live cd,note them down.

Installing ubuntu will bring you to the build in partitioner,choose manual partition here.
This opens a list with your existing partitions.
Mount the correct partition as /  set it to format ext3 and set the bootflag on. [10GB]
Mount the swap as swap and set it to format as swap  [1GB]
Mount /home as /home and format it ext3 [xxGB]
Mount /data as /data and format it ext3 [xxGB]

That's all,if done as you want,hit apply and continue the install.

---

### Post by Haama on 2007-04-30
Thank you so much! I think I'll test that in VMWare so I don't mess everything up in the real install.

---

### Post by ubuntu27 on 2007-04-30
> **Haama said:**
> Hi!

I'm right now running Ubuntu 7.04 on a VMWare player (typing this on Ubuntu :P) on Windows XP Professional SP2 (hate it...). I'm getting a new computer this summer and I want to Ubuntu on it... and probably the XP (just for gaming) so I'm gonna use grub right? Also if I understood this correctly I have to install windows first cause if I install it after Ubuntu it will mess up the master boot record and not start grub right?? That's what i found googling but there's soooooo much c**p in the net so you never know....

I've pretty clearly what are the specs of the new computer, so I can give some info if you need it to help.
The idea is to have one 250 GB hard drive. And I thought I'd make a XP partition and a Ubuntu partition. And Ubuntu can't write to NTFS so it needs a FAT32 partition..? Well if Ubuntu has a FAT32 then how about XP?? Is it possible to make the XP partition a NTFS one?? Or if not, can XP on a FAT32 partition and will that affect performance on gaming or something? Also, about driver support on Ubuntu. I'm probably getting a Intel chipset, an Intel processor and a GeForce video card. Are there up-to-date drivers form them? And the program support for those? I looked at WINE homepage and found out that it doesn't run on 64-bit? The processor will probably be a Intel Core Duo 2 E4300 so it's an x86(32-bit)? 

That's all I have to ask for now... Thanks in advance! :P

P.S. I'm not a native English speaker so I probably typed something wrong....

Your english is not bad. :)

Like otheres were saying you can now read and Write the NTFS partition from Linux. But if you wanna be on the safe side, you can create a separete partition for your personal files that you wanna share between Windows and (K/X)Ubuntu Linux.

[Here,]("http://www.psychocats.net/ubuntu/partitioning") [this link]("http://www.psychocats.net/ubuntu/partitioning") will explain in great details about PLANING for your partition.

Here is other guides:
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by bulldog on 2007-04-30
> **Haama said:**
> Thank you so much! I think I'll test that in VMWare so I don't mess everything up in the real install.

You can't test this in VMWare,you can't resize a partition 'virtual' I'm afraid.
Do some reading,ask questions,try to understand what you're gonna do,before you install,and all will go smoothly.

Most users just install and come to the forums complaining it doesn't work as it should be.
If you do properly research before the install,you should know what can go wrong and what to do about it.

---

### Post by Haama on 2007-04-30
> Quote:
[QUOTE]Originally Posted by Haama View Post
Hi!

I'm right now running Ubuntu 7.04 on a VMWare player (typing this on Ubuntu :P) on Windows XP Professional SP2 (hate it...). I'm getting a new computer this summer and I want to Ubuntu on it... and probably the XP (just for gaming) so I'm gonna use grub right? Also if I understood this correctly I have to install windows first cause if I install it after Ubuntu it will mess up the master boot record and not start grub right?? That's what i found googling but there's soooooo much c**p in the net so you never know....

I've pretty clearly what are the specs of the new computer, so I can give some info if you need it to help.
The idea is to have one 250 GB hard drive. And I thought I'd make a XP partition and a Ubuntu partition. And Ubuntu can't write to NTFS so it needs a FAT32 partition..? Well if Ubuntu has a FAT32 then how about XP?? Is it possible to make the XP partition a NTFS one?? Or if not, can XP on a FAT32 partition and will that affect performance on gaming or something? Also, about driver support on Ubuntu. I'm probably getting a Intel chipset, an Intel processor and a GeForce video card. Are there up-to-date drivers form them? And the program support for those? I looked at WINE homepage and found out that it doesn't run on 64-bit? The processor will probably be a Intel Core Duo 2 E4300 so it's an x86(32-bit)?

That's all I have to ask for now... Thanks in advance! :P

P.S. I'm not a native English speaker so I probably typed something wrong....
Your english is not bad.

Like otheres were saying you can now read and Write the NTFS partition from Linux. But if you wanna be on the safe side, you can create a separete partition for your personal files that you wanna share between Windows and (K/X)Ubuntu Linux.

Here, this link will explain in great details about PLANING for your partition.

Here is other guides:
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)[/QUOTE]

Thanks! :) 


> Quote:
[QUOTE]Originally Posted by Haama View Post
Thank you so much! I think I'll test that in VMWare so I don't mess everything up in the real install.
You can't test this in VMWare,you can't resize a partition 'virtual' I'm afraid.
Do some reading,ask questions,try to understand what you're gonna do,before you install,and all will go smoothly.

Most users just install and come to the forums complaining it doesn't work as it should be.
If you do properly research before the install,you should know what can go wrong and what to do about it.[/QUOTE]

Ok!

Edit:Didn't really get the quote thing...

---

### Post by az on 2007-04-30
> **Haama said:**
> Nice!
I think I can handle that. But when I make the partitions how do i set them? I mean how do I make root work in it's own partition and home in it's own? Can Ubuntu installer do that?

I suggest forgetting about making a home partition.  Just let the installer partition the drive automagically for you.  It does that by default.

It will detect your windows partition which takes up your whole drive.  You will be asked how small you want to shrink that partition.  The Ubuntu installer will do the rest (create a root and swap partition for you).  Nothing for you to make a mistake about.

---

### Post by bulldog on 2007-04-30
> **az said:**
> I suggest forgetting about making a home partition.  Just let the installer partition the drive automagically for you.  It does that by default.

It will detect your windows partition which takes up your whole drive.  You will be asked how small you want to shrink that partition.  The Ubuntu installer will do the rest (create a root and swap partition for you).  Nothing for you to make a mistake about.

I agree,it can be that simple,but..........when you want to do a reinstall,the problems begin,losing data,not knowing how to copy it,and so on.

That's why I advice to make a separate /home and or a /data partiton,to avoid future problems :)

---

### Post by az on 2007-04-30
> **bulldog said:**
> the problems begin,losing data,not knowing how to copy it,and so on.



Again, I find it a lot simpler to just back things up the old fashion way.  And you're just a keystroke away from deleting your partition when you reinstall.

It does also happen that you bugger up your configurations in your home drive and you actually nned to flush them to make things work.  In that case, copying your home partition will just cause the problem on a fresh install.

When a new user needs help about installing Ubuntu for the first time, I find that the simplicity of the default install is an advantage.  I don't see any compelling reason to complicate the process.

---

### Post by bulldog on 2007-04-30
Hmmm,making some extra partitions isn't that complicating.

But I think we can argue a lot about how 'things should be done'
There are pro's and con's for either way,so I let the new user decide what he want to do.
 I only think he should know on fore hand,you can do this in different manners.

---

### Post by Haama on 2007-05-01
Az has a point... But i really liked the idea of the data storage. And I don't mind doing some extra work.
I'm installing it on a new computer so there will be now chance losing anything. If I do make a mistake can  I just format the hard drive and try again?

---

### Post by Surkow on 2007-05-01
> **Haama said:**
> Az has a point... But i really liked the idea of the data storage. And I don't mind doing some extra work.
I'm installing it on a new computer so there will be now chance losing anything. If I do make a mistake can  I just format the hard drive and try again?

Yes, when you mess up the install just reinstall Windows/Ubuntu. Since there is no risk of data loss nothing can go wrong. ;D

---

