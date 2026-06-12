---
title: "Help with dual booting xp and ubuntu 6.10"
date: 2006-12-31
forum: Installation &amp; Upgrades
---

### Post by AgentKilo on 2006-12-31
Hi all Semi-Linux noob here. Please read on.

After using windoze for the past 5 years and knowing about the security issues of windoze compared to that of a linux system and ubuntu's latest release out i decided to try it.

So i downloaded the ubunbtu 6.10 release. I actually got it off a bit torrent site as it came down alot faster compared to the ubuntu mirrors (assuming it was on the ubuntu tracker)

Anyway i burned the iso to cdr (at a slow burn) and booted from the cd.
I didnt do an md5 check first tho as there was about 1000 seeds and twice as many peers so just went for the burn without doing the md5 check.

Anyway ubuntu loaded and the desktop appeared and after playing around with it and managing to get it onto the internet. i decided to go for the install.

Everything went well at first and i entered all the needed options in, name, country etc.
I just chose to resize the first partition of the hdd and use freed space. ok..

It starts the install progress fine but locks up and freezes at 24%.

I decided to leave it for a while (about an hour) only to return to see it was still stuck at 24%. So i had no choice but to shut the pc down via a long press on the power button.

What happened next?
Black screen with 3 ugly words informing me
Operating Sytem not found.
Great!

Obviously at the begining of install it changed the MBR ?

Had to use my windoze cd to do an over-the-top install, which sorted that out.
I was able to boot into windoze again and no changes were made. 
Apart from there being another windoze folder called WINDOWS.0 which was right for what i done.
I simply edited the boot.ini and deleted that folder along with the ones in all users documents etc. Saving all my files, data on my C:

Looking in disk managment now and seeing more partitions, obviously what the installer done for the ext3 fs and swap partition etc.

Had to use partition magic to sort that out, which on launch aplty informed me the MBR had an error but fixed it.

Anyway my drives are back to normal and my os is fine (can u say that about windoze?)
But ive still not got a dual boot system ](*,) 

I decided to do an md5 check. i used 2 programs for this and got 2 results.
winMd5Sum and md5summer
winMd5Sum said that the md5 sum was wrong and md5summer said it was ok. :???: 
Compared to the results on the [http://releases.ubuntu.com/6.10/MD5SUMS](http://releases.ubuntu.com/6.10/MD5SUMS) page

Anyway going to re-download it again and try again.

The moral of my story? Always do an md5 sum check and do a cd integrity check after before trying to install ubuntu!

My specs are.
Sony VAIO vgn laptop with wireless.
Intel Duo 1.66 GHz
1GB RAM
80GB HDD
xp pro media center edition (not dual booted with ubuntu!)

Any ideas why the installer froze on me? maybe because the download got corrupt or the cd had a deffect?

AgentK - Not easily defeated (especially by software)

---

### Post by bulldog on 2006-12-31
Try and download the gparted live cd and partition your hard disk before you attempt to install.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

When the installer comes to the partitioner,just choose manual and mount the already created partitions at the proper place,and reformat them.
Continue the install and all should go well.

---

### Post by AgentKilo on 2006-12-31
Thanks for the help, Ill give it a go. Its the gparted-livecd-0.3.3-0.iso I want isnt it.

Burn to cd and boot from it yes. Will check the docs/faq anyway.

Also whats the difference between the *ubuntu-6.10-desktop-i386.iso* and the *ubuntu-6.10-alternate-i386.iso*?

Will return with the results at some point being as its nye today and dont really wana be stuck in waiting for a system to install ;)  wish me luck.

---

### Post by bulldog on 2006-12-31
> **AgentKilo said:**
> Thanks for the help, Ill give it a go. Its the gparted-livecd-0.3.3-0.iso I want isnt it.

Burn to cd and boot from it yes. Will check the docs/faq anyway.

Also whats the difference between the *ubuntu-6.10-desktop-i386.iso* and the *ubuntu-6.10-alternate-i386.iso*?

Will return with the results at some point being as its nye today and dont really wana be stuck in waiting for a system to install ;)  wish me luck.

The difference between the desktop [live cd] and the alternate cd is that the alternate is a text based install and no live cd functions.
It runs much smoother and the installer seems to work a little better :D 
If I had to choose I would go for the alternate.

---

### Post by AgentKilo on 2007-01-01
Thanks for that i think ill try the alternate cd especially considering i just downloaded the live cd again and burnt it on the lowest speed and i got a blank cd!!!!?!?!?!

i done the same as before, used nero to burn an image to disc as an image and not as data but the cd is blank even in explorer. weird!!!!! know why it would have done that?

think ill dl the alternate and burn it to a good quality dvd.

Also i used the gparted live cd to partition my hdd but all ive got to so far is to create a new partition which is formatted with the ext3 fs. What i realised is that once the live cd has booted you can run gparted from the system > administrative tool bar option anyway cant you. Will it work the same way though?

Going to try again....

---

### Post by bulldog on 2007-01-01
The partitioner on the live or alternate cd works the same way too,but using the gparted live cd is much more clear.
It will be quicker and I personally like it a lot better.

To install ubuntu you have to create a minimal of 2 partitions, a /  (root) and a swap file,which size is depending of the amount of RAM installed in your computer.
A rule of thumb is twice the amount of RAM but if you have 1GB or more,a swap of about 1GB is sufficient.

Some suggestions
Make an ext3 partition 10GB for /
Make an ext3 partition as big as you like for /home
Make a swap 1GB

---

### Post by Bartender on 2007-01-01
If you continue having problems with the GParted LiveCD (I agree with bulldog, the stand-alone partitioner just seems to work better) then I'd suggest taking a screenshot of your partition map and showing us what you've got.

"Partition Map" isn't an official term; it's just what I call the map of your drive that shows up in GParted. 
Do you have a USB thumb drive?  Start up the Ubuntu LiveCD.  When it gets to the desktop plug in your USB thumbdrive.  It should be recognized and an icon should pop up on the desktop.

Go into System>Gnome Partitioner, bring up the map, then go over to Applications>Accessories>Take Screenshot.  Take the shot.  I think the next thing that happens is you get a Save As window.  If so, your USB drive should be there in the list of folders.  It might have a funny title but you should be able to figure it out. 

If you can do all that, you're doing well for a beginner.  Right-click on the USB icon on the desktop, left-click on Eject, wait a few seconds, then remove the thumb drive.  Close out of the Live CD, come on back to the forum, and attach your map.

You can take a screenshot directly from the GParted LiveCD, but it's a little trickier.  Not hard, just confusing until you've got a bit more time in the seat.  I wrote up a How-To

[http://ubuntuforums.org/showthread.php?t=325775](http://ubuntuforums.org/showthread.php?t=325775)

The simpler way is to bring up a terminal from within the Ubuntu LiveCD, type 
```
sudo fdisk -l
```, and save the output to your thumb drive as a .txt file
but I find the partition map a lot more helpful.

---

### Post by AgentKilo on 2007-01-02
Hi im back, thanks for those that have posted its been helpfull reading your replies.

Well all i can say is GRRRR!!! Im really fcukng mad right now!!
I dl the alternate text installer, done an md5 check, that was fine.
Burned to a high quality DVD disc on the slowest speed.
Booted from it and done an integrity check... it failed ](*,) 
I went ahead with the install anyway just in case it was a not v important system file that was corrupt?.
Well what a mistake that was!

I chose to resize the C: drive partition for it to make its own partitions as needed for /root and swap etc. 

WHY THEN DID IT DELETE MY D: DRIVE AND ALL MY DATA ON IT?!?!?!?!?!?!

It says before install it will delete any data on partitions to be formatted and those not selected or something doesnt it. why??? why format a partition that isnt even anything to do with the install?!?!? JUST LEAVE MY D: DRIVE ALONE FFS!!!!!!

Twice now ive had to reload all my music back onto my laptop.
Not to mention all the apps i had on that drive ive lost!

Anyway the installer failed at 6% and i was forced to reboot the laptop only to find i only had a C: drive which sure enough was resized.
Partition Magic showed the other partitions ext3 root and swap partitions it had created and apparantly the D: drive was "Unallocated"!! So had to delete the ext3 partitions and resize C: back to the original and then format D: NTFS (Which is now empty!!)

Why am i having such bad luck with installing ubuntu onto this box?
Im not a pc noob in fact i used to be a global mod on a forum where id help people out often being the one with the know how. Ive dual booted windows with other windows versions countless times.
Is it my laptop? I looked on the test dec list and i see other people have installed it onto a sony vaio similiar to mine.

I think it must have just been the burn went bad somewhere.
Actually did it at 4x so will try 2x.
Am determined to beat this and have a smooth running dual booting laptop with windoze and ubuntu on it!

oh to mention as well i did do an md5 check and it was correct just the integrity check failed. How many coasters im gonna make before i succeed is another matter.....

---

### Post by Bartender on 2007-01-03
Kilo -
I'm sorry to hear that things have not gone well.  

I don't have the anwers for you off the top of my head but can tell you one thing for sure - if "Check CD for Errors" reports ANY errors that's it.  Don't be thinking dangerous thoughts like "well, maybe it's not an important file".  We've all pushed forward with some project in Windows even though it was reporting some sort of error.  Windows is stupid and very often what you're trying to do works anyways.

Linux is not stupid.  If it's telling you there's something wrong you better listen.

I don't have broadband at home.  I take a 1GB thumbdrive (td) to a place that does have broadband to download Linux distros.  I leave the PC alone while it's downloading.  No surfing the net, playing games, etc.  Then I take the td home and transfer the data to a new folder.  Then I burn to a CD.  I don't touch the mouse or keyboard while it's burning.  I've done this a dozen times and never made a coaster yet.  (Knock on wood)

I use good quality 700MB CD's & burn them at 8X (would do it slower but my NTI burn utility doesn't go lower and it's worked so far).  Do not, repeat *do not*, do anything else while the PC is downloading or burning.

If you've got a good download (the md5 checks out) and have a way to transfer the .iso to a friend's PC, maybe you should try that.  Maybe your optical drive is losing its tolerances.  At this point, the thing to do is try something different and see if the problem follows you around or doesn't.  That may help you to pinpoint what exactly is going wrong.

Are you saying that your Windows install is kaputski?  Finito?  Gone with the wind?  If so, and you gotta start over anyways, maybe wipe the drive clean with dban or some other utility that'll nuke whatever formatting is there now, then try telling Windows to install to part of your HDD instead of the whole thing, then use the free space to install Linux.

That worked for me when I had to reinstall Windows once before.

---

### Post by Bartender on 2007-01-03
Something else to try - 
Apparently Partition Magic works for some people and has wreaked havoc for others.  Why not download GParted LiveCD (GPLCD)?  It's an incredible tool for partitioning projects, and it describes the partitions in Linux-speak (hda) instead of Windows's C drive, D drive, etc.  I'm in the habit now of taking a screenshot before leaving GPLCD and printing it out.  Very helpful to have when you go back in with the Linux install CD.  Or take a screenshot from the LiveCD's partitioner - that's easier than from GPLCD.

Here's [instructions]("http://www.ubuntuforums.org/showthread.php?t=325775") for doing it while still in GPLCD.

It's funny - a year ago I couldn't make myself stop thinking in terms of C drive, D drive.  Now the Windows method seems lame.

Anyway, using GParted instead of PM removes one more variable from the equation...

---

