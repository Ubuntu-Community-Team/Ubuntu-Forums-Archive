---
title: "Help with install screen &quot;Installation type&quot; screen"
date: 2013-02-13
forum: Installation &amp; Upgrades
---

### Post by RabblerouserGT on 2013-02-13
So this morning I found out my 127GB WinXP installation didn't take up the entirety of my hard drive. I had a whopping ~21GB of unallocated disk space. I went about setting this up as a FAT32-formatted partition within windows.


What I'd like to know now is how can I install Ubuntu onto it. The installer isn't very straightforward in its instructions. And from what I could gather, doing it the "install alongside WinXP professional" option would've tried to install Ubuntu to my NTFS C drive.


I'd like to know what I can do to transform "sda2" below into a useful Ubuntu drive. Possibly changing it from fat32 to ext4 if Windows XP can still read the drive after that.

Please be as concise as possible. Don't skimp out on any details. I wouldn't like for things to go awry.

[IMG]http://i.imgur.com/4Rfekw8.png[/IMG]

---

### Post by carl4926 on 2013-02-14
Boot Ubuntu as if to try it and in the live session, open Gparted. If it's not installed, (you need a live internet for this)
```
sudo apt-get install gparted
```

Start gparted
select sda2 and Delete > then Apply
Now focus on the Unallocated space and create New > Extended Partition to use all the space
Next with focus on the Extended space Create New Swap (logical) 2GB
Next with focus on the Extended space Create New ext4 (logical) to use all the remaining space
Apply
Then close gparted

Now start the installer and choose:
[https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_advanced.png](https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_advanced.png)

Now point the installer to the ext4 partition you see:
[https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png](https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png)
(you don't have a /home so ignore that, and this is just an example, your partitions look different)
swap looks after itself, so don't worry about it.

Now just carry on....

---

### Post by ahallubuntu on 2013-02-14
~

---

### Post by montenik on 2013-02-14
First of all, let me say that I am not an expert on this subject so you probably want to get confirmation from someone else before trying my suggestions.


[LIST]
[*]When you get to the partition screen, I think you click the "New Partition Table..." button.
[*]Change the type of partition for /dev/sda2 to ntfs.
[LIST]
[*]Ext4 is probably better for Ubuntu, but Windows XP isn't going to be able to read or write to it unless you install 3rd party software.
[*]I suppose you could also stick with fat32 if you want to.
[/LIST]
 
[*]Change the mount point of "/dev/sda2" to "/"
[*]Check the box "format" for "/dev/sda2" (unless you are using fat32, in which case you probably don't need to)
[*]Make sure the mount point for "/dev/sda1" is blank and the checkbox for "format" is unchecked.
[*]You should end up with something similar to the attached picture
[/LIST]
[ATTACH]231398[/ATTACH]

---

### Post by carl4926 on 2013-02-14
> **montenik said:**
> First of all, let me say that I am not an expert on this subject so you probably want to get confirmation from someone else before trying my suggestions.


[LIST]
[*]When you get to the partition screen, I think you click the "New Partition Table..." button.
[*]Change the type of partition for /dev/sda2 to ntfs.
[LIST]
[*]Ext4 is probably better for Ubuntu, but Windows XP isn't going to be able to read or write to it unless you install 3rd party software.
[*]I suppose you could also stick with fat32 if you want to.
[/LIST]
 
[*]Change the mount point of "/dev/sda2" to "/"
[*]Check the box "format" for "/dev/sda2" (unless you are using fat32, in which case you probably don't need to)
[*]Make sure the mount point for "/dev/sda1" is blank and the checkbox for "format" is unchecked.
[*]You should end up with something similar to the attached picture
[/LIST]
[ATTACH]231398[/ATTACH]


Please do Not follow this!

---

### Post by RabblerouserGT on 2013-02-14
This is all so much information to absorb. :D

Are you guys sure WinXP can't read ext4? If not, I think I'll stick with FAT32.. unless there's some complications installing Ubuntu on FAT32.

---

### Post by carl4926 on 2013-02-14
You can't use windows file systems such as FAT or NTFS to install Linux.

You can copy files back and forth when running Ubuntu, because it can read and write to windows.

There is a application you can install in XP that lets you read Ubuntu but no more than that.

There really isn't a problem here, I don't know what you are worried about?

---

### Post by RabblerouserGT on 2013-02-14
Am I doing it right?

[IMG]http://i.imgur.com/0MM3mOS.png[/IMG]

---

### Post by carl4926 on 2013-02-14
Correct

Now just apply....wait then

Then close gparted
Start the installer and follow the steps I gave earlier
Basically you just need to point the installer to sda6 and set the mount point as /

---

### Post by RabblerouserGT on 2013-02-14
How do I set mount points? :S

EDIT: Not sure, but I think the installer just become unresponsive to any input. It's still working and not dimming, but it's not reactiing to any input.

---

### Post by carl4926 on 2013-02-14
At this part
[https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png](https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png)

(remember your partitions look different)
Double click sda6
And a box should popup to set format to ext4 and set mount point
It will look something like this:
[https://dl.dropbox.com/u/10573557/Ubuntu/Ubuntu%2010.04%20Install/9.%20edit_root.jpg](https://dl.dropbox.com/u/10573557/Ubuntu/Ubuntu%2010.04%20Install/9.%20edit_root.jpg)

---

### Post by carl4926 on 2013-02-14
> **RabblerouserGT said:**
> How do I set mount points? :S

EDIT: Not sure, but I think the installer just become unresponsive to any input. It's still working and not dimming, but it's not reactiing to any input.

How much RAM do you have
If it's 1GB or less you might want to retry the install but don't boot to the Live desktop first
Boot the CD and wait
At this screen:
[https://dl.dropbox.com/u/10573557/Ubuntu/ubuntu_boot/2013-02-10%2008.42.25.jpg](https://dl.dropbox.com/u/10573557/Ubuntu/ubuntu_boot/2013-02-10%2008.42.25.jpg)
Just choose Install Ubuntu

---

### Post by RabblerouserGT on 2013-02-14
I'd rather have the Live Ubuntu running so I can talk to you guys.


Are these two right?
swap: [http://i.imgur.com/y8OXdDQ.png](http://i.imgur.com/y8OXdDQ.png)
ext4: [http://i.imgur.com/xjXbXf8.png](http://i.imgur.com/xjXbXf8.png)

And the boot loader installation stays where it's at in the pictures?


My apologies. This is all so new and I would love to be thorough.

---

### Post by RabblerouserGT on 2013-02-14
Hello?


Again, sorry for all the questions. So far, I've been using Wubi, which is veeery straightforward and easy to set up, but from what I hear, it's slower than a dual-boot install.

I've learned a lot about Ubuntu within Wubi, but am total newb when it comes to mount points and swaps.

---

### Post by carl4926 on 2013-02-14
> **RabblerouserGT said:**
> I'd rather have the Live Ubuntu running so I can talk to you guys.


Are these two right?
swap: [http://i.imgur.com/y8OXdDQ.png](http://i.imgur.com/y8OXdDQ.png)
ext4: [http://i.imgur.com/xjXbXf8.png](http://i.imgur.com/xjXbXf8.png)

And the boot loader installation stays where it's at in the pictures?


My apologies. This is all so new and I would love to be thorough.

Correct
Only you don't actually need to do anything with swap
The installer will automatically use it

---

### Post by RabblerouserGT on 2013-02-14
> **ahallubuntu said:**
> Now this creates a file (very tiny) called "xpmbr.bin."  SAVE that file somewhere.  Pop in a USB flash drive and copy it there, or open Firefox and email that file as an attachment using your Gmail or Yahoo account or something. If you ever need to get rid of Ubuntu later (hope not!) and don't have an XP disc, you can use this xpmbr.bin file you created before installing Ubuntu...to restore the XP boot loader...

How would I reinstall the bootloader it from the .bin? Just run it in Windows?

All I can say is right now I severely regret using GRUB as the main bootloader when there are walkthroughs on how to install GRUB as a sort of secondary loader.

---

### Post by ahallubuntu on 2013-02-14
~

---

### Post by ahallubuntu on 2013-02-14
~

---

### Post by carl4926 on 2013-02-14
> **RabblerouserGT said:**
> How would I reinstall the bootloader it from the .bin? Just run it in Windows?

All I can say is right now I severely regret using GRUB as the main bootloader when there are walkthroughs on how to install GRUB as a sort of secondary loader.

Now we are just going off track.
Grub works fine

Are you installing Ubuntu or not?

---

