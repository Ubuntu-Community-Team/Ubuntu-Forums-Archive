---
title: "Help With Install"
date: 2012-04-11
forum: Installation &amp; Upgrades
---

### Post by ghughes20 on 2012-04-11
Greetings all.  After playing with Ubuntu via a thumb drive for a few weeks on an old Dell computer, I've decided to commit to a full install on the hard drive.  I've not attempted to make this a dual boot system so I'm installing with Ubuntu as the only OS.

 During the install, I get the following error message...  "Executing 'grub-install/dev/sda' failed.  This is a fatal error"  The next prompt asked me if I want to place the boot loader in a different location.  I tried to place in in something called an array and continue the install.  I do this and restart the computer and I'm unable to boot.  When I go into the bios screen and select the "Intel Array" to boot from, the PC hangs and I have to restart.  I attempted to install twice from the thumb drive with the same result.

I suspect the problem is related to the fact that I have two hard drives that the PC synthetically combines as one.  During the bios boot up screen it lists both hard drives.  (See attached photo).

Any advice would be greatly appreciated.

Greg

---

### Post by acimi66 on 2012-04-11
It is impossible to see that image I 'm afraid.
Have you partitioned the hard drive?

You want to consider downloading another copy of the OS, just a thought.

---

### Post by ghughes20 on 2012-04-11
Here are some larger pics.   Photo 5 shows an early screen during the install process.  It displays where it will install Ubuntu.  Photo 6 shows the screen I see after I get the error message during the install and attempts to prompt me as to where it should install the boot loader since the first option failed.  Photo 7 shows the bios screen where the PC hangs up.  

Greg

---

### Post by acimi66 on 2012-04-12
Hey Greg, this is something I am not familiar with... 
But I did get this from another post..

"If installer is throwing that error( Executing 'grub-install/dev/sda' failed) then some thing is wrong with either .iso image(s) or the way your burning those images.
 
From where did you download Ubuntu .iso image? Have you verified its  MD5SUM? Try to burn .iso image at lowest possible speed supported by  your CD/DVD burner."

It could be as simple as burner another copy.

---

### Post by ghughes20 on 2012-04-12
I downloaded Unbuntu a second time and reinstalled from CD and had the same problem.

I've included so new pics from my bios that might help illustrate my set up, and hopefully my problem.

Photo 8 shows the boot sequence of my drives

Photo 9 shows the SATA operation

Thank you,

Greg

---

### Post by Rodney9 on 2012-04-12
Burn the discs at the slowest speed you can.

Try a different brand of cd.

Check MD5SUM for your CD/DVD

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)



For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by mastablasta on 2012-04-13
you have a RAID array (maybe even software RAID). It doesn't combine them into one disk, raid usually creates redundancy which is good if one disk fails the other still holds the same data. but it all depends on the setup i guess.
 
anyway to install it on a raid array have a look here [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
 
scroll down for info regarding RAID install.
 
if you are sure you are using software raid array you can try following this: 
[https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html)

---

### Post by ghughes20 on 2012-04-22
So, based on the advice in this chain, I tried a few things.  First, I use MD5SUM to check the ISO file I downloaded and it checked out fine.  I then tried to burn the ISO image on a new disc.  (I couldn't figure out how to use MD5SUM to check that the ISO file burned correctly on the CD or thumb drive that I attempted.)

I also tried to install an "alternate" version which I learned about from this link.... [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation) .   During this install, it seemed to recognize my RAID, however, during the installation, the PC repeatedly hung up.  

Not to be deterred, I discovered a way to disable the RAID.  When I did this, I tried to create two ATA drives to match the two physical drives I have in my Dell XPS 400.  (The RAID was set up so that the PC only saw one hard drive).  I was able to disable the RAID, however, the Dell now only recognizes one of my two hard drives.  I decided to try and install Ubuntu onto this hard drive using my thumb drive image of the iso file.  It worked and I'm typing this post from Ubuntu.  

However, once I did the install, I was prompted by Ubuntu to update the driver for my video card.  When I did this I was unable to access 3D, so now I can only use 2D.  I'll try to learn how to undo this change so I can use 3D, but that will be a topic for a different thread.

If I figure out how to reactivate the other hard drive I will repost to this thread.

Thank you for all the advice.

Greg

---

