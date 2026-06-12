---
title: "Best was to Upgrade from 8.10 to 9.04"
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Scunnered on 2009-04-08
I currently have 8.10 in 64 bit and am considering updating to 9.04 when it becomes available and wish guidance on the best approach.

When I purchased my laptop 8.10 was pre-installed but it took a great deal of work to effect a connection to my wireless router.  In then end my supplier effected a remote connection and finally I was able to work with wireless. However in establishing the required changes they downloaded directly from their system and I ended up with a mixture of Gnome and KDE.

I would much prefer to keep matters simple and have either Gnome or KDE and the minimum to meet my preferences for Applications etc.  

I am concerned that if I just take the upgrade route that there will be a mixture of what exists and  9.04 and feel that it might be safer to treat 9.04 as a separate install.  This will I hope ensure that I can have a wireless connection if 9.04 does not automatically connect.  

Currently I have only 8.10 on an ext 3 and an 2 GiB extended and swap partitions so there is plenty of room to play with.  Should I use ext 3 or ext 4 and how do I best achieve this aim ?   I am prepared to be patient and propose to wait until the 2nd/3rd week before effecting any changes.

Thanking you in anticipation

---

### Post by Sam Lars on 2009-04-09
Upgrading may work fine, but it will leave you with a bit more of a mess.  It won't necessarily "mix" what you have now with Jaunty, it will install all the new versions of packages that are in Jaunty, but the upgrade can be messy sometimes.  If you've done a lot of package installing and such, it may end up removing some third party packages and other packages as part of the upgrade anyway.
Installing Jaunty fresh would definitely be a good way to clean up and get a good start.
If you have the space and anticipate issues, I would definitely install Jaunty separately.
Ext4 will not be default for a reason.  Even though it's been officially released, there will most likely be some bugs that are found and that must be fixed in the coming months.
You may experience a bit of a performance improvement, but nothing drastic.
Ext4 should be reasonably safe, but you should stick with Ext3 if you want the safest option.

---

### Post by Scunnered on 2009-04-09
Sam Lars

I am unsure of my best approach therefore the post.  I would much prefer to keep 8.10 active and add 9.04 as a fresh install effectivly giving a dual boot option. Will this work OK.  If so, if I have read things right so far, is it a case of when given the option to partition that I resize the main partition ?  I bought Begining Ubuntu Linux third edition to aid my adventure but keep getting confused as they seem to thing that I am a refugee from Windows and playing with Ubuntu.  I gave up on Windows so my total HD is devoted to Ubuntu and there is no going back.

If I therefore accept that resize the main partition is the road to go down other than splitting the ext3 on a 50 - 50 basis is there anything other that I need to do?
This is where I am a bit unsure.

I will accept that perhaps ext4 might be best left alone at the moment. I had only thought that by using 8.10 as ext3 and 9.04 as ext4 I would have kept them well apart but I will bow to your superior knowledge. I am all for safety first.  

If you can clear things up on these points it will be appreciated.

Thanking you for your kind assistance

---

### Post by Sam Lars on 2009-04-09
Yes, you can install another instance of Linux and have it as an option at boot.  It would be as simple as resizing the correct partition in the installation process.  When it installs the grub bootloader, it should detect both installations and add them as options.
Separate filesystems would separate your installations, but I'm not sure that's really for the best...
If they're both ext3, then whichever partition you do not boot to will show up under Computer (probably as "50 GB Media" or whatever size you have).  Setting 9.04 to ext4 would allow it to read 8.10's drive but not the other way around.
Another thing you might want to consider is putting your /home on yet another partition.  This will let you share it across both versions, which should be reasonably safe depending on what you're doing.  It would also let you easily reinstall either version of Ubuntu without worrying about your data, just the programs installed.

---

### Post by Scunnered on 2009-04-10
Since I last posted I downloaded the beta and ran it as a live DVD. It worked a treat and I like what I see.  I was pleased to see my biggest worry vanish before my eyes.  To see the wireless network connection icon and have it immediately connect with my network was exactly what I wanted.  I had visions of having to arm wrestle the laptop into submission so this was beyond my expectations.  

What I think I will do between now and the release is to check out what I currently am using and what I will need to download to bring Jaunty in line to meet my needs. It should be reasonably simple as I am far from being a power user.  In the main I use the PC to get my daily news fix from the BBC radio and TV while I am working on the system and cooking the bowling club books.  

Just a thought if I copied the beta to a 2 GB USB stick could I run it like a live DVD but load the plugins etc that I require to get my radio etc and programmes like Rhythymbox etc.

I feel a lot happier now about doing a fresh install and think that if I can set up a USB to work the way I want that I will load it to my HD in the first instance and then update to the final issue of Jaunty once the servers have a chance to cool down.

Would this be a practable approach or should I just identify what I will need to install to the final Jaunty and then be patient?

I thank you for your assistance and look forward to hearing further from you. Your guidance is most appreciated and is making me feel more confident in working with Ubuntu.

---

### Post by Sam Lars on 2009-04-10
The utility in Jaunty lets you copy an Ubuntu CD to a USB drive, and determine how much space to leave for settings and files.  This should let you make a customized installation on a USB drive.
As for copying it to the hard drive, I'm not sure if that will work.  Is that what you meant?
If you go into Synaptic to File > Save Markings As, it will save a list of all packages you have installed.  You could then load it into Jaunty and let it install them all for you.  I've never tried this, but if you have a bunch of stuff you want to keep straight, you may want to.
For now you could identify what all you need to install.  For me, I installed the obvious stuff, and then as things came up that I needed I installed them.

---

### Post by drs305 on 2009-04-10
I installed Jaunty on a separate partition for the reasons you initially stated - making sure I still could access a working system. So far I've been very pleased with Jaunty. 

I initially installed it with ext3 but converted to ext4 after the install. I've had no problems with ext4 as a file system but there is one thing to consider if that is the way you go. For troubleshooting, with an ext4 / partition, I couldn't get into the file system to check things from my intrepid install since intrepid couldn't read the ext4 format. I hadn't anticipated that even though it should have been obvious. It wasn't a big deal, and shouldn't be for you - especially if you plan on keeping a single version. Just thought I'd bring it up.

---

### Post by Scunnered on 2009-04-11
My thanks to you both for your replies. 

I have been in the interim attempting to see what I need to do to ensure that my existing set up is replicated.  I was a bit surprised to find that access to the BBC in the UK was not immediately available and when attempting to find what had been loaded in 8.10 to achieve my aim was not available.  I have covered this elsewhere.

From what you both indicate I think that I will just be patient and after the first rush is over download and load Jaunty as a single entity.

I thank you for your kind assistance and look forward to the arrival of Jaunty as it looks just what the doctor ordered.

---

