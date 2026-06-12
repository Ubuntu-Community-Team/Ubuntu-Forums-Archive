---
title: "help with triple boot.....please"
date: 2008-01-31
forum: Installation &amp; Upgrades
---

### Post by DeathGrind on 2008-01-31
yeah i would really like to reinstall ubuntu 7.10 on my laptop.  But i am hesitant for one reason.  Boot configuration.  Maybe someone can help me out.
Okay to start:
created three partitions on a newly formatted drive using Windows XP install CD:  C,D,E partitions.
-Installed XP on C partition
-Installed Vista on D partition
         -NOTE: when in XP, XP is the C partition, Vista is the D partition (20GB).
         -NOTE: when in Vista, Vista is the C partition and XP is the D partition (50GB).  (Is this normal?)
-In Vista-formatted the E partition for a storage partition for music, videos and what not (80GB).

okay so now i would shrink a partition using vista disk management.  So i would shrink my E partition by about 10GB.  Now I have about 10GB of unallocated disk space.

Get the LiveCD 7.10.  Reboot and install.  Choose guided method so it  automatically will install ubuntu on unallocated disc space.  

Cool.....been there done all that a few times now!

ubuntu installs.  at system start i am greeted by GRUB.  Cool choose vista loader option, boots into vista bootloader, pick XP or Vista.  Everything is golden.

Here's my problem.  I would like to use Vista Boot loader as my primary bootloader and boot into ubuntu or grub from there.

So i installed EasyBCD and reinstalled Vista bootmanager.  Finally figured out how to add grub/ubuntu loader to vista's bootloader.  Although i had to edit the start up screen everytime from hda 0,2 to hda 0,1.
After i figured that out i changed the actual boot file in ubuntu to hda 0,1.  Ubuntu booted from grub without need of a quick boot path correction.

PROBLEM.....My Windows XP became unbootable, gave me different errors no matter what i tried in EasyBCD.  

So after hours of researching i was unable to figure out what went wrong so i formatted and reinstalled everything! 
 I have followed all the steps i listed above.  Three partitions, C, D, and E (XP, Vista, Storage).  And now i really want ubuntu back.  Please Help me out.  I am ready to go just waiting for some pointers.

As to why I want to triple boot....
I run XP for my studio recording, XP is just better then vista for pro-tools, Waves plugins, ableton live, etc.  Plus there are no stable Vista drivers for a majority of my audio hardware.
I run Vista mainly for the media center, to hook up to my xbox360 and other extenders around the house.  And because it's new and came with my PC.
I would like to run ubuntu as a option to play with.  I like ubuntu so much i would consider switching completely if it had top notch audio applications, truth is I still need windows for that.

I have a gateway mt3423 laptop, i already know how to get the video and the stigmatel 9200 sound working.  As i have had ubuntu installed before.  

When it comes to boot loading i have no idea.  Please someone direct me in how to install ubuntu and make vista bootloader the primary after ubuntu install, how to add ubuntu to easyBCD, without messing with my XP boot.
Please i have spent the last 2 days getting XP and Vista running with all my apps and recording hardware, and really don't want to do it all again cause i messed up the boot loader or MBR or what ever it is.


and yes i did search before posting.  
thanks

---

### Post by logos34 on 2008-01-31
Did you follow the directions here:
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)
(main page: [http://neosmart.net/wiki/display/EBCD/linux](http://neosmart.net/wiki/display/EBCD/linux))

The important point is to install grub to the bootsector of the linux root partition.

Or try NeoGrub:
[http://neosmart.net/wiki/display/EBCD/NeoGrub](http://neosmart.net/wiki/display/EBCD/NeoGrub)

> After i figured that out i changed the actual boot file in ubuntu to hda 0,1. Ubuntu booted from grub without need of a quick boot path correction.

I'm not sure where you're getting that or why it worked--ubuntu root should have been the fourth or fifth partition (the latter if ubuntu guided install put / and /swap inside an extended)

---

### Post by DeathGrind on 2008-01-31
Thanks for the relpy. Will start trying this again.  Thank you.

> I'm not sure where you're getting that or why it worked--ubuntu root should have been the fourth or fifth partition (the latter if ubuntu guided install put / and /swap inside an extended)

okay after i set vistabootloader as the default, and i run ubuntu/grub from there, it boots into grub, it won't just boot into ubuntu.  I have to pick the ubuntu option (the first one in Grub) and hit e to edit it and the first first option i change from hda 0,2 to hda 0,1.  and then ubuntu boots.


anyway going to try it out again.  You poseted a page i did not read.  Thanks again.

---

### Post by logos34 on 2008-01-31
> **DeathGrind said:**
> 
okay after i set vistabootloader as the default, and i run ubuntu/grub from there, it boots into grub, it won't just boot into ubuntu.  I have to pick the ubuntu option (the first one in Grub) and hit e to edit it and the first first option i change from hda 0,2 to hda 0,1.  and then ubuntu boots.

what I referring to specifically was how grub is booting ubuntu at hd0,1--that's the second partition (I would have thought windows was on it).  I guess I should have asked you to boot from the live cd and run 

sudo fdisk -l

---

### Post by DeathGrind on 2008-01-31
Thanks logos34.  I followed the instructions on this link:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

It worked. just one thing i had to do that wasn't in the guide.  That was in EasyBCD,  check the box when adding linux boot option.

Also my main problem was that on my previous installations of ubuntu i was choosing guided method (the one that automatically install on free space) in the partition set-up.  I think that was it.  And i followed the guide and chose the advanced option and chose where i wanted grub installed.  Worked!

i am using ubuntu right now.  Just taking care of my sound now.  
All other os's boot fine.

Thanks again logo34 for taking your time to help me out.  
I was overwhelmed by all the dual/triple boot guides when i was searching for them.  
THANKS!

---

### Post by logos34 on 2008-02-01
> **DeathGrind said:**
> It worked. just one thing i had to do that wasn't in the guide.  That was in EasyBCD,  check the box when adding linux boot option.

now that you mention it, I noticed that too (it's not checked in the pictures, nor is there mention of it)

> Also my main problem was that on my previous installations of ubuntu i was choosing guided method (the one that automatically install on free space) in the partition set-up.  I think that was it.  And i followed the guide and chose the advanced option and chose where i wanted grub installed.  Worked!

Whether you use guided or manual, you still (IIRC) come to the 'Ready to install' (step 7) screen with the 'Advanced' button where you can change the grub location.  At any rate, glad it worked. 

> i am using ubuntu right now.  Just taking care of my sound now.  
All other os's boot fine.

Thanks again logo34 for taking your time to help me out.  
I was overwhelmed by all the dual/triple boot guides when i was searching for them.  
THANKS!

My pleasure! Take care.  Mark as 'Solved' (>thread tools).

---

### Post by Computer Guru on 2008-02-02
There shouldn't be a need to check the "GRUB isn't installed to the bootsector" box in EasyBCD unless you directed Ubuntu setup to install GRUB to the MBR.

---

### Post by logos34 on 2008-02-02
> **Computer Guru said:**
> There shouldn't be a need to check the "GRUB isn't installed to the bootsector" box in EasyBCD unless you directed Ubuntu setup to install GRUB to the MBR.

you're right...I just had a another look at it and the keyword is '**isn't**', so no, it shouldn't be checked in this case.

---

