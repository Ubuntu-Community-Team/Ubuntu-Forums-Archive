---
title: "[SOLVED] Why shrink Vista partition to install?"
date: 2008-09-24
forum: Installation &amp; Upgrades
---

### Post by Morty007 on 2008-09-24
**Scenario**-I want to install ubuntu on my new XPS m1530. Vista is already on there.  

I have read in most places to defrag, shrink vista, then install and put ubuntu in the unallocated space. 

**My question-** Why not just skip the vista shrinking and let the installer handle things? 

I went through a test run sort to speak-without installing anything...and it let me get to the partitions and I just used the slider to make vista a certain size and have ubuntu have the rest-but I stopped there because most tutorials I have read say to shrink Vista first while in windows.

Am I missing something?

XPS- 320 gb
4 gb ram

---

### Post by lisati on 2008-09-24
If you have only one physical disk drive which already has an operating system on it that takes up the whole disk drive, you basically have two choices: shrink the partition with the existing OS, or delete it completely. Otherwise you're not going to be able to put the new OS on your system. Unless, of course, you use something like a virtual machine to install the second OS within the first.

---

### Post by Pumalite on 2008-09-24
Use Vista partitioner to allocate space for Ubuntu. Then install in that space.

---

### Post by Morty007 on 2008-09-26
Thanks for the reply Pumalite. 

Do I leave the other partitions alone? This is a new dell system, so one is the media direct and other is recovery. Also,how much will it let me shrink it? 

I would like around 50 gigs for vista and the rest for linux. 

[[img]http://xs231.xs.to/xs231/08395/vista_partitions246.jpg[/img]](http://xs.to)

---

### Post by davidryder on 2008-09-26
The space occupied on the drive is how far you can shrink it down. I would leave at least a 5gb buffer though; 10-15 if you can spare it.

---

### Post by Morty007 on 2008-09-26
> **davidryder said:**
> The space occupied on the drive is how far you can shrink it down. I would leave at least a 5gb buffer though; 10-15 if you can spare it.

I'm sorry, that doesn't make sense to me. I only have 22 gigs used. (Just bought this and haven't installed anything other than firefox.) Your saying I can only shrink it by 22?

---

### Post by davidryder on 2008-09-26
> **Morty007 said:**
> I'm sorry, that doesn't make sense to me. I only have 22 gigs used. (Just bought this and haven't installed anything other than firefox.) Your saying I can only shrink it by 22?

No I mean if your drive is occupying 22gb you can shrink it all the way down to 22gb.

---

### Post by gettinoriginal on 2008-09-26
According to your specs, you have a 250 GB HD, so you can leave 50 or 60 for Vista, and allocate the rest to Ubuntu :)

---

### Post by Morty007 on 2008-09-26
Ah, ok. Thanks David and getinoriginal:guitar:

I plan on installing tomorrow and hopefully all will go well. I have my supergrubdisk, windows dvd, and easy bsd all ready to go just in case. I'll bump this thread if I need help, Thanks!

---

### Post by Morty007 on 2008-09-30
Ok, I was about to shrink my partition but I see it can only shrink it by 11225 megabytes. That's how many gigs? I want vista to have around 50 gigs, the rest for linux.

 The number doesn't seem right. I've installed no major programs on vista, this is a new laptop. 

[[img]http://xs231.xs.to/xs231/08402/space_shrink884.jpg[/img]](http://xs.to)

---

### Post by snowpine on 2008-09-30
I guess the question is, when I installed dual boot on my XP computer, the Ubuntu installer shrank the partition no problem. But I have read this is not a good idea with Vista; you should shrink the Vista partition from within Vista. What is different about Vista vs. XP partitions?

---

### Post by caljohnsmith on 2008-09-30
> **snowpine said:**
> I guess the question is, when I installed dual boot on my XP computer, the Ubuntu installer shrank the partition no problem. But I have read this is not a good idea with Vista; you should shrink the Vista partition from within Vista. What is different about Vista vs. XP partitions?
Microsoft (in their infinite wisdom :rolleyes:) designed Vista so that it maintains its own partition table outside of the main partition table in the HDD's MBR (Master Boot Record); practically speaking, that means that if you use anything but Vista to do your partitioning, then Vista can break and become unbootable. That's why it's safest to use the Vista Disk Management for any repartitioning instead of some other partition editor. :)

---

### Post by snowpine on 2008-09-30
> **caljohnsmith said:**
> Microsoft (in their infinite wisdom :rolleyes:) designed Vista so that it maintains its own partition table outside of the main partition table in the HDD's MBR (Master Boot Record); practically speaking, that means that if you use anything but Vista to do your partitioning, then Vista can break and become unbootable. That's why it's safest to use the Vista Disk Management for any repartitioning instead of some other partition editor. :)

Thank you, I knew there must be a good reason. :)

---

### Post by Morty007 on 2008-09-30
Ok, maybe my math is wrong but according to my last screenshot it can only shrink it by 11 Gigs.

Is that right??:confused:

---

### Post by issih on 2008-09-30
Most likely something to do with pagefiles or as it calls them snapshots (system restore I guess).

I'd try temporarily turning off or at least reducing the size of the pageing file and see how much you can shrink the drive then.

Alternatively you could shrink the drive by a few gig as is, then create a small partition (a few gig or so) and set the page file to live on that partition whilst you shrink the main partition down to a size you are happy with. You could then delete the little partition to leave plenty of free space for the ubuntu install

Hope that helps

---

### Post by Morty007 on 2008-09-30
Ok, I feel stuck now. I deleted all the system restore shots except for the last one, and it still gives me the same number. Maybe Puma can give his input on this.

---

### Post by caljohnsmith on 2008-09-30
Have you defragmented your Vista partition yet? Maybe that is the problem. I'm not sure how to defragment in Vista though, I only have direct experience in XP.

---

### Post by Morty007 on 2008-09-30
Yes I defragged, even though it said that it didn't need to. I will try again.

I also turned off system restore, and did a disk cleanup. (Even though this thing isn't a week old yet.)

---

### Post by Pumalite on 2008-09-30
Turn Vista PageFile to 0. Shrink the partition. Later return it to its original size

---

### Post by Morty007 on 2008-09-30
I put it to 0, rebooted and it still says I can only shrink it by 1125. I am defragging now and hoping that will change it.

---

### Post by Morty007 on 2008-09-30
No go. I'll try this:

Making Shrink Volume Work

To absolutely ensure that you can shrink the volume, you should disable as many of the system files as you can, at least temporarily. Here's the list of steps:

   1. Run the Disk Cleanup Wizard, making sure to remove the hibernation file and all restore points.
   2. Disable System Restore
   3. Disable the pagefile ( Open up System in Control Panel, then Advanced System Settings \ Advanced \ Performance \ Advanced \ Change \ No Paging File.
   4. In the same Advanced Settings, go to Startup and Recovery \ Settings and then change the Write debugging information drop-down to "None" to disable the kernel memory dump.
   5. Disable Hibernation mode in your power options \ advanced power options screen.
   6. Reboot the machine, and then delete your c:\pagefile.sys file, following these instructions if you are having issues.




Which I got from here [http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

---

### Post by Morty007 on 2008-09-30
Didn't work. Any other suggestions?

---

### Post by Pumalite on 2008-09-30
Take a look at these links:
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)

---

### Post by Morty007 on 2008-09-30
Puma, I like the apcmag tutorial and know it would work except for the fact that it won't give ubuntu alot of space. (Only 11 gigs in my case.)

What do I do then?

---

### Post by lukjad on 2008-09-30
1 Gig=1,024 Megs.
So if you want 60 Gigs:
60x1,024= 61,440 Megs.

EDIT: Sorry, I didn't realize there were several pages. Ignore me.

---

### Post by Morty007 on 2008-09-30
I'm in gparted now. Why not just resize it like so?

[[img]http://xs231.xs.to/xs231/08402/screenshot325.png[/img]](http://xs.to)

---

### Post by Pumalite on 2008-09-30
It will probably break your Vista, but as far as I'm concerned; you should get rid of Vista and install Ubuntu, but that's I.

---

### Post by Morty007 on 2008-09-30
Ok so there is no clear answer since vista won't let me resize it to the way I want. I guess I'll try it and then try to make more space somehow.


Edit- I don't understand why it would break it. As you can see I'm leaving the beginning of the drive alone, just splitting it in the middle.

---

### Post by caljohnsmith on 2008-09-30
Did you happen to read post #12? If you use gparted to repartition your HDD, it changes the HDD's partition table in the MBR (Master Boot Record), but gparted doesn't know anything about the partition table that Vista keeps for itself; thus changing the partitions without doing it in Vista will confuse Vista the next time you boot it, since Vista's partition table will not agree with the main one in the MBR. 

You can probably get away with using gparted to resize Vista, but then you'll have to use a Vista Recovery/Install CD afterwards to rebuild Vista's "BCD" or Boot Configuration Data as they call it in Vista, which is where the partition table info is. You can do that from the Vista CD with:
```
bootrec /rebuildbcd
```

---

### Post by Morty007 on 2008-09-30
Thanks for that bit of info caljohnsmith.

I have the vista install dvd, along with super grub disk, system rescue cd, bcd, etc. 

I think I will resize in gparted, install ubuntu, and then restart with vista dvd and then repair.

But with all this info I may have to just sleep on it.

---

### Post by davidryder on 2008-09-30
> **Morty007 said:**
> Ok so there is no clear answer since vista won't let me resize it to the way I want. I guess I'll try it and then try to make more space somehow.


Edit- I don't understand why it would break it. As you can see I'm leaving the beginning of the drive alone, just splitting it in the middle.

Using GParted is how all the tutorials I read about resizing Vista said and that's how I did it. I left about a 20gb buffer for Vista though. 

If it's a new laptop and you have all your data backed up I wouldn't worry too much about it IMO.

---

### Post by Morty007 on 2008-09-30
So when you did it with gparted it did NOT break vista?

---

### Post by davidryder on 2008-09-30
> **Morty007 said:**
> So when you did it with gparted it did NOT break vista?

No, it didn't break my Vista. When I booted it asked to check my HDD and I said yes and it booted fine.

---

### Post by Morty007 on 2008-10-01
Great news!

I decided not to use the vista shrink method (because it would only shrink it by 11 gigs.) and instead loaded up gparted, did my partitioning, have windows fix the boot, and then loaded mint on there and had it use the largest continuous space.

Everything is great. 


The vista method is useless in my case...just like their operating system. Gparted did exactly what I told it to do, so I recommend others stay away from the vista shrink method and do what I did.

---

### Post by davidryder on 2008-10-02
Good to hear!

---

### Post by Mark Phelps on 2008-10-02
Did all these "tutorials" you read also include detail instructions as to how to repair the Vista installation after the GParted SW corrupted it?

Problem with using GParted (or SystemRescueCD or SuperGrubDisk) is that, although they often work OK, sometimes they do NOT.  Plus, you only find out about that when you then attempt to boot back into Vista and you can't.

At that point, without a Vista DVD (which system providers generally do NOT supply), you have no way of repairing the Vista install so it can be used.

So, IMHO, unless you have a way of backing up and restoring your Vista image, I would strongly recommend AGAINST using Linux-based utilities to shrink Vista partitions.

---

### Post by davidryder on 2008-10-02
> **Mark Phelps said:**
> Did all these "tutorials" you read also include detail instructions as to how to repair the Vista installation after the GParted SW corrupted it?

Problem with using GParted (or SystemRescueCD or SuperGrubDisk) is that, although they often work OK, sometimes they do NOT.  Plus, you only find out about that when you then attempt to boot back into Vista and you can't.

At that point, without a Vista DVD (which system providers generally do NOT supply), you have no way of repairing the Vista install so it can be used.

So, IMHO, unless you have a way of backing up and restoring your Vista image, I would strongly recommend AGAINST using Linux-based utilities to shrink Vista partitions.

Just curious, where are getting your info from? I mean about gparted ruining Vista partitions.

---

### Post by caljohnsmith on 2008-10-02
> **Mark Phelps said:**
> Did all these "tutorials" you read also include detail instructions as to how to repair the Vista installation after the GParted SW corrupted it?

Problem with using GParted (or SystemRescueCD or SuperGrubDisk) is that, although they often work OK, sometimes they do NOT.  Plus, you only find out about that when you then attempt to boot back into Vista and you can't.

At that point, without a Vista DVD (which system providers generally do NOT supply), you have no way of repairing the Vista install so it can be used.

So, IMHO, unless you have a way of backing up and restoring your Vista image, I would strongly recommend AGAINST using Linux-based utilities to shrink Vista partitions.
True, but Morty007 (the OP) was having problems getting Vista to shrink his Vista partition enough; Vista's Disk Management would only let him shrink Vista by at most 11 GB, and he wanted more than that. If you happen to know why he had that problem, please share it so we can learn. But otherwise he really didn't have much choice but to try some other partition editor. Also, even though many Vista computers don't come with a Vista Install/Recovery CD/DVD, you can download a copy of the Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). So in general I totally agree with you that it is better to use Vista to do any partition changing, but in Morty007's case he didn't have much other choice than to try something else. :)

---

### Post by speeddemon8803 on 2008-10-02
> **caljohnsmith said:**
> True, but Morty007 (the OP) was having problems getting Vista to shrink his Vista partition enough; Vista's Disk Management would only let him shrink Vista by at most 11 GB, and he wanted more than that. If you happen to know why he had that problem, please share it so we can learn. But otherwise he really didn't have much choice but to try some other partition editor. Also, even though many Vista computers don't come with a Vista Install/Recovery CD/DVD, you can download a copy of the Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). So in general I totally agree with you that it is better to use Vista to do any partition changing, but in Morty007's case he didn't have much other choice than to try something else. :)

Would you happen to know the 32 bit version of that software?

---

### Post by caljohnsmith on 2008-10-02
> **speeddemon8803 said:**
> Would you happen to know the 32 bit version of that software?
Same web page as I linked to, just click the "Windows Vista Recovery Disc x86 Edition" instead of the "Windows Vista Recovery Disc x64 Edition". :)

---

### Post by tangibleorange on 2008-10-02
> **Morty007 said:**
> Ok, I was about to shrink my partition but I see it can only shrink it by 11225 megabytes. That's how many gigs? I want vista to have around 50 gigs, the rest for linux.

 The number doesn't seem right. I've installed no major programs on vista, this is a new laptop. 

[[img]http://xs231.xs.to/xs231/08402/space_shrink884.jpg[/img]](http://xs.to)

there's going to be a problem there in that you have 4 primary partitions. you will need to move one of them inside an "extended" partition because you're only allowed 4 primary partitions. apart from your 250 GB vista one, what are 3 other partitions. i see one is labelled recovery - do you know what the other 2 are?

in response to the question, it might be because you need to defrag the drive before shrinking it. NTFS dumps files all over the disk and so you can only resize by a certain amount. try defragging and see if the shrink space increases.

---

### Post by jerome1232 on 2008-10-02
edit: I was beaten to it


Looking at your screenshot your going to have a second problem if you do get the partition to shrink.

You already have 4 primary partitions sda1,sda2,sda3,sda4 (the extended area counts as one primary partition)

---

### Post by Morty007 on 2008-10-02
I just installed Mint and this is how my partitions are set up. When installing I simply clicked on the "guided-user largest continuous space". 

Dual boot works great.I defragged vista but it just wouldn't let me shrink the sucker. Gparted did it just fine. 


[[img]http://xs232.xs.to/xs232/08404/screenshot--dev-sda_-_gparted-1898.png[/img]](http://xs.to)

---

### Post by tangibleorange on 2008-10-03
if it works - great! when i resized my vista partition with gparted, it wouldn't boot afterwards... ended up getting rid of it.

best thing i ever did :popcorn:

---

### Post by Mark Phelps on 2008-10-04
Bunch of replies:

davidryder: From post after post in this forum and others where folks repeatedly mention being unable to boot their Vista OS after resizing it with Gparted or some other non-MS utility.  For an example, look at the post directly above from tangibleorange where he said "when i resized my vista partition with gparted, it wouldn't boot afterwards."  Yeah, he's happy about that -- but a lot of other folks who did NOT want their Vista system to fail, are not happy.

caljohnsmith:  I'm not opposed to folks using non-MS utilities, in fact, I'm disgusted that MS provides a feature that all too often, does not work.  But, at least it does no damage in the process. I'm a Mod on a Vista support board, and given how we're swamped with dealing with "legitimate" Vista problems, that last thing we need is hordes of folks running to our forum whining about how "Vista sucks" (not that it doesn't) because now, it won't even boot -- and all because they uses a non-MS utility to "shrink" their OS partition.

Morty007: you lucked out -- sometimes it works with no problems.  Good to hear it worked for you!

tangibleorange: Sorry to hear about that, but I think you'll be happier NOT having Vista to deal with.

to all: If Vista shrink is not reducing the partition enough, turn off hibernation (which is turned ON by default even though it usually does NOT work!) and remove the hibernation file.  This takes as much space as your memory or more.  Then try shrink again.  It should let you shrink the partition a lot more.

---

### Post by davidryder on 2008-10-04
> **Mark Phelps said:**
> Bunch of replies:

davidryder: From post after post in this forum and others where folks repeatedly mention being unable to boot their Vista OS after resizing it with Gparted or some other non-MS utility.  For an example, look at the post directly above from tangibleorange where he said "when i resized my vista partition with gparted, it wouldn't boot afterwards."  Yeah, he's happy about that -- but a lot of other folks who did NOT want their Vista system to fail, are not happy.



Fair enough. I don't doubt it's a legitimate problem, I just have never had any experience with it and didn't read anything about it before I did it myself. 

In fact, I didn't even know there was a utility in Vista to do that... I was a *little* skeptical about gparted but I had everything backed up and on network drives and I really didn't care if I lost Vista.

---

### Post by tangibleorange on 2008-10-04
> **Mark Phelps said:**
> Bunch of replies:

davidryder: From post after post in this forum and others where folks repeatedly mention being unable to boot their Vista OS after resizing it with Gparted or some other non-MS utility.  For an example, look at the post directly above from tangibleorange where he said "when i resized my vista partition with gparted, it wouldn't boot afterwards."  Yeah, he's happy about that -- but a lot of other folks who did NOT want their Vista system to fail, are not happy.

caljohnsmith:  I'm not opposed to folks using non-MS utilities, in fact, I'm disgusted that MS provides a feature that all too often, does not work.  But, at least it does no damage in the process. I'm a Mod on a Vista support board, and given how we're swamped with dealing with "legitimate" Vista problems, that last thing we need is hordes of folks running to our forum whining about how "Vista sucks" (not that it doesn't) because now, it won't even boot -- and all because they uses a non-MS utility to "shrink" their OS partition.

Morty007: you lucked out -- sometimes it works with no problems.  Good to hear it worked for you!

tangibleorange: Sorry to hear about that, but I think you'll be happier NOT having Vista to deal with.

to all: If Vista shrink is not reducing the partition enough, turn off hibernation (which is turned ON by default even though it usually does NOT work!) and remove the hibernation file.  This takes as much space as your memory or more.  Then try shrink again.  It should let you shrink the partition a lot more.

i think gparted should offer some kind of warning if it detects you are trying to resize a vista partition. i've resized XP partitions with no bother before, so i dont see why vista kicks up such a stink about it...

---

### Post by Mark Phelps on 2008-10-04
> **tangibleorange said:**
> i think gparted should offer some kind of warning if it detects you are trying to resize a vista partition. i've resized XP partitions with no bother before, so i dont see why vista kicks up such a stink about it...

There are a couple of reasons why Vista is so much of a problem with regard to resizing.  First, I've read that Vista handles MFT management different than did XP, such that some info is stored in a new way.  When a utility unaware of this changes the partition size, it runs the risk of corrupting the MFT.

Second, there are conflicting stories around about Vista being a different version of NTFS than XP, something to do with merging some of the features of the not-released-yet Windows File System into a "new", extended NTFS type of partition.  As with the MFT management, since MS designed the "new" NTFS, it also knows how to program utilities to take those features into account.

So, until folks outside MS are able to reverse-engineer the changes in Vista NTFS and MFT management, there will always be the risk that file system corruption can happen.

On the bright side, it has been reported that in every case, when repaired by booting from a Vista DVD, was able to be fixed -- problem is that when you buy a machine preloaded with Vista, you do not get a Vista DVD.  So if you try resizing with Gparted and it fails -- you're hosed!

---

### Post by tangibleorange on 2008-10-04
> **Mark Phelps said:**
> There are a couple of reasons why Vista is so much of a problem with regard to resizing.  First, I've read that Vista handles MFT management different than did XP, such that some info is stored in a new way.  When a utility unaware of this changes the partition size, it runs the risk of corrupting the MFT.

Second, there are conflicting stories around about Vista being a different version of NTFS than XP, something to do with merging some of the features of the not-released-yet Windows File System into a "new", extended NTFS type of partition.  As with the MFT management, since MS designed the "new" NTFS, it also knows how to program utilities to take those features into account.

So, until folks outside MS are able to reverse-engineer the changes in Vista NTFS and MFT management, there will always be the risk that file system corruption can happen.

On the bright side, it has been reported that in every case, when repaired by booting from a Vista DVD, was able to be fixed -- problem is that when you buy a machine preloaded with Vista, you do not get a Vista DVD.  So if you try resizing with Gparted and it fails -- you're hosed!

very useful info. thanks! yep i really object to manufacturers putting "recovery" partitions because they are too cheap to give you a CD. the whole point of a CD is you can access it no matter what the state of your hard disk. if you haven't got a bootloader, or have corrupted any partitions, you're borked! argh!

---

