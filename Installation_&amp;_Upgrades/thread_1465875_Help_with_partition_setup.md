---
title: "Help with partition setup"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by Rylin on 2010-04-29
I recently created a 60gb partition from one of my hard drives in windows but when i go to install ubuntu when i restart, it wants to install the various directories in multiple partition areas scattered on other hard drives. I just want Ubuntu to use just the 60gb partition but it doesn't seem to recognize it. I would select the manual partition but I don't know how to set that up (confusing for the average user).

Any ideas how to get Ubuntu to install everything on the 60gb partition I created?

Thanks

---

### Post by 2hot6ft2 on 2010-04-29
The manual partitioner is no more confusing than the windows disk management utility and you already used that.
Give it a try it doesn't make any changes until after step 7 so you can change your mind up to then or cancel.
If you know the size that you left for ubuntu and you know the drive it's on you should be able to figure it out.
File system type ext3 or ext4
mount point /
that's about it.

I always use the manual partitioner it gives me the control I want.

---

### Post by bmuluu on 2010-04-29
Select manual partition, find/identify the 60GB partition and select it. 
Choose a filesystem and use it as root (/) - that way the Ubuntu installation
shall be in that one partition.

---

### Post by Rylin on 2010-04-29
Thanks for the help guys.

It tells me I should create a swap partition as well. Do I really need that for the installation or can I just skip that?

Thanks a bunch

---

### Post by bmuluu on 2010-04-29
Swap is good for your system. Partition your 60GB and assign swap at least 
just as much physical RAM as your computer has.

---

### Post by 2hot6ft2 on 2010-04-29
You should create a swap partition the size of your RAM to 1.5 times your RAM for suspend and hibernate to work.
file system type: linux swap

I don't know if it will let you finish without it I've never tried to.

And if you already have a swap partition don't create another one.
You're welcome.

---

### Post by TBerk on 2010-04-29
> **Rylin said:**
> I recently created a 60gb partition from one of my hard drives in windows but when I go to install Ubuntu when I restart, it wants to install the various directories in multiple partition areas scattered on other hard drives. 

OK, what version of Windows, what version of Ubuntu? We need some details here my friend.

Are you booting from an Ubuntu CD? (I'm going to assume you are. This is instead of installing Ubuntu *inside* of Windows.)

In general, when you boot from an Ubuntu Install CD, you have a choice to let it prep the partitions automatically OR you can set them up manually.

After you choose USA or some other country to default the keyboard to etc, etc, you get a screen showing the partitions and a recommended setup; look to the bottom choice where you can select a small 'button' to choose MANUAL.

> 
I just want Ubuntu to use just the 60gb partition but it doesn't seem to recognize it. I would select the manual partition but I don't know how to set that up (confusing for the average user).

Any ideas how to get Ubuntu to install everything on the 60gb partition I created?

Thanks

I would suggest you not install it all on the 60Gigi partition you've created for a number of reasons, namely;

1) You might want to install the Linux OS in a (smallish) partition to itself & the documents/data (or ** /HOME**) partition could get the bulk of the space. Something like 6 to 8Gigs should be plenty for the partition you make as mount-point [b]
/[/b]  .

2) If and when you want to trash, re-install, remove the installed Ubuntu OS you won't endanger the /HOME files as much; you just wipe the / partition and reinstall. (Theres more to it but thats the nutshell version.)

I'd think, in a case like this, that Google is your friend...

Cheeeeeck it out-

[http://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+partition+partitioning+setup+how+do+I&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+partition+partitioning+setup+how+do+I&ie=utf-8&oe=utf-8)

Of special note is/are the link(s) describing how to choose a Partitioning Scheme. (There be pictures and everything...)


berk

---

### Post by Rylin on 2010-04-29
Maybe I should provide a screenshot:

The partition with (62970 MB) where it has /dev/sdb5 is where i want the entire linux installation to be but how to I get rid of the other areas it wants to install the files? I just want to make sure I'm not overwriting my windows files by installing over them.

[IMG]http://img504.imageshack.us/img504/6203/partitionf.png[/IMG]

---

### Post by 2hot6ft2 on 2010-04-29
What I would do for what you're wanting is select sdb5 and click delete.
Select the space where it was and click Add
create the partition for ubuntu
file system ext3 or ext4
select it and click Change and set it to
mount point /
leave enough space to create a swap partition the size or your RAM to 1.5 times your RAM plus a couple hundred MB's for the partition itself.
select that empty space and click Add
create a partition choosing linux swap for the file system type.

It wont touch the others unless you tell it to.
I've never had good luck with having a separate home partition myself.

That's it continue with the installer.

---

### Post by -kg- on 2010-04-29
All of the partitions you have are formatted as NTFS.  I was afraid of that, considering your statement:

> I recently created a 60gb partition from one of my hard drives in windows...

Whichever one you created for Ubuntu (I assume it is sdb5) you need to reformat to ext3 or ext4.  Ubuntu does not install into ntfs partitions, and you can't create a Linux partition using the Windows disk management tool.

You will need to use the partitioner contained on the LiveCD to do that.  Read at the link in my signature block for more information on Partitioning.

You will also need to leave a little free space in which to create your swap partition. Around 1.5X the size of your RAM will do.

<edit> LOL 2hot!  We posted almost the same time.

---

### Post by TBerk on 2010-04-29
> **2hot6ft2 said:**
> 
I've never had good luck with having a separate home partition myself.


Not to hijack the thread but I've had very good experiences with separate OS and /Home partitions.

It's not a must have but now would be the time to do it, during Install.

As always, some independent research and verification of any forum advise (including my own) that you get is advisable. That said, the other guys are spot on, in the main.


berk

---

### Post by 2hot6ft2 on 2010-04-29
> **-kg- said:**
> 
<edit> LOL 2hot!  We posted almost the same time.
4 minute gap but who's counting.
The installer can change the partition from NTFS by deleting and creating a new one with a linux file system. No need to leave the partitioner and go to GParted to do the same thing.

---

### Post by 2hot6ft2 on 2010-04-29
> **TBerk said:**
> Not to hijack the thread but I've had very good experiences with separate OS and /Home partitions.

It's not a must have but now would be the time to do it, during Install.

As always, some independent research and verification of any forum advise (including my own) that you get is advisable. That said, the other guys are spot on, in the main.


berk
I've tried it about a half dozen times and always had problems with a separate home so now I just back my home up and restore it if I need to re-install. It accomplishes the same thing and takes a few minutes longer.

You're right. The more input the better. And always research.

---

### Post by srs5694 on 2010-04-30
> **Rylin said:**
> The partition with (62970 MB) where it has /dev/sdb5 is where i want the entire linux installation to be but how to I get rid of the other areas it wants to install the files? I just want to make sure I'm not overwriting my windows files by installing over them.

This window is showing all the partitions that exist on your system, but that does *not* mean that the installer will *use* them all. Specifically, the "mount point" column shows where a partition will be mounted. These are all empty in your screen shot, meaning that the installer will use none of those partitions. With the exception of a swap partition and a few other partition types that you don't have, a partition must be assigned a mount point in order for Linux to use it. Thus, to do what you want, you should, at a minimum, select /dev/sdb5, click Change, assign it a mount point of root (/) and a Linux filesystem type (such as ext3fs; and check any option to create that filesystem [aka format the partition]), and proceed. The system will then ignore all the remaining partitions and install everything to /dev/sdb5.

As others have said, you'll do better to delete /dev/sda5 and create at least two partitions in its place, one for swap and one for root (/). (The root partition is the only one that's absolutely required for Linux.) I agree with some others that a separate /home partition will also be helpful. Linux user files go in /home (whether that's a separate partition or just a directory in the root partition), so using a separate /home partition isolates system and user files from each other, which simplifies some types of future upgrades and re-installations. Make root (/) 5-20GB, depending on how much software you plan to install, make swap 1-2x your RAM size, and give the rest to /home.

You can also mount any or all of your NTFS partitions at fixed points in your Linux directory tree. For instance, if you plan to make your username "rylin", your home directory (where your user files will be stored) will be /home/rylin. You might then make mount points things like /home/rylin/winD or /home/rylin/work, to store the contents of the Windows D: drive or work files (whatever partition they're on). (You can name mount points anything you like.) When you set these up, just be sure you do *not* select the option to create a new filesystem (aka format the partition; I don't recall the term that the Ubuntu installer uses). If you don't do this, you'll still be able to access the partition, but it will either appear as a separate drive icon in the desktop environment or will require manual configuration after you install Ubuntu. If you're nervous about messing with it at this time, don't; you can always do it later.

---

### Post by -kg- on 2010-05-20
> **2hot6ft2 said:**
> I've tried it about a half dozen times and always had problems with a separate home so now I just back my home up and restore it if I need to re-install. It accomplishes the same thing and takes a few minutes longer.

You're right. The more input the better. And always research.

It's been a while since these posts, but....

It's not really a problem to preserve your /home partition.  You need to use "Manual Partitioning," of course, but during the partitioning phase, you mount that partition as /home but specify that the partition ***_not_*** be formatted.  It preserves all your data and only changes what *must* be changed in the upgrade.

---

