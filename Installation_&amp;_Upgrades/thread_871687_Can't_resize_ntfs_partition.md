---
title: "Can't resize ntfs partition"
date: 2008-07-27
forum: Installation &amp; Upgrades
---

### Post by WunderSlug on 2008-07-27
Alright...I'm going buggy...I'm trying to install ubuntu on my in-laws Dell Inspiron 640m and I can't resize the ntfs partion.  I wanna dual boot xp and ubuntu and I've gotten rid of the two useless dell partitons but i can't resize the ntfs.  I did this exact same process on my dell desktop.  worked like a charm.  any ideas?****

---

### Post by Pumalite on 2008-07-27
Get Gparted Live CD to work with unmounted drives/partitions.
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.

---

### Post by Jozza The Wick on 2008-07-27
It may also be that there are bad sectors on your HD. If you find that GParted Live CD doesn't let you resize the unmounted partitions without giving you a clear reason why, that may be your problem.

If that's the case, you'll have to try installing via the Alternate (text based) CD, breaking out of the install process to start a shell, shrinking the ntfs filesystem with ntfsresize (using the force resize option - back everything up first!!), then deleting and recreating the ntfs partition (which if you do properly preserves the data). Then finally you can continue on with the install process...

Let's hope it doesn't come to that, though! :) Let me know if you need any help -I managed it, and I'm no expert...

---

### Post by vanadium on 2008-07-27
Yet another advice: defragment de disk under Windows, then make sure Windows is properly shut down before attempting the resize with gparted.

---

### Post by WunderSlug on 2008-07-28
Ugh...Sorry, my brains fried...my wife is in labor at the moment, so I'll keep this quick...She has a hours to go, so don't think I'm a bad husband.  I tried gparted, and I can't resize through that.  Checked the disk for bad sectors, the drive is fine.  I DEFINITELY don't know enough about linux to do a text based installer.  So is there another way to resize the ntfs partition, thourgh windows or dos maybe?  I'm a dos whiz, so thats preffered.  Thanks folks...Will check in a few days from now after the kid is born...

Thanks again.

---

### Post by WunderSlug on 2008-07-28
Hang on, you said unmounted partition.  What do you mean by unmounted?  Does the ntfs partition having a boot flag have anything to do with it?

By the way, The guided option in Ubuntu and the manual option both come back with the same error, just in case that matters.

Thanks AGAIN.

---

### Post by faizoro on 2008-12-08
I had the same problem and google searching lead me to this conversation thread you have been having on the subject.  I found help no-where, but a guess worked out for me after tried many many other things which failed.

I had successfully resized ntfs partitions on this very computer in the past.  The only difference between those times and this one was that recently I decided to put a password on my windows account to keep my eight year old off of the computer without permission.  

I changed the password to nothing (removed the value in the pw box) which got it auto-loging in again with no ntfs protections.  I booted in to Ubuntu- tried resizing and (to my credit I guessed this would happen- but I wanted to do it in this order to put a fine point on what I was learning with my experiment) had no luck resizing the partition even now.  

I then booted fully into windows again and booted fully and gracefully back down (the ntfs pw removal routine doesn't apparently complete until a full boot-in, so re-booting into ubuntu emediately after making the change wasn't enough to sove the problem.  I had to boot in to windows one more time).  Then I resized my ntfs partition w gparted and had no trouble what-soever.

Hope the same works for you.  Good luck!!  Let me know if it works by the way - I'm just curious (this forum may email me anyway but just in case: [email]faizoro@gmail.com[/email])

---

### Post by psusi on 2008-12-08
Run a chkdsk and defrag in windows.

---

### Post by hawkhock on 2008-12-14
> **psusi said:**
> Run a chkdsk and defrag in windows.

Basically the same problem - can't partition NTFS.  I've run both chkdsk, chkdsk /r and also defragged after aborted attempt at installing Ubuntu 8.10.  Received error message: resize operation failure.  Win XP hard drive uses NTFS.  Before I try again:

Read in another post that Ubuntu can't use NTFS for its file system, it needs ext3 or some other Linux file system.  If I use the GParted Live CD, will I be able to partition the hard drive to use NTFS for the Windows portion and ext3 for the Ubuntu portion?

Am computer beginner, newbie to Ubuntu and would appreciate very specific instructions on how to do the partitioning.
Sr. Citizen in UT

---

### Post by tommcd on 2008-12-15
> **hawkhock said:**
> 
Read in another post that Ubuntu can't use NTFS for its file system, it needs ext3 or some other Linux file system.  If I use the GParted Live CD, will I be able to partition the hard drive to use NTFS for the Windows portion and ext3 for the Ubuntu portion?


Yes, gparted *should* allow you to shrink the Windows ntfs partition to free up some space to install Ubuntu onto. You can then use the Ubuntu install CD to install Ubuntu onto the newly allocated free space.

---

### Post by Mark Phelps on 2008-12-15
IMPORTANT -- if the NTFS partition is holding Vista, be aware that changing the size with any Linux utility runs the risk of "breaking" the partition.  That's because MS does some wierd stuff with their NTFS partitions that the Linux utilities don't handle.  

If you have a Vista DVD or Vista Recovery CD, you will be able to boot using the CD/DVD and run Startup Repair to get Vista to boot again.  If you don't have either, you run a major risk of having Vista "broken" and not being able to boot into Vista again.

---

### Post by psusi on 2008-12-15
> **Mark Phelps said:**
> IMPORTANT -- if the NTFS partition is holding Vista, be aware that changing the size with any Linux utility runs the risk of "breaking" the partition.  That's because MS does some wierd stuff with their NTFS partitions that the Linux utilities don't handle.  

If you have a Vista DVD or Vista Recovery CD, you will be able to boot using the CD/DVD and run Startup Repair to get Vista to boot again.  If you don't have either, you run a major risk of having Vista "broken" and not being able to boot into Vista again.

I think you're a little out of date there.  Quoting the linux-ntfs.org web site:

> [2007-09-29 07:55] The long awaited 2.0.0 release is finally here! Highlights are that ntfsmount sports full read/write support, libntfs can read encrypted files and ntfsresize as well as all other tools support Windows Vista. Upgrade is strongly recommended

---

### Post by Mark Phelps on 2008-12-16
Linux, has been able to read and write, and resize, plain old NTFS partitions for some time.  It's when it tries to resize a Vista OS partition that folks get into trouble.

If what you posted was as true as you seem to think it is, we wouldn't have seen posts from people in 2008 whose Vista machines became suddenly unbootable because they used Linux utilities to shrink their Vista partitions.

So, I'll continue to post my warnings until I get proof (not some program notes) clearly stating that the problem no longer exists.

---

### Post by Pumalite on 2008-12-16
The OP seemed to be talking of XP; and this can be shrunk with Gparted Live CD. Another thing that helps is reduce PageFile to=0 (and later back to its normal size)

---

### Post by psusi on 2008-12-16
> **Mark Phelps said:**
> Linux, has been able to read and write, and resize, plain old NTFS partitions for some time.  It's when it tries to resize a Vista OS partition that folks get into trouble.

If what you posted was as true as you seem to think it is, we wouldn't have seen posts from people in 2008 whose Vista machines became suddenly unbootable because they used Linux utilities to shrink their Vista partitions.

So, I'll continue to post my warnings until I get proof (not some program notes) clearly stating that the problem no longer exists.

If the programmers saying they found and fixed the problem isn't proof, then I don't know what is.  I would also venture to guess that a large number of Ubuntu users have managed to resize their vista partitions just fine since the forums are not flooded with people complaining.

If it happens to one person out of 10,000 that's no reason to scare everyone else off.  Of course you should always have backups of your important data.

---

### Post by Mark Phelps on 2008-12-16
psusi:

Why you trying to turn this into a debate??  I'm not telling people it won't work -- because, sometimes, it does.  I'm only telling people that if it fails (and sometimes, it does!) and they do NOT have recovery media available for Vista, they run the risk of permanently damaging their Vista installation.

If presenting people a warning about possible permanent damage to their machine is "scaring them off", then they shouldn't be messing around with dual-boot scenarios in the first place!

As to the proof "debate", evidently you don't know what proof is.  It's not what someone says; it's what happens in the real world. I've been doing this work for decades -- on lots of different platforms.  If I had a dollar for every time someone claimed what a product WOULD do was different from what it actually DID do, I could have retired long ago.

I've not actually had my Vista partition corrupt on me because I'm not foolish enough to use a non-MS utility on it.  But I've read post after post, and some of them in this forum, about people who had.  

So, what do YOU think is more likely to be "proof"?  That these "developers" tested their code on every possible combination of Vista-and-other-OSs machines to confirm that it could NOT possibly corrupt the Vista NTFS file system under any conditions?  Or that other people, having used GParted to shrink their Vista partitions, simply invented false stories about Vista not booting anymore? Or that, in fact, in SOME situations, GParted really DOES corrupt Vista NTFS partitions -- as reported first-hand by the unfortunate  folks that had it happen to them?

As for me, I choose the third as the most likely "proof".

I'm not continuing what your pressing into a childish debate -- problems happen, and folks have a right to know what risks they're taking BEFORE they do something that could permanently damage their machines.

---

### Post by mrbiggbrain on 2008-12-16
ok let me see if i can explain to my understanding why gparted 
complains

- = empty
# = used

empty drive: 10GB
|----------|

Used drive: 10gb (3,3,2) with empty space = 2gb

|###-###-##|

now try making a 2gb partition with he rest of the space, go ahead, i dare you!

gparted is going to complaine.

now lets look at two gigs of that drive in 100mb chuncks.

|-###-#-###-#-------#|

now this is a common drive, there are areas of data and areas of not data, this is GOOD becuse the system can read data along the whole disk, not just part of it.

but try and resize this partiton to 1G, theres only 900mb of data, and yet it wont do it, becuse some of the space where the new partition would be created cant be allocated becuse its taken.

now defragging might give you the following

|-####--###-##-------|

but that still cant be configured into 2 1G drives, it could be configured into 1 512mb drive, and one 1.5gb drive, but the data cant be overwirrten, 

its like trying to make a lane on a highway go the other way, well there are cars on it, the other cars cant start, till the origional ones are gone.

at least thats why i get it, iv got the error a few times in my days, mostly defrag, fix disk errors, clean cache, turnoff virtual ram / pageing files, and clean out old vista/xp battery became low saved session to ram backups (those can reak havock on partitioning)

as well when partitioning space, set up a swap partiton, they are better then pageing files, it will be linux swap partiton, i usualy set about 2gb to it, i douno how much you actualy are suppose to have

---

### Post by psusi on 2008-12-16
> **Mark Phelps said:**
> psusi:

Why you trying to turn this into a debate??  I'm not telling people it won't work -- because, sometimes, it does.  I'm only telling people that if it fails (and sometimes, it does!) and they do NOT have recovery media available for Vista, they run the risk of permanently damaging their Vista installation.

Because at least to me, it sounded more like you were saying "don't do it, it will trash your system!" than "something might go wrong, so make sure you have backups".

> **Mark Phelps said:**
> As to the proof "debate", evidently you don't know what proof is.  It's not what someone says; it's what happens in the real world. I've been doing this work for decades -- on lots of different platforms.  If I had a dollar for every time someone claimed what a product WOULD do was different from what it actually DID do, I could have retired long ago.

If there were a widespread problem, I would expect tons of threads complaining about it on the forums since a large number of people these days are migrating to Ubuntu from Vista.  Since there aren't, that seems a good indication that gparted is fairly reliable.  That coupled with the fact that it has been generally considered reliable for years before Vista ( I myself have never seen it cause a problem and would recommend it over partition magic, which I have seen destroy data several times ), and I have not heard of anything Vista changed with the NTFS format, it seems to me there is no evidence that there is a problem.

Just the same, I went looking for evidence of problems and the only thing I could find was that reference saying that they did find and fixed some sort of problem, which is why I mentioned it.

> **Mark Phelps said:**
> I've not actually had my Vista partition corrupt on me because I'm not foolish enough to use a non-MS utility on it.  But I've read post after post, and some of them in this forum, about people who had.

I haven't seen any such complaints and can't find any when I search either.  Maybe you can point some out?

> **Mark Phelps said:**
> 
So, what do YOU think is more likely to be "proof"?  That these "developers" tested their code on every possible combination of Vista-and-other-OSs machines to confirm that it could NOT possibly corrupt the Vista NTFS file system under any conditions?  Or that other people, having used GParted to shrink their Vista partitions, simply invented false stories about Vista not booting anymore? Or that, in fact, in SOME situations, GParted really DOES corrupt Vista NTFS partitions -- as reported first-hand by the unfortunate  folks that had it happen to them?

As I have said, the proof is in the lack of complaints that I see, combined with the one mention I found saying some sort of problem was found and fixed.  Am I saying it is flawless and there is no way it will mess up?  Of course not; I was just pointing out reasons for not taking a totally hostile view of the attempt.

> **Mark Phelps said:**
> 
As for me, I choose the third as the most likely "proof".

I'm not continuing what your pressing into a childish debate -- problems happen, and folks have a right to know what risks they're taking BEFORE they do something that could permanently damage their machines.

Sure, problems happen.  But from where I am sitting, there is no known deadly bug with (g)parted resizing NTFS partitions created by vista, so there is no need to cause panic.  Cautious optimism is the way to go.

---

