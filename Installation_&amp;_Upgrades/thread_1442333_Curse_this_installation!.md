---
title: "Curse this installation!"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by Skyline969 on 2010-03-29
Ok, I'm installing a dual-boot with Ubuntu and Windows 7. Windows 7 is installed first. However, I also have some Dell proprietary stuff installed on two more primary partitions, which I can't get rid of. Meaning, I have one primary partition slot free... I shrunk my Windows 7 partition by 50GB... and booted my Live CD of Ubuntu 9.04. I chose to install, and when I got to the partitioning part, I saw the 50 GB of unallocated space. I chose to let Ubuntu install side by side, and choose what to let me boot. However, I got some error about too many primary partitions and, magically, my Windows partition got all of its space back, save for 2.5GB. Of course, I got enough errors and I didn't install Ubuntu. I rebooted back to Windows and I had to have chkdsk go through all my files.

I also checked when on the Ubuntu CD and I noticed something about my hard drive configuration I have NEVER seen before... it said something about 4 or 5 gigs containing WINDOWS XP! I have never had Windows XP on this thing! What gives?

Anyways, where did I go wrong, and what can I do to dual-boot Windows 7 and Ubuntu?

---

### Post by spiderbatdad on 2010-03-29
Using a partitioning tool you should be able to make an "extended" partition of the fourth partition.An extended partition is a single partition that allow multiple other partitions inside it.

---

### Post by raymondh on 2010-03-29
Kindly post/attach a screenshot of a gparted output.  That or, post the terminal results of

```
sudo fdisk -l
```

You can use the liveCD for either.  Boot into the liveCD and go live session (try ubuntu...).  

I had a dell laptop once that came pre-configured with Vista.  It, as well, had XP-named files/partition.  I never bothered to know more about it as my intention was to wipe windows clean on that laptop.  Wish I did investigate further though.

Raymond

---

### Post by Skyline969 on 2010-03-29
> **raymondh said:**
> Kindly post/attach a screenshot of a gparted output.  That or, post the terminal results of

```
sudo fdisk -l
```

You can use the liveCD for either.  Boot into the liveCD and go live session (try ubuntu...).  

I had a dell laptop once that came pre-configured with Vista.  It, as well, had XP-named files/partition.  I never bothered to know more about it as my intention was to wipe windows clean on that laptop.  Wish I did investigate further though.

Raymond
This is what GParted shows:
[IMG]http://i39.tinypic.com/15o8en4.png[/IMG]

I can't make an extended partition... the option to is completely grayed out. Oh, the 9.something unallocated space is my deleted Recovery partition. I deleted that when I installed Windows 7... as it was for Vista, and I didn't need it anymore. Oddly, it does not combine with the other unallocated space.

---

### Post by spiderbatdad on 2010-03-30
you already have an extended partition, but it is much too small. Try to reallocate space there.

---

### Post by coffeecat on 2010-03-30
> **Skyline969 said:**
> I can't make an extended partition... the option to is completely grayed out. 

You can have one extended partition only. Use Gparted to resize/enlarge sda3 (the extended) backwards so that it occupies the 46.44 unallocated space. Then move sda5 so that it is at the beginning of sda3. (This will probably take some time.) Now you will have 46.44 GiB unallocated space in the extended partition which you can use for Linux partitions (logicals). They will be numbered sda6 upwards.

**Backup sda5 before you do anything**.

> **Skyline969 said:**
> Oh, the 9.something unallocated space is my deleted Recovery partition. I deleted that when I installed Windows 7... as it was for Vista, and I didn't need it anymore. Oddly, it does not combine with the other unallocated space.

You cannot combine non-contiguous space. The best you can do is to make a primary partition there. You could try to move Windows 7 to the left into that 9.77 GiB with Gparted. In theory, it's possible, but Vista and W7 often have a fit of the vapours if they're interfered with by Gparted. Personally, I wouldn't do that unless I'd imaged Windows 7 first so that I could restore it if necessary.

---

### Post by Skyline969 on 2010-03-30
> **coffeecat said:**
> You can have one extended partition only. Use Gparted to resize/enlarge sda3 (the extended) backwards so that it occupies the 46.44 unallocated space. Then move sda5 so that it is at the beginning of sda3. (This will probably take some time.) Now you will have 46.44 GiB unallocated space in the extended partition which you can use for Linux partitions (logicals). They will be numbered sda6 upwards.

**Backup sda5 before you do anything**.



You cannot combine non-contiguous space. The best you can do is to make a primary partition there. You could try to move Windows 7 to the left into that 9.77 GiB with Gparted. In theory, it's possible, but Vista and W7 often have a fit of the vapours if they're interfered with by Gparted. Personally, I wouldn't do that unless I'd imaged Windows 7 first so that I could restore it if necessary.
Ahh ok, that makes much more sense. So I just extend the sda3 partition by all of the large chunk of unallocated space, and then... how do I make that sda5 at the beginning of sda3? I apologize, but I'm a total Linux idiot. Not used to working with this sort of filesystem/management. All I know is that I have to get my partitions right the first time, as you cannot shrink/expand a Linux partition without completely formatting it due to the inodes.

Once I have all of that space in my sda3, how should I format it? I know I'm gonna be making a 2-3GB linux-swap partition because my RAM is only 2GB, and I like to have some swap reserved. However, how do I have to format the rest? And also, once I have it all formatted, what do I have to do during installation to ensure that I can install the dual-boot successfully?

And yes, I know that Vista and 7 get kind of whiny if you touch their partitions at all with GParted, because when I told Ubuntu to install automatically, it just threw all of my unallocated space back onto the ntfs partition for Windows. When I rebooted to Windows (Ubuntu installation failed at that point), it had to go through 15 minutes of chkdsk to ensure all of my files were alright.

Again, I apologize that I'm completely clueless about all of this, but it's better I ask before I go in, guns blazing. That way, I won't completely ruin my hard drive.

---

### Post by Cavsfan on 2010-03-30
I know when I messed with my windows 7 partition (even accessing files on the disk), 
it messed it up (like coffeecat said) and I had to clean install windows 7.
(Not trying to interfere, just throwing in my 2 cents.)

---

### Post by coffeecat on 2010-03-30
> **Skyline969 said:**
> All I know is that I have to get my partitions right the first time, as you cannot shrink/expand a Linux partition without completely formatting it due to the inodes.

<panto-mode>

OOoooohhh, yes you can! :wink:

</panto_mode>

Been there. Done that. I managed to move **and** shrink two Linux partitions (one ext3, one ext4) with Gparted all in one go (one go each that is) without reformatting and without any data corruption. (Probably because I'd done double backups first.) And neither did the UUIDs change.

Anyway.... when you get to when you want to move sda5, in Gparted, Partition > Resize/Move. You'll have three fields to fill: Free space preceding, New Size, Free Space following. Clearly 'New Size' needs to be the same, and you'll need to make space preceding zero if you want to move it completely to the left. Which leaves space following. Simply press enter when you've got the first two fields correct and it will autofill. Then you can click the Resize/Move button, after which you get an 'are you sure?' type prompt which gives you a chance to take a deep breath. Health warning: fiddling with partitions is not risk-free, but I'm sure you know that.

As far as the rest is concerned, personally I would make sda6 my swap and then a sda7 ext4 of whatever size is needed. After which I would choose the 'manual' option at the partitioning stage of the installer where you have the opportunity to point the installer at pre-exisiting partitions instead of letting the installer do it for you. Creating partitions in Gparted is fairly straightforward, but post back if you need help.

Alternatively, you could abandon Gparted after you've moved sda5 and choose 'use continuous unallocated space (or words to that effect) in the installer, but I don't know how much control you have over the swap partition size if you choose that.

---

### Post by Skyline969 on 2010-03-30
> **coffeecat said:**
> <panto-mode>

OOoooohhh, yes you can! :wink:

</panto_mode>

Been there. Done that. I managed to move **and** shrink two Linux partitions (one ext3, one ext4) with Gparted all in one go (one go each that is) without reformatting and without any data corruption. (Probably because I'd done double backups first.) And neither did the UUIDs change.

Anyway.... when you get to when you want to move sda5, in Gparted, Partition > Resize/Move. You'll have three fields to fill: Free space preceding, New Size, Free Space following. Clearly 'New Size' needs to be the same, and you'll need to make space preceding zero if you want to move it completely to the left. Which leaves space following. Simply press enter when you've got the first two fields correct and it will autofill. Then you can click the Resize/Move button, after which you get an 'are you sure?' type prompt which gives you a chance to take a deep breath. Health warning: fiddling with partitions is not risk-free, but I'm sure you know that.

As far as the rest is concerned, personally I would make sda6 my swap and then a sda7 ext4 of whatever size is needed. After which I would choose the 'manual' option at the partitioning stage of the installer where you have the opportunity to point the installer at pre-exisiting partitions instead of letting the installer do it for you. Creating partitions in Gparted is fairly straightforward, but post back if you need help.

Alternatively, you could abandon Gparted after you've moved sda5 and choose 'use continuous unallocated space (or words to that effect) in the installer, but I don't know how much control you have over the swap partition size if you choose that.

Wow, so much new information... and I'm taking it all in. Yes, I know that partition editing is not risk-free, and I have a full backup of all of my data (no image, but I don't have external hard drive space for that... but all of my media is backed up) just in case something goes horribly wrong. I'm confident enough in my abilities that I'm not going to completely destroy my data, but you never know. Everyone makes mistakes, right?

Ok, writing this down... 
Expand the current extended partition to use all of the unallocated space. 
Edit the sda5(MEDIADIRECT) partition so its space preceding it is 0, and its size is unchanged, automatically changing the space following it to all that's left.
Create a 2GB linux-swap on sda6.
Create a ext4 partition with all of the remaining space on sda7.
Launch the install, and specify to manually choose, choosing sda6 as my swap and sda7 for my main installation.

Do I need to change any other settings during the installation, other than make sure I install the bootloader? Thanks a lot for your patience, I appreciate it. :)

---

### Post by coffeecat on 2010-03-30
I think that covers it. When you get to the 'manual' bit of the installer, I can't remember the exact details, but it presents you with all the partitions on the hard drive. You have to 'edit' or 'change' (or similar) each partition that you want mounted in /etc/fstab and specify the mountpoint. For sda7 the mountpoint needs to be '/' (root) and you don't have to bother with the swap partition. That gets picked up automatically.

You probably don't want the W7 NTFS partition mounted at bootup, but if you do, don't specify this at this stage of the installer. Better to edit fstab later. Or if you do, post back and I'll tell you how to edit /etc/fstab afterwards so that you are not hit by a nasty file date-change bug. (Yes, I filed a bug-report on Launchpad. Yes, it was ignored. :|)

If you don't specify that sda7 is to be formatted, the installer will grumble at you, but since you will only have just formatted it in Gparted, tell it to shut up! :p

---

### Post by Skyline969 on 2010-03-30
> **coffeecat said:**
> I think that covers it. When you get to the 'manual' bit of the installer, I can't remember the exact details, but it presents you with all the partitions on the hard drive. You have to 'edit' or 'change' (or similar) each partition that you want mounted in /etc/fstab and specify the mountpoint. For sda7 the mountpoint needs to be '/' (root) and you don't have to bother with the swap partition. That gets picked up automatically.

You probably don't want the W7 NTFS partition mounted at bootup, but if you do, don't specify this at this stage of the installer. Better to edit fstab later. Or if you do, post back and I'll tell you how to edit /etc/fstab afterwards so that you are not hit by a nasty file date-change bug. (Yes, I filed a bug-report on Launchpad. Yes, it was ignored. :|)

If you don't specify that sda7 is to be formatted, the installer will grumble at you, but since you will only have just formatted it in Gparted, tell it to shut up! :p
Will do! I'm writing all of this down now. I'll try this as soon as I get back home from class. It alarms me that none of my professors are overly skilled in Ubuntu, or Linux at all. Oh well, best that I learn somehow, as most of my second year is all about Linux... not Ubuntu, in particular, but some Debian-based distro I think. So I should definitely get some practice in. =P
My next post on this topic will (hopefully) be from my laptop... from within Ubuntu. :D

And yeah, I only want to mount sda7. I don't want Ubuntu to touch my Win7 partition at all, and vice versa. Ergo, I should only set the sda7 partition to mount at '/' which is the root. The linux-swap partition will automatically be picked up so I don't have to even think about it at all. From that, just let it install (choosing to install the bootloader, of course), and enjoy a dual-boot! Erm... I hope I got that right. I'm confident I understand what you've told me, and I hope that it works when I put it to the ultimate test.

---

### Post by coffeecat on 2010-03-30
> **Skyline969 said:**
> And yeah, I only want to mount sda7. I don't want Ubuntu to touch my Win7 partition at all, and vice versa. Ergo, I should only set the sda7 partition to mount at '/' which is the root. The linux-swap partition will automatically be picked up so I don't have to even think about it at all. From that, just let it install (choosing to install the bootloader, of course), and enjoy a dual-boot! Erm... I hope I got that right. I'm confident I understand what you've told me, and I hope that it works when I put it to the ultimate test.

Sounds good. Good luck!

You can always mount the Windows 7 partition from the Places menu, but I agree - it's best left alone. I discovered the bad NTFS fstab options in the installer with a shared data partition.

**Edit:** just had another thought for you to think about. I won't suggest any details - that's up to you. If you go the route of making sda7 your root partition, you'll have a 40+GiB partition. Which is fine. But some people prefer a separate /home. I'm fairly neutral about that - there are pros and cons to a separate /home. When I've got Windows on a machine with Linux, I like to have a separate data partition which I format NTFS (which is how I discovered the bug in the installer) and which I can access from both Linux and Windows. So - you have several options to think about. You've still got that 9+GiB lurking about unformatted which you could use for something or other. If you make a partition there it would be a primary one and would become sda4 - which would give you the maximum of three primaries and one extended.

So - if you decide on something more complex that swap=sda6 and root=sda7, make your partitions with Gparted and then at the 'manual' stage of the installer, be careful to allocate your partitions as you want them.

---

### Post by Skyline969 on 2010-03-30
> **coffeecat said:**
> Sounds good. Good luck!

You always mount the Windows 7 partition from the Places menu, but I agree - it's best left alone. I discovered the bad NTFS fstab options in the installer with a shared data partition.

**Edit:** just had another thought for you to think about. I won't suggest any details - that's up to you. If you go the route of making sda7 your root partition, you'll have a 40+GiB partition. Which is fine. But some people prefer a separate /home. I'm fairly neutral about that - there are pros and cons to a separate /home. When I've got Windows on a machine with Linux, I like to have a separate data partition which I format NTFS (which is how I discovered the bug in the installer) and which I can access from both Linux and Windows. So - you have several options to think about. You've still got that 9+GiB lurking about unformatted which you could use for something or other. If you make a partition there it would be a primary one and would become sda4 - which would give you the maximum of three primaries and one extended.

So - if you decide on something more complex that swap=sda6 and root=sda7, make your partitions with Gparted and then at the 'manual' stage of the installer, be careful to allocate your partitions as you want them.

I really don't care about separating the OS from my data (/home). This isn't a server, and I back up my data always (I'll probably just use everything off of my 320GB external hard drive, formatted NTFS... minus a few things of course, like frequently used stuff and Ubuntu-specific applications and application data) so I don't have to worry about separating data from the OS. I'm a simple kind of guy, and I think that sda7 as my root and sda6 as my swap will be all I'll need. ;)

As for that spare partition, I might use it for something else. Not sure yet... perhaps an install of Chromium OS in the future? Either way, that 9GB partition can just be there by itself for the time being, until I think of something to use it for.

EDIT: One more question, can I name that sda7 partition Ubuntu or something along those lines and have it show up in My Computer in Windows as Ubuntu, and then somehow not make my swap show up in My Computer in Ubuntu?

---

### Post by coffeecat on 2010-03-30
> **Skyline969 said:**
> EDIT: One more question, can I name that sda7 partition Ubuntu or something along those lines and have it show up in My Computer in Windows as Ubuntu, and then somehow not make my swap show up in My Computer in Ubuntu?

You can certainly give it a partition label in Gparted (or with the command line tool e2label) but it won't show up in My Computer unless you install a 3rd party Windows driver for ext2/3/4. But, at the moment, I believe there is no Windows driver for ext4, which is probably what you are going to use. And, personally, I wouldn't use a Windows driver for ext3 either.

No problem with swap - it simply won't show up. Not in My Computer - or "Computer" as it's now called in W7. :p

But if you go into Control Panel > View=icons > Administrative Tools > Computer Management > Disk Management, you'll see all your Linux (logical) partitions listed as "Healthy Primary Partitions". Which only goes to show how confused Windows can get.

Next question? :wink:

---

### Post by Skyline969 on 2010-03-30
> **coffeecat said:**
> You can certainly give it a partition label in Gparted (or with the command line tool e2label) but it won't show up in My Computer unless you install a 3rd party Windows driver for ext2/3/4. But, at the moment, I believe there is no Windows driver for ext4, which is probably what you are going to use. And, personally, I wouldn't use a Windows driver for ext3 either.

No problem with swap - it simply won't show up. Not in My Computer - or "Computer" as it's now called in W7. :p

But if you go into Control Panel > View=icons > Administrative Tools > Computer Management > Disk Management, you'll see all your Linux (logical) partitions listed as "Healthy Primary Partitions". Which only goes to show how confused Windows can get.

Next question? :wink:

Wow, is there any question you can't answer?

Hm... ok, try this one on until I install Ubuntu :P :
What's holier than God, more evil than Satan, the rich people need it, the poor people have it, and if you eat it you'll die?

---

### Post by coffeecat on 2010-03-30
> **Skyline969 said:**
> What's holier than God, more evil than Satan, the rich people need it, the poor people have it, and if you eat it you'll die?

What it costs to buy Ubuntu! :wink:

---

### Post by Skyline969 on 2010-03-30
> **coffeecat said:**
> What it costs to buy Ubuntu! :wink:

Touché.

I'm currently on the Live CD... I've expanded my partition, and now I'm moving the MEDIADIRECT partition to the front of sda3. I'll be editing this post while I work. I'm really nervous right now. I haven't been this nervous since I hacked my PSP for the first time. :P

Comments at this point: Is it SUPPOSED to take this long? It's been taking an awful long time just to move a partition within my extended partition.

Ok, done. Time to create the linux-swap and ext4 partitions.

linux-swap done successfully. That was easy. Odd... my unpartitioned space was, once again, split up. I have a 40-something gig space and a 5-something meg space.

ext4 partition created successfully. Filesystems are in place... time to install.... Now I'm nervous. :P

Comments at this point: I now have two sections of unallocated space in my extended partition - a chunk that's 5.69MB and a chunk that's 1.31MB. I'm not too worried about using them up, and I doubt they'll hurt anything, so I'm just gonna leave them be. And what's this? Just from formatting, 894.86MB of the Ubuntu (sda7) partition is used. I'm gonna assume that's for file allocation stuff.

OK, just told it I would specify partitions manually. Ooh, advanced. I guess I'm advanced. :P

Um, what do I set sda7 as? ext4 journaling file system? Logic would indicate that I would use it as an ext4 journaling file system... so that's what I'll do. Also, if I don't specify where to mount /home, does it automatically mount it on the root, provided I specify where to mount root (/)? Which, by the way, I chose to mount on sda7.

Whatever, pressing on. I chose to not migrate anything from any of the accounts listed. On the next screen, I chose to install the boot loader, and for hd0 to be the device for the boot loader installation. All of the other stuff on the Advanced window I left blank.

Installation window notes:
 Language: English
 Keyboard layout: USA
 Name: (My name)
 Login name: (My first name)
 Location: America/Regina (not where I live, but same time zone)
 Migration Assistant:



If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

The following partitions are going to be formatted:
 partition #6 of SCSI1 (0,0,0) (sda) as swap


Okay, going hot now. Whatever happens, happens. The rest is out of my hands. Will post back when I've rebooted into Ubuntu.

---

### Post by coffeecat on 2010-03-30
My last post for today - late here in the UK.

Just a few comments.

> **Skyline969 said:**
> Is it SUPPOSED to take this long? It's been taking an awful long time just to move a partition within my extended partition.

Yes, it's doing a dd - very slow. Try shrinking **and** moving an ext3 partition. :p There's time for a main meal - four courses!


> **Skyline969 said:**
> I have a 40-something gig space and a 5-something meg space.

...

Comments at this point: I now have two sections of unallocated space in  my extended partition - a chunk that's 5.69MB and a chunk that's 1.31MB

Those odd handful-of-MB bits left over are something to do with cylinder boundaries - I think.

> **Skyline969 said:**
> And what's this? Just from formatting, 894.86MB of the Ubuntu (sda7) partition is used. I'm gonna assume that's for file allocation stuff.

Partly. Also about 5% is set aside for use by root for trouble-shooting.

> **Skyline969 said:**
> Um, what do I set sda7 as? ext4 journaling file system? Logic would indicate that I would use it as an ext4 journaling file system... so that's what I'll do. Also, if I don't specify where to mount /home, does it automatically mount it on the root, provided I specify where to mount root (/)? Which, by the way, I chose to mount on sda7.

Ext4 is fine - better than ext3. If you don't specify a separate /home, your home folder is set up in the root filesystem. Looks like you're doing the right thing.

Good luck!

---

### Post by Skyline969 on 2010-03-30
> **coffeecat said:**
> My last post for today - late here in the UK.

Just a few comments.



Yes, it's doing a dd - very slow. Try shrinking **and** moving an ext3 partition. :p There's time for a main meal - four courses!




Those odd handful-of-MB bits left over are something to do with cylinder boundaries - I think.



Partly. Also about 5% is set aside for use by root for trouble-shooting.



Ext4 is fine - better than ext3. If you don't specify a separate /home, your home folder is set up in the root filesystem. Looks like you're doing the right thing.

Good luck!

I have successfully rebooted into Ubuntu. The sound is terribly quiet, even with the volume maxed. I hope an upgrade to 9.10 will fix that. Anyways, time to reboot into Windows 7 to make sure that works still!

Well, this is my edit from inside Windows 7! It works! However, in the bootloader there's an option for Windows XP Embedded or something... I don't want to try booting to it, I want it off of the boot menu. How can I do this?

Holy crap, the speed increase from Win7 to Ubuntu is incredible! You could say... it's over 9000....
Anyways, the sound is so low it's almost non-existent, even on max volume, which is a big problem for me. I'm running all the updates and then upgrading to 9.10, so hopefully that irons things out.

---

### Post by dreamingdarkness on 2010-03-30
From what I remember, I had some problems like that when I first installed, with the volume levels.
Make sure all the volume settings are turned up to the top, including alsamixer, which you can access from terminal, typing in aslamixer, not a very good GUI but it may let you fix the issue.
If that doesn't work, there are some threads for low sound in the forums here, might give those a read.
Best of luck!

---

### Post by Skyline969 on 2010-03-30
> **dreamingdarkness said:**
> From what I remember, I had some problems like that when I first installed, with the volume levels.
Make sure all the volume settings are turned up to the top, including alsamixer, which you can access from terminal, typing in aslamixer, not a very good GUI but it may let you fix the issue.
If that doesn't work, there are some threads for low sound in the forums here, might give those a read.
Best of luck!

Actually, 9.10 fixed my sound... but killed my Wifi. Great. Time to post a new thread for that!

---

### Post by RJARRRPCGP on 2010-03-31
> **Skyline969 said:**
> Touché.

I'm currently on the Live CD... I've expanded my partition, and now I'm moving the MEDIADIRECT partition to the front of sda3. I'll be editing this post while I work. I'm really nervous right now. I haven't been this nervous since I hacked my PSP for the first time. :P

Comments at this point: Is it SUPPOSED to take this long? It's been taking an awful long time just to move a partition within my extended partition.

Ok, done. Time to create the linux-swap and ext4 partitions.

linux-swap done successfully. That was easy. Odd... my unpartitioned space was, once again, split up. 

Just delete the sda3 partition and this time, create a PRIMARY partition!

---

### Post by coffeecat on 2010-04-01
> **Skyline969 said:**
> Actually, 9.10 fixed my sound... but killed my Wifi. Great. Time to post a new thread for that!

I'm glad it all got installed correctly. Sorry I haven't posted before but a fire and flood (together!? :?) in a major switching centre took out telephone and/or broadband for "tens of thousands of households" - including mine. :(

I'll post a comment on your wireless thread.

> **RJARRRPCGP said:**
> Just delete the sda3 partition and this time, create a PRIMARY partition!

Except that takes out sda5, which the OP seemed to want to keep.

---

### Post by Skyline969 on 2010-04-01
Haha, and like magic my wireless is fixed. Ubuntu is so random. :P

---

