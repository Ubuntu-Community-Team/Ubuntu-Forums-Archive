---
title: "Uninstalling and Partition Help Ubuntu 9.10"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by emagine on 2009-12-07
Hello everyone,

I recently installed Linux on an old machine, and I love it!  I now would like to install it on my machine, but I had a few questions first.  I only have 40 GB of free space left on my hard drive.  I know this is plenty to install Linux, but I may run into the problem of having to free up more space some time in the future.  I have done some research and am a bit confused on how I would (in the sad case) go about uninstalling Linux and erasing the partition.  Is it possible to delete partitions?  And, when you partition upon installation, must you choose a set amount to partition aside for Linux and that is it?  What I mean is, if you partition 20 GB aside, and end up needing more space to free up for Linux later, is that possible?  Or is it set in stone?  Thank you very much!

---

### Post by raymondh on 2009-12-07
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Yes .... you can modify, alter, shrink, enlarge, delete, reformat, etc. your partitions.  I suggest the above link for reading to get yourself familiar and comfortable.

As for getting space, it depends on "where you're getting it from".  If Ubuntu is a logical partition inside an extended partition, and you need to get space from a primary partition beside it, you'll need to shrink the said primary (neighbor) and then enlarge the extended before enlarging the ubuntu root.

Talking about partitions, we all have to abide by the 4-rule per HD.  Either 4 primary partitions or 3 primary + 1 extended (with as many logical partitions inside it). That said, look into your HD and check what you have.  You can use gparted from Ubuntu (system > admin > partition editor).

Once you decide to move/alter partitions, use a liveCD and in live session.  Better yet, download and burn a live gparted CD.  Look into the GENERAL DOCUMENTATION in the above link.

Lastly (re-reading your thread), if you need to resize to enlarge, there usually is no need to delete Ubuntu as it can be resized/moved.  Nevertheless, it is always prudent to have a working/tested back-up of your files just in case.

Regards,

---

### Post by emagine on 2009-12-07
Thank you for your help.  I do still have a few questions though. When you say "logical partition inside an extended partition, and you need to get space from a primary partition beside it, you'll need to shrink the said primary (neighbor) and then enlarge the extended before enlarging the ubuntu root."
What exactly is a logical partition, an extended partition, a primary partition, and a ubuntu root.  And how do they relate to eachother.

when you say "Talking about partitions, we all have to abide by the 4-rule per HD. Either 4 primary partitions or 3 primary + 1 extended (with as many logical partitions inside it). That said, look into your HD and check what you have. You can use gparted from Ubuntu (system > admin > partition editor)."

What does all that even mean, could you be a little more clear?

When you say "Once you decide to move/alter partitions, use a liveCD and in live session. Better yet, download and burn a live gparted CD."
What do you mean by use a liveCD and in live session.  What exactly does the gparted CD do?

At the end of your reply you say Ubuntu can be moved.  What do you mean by moved?

Thank you for your help!

---

### Post by darkod on 2009-12-07
> **emagine said:**
> Thank you for your help.  I do still have a few questions though. When you say "logical partition inside an extended partition, and you need to get space from a primary partition beside it, you'll need to shrink the said primary (neighbor) and then enlarge the extended before enlarging the ubuntu root."
What exactly is a logical partition, an extended partition, a primary partition, and a ubuntu root.  And how do they relate to eachother.

when you say "Talking about partitions, we all have to abide by the 4-rule per HD. Either 4 primary partitions or 3 primary + 1 extended (with as many logical partitions inside it). That said, look into your HD and check what you have. You can use gparted from Ubuntu (system > admin > partition editor)."

What does all that even mean, could you be a little more clear?

When you say "Once you decide to move/alter partitions, use a liveCD and in live session. Better yet, download and burn a live gparted CD."
What do you mean by use a liveCD and in live session.  What exactly does the gparted CD do?

At the end of your reply you say Ubuntu can be moved.  What do you mean by moved?

Thank you for your help!

The short simple answer is, YES, you can adjust partitions later as much as you want (mainly). But that is not preferred. Any partition resize can possibly lead to data corruption, so if you manage to make a plan of your partitions that works for you, do it like that. 40GB is plenty, even 30GB is good enough for a start because if you are new to Ubuntu I don't think you will fill it up with software/files that fast. Plus, don't forget that Ubuntu can read ntfs partitions so any data ntfs partition that you have for windows, Ubuntu can use it too.

If you want more detailed advice and if you have specific question, open Dsik Management in windows (windows button + R, type diskmgmt.msc, hit Enter), maximize it full screen, make a screenshot of that and attach it here in one of the replies. When we see what you have exactly, we can give better advice.

---

### Post by emagine on 2009-12-07
> **darkod said:**
> The short simple answer is, YES, you can adjust partitions later as much as you want (mainly). But that is not preferred. Any partition resize can possibly lead to data corruption, so if you manage to make a plan of your partitions that works for you, do it like that. 40GB is plenty, even 30GB is good enough for a start because if you are new to Ubuntu I don't think you will fill it up with software/files that fast. Plus, don't forget that Ubuntu can read ntfs partitions so any data ntfs partition that you have for windows, Ubuntu can use it too.

If you want more detailed advice and if you have specific question, open Dsik Management in windows (windows button + R, type diskmgmt.msc, hit Enter), maximize it full screen, make a screenshot of that and attach it here in one of the replies. When we see what you have exactly, we can give better advice.

Thanks Darkod.  I added the attachment of my Disk Management.  Also, what do you mean by ubuntu can read ntfs partitions?

---

### Post by raymondh on 2009-12-07
A reference read ...

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

To simplify, a partition is a set space within your HD.  Let's call it a "fenced-in" area which contains files (either it be data, an operating system, etc).  Partitions are classified as primary or extended.  You and I were limited to 4 primary partition within a HD until someone came up with the concept of an EXTENDED partition.  But, we can only have 1 extended partition in an HD.  Hence the rule ... 4 primaries or, 3 primary + 1 extended.  We can further "subdivide" an extended partition into various partitions and we call them LOGICAL partitions. They reside ONLY inside an EXTENDED partition.

Linus does not care whether it be a logical partition or primary.  Windows REQUIRES that it reside in a primary partition. 

As for moving partitions around to create more space ..... and as an example where Ubuntu is in a logical partition (hence residing inside an extended) .... you have to enlarge the outer border (EXTENDED) first and then enlarge the logical.

From your attachment .... as you can see you have 2 primary partitions already.  

As for ubuntu root .... I was referring to how Ubuntu organizes itself.  ROOT , or also known as / , is the Ubuntu system files (in windows speak, the C: drive).  Here is a quick article about the linux filesystem

[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

---

### Post by raymondh on 2009-12-07
> **emagine said:**
> 

At the end of your reply you say Ubuntu can be moved.  What do you mean by moved?



[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by emagine on 2009-12-08
What can an extended partition do that a primary cant?   What are each type used for.  Also, you say I have two primary partitions.  Isn't the hp recovery drive on my computer a whole separate drive, apart from my C drive.  It is not partitioned is it?  because I thought the whole point of a recovery drive was if the main drive (C) fails.

---

### Post by darkod on 2009-12-08
You have only one disk, as you can see in Disk Management. And two primary partitions. The recovery is just a partition. Quick lesson about primary/extended/logical partitions: on one drive you can have only 4 partitions. If you create 4 primary you can't create any more. That's why extended partition was created. You can have 3 primary for example, and 1 extended but in the extended you can create up to 16 logical I think. So in total you can have 3 + 16 = 19 which is much more than just 4 primary.

On your windows system partition you have 42GB free space but have in mind that you can't shrink the partition that much to free all the space. You can try setting up Ubuntu on 20GB for start.
Or better alternative would be to move some of the data on C: (music, videos, etc) on texternal drive or DVDs, and free up more space. You need to decide how to do it, your choice. It's better to have at least 30-35GB for Ubuntu but with the current 42GB free it's very tight at the moment.

Not to throw too much information at you at once, decide how you want to create more free space on C: and we will continue with part 2, shrinking C: to make unallocated space for Ubuntu.

---

### Post by Bartender on 2009-12-08
emagine -
I really think you need to read up on this stuff a little more.  By the nature of your questions, it's clear to me that you need to get a clearer picture in your head of how all this partitioning stuff works.

It's not hard as such, but it is confusing at first.

I'll attach a screenshot of a typical dual-boot in our household.
This is on an Acer laptop.
Look at /dev/sda1.  That's Vista.  GParted identifies it as ntfs, 111.7 GiB, etc.  The jade green border around the ntfs partition is the color used by GParted to signify NTFS formatting.  Well, it is right now, anyway, some day they'll probably change the color then I'll have to start all over.  Just kidding.

Windows will not boot unless it's installed to a primary.  When I made the partition I asked GParted to make it a primary partition.

Now look at /dev/sda2.  That's an extended partition.  See the color?  A sort of light cerulean blue?  Notice that cerulean blue box takes up the rest of the hard drive.  I think of the extended partition as a "box" because that's its purpose.  You put logical partitions inside the extended "box".  An extended partition isn't formatted as NTFS or ext3 or anything else.  It's just there, ready to hold your logical NTFS or ext or swap partitions.

Now, notice inside the "box" are three more partitions.  Since they're inside the extended, these are all by definition logical partitions.  /dev/sda5 is Ubuntu 8.10, the operating system.  When people partition their drives so that they have a separate /home partition, as I did here, you'll see the operating system referred to as /.  Just /.  I found that confusing at first, i wanted something longer and more explanatory, but that's the way it is in the Linux world.

/dev/sda6 is swap.  That's pretty basic - the general rule of thumb with any modern PC (more than 2GB of RAM) is to make swap just a little bit bigger than your physical RAM if you want to use suspend.  When I set this laptop up I didn't know that and I made swap a little bit too small.  One of these days I'll shove either sda5 or sda7 aside a little bit and make swap bigger, but I am hesitant to mess with partitions that have data.

/dev/sda7 is /home.  I like to have a separate /home partition.  The reasons for that have been discussed here on the forum about a million times.

Have you made your recovery discs yet?  If so, you can get rid of the HP recovery partition, making your partitioning a little simpler.  I've set up two new HP rigs in the last year.  In the instruction manuals, both of them specifically said that you could get rid of the recovery partition once you'd made recovery DVD's because the recovery partition makes itself inaccessible after the discs have been burned.

Also, if you have some money and this is a desktop PC you own, have you thought about installing a second HDD?  I think that would be a better solution for you considering you're running out of space.

---

### Post by raymondh on 2009-12-08
+1 on bartenders' suggestion to do some reference reading.  See the links provided in previous posts'

I (also) am attaching 3 screenshots of my dual-boot system.  You will see primary and extended partitions.  Since I have 3 HD's in my desktop, you will note that Ubuntu is in 1st HD, win7 is in 2nd HD and, the 3rd HD is for data/storage/back-up.

Regards,

---

### Post by emagine on 2009-12-08
Thanks for all your help guys.  And Bartender, you are right, I need to do a little hw.  Once I get familiar with partitioning in general I will be able to ask more specific questions, probably early this weekend.  Thanks again!

---

### Post by Bartender on 2009-12-08
emagine, another route is good old trial-and-error.  Trial-and-error is very effective at getting you up to speed.  But it MUST be done with an old spare HDD that you can goof up on, wipe, start over, etc.  Too many people use the trial-and-error approach on their daily use PC's and then come back here on the forums and yell about how Ubuntu ruined their Windows...

You can read and ask questions til the cows come home, but there's no substitute for a GParted LiveCD, a couple of Linux install CD's, and an old HDD or two.

After I fumbled around for several hours with an old test PC, formatting, installing, screwing up, wiping the drive, try again, etc. I came back to the forums.  Suddenly the posts made a lot more sense! ;)

EDIT: Hey, raymondh, thanks for posting a few screenshots!  I think it's very helpful for a beginner to see several people's setups.  People get to see how things are different, but more importantly, they should spot similarities.

---

### Post by emagine on 2009-12-08
I actually do have an old machine.  I just recently did a clean install of Ubuntu on it and now it works beautifully.

---

### Post by Bartender on 2009-12-09
> **emagine said:**
> I actually do have an old machine.  I just recently did a clean install of Ubuntu on it and now it works beautifully.

That's perfect!  You can gain a lot of confidence and experience quickly using an old PC that doesn't have any important data on it.  You should try dual-booting two Linux OS'es on the old rig, then wipe it clean, make some partitions with a GParted LiveCD, etc.

---

### Post by raymondh on 2009-12-09
> **emagine said:**
> I actually do have an old machine.  I just recently did a clean install of Ubuntu on it and now it works beautifully.

well done.  Download and burn a gparted liveCD and play around.  Also note the differences if you check & uncheck the "round to cylinder" box; if you move partitions; etc.

@ bartender .... you're welcome.  I agree.  By showing various set-ups', an operator could spot similarities amongst the differences :)  (whew, did I make sense there?)

Happy Ubuntu-ing

---

### Post by emagine on 2009-12-09
Ok, guys.  I will do that this weekned.  Any idea on what other Linux OS I should install.  Also, any links you could send me on hot to do that?

---

### Post by raymondh on 2009-12-09
> **emagine said:**
> Ok, guys.  I will do that this weekned.  Any idea on what other Linux OS I should install.  Also, any links you could send me on hot to do that?

For the Ubuntu-flavor:

masonux (which uses lxde ... quite fast)
crunchbang (uses openbox ... also speedy)

For Ubuntu :

Download and try the alpha release of Lucid (10.4) LTS.

For others :

[http://distrowatch.com/](http://distrowatch.com/)

Have fun.

---

### Post by emagine on 2009-12-09
The more I learn, it seems, the more I discover how much I don't know.  I guess that's why I'm here right?  I am not understanding something I thought that Ubuntu was a flavor of Linux and that's it.  Now your telling me you can have flavors of Ubuntu?  Also, what is lxde and openbox?  thanks!

---

### Post by raymondh on 2009-12-09
> **emagine said:**
> The more I learn, it seems, the more I discover how much I don't know.  I guess that's why I'm here right?  I am not understanding something I thought that Ubuntu was a flavor of Linux and that's it.  Now your telling me you can have flavors of Ubuntu?  Also, what is lxde and openbox?  thanks!


LXDE and Openbox are window managers/desktop environments ... much like GNOME which you are using now.

[http://lxde.org/](http://lxde.org/)
[http://icculus.org/openbox/index.php/Main_Page](http://icculus.org/openbox/index.php/Main_Page)

Some distros are 'derivatives' of Ubuntu.  Crunchbang and Masonux are a few of them.  For a better understanding on how this can happen,  google about GNU/Linux license and FOSS.  Basically, we can use an existing distro and re-compile it to suit our needs and, share it with others as well.

[http://sites.google.com/site/masonux/home](http://sites.google.com/site/masonux/home)
[http://crunchbanglinux.org/](http://crunchbanglinux.org/)

This is a quote from a fellow ubuntu-member .... :"the more I know and discover, the more I realize I need to learn more"...... just like what you said.

happy Ubuntu-ing.

---

### Post by emagine on 2009-12-09
I have a lot of work to do this weekend.  Just add that stuff to the list.  This stuff is so interesting!

---

### Post by Bartender on 2009-12-10
As raymondh mentioned, there are "variants" or "derivatives" within the Linux/GNU constellation.  And there are "distros".

For instance, Ubuntu is based on Debian.  I honestly don't know if Ubuntu is considered a "derivative" of Debian or if there are enough differences for it to be considered a "distro".  And I don't want to start a heated discussion on the subject either! :popcorn:

Mint is based on Ubuntu.  I believe Mint is considered a variant.

I think Xubuntu and Lubuntu (when it arrives) are variants of Ubuntu.  Basically Ubuntu running under a lighter-weight GUI.  In some people's eyes Xubuntu doesn't really live up to its reputation as a lighter-weight version, so I'm very curious to see how Lubuntu turns out.

If you've got the broadband, OpenSUSE is an interesting distro.  I don't know if maybe it's lost respect because of Novell's deal with the devil, but I downloaded the 4 GB install disc and have been having a look.

---

### Post by raymondh on 2009-12-10
> **bartender said:**
>   i don't know if maybe it's lost respect because of novell's deal with the devil, 


lol

---

### Post by emagine on 2009-12-10
Wait, what is the deal with this "devil" stuff.

---

### Post by Bartender on 2009-12-10
You don't know about Novell's little partnership with Microsoft?  Here's one guy's opinion, there are many more...

[http://www.linuxjournal.com/node/1000121](http://www.linuxjournal.com/node/1000121)

---

### Post by emagine on 2009-12-13
Sorry guys, I couldn't get to it this weekend.  I will have plenty of time next week because I have a 2 week break starting on the 19th of December.  I am sure i will have questions once I start fooling around with this stuff.  Talk to you then!

---

### Post by emagine on 2010-02-05
Hey guys, I know it has been awhile.  But I am finally installing Linux.  I freed up more space on my hard drive and am downloading the Linux image now.  Right now, I have 50 GB of free space.  When I install Linux, how big do you recommend I make the partition?  I plan to use Linux only for browsing and for education, with minimal file storage.  How much room should I leave?

---

### Post by raymondh on 2010-02-06
> **emagine said:**
> Hey guys, I know it has been awhile.  But I am finally installing Linux.  I freed up more space on my hard drive and am downloading the Linux image now.  Right now, I have 50 GB of free space.  When I install Linux, how big do you recommend I make the partition?  I plan to use Linux only for browsing and for education, with minimal file storage.  How much room should I leave?

30GB for linux should be fine ... just remember that when you start dealing with, or saving those, media files ;)

Raymond

---

### Post by oldfred on 2010-02-06
Remember you need to leave 10-20% free space for windows or else it will run slow or lockup as it then does not have space to move things around.
If you are just starting out root(/) and swap are all you need. Some suggest a separate /home for ease of new installs (it will preserve most of your settings), but if home is small it is easy to backup before a new install. Swap  should be 2GB or your RAM memory size if you want to hibernate. If you have lots of RAM, swap is not used much anymore unless you run lots of large applications at once.

---

### Post by emagine on 2010-02-07
> **raymondh said:**
> 30GB for linux should be fine ... just remember that when you start dealing with, or saving those, media files ;)

Raymond

Raymondh, what do you mean by this.  It sounds like an incomplete thought.  Do you mean that I need to allow for enough space in case I do deal with media files on Linux?  I don't understand.

Also, Oldfred, I am a complete noob.  I have read a lot of information but I am having trouble piecing it together.  I have some questions:
1.) What do you mean leave 10-20% free space for Windows? 10 to 20 percent of what, my hard drive?
2.) What do you mean by root(/), swap, and /home for new installs?  What is a "swap" used for and how does it relate to hibernation?
3.) All these terms are getting thrown at me, I am a noob, when in the installation process to I make all these home and swap things.  I have done a clean install of Linux on and old machine, everything went great.  But now I want to install it on my primary but still keep Windows. Do I have to do all this before I put the Linux CD for installation?  Or is this something that happens during the installation?  I remember having configuring screen come up during the installation of Windows and I could choose how much space I wanted for Linux.

I am sorry guys, I just want Linux on my system, and I dont want to screw anything up(even though my files are backed up)

Thank you so much guys!  Please help.

---

### Post by oldfred on 2010-02-07
If your windows is 30GB you need 3 to 6GB as a minimum to keep windows working so that is not free space available for other use.

root (/) is where ubuntu or other linux is installed. swap is overflow space if all your memory is used. Hibernate is when a (usually laptop) is shutdown in a mode that just copies memory to the hard drive and does not reboot but just reload memory. /home is normally inside root and is a location where all your informations is stored. It has hidden configuration files and setting and all your data including folders like documents, music, videos etc. If you start storing lots of large data files it can grow rapidly. You should have seen these folders on you other install.

there are a lot of dual boot sites. You should reveiw several. The only real differences between all dual boots are if Vista or Win7 use the windows tools to shrink the windows partition and reboot windows several times before installing. If XP use gparted or the ubuntu installer. If installing Karmic it now has grub2, all other versions have grub (0.97) so if following instructions on grub make sure you follow the correct version.

Dual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)
APC various dual boot graphical install
[http://apcmag.com/howto_search.htm?q=Keyword&catid=198](http://apcmag.com/howto_search.htm?q=Keyword&catid=198)
Installing Ubuntu 9.10 Step-by-step installation tutorial with screenshots
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)
Jaunty Jackalope / Windows7 Ultimate MultiBoot 'C' (with checkbox graphic for vista/7) 
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

### Post by emagine on 2010-02-07
> **oldfred said:**
> If your windows is 30GB you need 3 to 6GB as a minimum to keep windows working so that is not free space available for other use.

root (/) is where ubuntu or other linux is installed. swap is overflow space if all your memory is used. Hibernate is when a (usually laptop) is shutdown in a mode that just copies memory to the hard drive and does not reboot but just reload memory. /home is normally inside root and is a location where all your informations is stored. It has hidden configuration files and setting and all your data including folders like documents, music, videos etc. If you start storing lots of large data files it can grow rapidly. You should have seen these folders on you other install.

there are a lot of dual boot sites. You should reveiw several. The only real differences between all dual boots are if Vista or Win7 use the windows tools to shrink the windows partition and reboot windows several times before installing. If XP use gparted or the ubuntu installer. If installing Karmic it now has grub2, all other versions have grub (0.97) so if following instructions on grub make sure you follow the correct version.

Dual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)
APC various dual boot graphical install
[http://apcmag.com/howto_search.htm?q=Keyword&catid=198](http://apcmag.com/howto_search.htm?q=Keyword&catid=198)
Installing Ubuntu 9.10 Step-by-step installation tutorial with screenshots
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)
Jaunty Jackalope / Windows7 Ultimate MultiBoot 'C' (with checkbox graphic for vista/7) 
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

Ok, now it seems I am starting to understand.  I am just really cautious because I am dealing with two Operating systems on one hard drive.  Thank you for the links.  Honestly, I need to be told the exact steps for the partitioning part of the installation.  Here is what I want:
I want both Windows and Linux installed on my computer, so I can choose which one to run at startup.  I have a 140 GB hard drive with 50 GB of free space, so only 90GB used.  I only have one partition, and that is for running windows.  I want to partition enough space for Linux so that there is EXTRA room for installing some Linux software, but I will not be using Linux to store media files.  I also don't want Windows to be crammed for space, so I think 30GB for Linux will be perfect.  I want a swap drive so I can use hibernation/suspend/sleep.  I also think it is a good idea to use the /home to keep my settings safe upon installing a newer version.
So, if someone could post explicit instructions on how to do the type of install I want, that would be more than awesome.  You can use this link as a guide because it will refresh your memory on each step of the installation.  I did read it, but I am still confused:
  [http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

I only need help with the "Hard Disk Partitioning" part, because the rest is self explanatory.  Thank you Linux community!  Please help!!

---

### Post by oldfred on 2010-02-07
If you are running Vista you should shrink the Vista partition using the Vista tools- disk management and reboot Vista several times to make sure it has resolved any issues with the resize and possibly filechecks. Then you can use the install in the largest free space choice.

Resize Vista partition
If problems, try disabling system restore, pagefile, (in advanced settings in computer properties) and hibernate option (in power management). Don&#8217;t forget to turn them on back later.
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

If dual booting do not hibernate one system and boot into the other as that can lead to file corruption. It is ok if you are just hibernating and returning to the hibernated system.

---

### Post by oldfred on 2010-02-07
If you want a separate /home you have to use the more advanced manual partitioning. You should understand partitions.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

these show gparted running separately but it is the partitioner running in the ubuntu install.
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition](http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition)
With add'l info on manually partitioning
[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)
[http://guvnr.com/pc/karmic-install-tutorial/](http://guvnr.com/pc/karmic-install-tutorial/)

---

### Post by raymondh on 2010-02-07
> **emagine said:**
> 

I only need help with the "Hard Disk Partitioning" part, because the rest is self explanatory.  Thank you Linux community!  Please help!!

Aside from the great links provided by OldFred, here are a couple to help you understand.

This is from Bodhi Zazen .... dated but very informative.

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

This next link was assistance provided by forum-member Didius Falco in creating partitions beforehand and manually installing unto them.  Relevant posts' begin in post # 6.  OP in this link may be installing an older version but the logic is still the same

[http://ubuntuforums.org/showthread.php?t=1175277](http://ubuntuforums.org/showthread.php?t=1175277)

regards,

Raymond

---

### Post by emagine on 2010-02-07
Thanks for all the info oldfred and raymond.  Ok, so I am in the vista tools management and I noticed that I have 8.20 GB unallocated [Screen Shot Attached]. I think it has something to do with me deleting my hp recovery drive partition that came with my computer which was about 8 GB.  I know that unallocated space means it hasn't been assigned to a partition, can I assign it to my primary partition?  How do I do that?

---

### Post by oldfred on 2010-02-07
When you shrink your Vista it will add to the unallocated, since they will be adjacent. You then should be able to use all the unallocated for your install.  Make sure you have housecleaned out your Vista and run defrag once or even twice before shrinking the Vista partition.

---

### Post by emagine on 2010-02-07
Ok, so is my hard drive actually around 150 GB because the unallocated space has not been counted- or is it still just 140 GB?  And how do I shrink my vista partition?  Do you recommend a third party program?

---

### Post by oldfred on 2010-02-07
You probably have a standard 160GB which is not 160Gib and then the file system take up about 5%. So about 150 is correct.
[http://en.wikipedia.org/wiki/Gibibyte](http://en.wikipedia.org/wiki/Gibibyte)

My post #33 had info on using the Vista tools to resize. They say it has issues but I believe many have used it. You can use gparted but the round to cylinders unchecked. You still need to do that separately and reboot Vista before the install. If you have a version of gparted that does not have the checkbox do not use it. Also gparted had several versions with issues on NTFS. See their notes first on what versions to use, if you go to download gparted liveCD.

starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)

---

### Post by emagine on 2010-02-07
> **oldfred said:**
> You probably have a standard 160GB which is not 160Gib and then the file system take up about 5%. So about 150 is correct.
[http://en.wikipedia.org/wiki/Gibibyte](http://en.wikipedia.org/wiki/Gibibyte)

My post #33 had info on using the Vista tools to resize. They say it has issues but I believe many have used it. You can use gparted but the round to cylinders unchecked. You still need to do that separately and reboot Vista before the install. If you have a version of gparted that does not have the checkbox do not use it. Also gparted had several versions with issues on NTFS. See their notes first on what versions to use, if you go to download gparted liveCD.

starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)

I am not understanding.  What do you mean "round to cylinders" and "checkbox".  And I can't use gparted on Windows unless I use a live CD.  But here it tells me I will need my Windows vista installation disc which I dont have:
[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

So you aren't making to much sense.  I apologize, I JUST WANT LINUX!!!!! :)

---

### Post by oldfred on 2010-02-07
If you have windows they tell you to make a recovery cd as the first thing. I thought you could resize from within Vista? But it would be better from a recovery disk.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP(they create the boot sectors differently) but can run check disk.

this shows checkbox
Jaunty Jackalope / Windows7 Ultimate MultiBoot 'C' (with checkbox graphic for vista/7) 
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

about 1/3 way down is graphic with checkbox.

---

### Post by emagine on 2010-02-08
> **oldfred said:**
> If you have windows they tell you to make a recovery cd as the first thing. I thought you could resize from within Vista? But it would be better from a recovery disk.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP(they create the boot sectors differently) but can run check disk.

this shows checkbox
Jaunty Jackalope / Windows7 Ultimate MultiBoot 'C' (with checkbox graphic for vista/7) 
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

about 1/3 way down is graphic with checkbox.

Thank you, I just downloaded the windows vista recovery iso image from the link you gave me.  I am burning it now.  The reason I will not use Gparted is because I have heard it does not play too nicely with Windows, and could rend my partition unbootable.

---

### Post by emagine on 2010-02-11
i know this has been a long battle. Thanks for all your help!!  NOW ENTERING DUAL BOOT CITY!!!!  Installation went very well.  Anyone interested in doing this I recommend going to this site:
  [http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

It will give you steps to shrink vista partition and give you a better understanding.  I really didn't follow these step, because if you look at the comments, everyone said they just used perfect disk, which is what I did.  All you have to do is defrag system files, which can only be done right when the computer starts, before windows loads.  Perfect disk will allow you to do this, one of the only defraggers that can. Be sure to restart computer multiple times after defrag and volume shrink so the computer recognizes the changes.  THANK YOU SO MUCH GUYS!!!

---

