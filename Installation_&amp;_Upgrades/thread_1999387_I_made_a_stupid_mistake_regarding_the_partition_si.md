---
title: "I made a stupid mistake regarding the partition size"
date: 2012-06-08
forum: Installation &amp; Upgrades
---

### Post by Scozzar on 2012-06-08
So I am running dual boot with Windows 7 (I'm typing this using ubuntu) and for some reason I accidentally made my Windows 7 partition VERY SMALL.  I was at the menu where you drag the two slides and I didn't know which one was which so I assumed that the right side was for Linux.  So I dragged the line as far as I could to the left.  WELL, it turns out that was for the Windows Partition and now I only have 10gb left of space for Windows and a whopping 641gb free for the Linux partition.  I intended it to be the other way around, 641gb for Windows and 55 for Linux.  I, unfortunately and blindly, made the mistake of not backing up a disk image file before I did this...So I'm not too happy about that.  What can I do to reclaim my space????  I tried going into WIndows manager and trying to extend the Windows partition but I could only shrink the partition...I'm in Linux (brand spankin' new to this fresh OS)  so I am completely lost on what to do.  Could someone help me please?

Thanks, Scozzar

---

### Post by wilee-nilee on 2012-06-08
Make the image of windows now, and boot a live ubuntu cd, and use gparted to resize the partitions.

You are better with the image of windows being as small as possible in my opinion.

I'm surprised it runs now honestly.

The windows partitioner will make it bigger if you have unallocated space I believe.

---

### Post by QuiGonJinn130 on 2012-06-08
Unless you are using Windows 7 for gaming, I would suggest virtualizing  Windows 7.  Go to Ubuntu Software Center and download and install VirtualBox.  Create a dynamic disk and install 7 then you have no need to dual boot and since the disk size is dynamic.... well there is always room to grow.

---

### Post by darkod on 2012-06-08
If you didn't shrink the ubuntu partition(s) first, windows Disk Management can't expand the windows partition. In order to be able to expand it, you need to have unallocated space next to it.

You can shrink the ubuntu partitions from live mode, they have to be unmounted.

---

### Post by wilee-nilee on 2012-06-08
> **QuiGonJinn130 said:**
> Unless you are using Windows 7 for gaming, I would suggest virtualizing  Windows 7.  Go to Ubuntu Software Center and download and install VirtualBox.  Create a dynamic disk and install 7 then you have no need to dual boot and since the disk size is dynamic.... well there is always room to grow.

I'm not sure it is legal to move a OEM to a virtual, and it probably would not activate as well.

---

### Post by Scozzar on 2012-06-08
> **wilee-nilee said:**
> Make the image of windows now, and boot a live ubuntu cd, and use gparted to resize the partitions.

You are better with the image of windows being as small as possible in my opinion.

I'm surprised it runs now honestly.

The windows partitioner will make it bigger if you have unallocated space I believe.

Okay so what program do I use to make an image of Windows?  

Why is it better that Windows is as small as possible?  I need it to be as big as possible!  I am going to need it for college.  Linux is just nice to have avaliable, or so I've heard for certain program my college uses...but it's mainly all WIndows.  Why are you surprised it runs now?  

If it makes it any easier, I would have no problem just deleting the Linux partitions and reallocating all the space back to WIndows. I haven't done anything except browse the internet with it so I wouldn't be losing anything,,,

> You can shrink the ubuntu partitions from live mode, they have to be unmounted.     So I just plug in the Live boot cd and it'll take me to gparted?

Btw, I'm not virtualizing Windows 7.  It's too important and I really would have it at the mercy of the HDD than mercy of a program...The CD type I used for the live boot is a CD-R, so do I have to make another one or could I just re-use the same disk I used in the first place?

Thanks guys for the help so far!  Hopefully this can be taken care of soon.  

Thanks, Scozzar

---

### Post by snowpine on 2012-06-08
Boot the CD you already made in "Live" mode, and use GParted to shrink the Ubuntu partition(s) so you have some free space to expand the Windows partition.

Partition resizing is usually pretty safe, but I always recommend a full backup before proceeding, just in case.

---

### Post by wilee-nilee on 2012-06-08
> **Scozzar said:**
> Okay so what program do I use to make an image of Windows?  

Why is it better that Windows is as small as possible?  I need it to be as big as possible!  I am going to need it for college.  Linux is just nice to have avaliable, or so I've heard for certain program my college uses...but it's mainly all WIndows.  Why are you surprised it runs now?  

If it makes it any easier, I would have no problem just deleting the Linux partitions and reallocating all the space back to WIndows. I haven't done anything except browse the internet with it so I wouldn't be losing anything,,,

So I just plug in the Live boot cd and it'll take me to gparted?

Btw, I'm not virtualizing Windows 7.  It's too important and I really would have it at the mercy of the HDD than mercy of a program...The CD type I used for the live boot is a CD-R, so do I have to make another one or could I just re-use the same disk I used in the first place?

Thanks guys for the help so far!  Hopefully this can be taken care of soon.  

Thanks, Scozzar

A small image allows it to be put in a small place and resized bigger. Windows 7 below a pro version has a one time image allowance it seemed prudent to image it now before you expanded it. Make sure you have a recovery disc that is made in the same backup recovery area.

I am surprised it works as resizing a windows distro that much usually results in a bricked system when done from linux. There are immovable files in windows when moved can leave a bricked OS.

To be honest before you do this ever again do some research.

You used methods that no one would recommend, or at least not within a safe margin.

---

### Post by Scozzar on 2012-06-08
Yeah, I know, I'll do some more research next time.  But this was all accidental in the first place so there wasn't much I could "prepare for."  

So I'll do an image backup and more backup stuff to an external HDD here soon.  If I don't respond, it's probably because I bricked Windows...BUT thanks for the advice so far 

Scozzar

---

### Post by llanitedave on 2012-06-08
I was just logging on to ask a question that would keep me from doing the same thing.  The installation wizard shows two partitions, but doesn't label either one, so I had no way of knowing which was windows and which was Ubuntu.

I'm glad I could learn from another's mistake, but sorry you had to go through all that trouble.  I think the Ubuntu team should try to label the choices next time around.

---

### Post by Scozzar on 2012-06-08
Well at least SOME good came out of this!

Well I'm off to the boot cd...wish me luck.

---

### Post by wilee-nilee on 2012-06-08
> **llanitedave said:**
> I was just logging on to ask a question that would keep me from doing the same thing.  The installation wizard shows two partitions, but doesn't label either one, so I had no way of knowing which was windows and which was Ubuntu.

I'm glad I could learn from another's mistake, but sorry you had to go through all that trouble.  I think the Ubuntu team should try to label the choices next time around.

You need to research what you are doing, the slider is going from left to right just like the install looks in a gui looking at the HD, it is quite obvious.

---

### Post by Scozzar on 2012-06-08
> **wilee-nilee said:**
> You need to research what you are doing, the slider is going from left to right just like the install looks in a gui looking at the HD, it is quite obvious.


I think he is trying to say that neither side is labeled so you are left to guess.  I assume that most members have never dealt with partitioning before until they want to use Ubuntu.  The installation guide Ubuntu provides doesn't go over this section.

Also, I am in "live" mode right now.  I am at the Gparted Sourceforge page and I don't know which version of Gparted to download.  The .iso or the .zip.  Do I use the .zip because I'm already in live mode?

---

### Post by wilee-nilee on 2012-06-08
> **Scozzar said:**
> I think he is trying to say that neither side is labeled so you are left to guess.  I assume that most members have never dealt with partitioning before until they want to use Ubuntu.  The installation guide Ubuntu provides doesn't go over this section.

Also, I am in "live" mode right now.  I am at the Gparted Sourceforge page and I don't know which version of Gparted to download.  The .iso or the .zip.  Do I use the .zip because I'm already in live mode?

Gparted is on the live cd already.

---

### Post by Scozzar on 2012-06-08
Where is it though?  I watched a few youtube videos and i saw it's in the "administration" folder, but I can't find that folder.  The videos were all using past versions so I know it's going to be different.  Do I need to go into the terminal and use "sudo?"  I've tried system settings and so forth and no folder..

---

### Post by wilee-nilee on 2012-06-08
> **Scozzar said:**
> Where is it though?  I watched a few youtube videos and i saw it's in the "administration" folder, but I can't find that folder.  The videos were all using past versions so I know it's going to be different.  Do I need to go into the terminal and use "sudo?"  I've tried system settings and so forth and no folder..

 I assume you have booted a live ubuntu cd is this correct, look in the dash, hit the windows key and type in gparted.

The top button in the left panel opens the same area to look.

---

### Post by Scozzar on 2012-06-08
Got it!  Thanks!

---

### Post by Scozzar on 2012-06-08
Okay sorry for the double post.  I don't think you would see my post if I edited it :P

ANYWAY so I was able to obtain 550gb of free space after shrinking the Linux partition.  That part was a success.  But now I have to add that back to the Windows partition and I don't know how.  Windows disk management wouldn't let me extend the volume (my guess is that it's to to me actually using the partition I was going to extend.  The volume was mounted.  Please correct me if I'm wrong).  So now I am trying to find a partition manager that would be able to extend Windows partition from the Linux OS.  Would Gparted work for this?  Could I just do another boot from the live cd and use gparted from their or does it have to be installed on the HDD to work?

EDIT: I found the following article.  [http://askubuntu.com/questions/143327/how-can-i-succesfully-merge-the-two-partitions-shown-using-gparted](http://askubuntu.com/questions/143327/how-can-i-succesfully-merge-the-two-partitions-shown-using-gparted)

Would it be safe to take some advice from this?

---

### Post by wilee-nilee on 2012-06-08
> **Scozzar said:**
> Okay sorry for the double post.  I don't think you would see my post if I edited it :P

ANYWAY so I was able to obtain 550gb of free space after shrinking the Linux partition.  That part was a success.  But now I have to add that back to the Windows partition and I don't know how.  Windows disk management wouldn't let me extend the volume (my guess is that it's to to me actually using the partition I was going to extend.  The volume was mounted.  Please correct me if I'm wrong).  So now I am trying to find a partition manager that would be able to extend Windows partition from the Linux OS.  Would Gparted work for this?

Post a screenshot of gparted, on a ubuntu install a extended partition is made many times that encases the ubuntu I am wondering if it is still in that space left by the resize of Ubuntu.

The W7 partitioner runs in a live environment if that is what you mean by mounted. I'm not real sure about its use in making a NTFS larger I think it is possible but just not sure on the exact method. 

Gparted would probably be okay to use, just make sure that space is truly unallocated, and not limited by a extended partition still there.

You may have to reload grub to the mbr after this is all done to boot ubuntu again, due to moving the front of the partition such a large distance, no biggie it is easy.

I'm going for some coffee and donuts now, so I will be gone for awhile, in  case you wonder why you are not getting an answer. Lots of good helpers on the site though. ;)

---

### Post by darkod on 2012-06-08
> **llanitedave said:**
> I was just logging on to ask a question that would keep me from doing the same thing.  The installation wizard shows two partitions, but doesn't label either one, so I had no way of knowing which was windows and which was Ubuntu.

I'm glad I could learn from another's mistake, but sorry you had to go through all that trouble.  I think the Ubuntu team should try to label the choices next time around.

It's sort of like highjacking the thread, but can you post a screenshot of the screen confusing you?

Usually it does say on which partition you have windows, as long as it can recognize it. Also, ntfs and linux partitions are marked with different colors so you can tell them apart.

On top of that, you can judge by the size of the partition(s). You don't know how big your windows partition is?

I don't use the automatic methods because the manual gives you best control, so I don't know what it looks like exactly right now, but earlier everything was marked pretty well.

---

### Post by Scozzar on 2012-06-08
[IMG]http://s865.photobucket.com/albums/ab219/scozzar316/?action=view&current=Screenshotfrom2012-06-08133730.png[/IMG]

Okay, well hoping that the picture thing actually works, there's a screenshot of Gparted from the LiveCD.  Moderators, feel free to size down the picture and so forth.  I tried using the links photobucket gave me but that wouldn't work...SO here it is

---

### Post by wilee-nilee on 2012-06-08
> **Scozzar said:**
> [IMG]http://s865.photobucket.com/albums/ab219/scozzar316/?action=view&current=Screenshotfrom2012-06-08133730.png[/IMG]

Okay, well hoping that the picture thing actually works, there's a screenshot of Gparted from the LiveCD

You use the paper clip in the reply panel to find the picture, then upload it then put it in the reply with the paperclip again.

---

### Post by Scozzar on 2012-06-08
Okay, that's much better!  Here's the screenshot.

---

### Post by wilee-nilee on 2012-06-08
hehe you moved the wrong end, but you can move that whole partition the sda5 to the right to the end of that extended the sda4.

Then move the left end of the extended up against the sda5 from left to right, this leaves an actual unallocated for windows to expand into. I would try the W7 partitioner then.

The sda4 the extended needs you to click on the listing of it to shrink it rather then the partition are at the top, easier to change it that way.

So your order of operations is move the sda5 first then snug the sda up against it.

You will be a pro at this after this now. :)
[B]
Make sure you unmount the swap before doing anything.[/B]

---

### Post by darkod on 2012-06-08
1. You can clearly see the unallocated space is still included inside the extended partition, that's why you can't use it.

2. Why did you shrink (resized) it like that? It was mentioned few times to shrink it in a way that the unallocated space is next to the windows partition. This is not. You still have the ubuntu partition between them.

You were supposed to drag the left end of the ubuntu partition to the right, so that the unallocated space is next to sda2.

Take into account that the more times you resize partition, more chance things to go real bad.

If you don't have any important data in ubuntu, I would just delete all ubuntu partitions from live mode, expand sda2 as much as you plan to (leave unallocated space for ubuntu), and then install ubuntu again. Note that you can't delete swap until you right-click it and select Swapoff. The key symbol in Gparted should be gone. Then you can manipulate it.

---

### Post by wilee-nilee on 2012-06-08
> **darkod said:**
> 1. You can clearly see the unallocated space is still included inside the extended partition, that's why you can't use it.

2. Why did you shrink (resized) it like that? It was mentioned few times to shrink it in a way that the unallocated space is next to the windows partition. This is not. You still have the ubuntu partition between them.

You were supposed to drag the left end of the ubuntu partition to the right, so that the unallocated space is next to sda2.

Take into account that the more times you resize partition, more chance things to go real bad.

If you don't have any important data in ubuntu, I would just delete all ubuntu partitions from live mode, expand sda2 as much as you plan to (leave unallocated space for ubuntu), and then install ubuntu again. Note that you can delete swap until you right-click it and select Swapoff. The key symbol in Gparted should be gone. Then you can manipulate it.

Not bad advice here as well OP, we just posted at the same time.

---

### Post by Scozzar on 2012-06-08
So would it be better to:

> So your order of operations is move the sda5 first then snug the sda up against it.or

> If you don't have any important data in ubuntu, I would just delete all  ubuntu partitions from live mode, expand sda2 as much as you plan to  (leave unallocated space for ubuntu), and then install ubuntu again.  Note that you can delete swap until you right-click it and select  Swapoff. The key symbol in Gparted should be gone. Then you can  manipulate it.     What's the easier, safer method?  My guess it would be better to remove all traces of Linux, then use the boot CD and partition it CORRECTLY the next time around.  Seriously, thanks for all the help guys.

btw, I have never used Gparted before so I didn't know how to resize it to where it would be next to the Windows partition, so cut me some slack! :)

---

### Post by darkod on 2012-06-08
We will cut you all the slack you want, your computer won't. :)

If we go by safer, and probably easier, deleting the ubuntu partitions is better. You don't have to wait for "next time around", the job is almost done.

The sequence would be something like:
1. Boot live mode with the cd, open Gparted.
2. Right-click the swap partition, select Swapoff. The key symbol next to it and the extended partition should be gone. Now you can work freely with the partitions.
3. Delete one by one /dev/sda6, /dev/sda5, then /dev/sda4. Leave the space as unallocated.
4. Tick the green button in Gparted to execute the changes.

Biggest part of the job is done. Since you deleted ubuntu, grub2 would give you error if you try to boot from the hdd like this. Temporarily, while still in live mode, open terminal and install generic mbr with lilo:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

There will be some warning, but ignore it, it's safe.

Restart without the cd and it should boot win7. Hopefully it still works fine on the small space. Open Disk Management and expand the partition for as much as you plan to, leave some unallocated space for ubuntu. Restart win7 few times in case it wants to do some disk checks.

After win7 is happy again (and you also), install ubuntu into the space you left unallocated.

Enjoy your dual boot.

---

### Post by Scozzar on 2012-06-08
Thanks for the step-by-step!  It's what I was looking for!  I will be printing that out.  I will be trying this out right now.

---

### Post by Scozzar on 2012-06-08
Okay it worked!!!   So one last question, the space I can actually use is not in the Swap space right?

---

### Post by llanitedave on 2012-06-09
> **wilee-nilee said:**
> You need to research what you are doing, the slider is going from left to right just like the install looks in a gui looking at the HD, it is quite obvious.

It's not obvious -- and an installation wizard should not have to have each step researched independantly.  That removes the entire purpose of having a wizrd, which is supposed to make the process automatic and convenient.

Anyway, turns out it was worse that "not obvious", because I resized the partition from left to right, making the left-hand partition largest and the right hand partition smallest.  And that had the opposite effect of what I wanted.  I ended up expanding the Windows side at the expense of the Linux side.  Now I need to come up with a way of reversing it.

---

### Post by wilee-nilee on 2012-06-09
> **llanitedave said:**
> It's not obvious -- and an installation wizard should not have to have each step researched independantly.  That removes the entire purpose of having a wizrd, which is supposed to make the process automatic and convenient.

Anyway, turns out it was worse that "not obvious", because I resized the partition from left to right, making the left-hand partition largest and the right hand partition smallest.  And that had the opposite effect of what I wanted.  I ended up expanding the Windows side at the expense of the Linux side.  Now I need to come up with a way of reversing it.

Had you asked for help you would not be here now.

---

### Post by llanitedave on 2012-06-09
> **darkod said:**
> It's sort of like highjacking the thread, but can you post a screenshot of the screen confusing you?

Usually it does say on which partition you have windows, as long as it can recognize it. Also, ntfs and linux partitions are marked with different colors so you can tell them apart.

On top of that, you can judge by the size of the partition(s). You don't know how big your windows partition is?

I don't use the automatic methods because the manual gives you best control, so I don't know what it looks like exactly right now, but earlier everything was marked pretty well.

I can't seem to any more, because it's on the Ubuntu installation wizard.

I was booting off a usb stick, but now, even though I have "usb" selected in my bios boot record, it goes straight to grub when I boot up, bypassing the installation usb stick.

Anyway, when I got to that point in the install process where it detected the Windows OS, it displayed a box with two equally-sized panels.  Neither one was specifically labeled.  I enlarged the box on the left side, and it expanded to 585 GB on the left side, which I thought was the Ubuntu partition.  Turns out the left side was the Windows partition.

I can use gparted to shrink the size of the windows partition, but I'm not yet sure how to expand the sda4 partition into the unallocated space.

---

### Post by llanitedave on 2012-06-09
> **wilee-nilee said:**
> Had you asked for help you would not be here now.

Probably not.  I would have been told "it's obvious" and blown off.

---

### Post by wilee-nilee on 2012-06-09
> **llanitedave said:**
> Probably not.  I would have been told "it's obvious" and blown off.

So here is my advice dispense with the attitude and blame. Boot a live ubuntu cd, take a screen shot of gparted, open a thread post it, and what you want to do, and what your final goals are and you will get help.

---

### Post by llanitedave on 2012-06-09
Ultimately, my problem (in addition to the ambiguity in the installation wizard) was that having the usb stick inserted while Windows was booted somehow hosed the bootloader on the usb device itself, and no matter what I did I couldn't boot from the usb device.  I ended up having to re-format the stick from windows, put the installation program and the bootloader back on it from my old Ubuntu machine, and reinstall. 

In the meantime, I was able to use gparted to adjust the partition sizes the way I wanted them.  

Interestingly enough, the installation wizard once again displayed the two panels of nearly equal size, without labeling which was which.  I went to the advanced option and the partitions displayed correctly there.  I installed the boot and root in their proper locations, and it has since installed smoothly.

It cost me a few extra hours, but ok.

I still think it's a bug that the partition options are not labeled in the main installation wizard.

That, and Windows seems designed to sabotage any linux bootloader it sees.

---

### Post by darkod on 2012-06-09
> **Scozzar said:**
> Okay it worked!!!   So one last question, the space I can actually use is not in the Swap space right?

I'm confused. If you did step 3 from my post and deleted all ubuntu partitions, the swap partition is deleted too. You are left with only unallocated space so you can expand the win7 partition. So, no swap partition (swap space) exists.

Did you already expand win7?

If you did, and it's working fine, the only thing to do is install ubuntu using the unallocated space you left. That's it.

---

### Post by Scozzar on 2012-06-09
No no, I was talking about when using Linux, the swap space is just there for what reason?  Like it's purpose.  I did delete all the partitions before reinstalling :P

---

### Post by black veils on 2012-06-09
when there isnt enough ram, it uses virtual memory from the harddrive, which is swap, in windows this is referred to as page filing. you need it for hibernating, maybe also for suspend.

---

### Post by Scozzar on 2012-06-09
Oh okay, thanks

---

