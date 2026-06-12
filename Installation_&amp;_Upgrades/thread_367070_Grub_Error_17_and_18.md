---
title: "Grub Error 17 and 18"
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by goofeyfoot on 2007-02-21
I tried installing Ubunto.  First I tried the 6.10.  That gave a grub error 18 message and machine froze.  So I tried 6.06.  That gave a grub error 17 message and machine froze.

This computer is a PIII with one 30 gig hard drive.

Only Ubonto on the machine.  I don't have windows on it and I don't want it on it.

I don't know anything about Linux yet.  In fact the reason I am making this machine is so I can learn.  But that ain't happening because I can't get the program onto the machine.

I don't want to use my  other computer, AMD windows machine,  for dual boot.  For one thing I already tried that  and it wouldn't work.  I also don't want to ruin that machine, so it is hands off the windows machine for now.

I have already reburned the images as slow as I could.  I have done multiple installs.  Same result every time.  Yes I checked the hash.  Yes I verified the burns.  Believe me.  I have a stack of disks a mile high and they were all checked.  Yes Live cd runs.  Can't install.  All the simple stuff has been checked.

Also, since I don't know much (anything) about Linux commands I can't do a lot of home made changes for the simple reason that I don't know how.

Wow, am I frustrated.

Michael

---

### Post by Belyel on 2007-02-21
The GRUB error can (and does) happen regardless of whether your ubuntu install was successful.  You have the same problem as I (and many) do.  The problem is that GRUB isn't finding the partition with the boot list on it.  Seach around the forums for GRUB error 17 and you should find some help.  YOu most likely have a successful install, so I wouldn't mess with reburning or reinstalling agian.

---

### Post by goofeyfoot on 2007-02-21
Thanks for your reply.  If you run across a link perhaps you could send it along.

I did run into some references to this but I couldn't tell whether it was like my problem or not and I sure couldn't decipher what the cures were.

Thanks again.

Michael

---

### Post by mikewhatever on 2007-02-21
Hi,
Here are the links for errors 17,18
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17)
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18)

I am not sure what's the cause though.

---

### Post by goofeyfoot on 2007-02-21
Thanks for writing back.  Here is what the link said to do, quoting:

"17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

Most commonly this is caused by using the 'root' command instead of 'rootnoverify' when booting Windows having the NTFS file system.
Edit your commands in your menu.lst or grub.conf file with 'rootnoverify' to get rid of this error message.

If you get this error when trying to boot Linux, check your grub conf. or menu.lst file and make sure to check your operating system entry's 'root (hdx,y)' details are correct.

You will need Super Grub Disk to boot Linux for you so that you can easily check and repair your operating system's entry in menu.lst.
Super Grub can boot your operating system by symlinks to the kernel if you use, from the Main Menu,--> Boot Gnu/Linux and  Other OSes --> Boot Gnu/Linux -->...

If you have used hard disk partitioning software recently and you have copied and pasted your partition that contians Grub, it probably has a different partition number now than it had before. You can use Super Grub Disk to re-install Grub. You will also need to edit /etc/fstab if your partition numbers have changed."

As mentioned, I don't know too much about linux so when this fellow is talking about editing commands and changing the root details, I really don't know what he is referring to.

Is there some sort of explanation of how to do this once you get the grubdisk running?

Thanks again.

Michael

---

### Post by confused57 on 2007-02-21
Here's some documentation & screenshots for using the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

You'll need to open a terminal(Applications---Accessories---Terminal) to enter commands,
(copy & paste):

```
sudo fdisk -l
```
the -l is a small "L"
this command will show your partition tables

to edit your menu.lst:
```
cd /boot/grub
```
changes to your grub directory

```
sudo cp menu.lst menu.lst_backup
```
creates a backup of your menu.lst

```
gksudo gedit menu.lst
```
opens your menu.lst file in the gedit text editor
you should probably just need to change the root entry, according to the results of "fdisk -l"...(hd0,0) is the first partition, (hd0,1) is the 2nd, (hd0,2) is the 3rd partition, etc.

You can also highlight your Ubuntu entry in your grub menu entry at boot, press "e" to edit, then change the root here, press "b" to boot...this change is temporary, if it works...make the changes permanent in your /boot/grub/menu.lst

This should get you started.

---

### Post by mikewhatever on 2007-02-21
Let me ask you something I should have asked already. Does the installation completes at all and you are asked to reboot, and then you get those GRUB errors, or do you get them during the installation? The same applies to the freeze. 

About those links, I have to agree that it looks complicated and it's a lot of stuff, but first, I can hardly explain it any better, and also, it's a chance to learn. You'll see that it isn't hard at all.

What Confused had suggested should work if GRUB is installed, in other words, Ubuntu installation was completed and you are having problems booting it.

If the installation has not completed, I think you should fist look into error 18, because it applies to older PCs and BIOS settings.

---

### Post by goofeyfoot on 2007-02-21
Gentlemen:

Thanks for taking the time to write up the explanation.  I think I see where to make changes.

To answer your question.  I did the install.  Then after rebooting, I hit the errors.  The install seemingly went smooth, but I guess internally something must have gone wrong.  Thus the error.

Today I did get the grub disk and I tried all the options.  I couldn't find one  that would actually start the application.  Does that mean I have to make the changes through the live cd?

Basically , the grub disk couldn't start linux at all.  Every option failed.  So maybe the live cd thing is the way to go.

Thanks again for your help.

Michael

---

### Post by confused57 on 2007-02-21
You could boot up the live cd & determine your partition table with:
```
sudo fdisk -l
```

If you're actually getting a grub menu when you start your computer, you can try what I suggested earlier:

> You can also highlight your Ubuntu entry in your grub menu entry at boot, press "e" to edit, then change the root here, press "b" to boot...this change is temporary, if it works...make the changes permanent in your /boot/grub/menu.lst

You might want to "mount" your Ubuntu partition, using the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

If you want to learn a little more about the terminal, commands, shells, etc, here's an excellent, interactive tutorial:
[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)

---

### Post by mikewhatever on 2007-02-22
Yes, it seems that Live CD is the way to go. You should run a live session, then mount Ubuntu partition to have read access to it, and then, try to copy the output of these to some removable media.
> sudo fdisk -l
gksudo gedit /media/ubuntu/boot/grub/menu.lst

I am assuming that Ubuntu partition is mounted in /media/Ubuntu as shown in the link Confused suggested.

I hope it can be done so that you can post them here later.
You type the commands in Applications->Accessories->Terminal.

---

### Post by goofeyfoot on 2007-02-22
Thanks again folks.

Right now I can't get to the grub menu because of the error and because the grub disk fails too.

But what I will do is go through the tutorial and see whether I can figure out a workaround to go where I need to go.  Maybe this PIII machine needs new BIOS too.

But for now, I have to go out of state fishing.  I will try these things and more when I get back and let you know next week what, if anything, happens.

Thanks again for the input, the detailed instructions, and most of all - patience with new guy.

Michael

---

### Post by mikewhatever on 2007-02-22
Have a good time.

---

### Post by goofeyfoot on 2007-02-22
Thanks, hope to.  Plenty of ice I hear.  Now for the fish.

Michael

---

### Post by goofeyfoot on 2007-03-03
Well I am back and nothing works.  I tried all the cures I could for error 18.  I read about seventy five pages of basic stuff about Linux and I finally gave up after wasting an entire day.  Linux seems too hard to use.  For every post I see on line there seems to be several hours of thankless work to try to get the thing to run.

To make matters worse, I tried to install to my good WinXP machine and I get a whole new error that says "TTY error" something or other turned off.

Ubuntu is a free operating system I guess, and from my limited perspective, it's worth every penny.

Michael

---

