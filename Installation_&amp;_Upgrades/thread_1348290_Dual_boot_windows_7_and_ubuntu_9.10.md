---
title: "Dual boot windows 7 and ubuntu 9.10"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by Jackzor on 2009-12-07
Okay.. Here is my problem..

I have been at it for hours but I just can't find any help with this. I have 4 partitions. One that 7 put on there (100mb) my 30gb c drive and a 100gb d drive. THEN I have this 100gb unpartitioned space that I plan to use for Ubuntu. 

[http://i72.photobucket.com/albums/i183/kissfanbjm/Wtf.jpg](http://i72.photobucket.com/albums/i183/kissfanbjm/Wtf.jpg)

Only when I boot the live disc to install Ubuntu It shows my hard drive as blank. I don't really know what else to add. I can't figure this out at all. I have tried 9.04 and 9.10

---

### Post by Jackzor on 2009-12-07
Help? Please?

---

### Post by Jackzor on 2009-12-07
Well I did that before. But I'll try again and let you know.

Please. Anyone else? Lol.

---

### Post by kristine12 on 2009-12-07
Booting the live cd is not the only way of installing Ubuntu. Actually you can install Ubuntu even when Windows is running. 

It seems that Windows is first installed before Ubuntu.
So, all you have to do is plug in the cd while Windows is running then the AutoPlay will run then follow the instruction. Then that's it!

^_^

Hope this thing help!

---

### Post by Jackzor on 2009-12-07
Um.. This should help explain some things.

[http://i72.photobucket.com/albums/i183/kissfanbjm/Screenshot-1.png](http://i72.photobucket.com/albums/i183/kissfanbjm/Screenshot-1.png)

---

### Post by Jackzor on 2009-12-07
> **kristine12 said:**
> Booting the live cd is not the only way of installing Ubuntu. Actually you can install Ubuntu even when Windows is running. 

It seems that Windows is first installed before Ubuntu.
So, all you have to do is plug in the cd while Windows is running then the AutoPlay will run then follow the instruction. Then that's it!

^_^

Hope this thing help!

I want to install it on my partition that I made for it you see...

I want the full  experience from Ubuntu

---

### Post by Jackzor on 2009-12-07
bumpt'd

---

### Post by Jackzor on 2009-12-07
No one has had this problem?

---

### Post by wilee-nilee on 2009-12-07
It is 2:19 am where I am at, you will probably get help with this but it seems a large part of the people are not available.

Bumping your thread will not get help faster and is not liked by the mods or others any faster then every 24 hrs. I can understand you want it done, and you want it done now, but this is a free support forum. :)

---

### Post by darkod on 2009-12-07
Did you try removing dmraid?

If you are not running raid boot with the liveCD and in terminal do:
sudo apt-get remove dmraid

Then boot with the cd again select Install Ubuntu and see if it can see the drive now.

And just for the record, it seems you have created the 101GB extended partition from windows. Do not do that for ubuntu, just leave the space as unallocated. Now you have created a further step you need to do, removing that partition. Provided after the above command the installer can see your drive, you will need to go into manual partitioning and delete that 101GB partition to make unallocated free space.
Alternatively, boot as LiveCD and if Gparted can see the drive use it to delete that partition.

---

### Post by spandon on 2009-12-07
Hi Jackzor
I think I may be able to help, but it's not a quick answer, so if You can wait a little (poss 1/2 hr) I will give more info then.
Don

---

### Post by Jackzor on 2009-12-07
> **darkod said:**
> Did you try removing dmraid?

If you are not running raid boot with the liveCD and in terminal do:
sudo apt-get remove dmraid

Then boot with the cd again select Install Ubuntu and see if it can see the drive now.

And just for the record, it seems you have created the 101GB extended partition from windows. Do not do that for ubuntu, just leave the space as unallocated. Now you have created a further step you need to do, removing that partition. Provided after the above command the installer can see your drive, you will need to go into manual partitioning and delete that 101GB partition to make unallocated free space.
Alternatively, boot as LiveCD and if Gparted can see the drive use it to delete that partition.


Tried it. No change :(

---

### Post by wilee-nilee on 2009-12-07
Take a look at this thread it is addresing multiple HD's but the drop down in the top right corner seems to be a possibility here.
[http://ubuntuforums.org/showthread.php?t=1339631](http://ubuntuforums.org/showthread.php?t=1339631)

---

### Post by Jackzor on 2009-12-07
> **wilee-nilee said:**
> Take a look at this thread it is addresing multiple HD's but the drop down in the top right corner seems to be a possibility here.
[http://ubuntuforums.org/showthread.php?t=1339631](http://ubuntuforums.org/showthread.php?t=1339631)



Thanks but thats not doing it either. Its only one hard drive so there is only one to select. If you think of anything else I will be waiting for about 2 more hours.. Then I will nap for about an hour and be right back on these forums. I really want to get this done within the next 8 hours. :D

---

### Post by spandon on 2009-12-07
Hi Jackzor,
Back with you now.
The first things you must do, start up Windows and rename your Windows partition to Win 7 or anything that you can recognise  this partition, when dealing with your drives partitions later
Then make a copy of your Window 7 System and also a recovery disk &#8211; you can use Windows 7's own System to do this, use an external HD for this or DVDs.
Once you have done this, then restart your machine with the Ubuntu Live CD, once in Ubuntu, use its Disk Tools (Gparted) to re-adjust / create partitions similar to this after your Win 7 partition:
(a)  Data partitions formatted to NTFS for Office data, Music, Photo's etc (if you already have data in a partition, then this partition may need re-sizing).
When doing (a), leave room at the end for Ubuntu and a SWAP partition, the size depends on size of disk and what you want it to be, but for a guide I do all machines thus &#8211; 15gb for Ubuntu and 2 gb for the Swap partition, I always have plenty of space left and have never had any problems with this config.
(b) create 2 partitions at the end of the drive 1 for Ubuntu (format to ext 4) and 1 for Swap (format to Swap).
Once this has been completed, you are now ready to Install Ubuntu.

If you are happy with the above, let me know by replying to this then go and do it &#8211; in the meantime I must check on a couple of things, as I have done that many double/triple and quad Ubuntu installs that I am in Auto mode when doing it, now it comes to explaining I have got to think of the procedure, but it is quite simple, also you have knowledge of the recovery set-up to recover your Windows if you were to go wrong.
Don

---

### Post by wilee-nilee on 2009-12-07
I have W7 and Karmic running but I did this on a netbook that didn't have the usual MS c-d-e partition scheme. I had just 2 partitions, a recovery then the main, so it was a easy install. I think you will get help here, but do you have the Windows install disc in case it is needed, and do you have everything backed up off the computer that you would want to save.

---

### Post by Jackzor on 2009-12-07
> **spandon said:**
> Hi Jackzor,
Back with you now.
The first things you must do, start up Windows and rename your Windows partition to Win 7 or anything that you can recognise  this partition, when dealing with your drives partitions later
Then make a copy of your Window 7 System and also a recovery disk – you can use Windows 7's own System to do this, use an external HD for this or DVDs.
Once you have done this, then restart your machine with the Ubuntu Live CD, once in Ubuntu, use its Disk Tools (Gparted) to re-adjust / create partitions similar to this after your Win 7 partition:
(a)  Data partitions formatted to NTFS for Office data, Music, Photo's etc (if you already have data in a partition, then this partition may need re-sizing).
When doing (a), leave room at the end for Ubuntu and a SWAP partition, the size depends on size of disk and what you want it to be, but for a guide I do all machines thus – 15gb for Ubuntu and 2 gb for the Swap partition, I always have plenty of space left and have never had any problems with this config.
(b) create 2 partitions at the end of the drive 1 for Ubuntu (format to ext 4) and 1 for Swap (format to Swap).
Once this has been completed, you are now ready to Install Ubuntu.

If you are happy with the above, let me know by replying to this then go and do it – in the meantime I must check on a couple of things, as I have done that many double/triple and quad Ubuntu installs that I am in Auto mode when doing it, now it comes to explaining I have got to think of the procedure, but it is quite simple, also you have knowledge of the recovery set-up to recover your Windows if you were to go wrong.
Don

I have the repair disc if that is what you are speaking of. I made it before trying anything in the first place. But the thing is, my windows partition doesn't show up at all. It shows as one blank disc in Gparted and in the installer.


> **wilee-nilee said:**
> I have W7 and Karmic running but I did this on a netbook that didn't have the usual MS c-d-e partition scheme. I had just 2 partitions, a recovery then the main, so it was a easy install. I think you will get help here, but do you have the Windows install disc in case it is needed, and do you have everything backed up off the computer that you would want to save.

I have the repair disc.. And I can deal with losing my documents and all.


I just really wish that I could figure this out already. I COULD do a fresh install of everything the way you are supposed to dualboot. But I dunwanna. Lol.

---

### Post by wilee-nilee on 2009-12-07
> **spandon said:**
> Hi Jackzor,
Back with you now.
The first things you must do, start up Windows and rename your Windows partition to Win 7 or anything that you can recognise  this partition, when dealing with your drives partitions later
Then make a copy of your Window 7 System and also a recovery disk – you can use Windows 7's own System to do this, use an external HD for this or DVDs.
Once you have done this, then restart your machine with the Ubuntu Live CD, once in Ubuntu, use its Disk Tools (Gparted) to re-adjust / create partitions similar to this after your Win 7 partition:
(a)  Data partitions formatted to NTFS for Office data, Music, Photo's etc (if you already have data in a partition, then this partition may need re-sizing).
When doing (a), leave room at the end for Ubuntu and a SWAP partition, the size depends on size of disk and what you want it to be, but for a guide I do all machines thus – 15gb for Ubuntu and 2 gb for the Swap partition, I always have plenty of space left and have never had any problems with this config.
(b) create 2 partitions at the end of the drive 1 for Ubuntu (format to ext 4) and 1 for Swap (format to Swap).
Once this has been completed, you are now ready to Install Ubuntu.

If you are happy with the above, let me know by replying to this then go and do it – in the meantime I must check on a couple of things, as I have done that many double/triple and quad Ubuntu installs that I am in Auto mode when doing it, now it comes to explaining I have got to think of the procedure, but it is quite simple, also you have knowledge of the recovery set-up to recover your Windows if you were to go wrong.
Don

I would not hesitate to let gparted do the repartitioning, but I have all the install discs and everything backed up. I have seen advice to having the windows partition manager do the dirty work so having the backups are a good way of protecting the stuff needed to be saved. There seems to be a consensus even with Linux users at least some that using gparted can cause problems for re-partitioning but I think is it probably due to user error in not defragging and making sure windows in intact before install another OS. OP make sure you let the windows system do a auto disc check before and in between any partition adjustments just to be safe and make sure the windows system is still working.

---

### Post by spandon on 2009-12-07
Hi,Jackzor,
If you are still having probs with the disk, Go to [www.acronis.com](www.acronis.com) and download the test Disk director Suite 10, burn this to a cd and boot this up and see if this helps.
Don

---

### Post by spandon on 2009-12-07
Hi Jackzor,
The system backup I was refering to earlier, was a **COMPLETE Windows backup**, the recovery disk allows you to recover this System backup, back to your machines hard drive.
Hope this clarifies things
Don

---

### Post by wilee-nilee on 2009-12-07
If you want to make things simple, and have a hard drive that will be set up in the simplest manner I would get a W7 install disc from the manufacturer or MS for 30$. This would allow you to wipe the HD and install W7 with a custom install to the size you want and leave a open space for the Ubuntu install.

I suspect the Acronis back up is is going to save the multi partition set up which is not actually need, and actually is probably what is causing the problems. 

A fresh install will give you the primary partitions need for dual booting. I suggest this due to your not really needing to save anything in particular and if you do you can get a 16 gig thumb from Amazon for 32$ I was looking at one earlier today.

---

### Post by dream_coder on 2009-12-07
its not too difficult but will take you some time, Use gparted live cd ( [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) ) delete all partitions but NOT your recovery partition (the hidden one which allows you to use your recovery cd)

Create a partition for windows 7 using gparted not with windows (remembering to save some space for your new ubuntu install)

Now install windows 7 (**using an actual windows 7 install disc not recovery disc**) onto the partition you created using gparted.

Afterwards boot the installer for ubuntu and woo hooo it sees the drive and partitions :)

Or installing Ubuntu First [http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999) <-- works well more commands etc though

---

### Post by gs777 on 2009-12-07
I too have same dual booting configuration
!----windows 7 -64 bit
!-----ubuntu -9.10
the configuratin is harmonious.runs smooth.
A fewthings u should see
a)have u installed ubuntu directly , that means not under windows,if yes then the ubuntu drive (ext3 or ext 4 )cannot be seen from windows. you have to install some reader software which can read ex3,4 drives in windows . 
However, all the drives can be seen through ubuntu, go to places>computers and see which drive is listed. you can see all the drives here. 
b) If you have Installed ubuntu under wubi (within windows )  then you can access all the drives in windows also.
  Could understand ur problem or I answered a differnt problem




> **Jackzor said:**
> Okay.. Here is my problem..


I have been at it for hours but I just can't find any help with this. I have 4 partitions. One that 7 put on there (100mb) my 30gb c drive and a 100gb d drive. THEN I have this 100gb unpartitioned space that I plan to use for Ubuntu. 

[http://i72.photobucket.com/albums/i183/kissfanbjm/Wtf.jpg](http://i72.photobucket.com/albums/i183/kissfanbjm/Wtf.jpg)

Only when I boot the live disc to install Ubuntu It shows my hard drive as blank. I don't really know what else to add. I can't figure this out at all. I have tried 9.04 and 9.10

---

### Post by wilee-nilee on 2009-12-07
> **dream_coder said:**
> its not too difficult but will take you some time, Use gparted live cd ( [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) ) delete all partitions but NOT your recovery partition (the hidden one which allows you to use your recovery cd)

Create a partition for windows 7 using gparted not with windows (remembering to save some space for your new ubuntu install)

Now install windows 7 (**using an actual windows 7 install disc not recovery disc**) onto the partition you created using gparted.

Afterwards boot the installer for ubuntu and woo hooo it sees the drive and partitions :)

Or installing Ubuntu First [http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999) <-- works well more commands etc though

Gparted will create a NTFS partition that W7 will slip into. In part of the upgrade from XP to W7 I at one point created a a partition this way and W7 was installed with no problem.

W7 though does have that 100mib boot that might cause problems I am not sure with keeping the recovery, if you have a install disc and you can make a backup disc for the new install after wiping the HD then you have the same set up without worrying if the recovery is going to work. Looking at the OP's original screen shot I am not sure there is a recovery C is 29 gigs and   D is 109 gigs, 29 gigs for a backup makes no sense. Any computer should have a recovery now a days but we haven't asked the OP whether this was a upgrade to W7.

So is C and D accessible with windows running?

---

### Post by audiomick on 2009-12-07
Hallo jackzor.
A couple of weeks ago there was a lot of advice around to try the Alternate CD for the install. There were a number of cases where people had similar problems (installer can't see the disc) for whom this apparently helped. The Alternate CD uses a different partitioning tool (palimpset???) to the live cd, apparently.

---

### Post by Mze on 2009-12-07
Read [this]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony") from LifeHacker website about dual booting Win7 and Ubuntu 9.10

---

### Post by darkod on 2009-12-07
> **Jackzor said:**
> I have the repair disc if that is what you are speaking of. I made it before trying anything in the first place. But the thing is, my windows partition doesn't show up at all. It shows as one blank disc in Gparted and in the installer.


One reason for the partitions not showing up might be messed up partition table. Don't forget, all info about the partitions is there (hence the name). That's why quick format takes seconds, it just deletes the part table.

I have heard of a utility TestDisk which can cure part table problem, provided that's your problem at all. But I haven't used it myself and I don't know whether to recommend it because there is always possibility to lose your data playing with partitions and tools.
However, some people have reported here that it managed to sort out the part table and all the data was there accessible again.

---

### Post by spandon on 2009-12-07
Hi all,
I concur with Mze, the article gives a very informative method for anyone wishing to make a dual booting Windows / Ubuntu system.
Don

---

### Post by darkod on 2009-12-07
> **spandon said:**
> Hi all,
I concur with Mze, the article gives a very informative method for anyone wishing to make a dual booting Windows / Ubuntu system.
Don

I agree the article is informative but the OP has a problem with his drive not being recognized properly during the install. With a quick look at the article it never mentions that case and what to do. Or maybe I missed it.
It's a different thing if the OP decides to wipe the drive and start clean. Then he might use the article or any other advice. But so far the problem of the drive not being recognized seems unsolved.

---

### Post by Jackzor on 2009-12-07
I have decided that since no one else has seen this problem that it may just be a one time thing. Nothing that I have tried worked so I'm assuming that something in my system is messed up. So I am doing a fresh install of both OS's. I will come back to let you guys know if that fixes my problem.

Thanks for all the help though. And if there are more ideas go ahead and post them up just in case someone else needs the info, ya know. Lol

---

### Post by Jackzor on 2009-12-07
Alright. I did the fresh install of both systems and everything is running great now. 

Thanks for all the ideas.

I just got impatient.

---

